---
title: "Rendering Javascript Charts in Elixir"
date: 2020-06-08T11:08:55-06:00
draft: true
tags: ["Elixir", "Phoenix", "Charts"]
---

If you're like me, you like to stay away from Javascript when writing your Elixir code.  That is why I was pleased to discover [chartkick-ex](https://github.com/buren/chartkick-ex) recently when I needed a chart solution for my Phoenix site. It makes embedding Javascript charts in to your Elixir templates a breeze. 

To install it, just add the following to your mix.exs file

<pre><code class='language-elixir'>[
...
{:chartkick, "~>0.4.0"},
{:poison, "~> 3.1"}
]
</code></pre>

Chartkick can use Google Charts, Chart.js, or Highcharts.  So you need to add one of the following to the `<head>` of your site

<pre><code class='language-javascript'><!--
-->{{< highlight html>}}<script src="//www.google.com/jsapi"></script>{{< /highlight >}}
//or
{{<highlight html>}}<script src="https://cdn.jsdelivr.net/npm/chart.js@2.9.3/dist/Chart.min.js"></script>{{</highlight>}}
//or
{{<highlight html >}}<script src="https://cdnjs.cloudflare.com/ajax/libs/highcharts/8.1.0/highcharts.min.js"></script>{{</highlight>}}
</code></pre>

Then, you can use Elixir in your template files to handle the rest.  

<pre><code class='language-elixir'><!--
--><% data = Poison.encode!([[175, 60], [190, 80], [180, 75]]) %>
<%= Chartkick.line_chart data %>
</code></pre>