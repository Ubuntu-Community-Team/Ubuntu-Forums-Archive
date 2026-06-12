---
title: "error when install ns 3.10 in ubuntu 10.10"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by abex11 on 2011-03-17
I got a problem when install ns 3:10 in ubuntu 10:10. messages that appear
[1190/1487]  cxx: src/tools/visualizer/model/visual-simulator-impl.cc ->  build/debug/src/tools/visualizer/model/visual-simulator-impl_2.o
../src/tools/visualizer/model/visual-simulator-impl.cc:20: fatal error: Python.h: No such file or directory
compilation terminated.
Waf: Leaving directory `/home/ymansyali/Documents/ns-allinone-3.10/ns-3.10/build'
Build failed:  -> task failed (err #1): 
    {task: cxx visual-simulator-impl.cc -> visual-simulator-impl_2.o}

how to fix this error??
please enlightenment
 thx

---

### Post by gmargo on 2011-03-17
> **abex11 said:**
> 
../src/tools/visualizer/model/visual-simulator-impl.cc:20: fatal error: [COLOR=Red]Python.h: No such file or directory[/COLOR]


This error message usually means that you are missing a development package.  If the probable package is not immediately obvious from the name, then you can use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search for that particular filename.

Here is the search for Python.h:
[http://packages.ubuntu.com/search?searchon=contents&keywords=Python.h&mode=exactfilename&suite=maverick&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=Python.h&mode=exactfilename&suite=maverick&arch=any)

And from that information, it is clear that you need the python development package appropriate for your python version. The default version is 2.6, so install the **python2.6-dev** package.

---

