---
title: "Native wifi driver and ndiswrapper"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by andyhumphries on 2009-05-27
Hi folks,

I was experiencing poor wifi network signal strength (10-20%) despite getting roughly 100% strength under Vista (dual-boot PC). I tried playing around with ndiswrapper, installed it and tried it but it didn't make a difference so I uninstalled it. It seems to have left residual traces though, as every time I reboot Linux I get no wifi support and have to explicitly give the command

```
sudo modprobe rtl8180
```in order to load my wifi drivers and use them. I also get an error about ndiswrapper when I do that.

Is there a way to remove the elements of ndiswrapper from my system and also make sure that the module rtl8180 loads on boot?

Cheers,

Andy

---

