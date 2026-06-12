---
title: "installing graphviz 2.29 in ubuntu 12.04"
date: 2012-10-04
forum: Multimedia Software
---

### Post by bidur on 2012-10-04
In my ubuntu 12.04, the graphviz is not the latest version(2.29). I need some features available in the latest version of graphviz.
I tried to install the graphviz version 2.29, which requires libgraphviz4(>=2.18).
I anyhow installed libgraphviz4 and installed graphviz 2.29. For that I have to remove packages libcdt4 and libpathplan4.

Now whenever I try to generate graph, I get some problems:
For e.g.: 
```
 dot -Kfdp -n -Tpng -o samplePOS.png test.dot
```
*It says:*
 ```
dot: error while loading shared libraries: libgvc.so.6: cannot open shared object file: No such file or directory
```

```
neato -Tps -o sample_1.ps sourcedot.gv
```
*It says:*
```
neato: error while loading shared libraries: libgvc.so.6: cannot open shared object file: No such file or directory

```
So, I am looking for some ways so that I can run graphviz 2.29 in my ubuntu 12.04.

Thanks

---

