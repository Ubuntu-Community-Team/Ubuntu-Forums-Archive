---
title: "TrendNet TEW-644 UB v1.0R not working"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by espressobeanie on 2010-09-04
I've been trying to get this card working for months with no luck, on different versions of Linux, namely Ubuntu and Backtrack. I downloaded the RT2870 version 2.4.0.0 linux drivers from Ralink and did a 'make' and 'install make' command in a root terminal. I've gotten more compiling errors in Ubuntu than I did with Backtrack. 

The only error in Backtrack was: "WARNING: Symbol version dump
/usr/src/linux-headers-2.6.34/Module.symvers is missing;
modules will have no dependencies and modversions."

In Ubuntu, there were more compiling errors that looked like a lot of type_char integers in the 'C' files are now defunct and no longer supported in the newer kernel releases.

Aside from installing some backport module or ndiswrapper, does anyone have any ideas? Ubuntu's great and all, but it performs badly at drivers. Heck, Win7 had the driver installed in 1 minute.

---

