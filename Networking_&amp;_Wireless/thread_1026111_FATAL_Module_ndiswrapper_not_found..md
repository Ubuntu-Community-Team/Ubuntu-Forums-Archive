---
title: "FATAL: Module ndiswrapper not found."
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by EggMasta on 2008-12-30
Hey guys. i recently tried installed ubuntu 8.10. I am trying to get my wireless to work. I have a RaLink RT2860. I used ndiswrapper to install rt2860.inf and when i try run ndiswrapper -l i get the result:

> 
rt2860 : driver installed
	device (1814:0681) present

When i try to do sudo modprobe ndiswrapper i get the result:

> FATAL: Module ndiswrapper not found.

And when i try to run ndiswrapper -v i get the result:

> modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

---

### Post by lyratzis on 2009-05-24
I am having this problem as well, did you get this resolved?

---

### Post by kenm_uk on 2010-02-08
I too am seeing this error... did you find a solution?

---

