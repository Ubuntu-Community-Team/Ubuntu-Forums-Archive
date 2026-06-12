---
title: "US Robotics USR5410 - WPA"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by ciaopaulo on 2010-04-21
Hi,

I've just installed Ubuntu on a laptop and I need help getting the USRobotics USR5410 wireless pcmcia card going.

I've managed to get it working through ndiswrapper, but I don't have options to enter WPA key.

If I go into Network Connections I can select WPA and enter the password there. But when I select a network manually by clicking the networks icon at the top right and then chosing the network name, I only get options for WEP. I suspect that the option to enter WPA in network conections actually has no effect, and is a benign bug.

The network I want to connect to uses WPA.

The Windows driver file I used was USR11g_v6.0b15.exe, from USR site.

This is reported to work with WPA under Ubuntu/Linux.

Any help greatly received!

System: Karmic 2.6.31-20-generic

---

### Post by ciaopaulo on 2010-04-23
Obligatory bump?

---

### Post by ciaopaulo on 2010-05-01
OK lets park this on up as "WPA doesn't work on USR5410".

---

### Post by NissanSkylineN1 on 2010-05-01
[https://answers.launchpad.net/ubuntu/+question/109103](https://answers.launchpad.net/ubuntu/+question/109103)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573273](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573273)

---

### Post by ciaopaulo on 2010-05-03
It wasn't a 10.04 issue, but seemed to be a problem with ndiswrapper. I mailed the support for ndiswrapper but it's got no luck.

What's worse is that I upgraded to 10.04 and now it won't work with my Dlink usb wireless now either! Aaaaargh!

---

