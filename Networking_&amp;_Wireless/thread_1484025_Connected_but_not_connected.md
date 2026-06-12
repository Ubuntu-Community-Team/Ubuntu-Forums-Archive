---
title: "Connected but not connected"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by poopeypants on 2010-05-15
Hi,

I bought a new Eee PC yesterday ripped off Windows and stuck Ubuntu 10.04 on (which is great by the way). It's all working fine except for the wireless I think I have: RT3090 Wireless 802.11n 1T/1R PCIe. I've installed ndiswrapper and installed the drivers and I can connect to my wireless but I get no internet. It works fine on my windows box or when I plug the cable in. Any ideas? I've looked around and been fiddling with it for hours and no joy, it all seems to be installed correctly its just not working!

Shaun

---

### Post by ronnielsen1 on 2010-05-15
Try this

> Just fixed the issue with having to do a "sudo modprobe rt3090sta" at login. Added "rt3090sta" to the end of /etc/modules and rebooted. Wifi now auto connects to WEP.
[http://ubuntuforums.org/showthread.php?t=1313132](http://ubuntuforums.org/showthread.php?t=1313132)

---

### Post by pradeepthundiyil on 2010-05-15
I guess you are not able to browse through firefox, is the problem.. Either you can install a different browser.. or search for a firefox issue.. I don remember exactly the config wat i have made.. 

search for it.. 



I had the same issue. . I solved it..........

---

