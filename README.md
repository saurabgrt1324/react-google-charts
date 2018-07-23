# React Google Charts

[![CircleCI](https://circleci.com/gh/rakannimer/react-google-charts.svg?style=shield)](https://circleci.com/gh/RakanNimer/react-google-charts)

[![NPM](https://nodei.co/npm/react-google-charts.png?downloads=true&downloadRank=true)](https://npmjs.org/package/react-google-charts)

A thin, typed, React wrapper over Google Charts Visualization and Charts API.

- [React Google Charts](#react-google-charts)
  - [Installation](#installation)
  - [Quick Start](#quick-start)
  - [Quick Walkthrough](#quick-walkthrough)
    - [Initialize from data array :](#initialize-from-data-array)
    - [Initialize using rows and columns :](#initialize-using-rows-and-columns)
    - [Listen to chart events](#listen-to-chart-events)
  - [Examples](#examples)
    - [Area Chart](#area-chart)
    - [Bar Chart](#bar-chart)
    - [Bubble Chart](#bubble-chart)
    - [Calendar Chart](#calendar-chart)
    - [Candlestick Chart](#candlestick-chart)
    - [Column Chart](#column-chart)
    - [Donut Chart](#donut-chart)
    - [Gantt Chart](#gantt-chart)
    - [Gauge Chart](#gauge-chart)
    - [Geo Chart](#geo-chart)
    - [Histogram Chart](#histogram-chart)
    - [Line Chart](#line-chart)
    - [Sankey Chart](#sankey-chart)
    - [Scatter Chart](#scatter-chart)
    - [Stepped Area Chart](#stepped-area-chart)
    - [Table Chart](#table-chart)
    - [Timeline Chart](#timeline-chart)
    - [Treemap Chart](#treemap-chart)
    - [Waterfall Chart](#waterfall-chart)
    - [Wordtree Chart](#wordtree-chart)
    - [Run the example app](#run-the-example-app)
  - [Contributing](#contributing)

## Installation

With your favorite package manager (yarn, pnpm or npm) :

```
yarn add react-google-charts
# or
npm i -s react-google-charts
```

## Quick Start

```javascript
import React from "react";
import { render } from "react-dom";
import { Chart } from "react-google-charts";

export default class App extends React.Component {
  render() {
    return (
      <div className={"my-pretty-chart-container"}>
        <Chart
          chartType="ScatterChart"
          data={[["Age", "Weight"], [4, 5.5], [8, 12]]}
          width="100%"
          height="400px"
          legendToggle
        />
      </div>
    );
  }
}
render(<App />, document.querySelector("#app"));
```

## Quick Walkthrough

### Initialize from data array :

```javascript
import { Chart } from "react-google-charts";
import React from "react";

class ExampleChart extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      options: {
        title: "Age vs. Weight comparison",
        hAxis: { title: "Age", minValue: 0, maxValue: 15 },
        vAxis: { title: "Weight", minValue: 0, maxValue: 15 },
        legend: "none"
      },
      data: [
        ["Age", "Weight"],
        [8, 12],
        [4, 5.5],
        [11, 14],
        [4, 5],
        [3, 3.5],
        [6.5, 7]
      ]
    };
  }
  render() {
    return (
      <Chart
        chartType="ScatterChart"
        data={this.state.data}
        options={this.state.options}
        graphID="ScatterChart"
        width="100%"
        height="400px"
        legendToggle
      />
    );
  }
}
export default ExampleChart;
```

### Initialize using rows and columns :

```javascript
import * as React from "react";
import { Chart } from "react-google-charts";

const ExampleChart = () => {
  return (
    <Chart
      chartType="ScatterChart"
      rows={[[8, 12], [4, 5.5], [11, 14], [4, 5], [3, 3.5], [6.5, 7]]}
      columns={[
        {
          type: "number",
          label: "Age"
        },
        {
          type: "number",
          label: "Weight"
        }
      ]}
      options={{
        title: "Age vs. Weight comparison",
        hAxis: {
          title: "Age",
          viewWindow: { min: 0, max: 15 }
        },
        vAxis: { title: "Weight", viewWindow: { min: 0, max: 15 } },
        legend: "none"
      }}
      graphID="ScatterChart"
      width={"100%"}
      height={"400px"}
      legendToggle
    />
  );
};
export default ExampleChart;
```

### Listen to chart events

Set the chart-specific events you want to listen to and the corresponding callback.
The callback has the component as an argument.

```javascript
import React from "react";
import { Chart } from "react-google-charts";

class ExampleChart extends React.Component {
  constructor(props) {
    super(props);
    this.chartEvents = [
      {
        eventName: "select",
        callback(Chart) {
          // Returns Chart so you can access props and  the ChartWrapper object from chart.wrapper
          console.log("Selected ", Chart.chart.getSelection());
        }
      }
    ];
    this.state = {
      options: {
        title: "Age vs. Weight comparison",
        hAxis: { title: "Age", minValue: 0, maxValue: 15 },
        vAxis: { title: "Weight", minValue: 0, maxValue: 15 },
        legend: "none"
      },
      rows: [[8, 12], [4, 5.5], [11, 14], [4, 5], [3, 3.5], [6.5, 7]],
      columns: [
        {
          type: "number",
          label: "Age"
        },
        {
          type: "number",
          label: "Weight"
        }
      ]
    };
  }
  render() {
    return (
      <Chart
        chartType="ScatterChart"
        rows={this.state.rows}
        columns={this.state.columns}
        options={this.state.options}
        graphID="ScatterChart"
        width="100%"
        height="400px"
        chartEvents={this.chartEvents}
      />
    );
  }
}
export default ExampleChart;
```

## Examples

### Area Chart

- [Code](./sandboxes/area-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/area-chart)

### Bar Chart

- [Code](./sandboxes/bar-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/bar-chart)

### Bubble Chart

- [Code](./sandboxes/bubble-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/bubble-chart)

### Calendar Chart

- [Code](./sandboxes/calendar/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/calendar)

### Candlestick Chart

- [Code](./sandboxes/candlestick/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/candlestick)

### Column Chart

- [Code](./sandboxes/column-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/column-chart)

### Donut Chart

- [Code](./sandboxes/donut-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/donut-chart)

### Gantt Chart

- [Code](./sandboxes/gantt-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/gantt-chart)

### Gauge Chart

- [Code](./sandboxes/gauge/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/gauge)

### Geo Chart

- [Code](./sandboxes/geo-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/geo-chart)

### Histogram Chart

- [Code](./sandboxes/geo-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/geo-chart)

### Line Chart

- [Code](./sandboxes/linechart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/linechart)

### Sankey Chart

- [Code](./sandboxes/sankey/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/sankey)

### Scatter Chart

- [Code](./sandboxes/scatter-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/scatter-chart)

### Stepped Area Chart

- [Code](./sandboxes/stepped-area-chart/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/stepped-area-chart)

### Table Chart

- [Code](./sandboxes/table/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/table)

### Timeline Chart

- [Code](./sandboxes/timeline/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/timeline)

### Treemap Chart

- [Code](./sandboxes/treemap/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/treemap)

### Waterfall Chart

- [Code](./sandboxes/waterfall/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/waterfall)

### Wordtree Chart

- [Code](./sandboxes/wordtree/index.js)
- [Sandbox](https://codesandbox.io/s/github/rakannimer/react-google-charts/tree/master/sandboxes/wordtree)

### Run the example app

```bash
git clone https://www.github.com/rakannimer/react-google-charts
cd react-google-charts
npm i
npm start
```

## Contributing

Contributions are very welcome. Check out [CONTRIBUTING.md](CONTRIBUTING.md)
