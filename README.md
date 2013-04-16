## edge-ps

This is a PowerShell compiler for edge.js.

![ScreenShot](https://raw.github.com/dfinke/edge-ps/master/edge-ps.png)

## What you need

* Windows
* node.js 0.6.x or later (developed and tested with v0.6.20, v0.8.22, and v0.10.0, both x32 and x64 architectures)  
* [.NET 4.5](http://www.microsoft.com/en-us/download/details.aspx?id=30653)  
* PowerShell

## PowerShell Driving D3 Graph

![ScreenShot](https://raw.github.com/dfinke/edge-ps/master/d3Graph.png)

```javascript
var ps=edge.func('ps', function(){/*

$dataset = Get-Process |
			Sort handles -desc |
            Select -first 10 name, company, handles |
			ConvertTo-Json -Compress

@"
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Top 10 Process with most handles</title>
        <script type="text/javascript" src="js/d3.v3.js"></script>

        <link rel="stylesheet" type="text/css" href="css/chart.css" />

        <h2>Top 10 Process with most handles</h2>
        <span>Host: </span><span><b>$(hostname)</span>
    </head>

    <body>
        
        <script type="text/javascript">

            var dataset = $dataset;
      
            d3.select("body")
                .append("div")
                .attr("class","chart")
                .selectAll("div.line")
                .data(dataset)
                .enter()
                .append("div")
                  .attr("class","line")
            
            d3.selectAll("div.line")
                .append("div")
                .attr("class","label")
                .text(function(data) { return data.Name })

            d3.selectAll("div.line")
                .append("div")
                .attr("class","bar")
                .style("width", function(d){ return d.Handles/10 + "px" })
                .text(function(d){ return d.Handles });

        </script>
    
    </body>

</html>
"@

*/})
```

See [edge.js overview](http://tjanczuk.github.com/edge) and [edge.js on GitHub](https://github.com/tjanczuk/edge) for more information. 
