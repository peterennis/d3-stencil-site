---
id: api-types
title: Types
---

## Type Reference

<AUTOGENERATED_TABLE_OF_CONTENTS>

### `GraphData`

- Passed by props to the components.
- `GraphData` is the source of information.
- It will be merged with the default data.

```typescript
type GraphData<T = number[][]> = Partial<{
  pieChart: PieChart;
  barChart: BarChart;
  lineChart: LineChart;
  lineAnnotationsChart: LineAnnotationsChart;
  bcgMatrixChart: BcgMatrixChart;
  styles: Styles;
  colors: string[];
  labels: string[] | number[];
  data: Data<T>;
}>;
```

| Properties           | Description                                                                                                                                                                                                                   | Type                                                                                           |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| pieChart             | [Specific Chart Options](#specific-charts)                                                                                                                                                                                    | [PieChart](#piechart-docs-api-api-introduction-pie-chart)                                      |
| barChart             | [Specific Chart Options](#specific-charts)                                                                                                                                                                                    | [BarChart](#barchart-docs-api-api-introduction-horizontal-bar-chart)                           |
| lineChart            | [Specific Chart Options](#specific-charts)                                                                                                                                                                                    | [LineChart](#linechart-docs-api-api-introduction-line-chart)                                   |
| lineAnnotationsChart | [Specific Chart Options](#specific-charts)                                                                                                                                                                                    | [LineAnnotationsChart](#lineannotationschart-docs-api-api-introduction-line-annotations-chart) |
| bcgMatrixChart       | [Specific Chart Options](#specific-charts)                                                                                                                                                                                    | [BcgMatrixChart](#bcgmatrixchart-docs-api-api-introduction-bcg-matrix-chart)                   |
| styles               | [Options](#options)                                                                                                                                                                                                           | [Styles](#styles)                                                                              |
| colors               | It is an array of strings where each position will be associated which the same place in the data attribute.                                                                                                                  | `string[]`                                                                                     |
| labels               | It is an array of strings or numbers where each position will be associated which the same place in the data attribute. Each label will be formatted with the same format that you have typed in the specific charts options. | `string[]` or `number[]`                                                                       |
| data                 | Fill it with your data. The format will depend on each component.                                                                                                                                                             | _T = number[][] by default_                                                                    |

### `LegendData`

- Passed by props to the Legend Component.
- `LegendData` lets you the opportunity to customise a bit your Legend.

```typescript
type LegendData = Partial<{
  labels: string[];
  colors: string[];
  type: 'horizontal' | 'vertical'; // Ignore the highlighting
  styles: Styles;
}>;
```

| Properties | Description                                                                                                    | Type                       |
| ---------- | -------------------------------------------------------------------------------------------------------------- | -------------------------- |
| labels     | It is an array of strings where each position will be associated which the same place in the colors attribute. | string[]                   |
| colors     | It is an array of strings where each position will be associated which the same place in the labels attribute. | string[]                   |
| type       | It sets the position of your legend.                                                                           | 'horizontal' or 'vertical' |
| styles     | [Options](#options)                                                                                            | [Styles](#styles)          |

## Specific charts

#### [PieChart](/docs/api/api-introduction#pie-chart)

```typescript
type PieChart = Partial<{
  labelFormat: Formats;
  dataFormat: Formats;
  currency: string;
}>;
```

| Properties  | Description                                             | Type                                                                                   |
| ----------- | ------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| labelFormat | Defines the format you want to set to the labels.       | [Formats](#formats)                                                                    |
| dataFormat  | Defines the format you want to set to the data.         | [Formats](#formats)                                                                    |
| currency    | Defines the currency using the ISO 4217 currency codes. | string - [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217#Códigos_de_divisa_ISO_4217) |

#### [BarChart](/docs/api/api-introduction#horizontal-bar-chart)

```typescript
type BarChart = Partial<{
  axis: Axis;
  margin: Margin;
}>;
```

| Properties | Description         | Type              |
| ---------- | ------------------- | ----------------- |
| axis       | [Options](#options) | [Axis](#axis)     |
| margin     | [Options](#options) | [Margin](#margin) |

#### [LineChart](/docs/api/api-introduction#line-chart)

```typescript
type LineChart = Partial<{
  axis: Axis;
  margin: Margin;
}>;
```

| Properties | Description         | Type              |
| ---------- | ------------------- | ----------------- |
| axis       | [Options](#options) | [Axis](#axis)     |
| margin     | [Options](#options) | [Margin](#margin) |

#### [LineAnnotationsChart](/docs/api/api-introduction#line-annotations-chart)

```typescript
interface LineAnnotationsChart {
  increaseHeight: number;
  tickSeparation: string;
  annotations: number[][];
  imagePathOneAnnotation?: string;
  imagePathSomeAnnotations?: string;
}
```

| Properties               | Description                                                                                       | Type       |
| ------------------------ | ------------------------------------------------------------------------------------------------- | ---------- |
| increaseHeight           | Defines the pixels to increase the SVG content.                                                   | number     |
| tickSeparation           | Set `px, em, or rem` to move the positions of ticks.                                              | string     |
| annotations              | A bidimensional array where each position is related to the same position in the array of labels. | number[][] |
| imagePathOneAnnotation   | Optional path to set an alternative image for a single annotation.                                | string     |
| imagePathSomeAnnotations | Optional path to set an alternative image for more than one annotation.                           | string     |

#### [BcgMatrixChart](/docs/api/api-introduction#bcg-matrix-chart)

```typescript
type BcgMatrixChart = Partial<{
  axis: Axis;
  margin: Margin;
  value: Partial<{
    format: Formats;
    currency: string;
  }>;
  quadrants: boolean;
}>;
```

| Properties      | Description                                                                                                            | Type                                                                                   |
| --------------- | ---------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| axis            | [Options](#options)                                                                                                    | [Axis](#axis)                                                                          |
| margin          | [Options](#options)                                                                                                    | [Margin](#margin)                                                                      |
| value: format   | Defines how the [`rel_size`](#bcgmatrix) will be formatted.                                                            | [Formats](#formats)                                                                    |
| value: currency | Defines the currency using the ISO 4217 currency codes.                                                                | string - [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217#Códigos_de_divisa_ISO_4217) |
| quadrants       | Defines if the quadrants that divide the graph between a dog, question mark, star and cash cows will be visible or not | boolean                                                                                |

## Data Types

#### BCGMatrix

```typescript
type BcgMatrix = {
  x_data: number;
  y_data: number;
  rel_size: number;
  tooltipInfo?: string;
};
```

| Properties  | Description                                                                           | Type   |
| ----------- | ------------------------------------------------------------------------------------- | ------ |
| x_data      | Data related to the x-axis, commonly it is "Relative market share".                   | number |
| y_data      | Data related to the y-axis, commonly it is "Market growth rate".                      | number |
| rel_size    | Data related to the size of your bubbles, commonly it could be revenues, visits, etc. | number |
| tooltipInfo | Using a template string, you can define a custom tooltip style.                       | string |

## Formats

```typescript
type Formats =
  | 'PERCENTAGE'
  | 'GROUPED_TWO_DIGITS'
  | 'GROUPED_THOUSANDS_TWO_DIGITS'
  | 'CURRENCY'
  | 'DAY_AND_MONTH'
  | 'SHORT_MONTH'
  | 'LARGE_MONTH'
  | 'ANY';
```

| Key                          | Input                              | Output                                                                                                                     |
| ---------------------------- | ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| PERCENTAGE                   | 0.123                              | 12%                                                                                                                        |
| GROUPED_TWO_DIGITS           | 42e6                               | 42M                                                                                                                        |
| GROUPED_THOUSANDS_TWO_DIGITS | 4223                               | 4,200                                                                                                                      |
| CURRENCY                     | 500                                | 500 € - [Intl.NumberFormat](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/NumberFormat) |
| DAY_AND_MONTH                | 1549750682<br/> _(Unix Timestamp)_ | Feb 09                                                                                                                     |
| SHORT_MONTH                  | 1549750682<br/> _(Unix Timestamp)_ | Feb                                                                                                                        |
| LARGE_MONTH                  | 1549750682<br/> _(Unix Timestamp)_ | February                                                                                                                   |
| ANY                          | >=65                               | >=65                                                                                                                       |

## Options

#### Styles

```typescript
type Styles = Partial<{
  width: string;
  height: string;
  margin: string;
  padding: string;
}>;
```

| Properties | Description            | Type   |
| ---------- | ---------------------- | ------ |
| width      | The width of the SVG   | string |
| height     | The height of the SVG  | string |
| margin     | The margin of the SVG  | string |
| padding    | The padding of the SVG | string |

#### Margin

```typescript
type Margin = Partial<{
  top: number;
  right: number;
  bottom: number;
  left: number;
}>;
```

| Properties | Description                                  | Type   |
| ---------- | -------------------------------------------- | ------ |
| top        | The top margin concerning the SVG content    | number |
| right      | The right margin concerning the SVG content  | number |
| bottom     | The bottom margin concerning the SVG content | number |
| left       | The left margin concerning the SVG content   | number |

#### Axis

```typescript
type Axis = Partial<{
  x: Partial<{
    visible: boolean;
    gridVisible: boolean;
    format: Formats;
    label: string;
    currency: string;
  }>;
  y: Partial<{
    visible: boolean;
    gridVisible: boolean;
    format: Formats;
    label: string;
    currency: string;
  }>;
}>;
```

| Properties  | Description                                                           | Type                                                                                   |
| ----------- | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| visible     | Defines if the axis will be displayed                                 | boolean                                                                                |
| gridVisible | Defines if the axis will be displayed                                 | boolean                                                                                |
| format      | Defines the format of your labels, and be used in the tooltip as well | [Format](#formats)                                                                     |
| label       | Defines a label to the axis                                           | string                                                                                 |
| currency    | Defines the currency using the ISO 4217 currency codes                | string - [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217#Códigos_de_divisa_ISO_4217) |
