---
title: "No Internet Connection"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by lpjz50 on 2009-11-30
OK i just installed Ubuntu 9.10 on my laptop, with my hardrive formatted before, leaving ubuntu as the only OS on it. I have no access to DSL cable only wireless, but my wireless isnt working. IM A SUPER NOOB at ubuntu, so please u a VERY VERY EASY STEP BY STEP way to get internet please. ive been trying for hours suing methods and idk what to do! :(

THANK YOU!

---

### Post by Iowan on 2009-11-30
Laptops and wireless are still kinda touchy... 
Gonna need to get the hands dirty (so to speak) to dig out some information. From a terminal (Applications>Accessories>Terminal) check:```
lshw -C network
``` to get information about networking devices (wireless card).

---

