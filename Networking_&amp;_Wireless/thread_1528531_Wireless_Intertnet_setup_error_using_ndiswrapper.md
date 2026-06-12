---
title: "Wireless Intertnet setup error using ndiswrapper"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by SquirrellyMcGee on 2010-07-10
Hi, I just installed Ubuntu 10.04 64 bit on my mac as a seperate OS, but I can't get my Internet working. It's wireless and Ubuntu isn't seeing any of the wireless networks in the area. I have installed ndiswrapper and tried installing a driver for my network but it didn't work. I followed this tutorial [http://ubuntuforums.org/showthread.php?t=616801]("http://ubuntuforums.org/showthread.php?t=616801") but when typed in this code: "ndiswrapper -i bcmwl5.inf && modprobe ndiswrapper" I got the "No such file or directory at usr sbin ndiswrapper line 219" error. Any help would be appreciated. Thanks!

---

### Post by Saeger on 2010-07-10
I'm not sure but I think the "modprobe" command should be on a separate line

---

### Post by SquirrellyMcGee on 2010-07-11
Well I typed in the code 
```
ndiswrapper -i bcmwl5.inf
```
and that is when I got the "No such file or directory at usr sbin ndiswrapper line 219" error.  I will try reinstalling ndiswrapper. Thanks for the reply

---

