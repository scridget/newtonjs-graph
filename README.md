# Newton Graph Prototype 

[![Build Status](https://travis-ci.org/julie-ng/architecture-graph-prototype.svg?branch=master)](https://travis-ci.org/julie-ng/architecture-graph-prototype)
[![Coverage Status](https://coveralls.io/repos/github/julie-ng/architecture-graph-prototype/badge.svg?branch=master)](https://coveralls.io/github/julie-ng/architecture-graph-prototype?branch=master)
[![Known Vulnerabilities](https://snyk.io/test/github/julie-ng/architecture-graph-prototype/badge.svg?targetFile=package.json)](https://snyk.io/test/github/julie-ng/architecture-graph-prototype?targetFile=package.json)
[![Maintainability](https://api.codeclimate.com/v1/badges/4f444f7b1046eb4aafda/maintainability)](https://codeclimate.com/github/julie-ng/architecture-graph-prototype/maintainability)

This repository contains learning and prototype code for a high-level dashboard for architects and stakeholders.

The goal is to illustrate *product and service dependencies* in a software architecture.

- [View API Documentation](https://julie-ng.github.io/architecture-graph-prototype/)

## Example Usage

### Network - Data Wrapper

A `Network` is essentially a data wrapper. Its biggest advantage is that it dynamically calculating links between nodes, based on a unique identifier `uid`, instead of array indexes.

The basic data format is as so:

```javascript
const nodes = [
	{ id: 1, name: 'foo' },
	{ id: 2, name: 'bar' }
]

const linksMap = [
	{ source: 1, target: 2 }
]

const network = new Network(nodes, linksMap, { uid: 'id' })
```

### Graph - Visualization

While `Network` handles the data, `Graph` handles the visualizations, including layout, animations, etc.


```javascript
const graph = new Graph({ 
	width: window.innerWidth 
})

graph.bind(network)
```

Note that `Graph` is **event-driven** means that it listens for events, e.g. `update` and updates the visualization automatically depending on the bound network data.

## Development

### Install dependencies

First install the dependencies required:

```
npm install
```

### Preview

To view the prototype in the browser, run

```
npm run server
```

which starts the webpack dev server and automatically opens [http://localhost:9000](http://localhost:9000) in a browser window.