# Angular-nvD3

[![NPM Version](http://img.shields.io/npm/v/angular-nvd3.svg?style=flat)](https://www.npmjs.org/package/angular-nvd3)

Angular nvd3 charts is designed to make it easier to work with [nvd3.js](https://github.com/novus/nvd3) re-usable charting library. This directive allows you to easily customize your charts via JSON API.

The key feature is that the original hierarchical structure of nvd3 models is completely preserved in directive JSON structure. This means that while you creating a complex chart that containing multiple elementary chart models (such as `line`, `bar`, `axis`, ...), you can in turn customize the properties of each internal elementary models as well as the global charting properties the way you want. This can be done as usual, but it becomes quite easily to customize while applying JSON approach to.

Try it [online](http://pertrai1.github.io/angular-nvd3-charts/).

##### npm

    $ npm install angular-nvd3-charts

##### download

If you don't use bower or npm, you can manually download and unpack directive with the latest version ([zip](https://github.com/pertrai1/angular-nvd3-charts/archive/v1.0.8.zip), [tar.gz](https://github.com/pertrai1/angular-nvd3-charts/archive/v1.0.8.tar.gz)).

### Basic usage

Inject `nvd3` directive into angular module, set up some chart options and push some data to the controller:
```javascript
angular.module('myApp', ['nvd3'])
       .controller('myCtrl', function('$scope'){
           $scope.options = { /* JSON data */ };
           $scope.data = { /* JSON data */ }
        })
```

and in html again you can use it like:
```html
<div ng-app='myApp'>
    <div ng-controller='myCtrl'>
        <nvd3 options='options' data='data'></nvd3>
    </div>
</div>
```

The chart would be displayed on the page.

### Example

Let's create a simple **Discrete Bar Chart**.

Configure options:
```javascript
$scope.options = {
    chart: {
        type: 'discreteBarChart',
        height: 450,
        margin : {
            top: 20,
            right: 20,
            bottom: 60,
            left: 55
        },
        x: function(d){ return d.label; },
        y: function(d){ return d.value; },
        showValues: true,
        valueFormat: function(d){
            return d3.format(',.4f')(d);
        },
        transitionDuration: 500,
        xAxis: {
            axisLabel: 'X Axis'
        },
        yAxis: {
            axisLabel: 'Y Axis',
            axisLabelDistance: 30
        }
    }
};
```

Push some data:
```javascript
$scope.data = [{
    key: "Cumulative Return",
    values: [
        { "label" : "A" , "value" : -29.765957771107 },
        { "label" : "B" , "value" : 0 },
        { "label" : "C" , "value" : 32.807804682612 },
        { "label" : "D" , "value" : 196.45946739256 },
        { "label" : "E" , "value" : 0.19434030906893 },
        { "label" : "F" , "value" : -98.079782601442 },
        { "label" : "G" , "value" : -13.925743130903 },
        { "label" : "H" , "value" : -5.1387322875705 }
    ]
}];
```

See the [result](https://pertrai1.github.io/angular-nvd3-charts/#/discreteBarChart).

Read more [docs](https://pertrai1.github.io/angular-nvd3-charts/#/quickstart).

---

## License
Licensed under the terms of the [MIT License](https://github.com/pertrai1/angular-nvd3-charts/blob/master/LICENSE)
