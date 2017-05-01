---
title: "Depth First Search"
layout: post
date: 2017-04-30 22:44
image: /assets/images/Boxing.jpg
headerImage: false
tag:
- graph theory
- algorithms
star: true
category: blog
author: Stylianos Kalamaras
description: Depth First Search explained with pseudocode.
---

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/1/1f/Depth-first-tree.svg">
</p>

## What is Depth First Search?

Depth first search is an algorithm which traverses a tree or graph. This algorithm searches each branch to maximum depth until there are no unvisited nodes, then backtracks until every node is searched. This runs on O(\|V\|+\|E\|) for full a full traversal.


## Visual Representation for DFS of an Undirected Graph


<video width="640" height="480" autoplay>
  <source src="/assets/images/DFS_Traversal.mov" type="video/mp4">
Your browser does not support the video tag.
</video>


### Pseudocode of the DFS Algorithm

DFS (G)
    <br>1. &emsp;for each vertex _u_ in G.V &emsp;&emsp;&emsp;//For every vertex
    <br>2. &emsp;&emsp;color[u] ==  "white" &emsp;&emsp;&emsp;//set vertex to white
    <br>3. &emsp;&emsp;d[u] == _nil_ &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;//set the d[time] to nil
    <br>4. &emsp;time == 0 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;//initialize time to 0
    <br>5. &emsp;for each vertex _u_ in G.V &emsp;&emsp;//for every vertex
    <br>6. &emsp;&emsp;if color[u] == WHITE; &emsp;&emsp;//if the color is white
    <br>7. &emsp;&emsp;&emsp;DFS-VISIT(G,u); &emsp;&emsp;&emsp;//visit that vertex

DFS-VISIT (G,u)
<br>1. &emsp;time += 1 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;//increment time
<br>2. &emsp;d[u] = time &emsp;&emsp;&emsp;&emsp;&emsp;//set time of discovery
<br>3. &emsp;color[u] = "GRAY" &emsp;&emsp;&emsp;//set vertex to gray
<br>4. &emsp;for each _v_ in Adj[u] &emsp;&emsp;//for every vertex v adjacent to u
<br>5. &emsp;&emsp;if color[v] == "WHITE" &emsp;//if v is white
<br>6. &emsp;&emsp;&emsp;parent[v] = u &emsp;&emsp;&emsp;//set v's parent to u
<br>7. &emsp;&emsp;&emsp;DFS-VISIT(G,v) &emsp;&emsp;//revursive call to v
<br>8. &emsp;color[u] = BLACK &emsp;&emsp;//blacken u; it is finished
<br>9. &emsp;time += 1 &emsp;&emsp;&emsp;&emsp;//increment time
<br>10.&emsp;f[u] =  time &emsp;&emsp;&emsp;&emsp;//set final time

### Explanation of the Pseudocode
#### DFS(G)

This function basically sets up some tracking parameters for the second function (DFS-VISIT (G,u)) to work. It sets every nodes color attribute to white, or you can think of it as a color array which stores the color of a particular a vertice at a given time. This will help the algorithm not repeat visits while its recursively calling through the graph. The d[u] is the discovery time of node _u_, which stores the time that the node was discovered. So every time a node is visited the time is first incremented, then set for that nodes d[u]. The d[] value for every node is initally set to nil, which will be changed once they are discovered. The second for loop initiates the second function, with any source node _u_.

#### DFS-VISIT(G,u)

This function first increments, then sets the time to d[u], and sets the color of the vertex u to gray (marking it visited). Then it checks the adjaceny matrix for vertex _u_ to see if any vertices are undiscovered by checking their color attribute. If the color is white, that means it is undiscovered. If it finds a node in the list that's white, it sets the parent to _u_, and then visits that node. Its important to note that everytime a node is visited, it is done so recursively. So the last node that is discovered will by the first node that will finish the sequence of the psuedocode from lines 8-10. (This is important because this will help introduce the parenthesis theorum) When the last node is visited, it will completely skip the for loop because there are no white nodes. It will execute sequence 8-10 which sets the color to black, increment the time and set it to f[u].


<!-- ### Comum Elements
- [Basic formatting](#basic-formatting)
- [Headings](#headings)
- [Lists](#lists)
- [Paragraph Modifiers](#paragraph-modifiers)
- [Urls](#urls)
- [Horizontal Rule](#horizontal-rule)
- [Images](#images)
- [Code](#code) -->


<!-- ## Basic formatting

This note **demonstrates** some of what [Markdown][1] is *capable of doing*.

And that's how to do it.

{% highlight html %}
This note **demonstrates** some of what [Markdown][some/link] is *capable of doing*.
{% endhighlight %}

---

## Headings

There are six levels of headings. They correspond with the six levels of HTML headings. You've probably noticed them already in the page. Each level down uses one more hash character. But we are using just 4 of them.

# Headings can be small

## Headings can be small

### Headings can be small

#### Headings can be small

{% highlight raw %}
# Heading
## Heading
### Heading
#### Heading
{% endhighlight %}

---

## Lists

### Ordered list

1. Item 1
2. A second item
3. Number 3

{% highlight raw %}
1. Item 1
2. A second item
3. Number 3
{% endhighlight %}

### Unordered list

* An item
* Another item
* Yet another item
* And there's more...

{% highlight raw %}
* An item
* Another item
* Yet another item
* And there's more...
{% endhighlight %}

---

## Paragraph modifiers

### Quote

> Here is a quote. What this is should be self explanatory. Quotes are automatically indented when they are used.

{% highlight raw %}
> Here is a quote. What this is should be self explanatory.
{% endhighlight raw %}

---

## URLs

URLs can be made in a handful of ways:

* A named link to [Mark It Down][3].
* Another named link to [Mark It Down](http://markitdown.net/)
* Sometimes you just want a URL like <http://markitdown.net/>.

{% highlight raw %}
* A named link to [MarkItDown][3].
* Another named link to [MarkItDown](http://markitdown.net/)
* Sometimes you just want a URL like <http://markitdown.net/>.
{% endhighlight %}

---

## Horizontal rule

A horizontal rule is a line that goes across the middle of the page.
It's sometimes handy for breaking things up.

{% highlight raw %}
---
{% endhighlight %}

---

## Images

Markdown can also contain images. I'll need to add something here sometime.

{% highlight raw %}
![Markdowm Image][/image/url]
{% endhighlight %}

![Markdowm Image][6]

*Figure Caption*?

{% highlight raw %}
![Markdowm Image][/image/url]
<figcaption class="caption">Photo by John Doe</figcaption>
{% endhighlight %}

![Markdowm Image][6]
<figcaption class="caption">Photo by John Doe</figcaption>

*Bigger Images*?

{% highlight raw %}
![Markdowm Image][/image/url]{: class="bigger-image" }
{% endhighlight %}

![Markdowm Image][6]{: class="bigger-image" }

--- -->

<!-- ## Code

A HTML Example:

{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <h1>Just a test</h1>
</body>
</html>
{% endhighlight %}

A CSS Example:

{% highlight css %}
pre {
    padding: 10px;
    font-size: .8em;
    white-space: pre;
}

pre, table {
    width: 100%;
}

code, pre, tt {
    font-family: Monaco, Consolas, Inconsolata, monospace, sans-serif;
    background: rgba(0,0,0,.05);
}
{% endhighlight %}

A JS Example:

{% highlight js %}
// Sticky Header
$(window).scroll(function() {

    if ($(window).scrollTop() > 900 && !$("body").hasClass('show-menu')) {
        $('#hamburguer__open').fadeOut('fast');
    } else if (!$("body").hasClass('show-menu')) {
        $('#hamburguer__open').fadeIn('fast');
    }

});
{% endhighlight %} -->
<!-- 
[1]: http://daringfireball.net/projects/markdown/
[2]: http://www.fileformat.info/info/unicode/char/2163/index.htm
[3]: http://www.markitdown.net/
[4]: http://daringfireball.net/projects/markdown/basics
[5]: http://daringfireball.net/projects/markdown/syntax
[6]: http://kune.fr/wp-content/uploads/2013/10/ghost-blog.jpg
 -->