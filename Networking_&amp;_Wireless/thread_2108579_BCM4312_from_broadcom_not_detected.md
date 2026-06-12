---
title: "BCM4312 from broadcom not detected"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by binary_dreamer on 2013-01-25
Hi. i was running ubuntu 12.10 to my netbook, Compaq mini 110c, but it is extremely heavy for it. All the drivers though worked well. I decided to move to lubuntu since it is light. after a few minutes my system is up and running with the cpu and ram to work at reasonable levels. The only problem is the wifi drivers. i did an update of the system through the software center, but no luck. is there a way to make it work?

---

### Post by rrich1974 on 2013-01-25
hello baby...
can you give us the output of "lspci" to see the wireless chipset?

---

### Post by Bucky Ball on 2013-01-25
> **rrich1974 said:**
> hello baby...


Hoping you know this user pretty well!

Also give the output of:

```
sudo lshw -C network
```

Also check Additional Drivers. Anything there for your wireless but disabled?

---

### Post by binary_dreamer on 2013-01-25
Sorry, my fault. i forgot to attach the files.

---

### Post by rrich1974 on 2013-01-25
damn it man! it seems that you have bcm4312 from broadcom. 
i have a bcm4311 and i always fallowed this post, it never failed me: 

> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

now, it works pretty well for my chipset....i dont know about yours, it worths to try. 

on the other hand...
the last thing is to try to use ndiswrapper. 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

or this, but for your card: 
[http://ubuntuforums.org/showthread.php?t=1481710](http://ubuntuforums.org/showthread.php?t=1481710)

you need the driver for windows XP

---

### Post by Bucky Ball on 2013-01-25
Try everything else before resorting to ndiswrapper. Avoid if possible. Problematic and largely superseded for Broadcom.

---

### Post by binary_dreamer on 2013-01-28
i got a solution, simply by typing
apt-get install b43-fwcutter firmware-b43-lpphy-installer

thanks a lot.

---

### Post by Bucky Ball on 2013-01-28
Excellent news. Please mark as Solved from Thread Tools at top right to help others.

---

### Post by sasar on 2013-03-29
Hi,
Just to put down my experience and help others just like I was helped. Compaq Mini 110, Ubuntu 12.10, updated as of 29-march-2013. Behavior: as if my laptop did not have a wireless adapter. BCM4312 (from lspci). Run into this thread trying to figure out a solution, and then installed "firmware-b43-installer" and "b43-fwcutter". Not working. Then I noticed "bcmwl-kernel-source" not installed (via synaptic). I installed it and then all is right, wireless adaptar working as expected.

---

