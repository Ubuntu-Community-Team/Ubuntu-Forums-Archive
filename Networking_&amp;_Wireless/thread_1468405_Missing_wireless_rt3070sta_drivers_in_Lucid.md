---
title: "Missing wireless rt3070sta drivers in Lucid"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by bedhead75 on 2010-05-01
Has anyone managed to get wireless Ralink rt3070 drivers working in Lucid?  Before in Karmic, you could "sudo modprobe rt3070sta" as they were "stagging" drivers already in the kernel, but apparently they're missing from the kernel in Lucid as reported here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566962]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566962")
I get errors when compiling the latest drivers from Ralink (DPO_RT3070_LinuxSTA_V2.3.0.2_20100412) and they don't seem to work.

---

### Post by simone.sdq on 2010-05-10
i've the same problem . Could someone help me?
 
i've a dwa 140 with ralink 3070 chipset
 
ubuntu 10.04
 
I've downloaded driver from ralink website version 2.3.0.2
 
I'm unable to install... 
 
if necessary i could post other information like iwconfig etc etc
 
thanks a lot

---

### Post by chili555 on 2010-05-10
Did you try this method?

[http://ubuntuforums.org/showthread.php?t=1473762&page=3](http://ubuntuforums.org/showthread.php?t=1473762&page=3)

---

### Post by bedhead75 on 2010-05-10
I managed to get the problem solved by consulting another forum:

[http://www.linuxforums.org/forum/wireless-internet/161550-solved-rt3070sta-module-license-unspecified-taints-kernel.html]("http://www.linuxforums.org/forum/wireless-internet/161550-solved-rt3070sta-module-license-unspecified-taints-kernel.html")

The rt3070sta driver works perfectly for me now, at least with the Alfa AWUS036NH wireless adapter.  A similar solution should apply to you I believe.

---

