---
title: "gxine - cannot open shared object file"
date: 2008-04-29
forum: Multimedia Software
---

### Post by Jazman on 2008-04-29
Recent upgrade from Gutsy 7.10 to Hardy 8.04
I did all the stuff in the Comprehensive Multimedia & Video How-to
gxine gives the following error 
jim@jim-desktop:~$ gxine
gxine: error while loading shared libraries: libsmjs.so.1: cannot open shared object file: No such file or directory

Removed and reinstalled gxine - still the same result.
It worked for me in Gutsy 7.10

How to fix?

---

### Post by cor2y on 2008-04-29
simplest solution would be to check if libsmjs is installed , search for it in synaptic if it is installed try reinstalling again or adding the dev version as well as the regular one.

---

### Post by Jazman on 2008-04-29
Found libsmjs1 (1.8.0.10-3ubuntu1) [universe]
    Migration package for the Mozilla SpiderMonkey JavaScript library in feisy libs and installed it.

Now gxine fails with a segmentation error.

Still looking for a solution.

---

