---
title: "Is this a router issue?"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by Literati on 2009-10-19
Hi there,

My dad has a pretty old Acer laptop (Acer Aspire 5001 I believe) and has been having lots of connectivity problems to our router which is located only one floor below where the laptop is. 

Both his computer and my computer are running Ubuntu 9.04, except mine is hooked up via ethernet to a Linksys WRT54G2 v1.0 We changed to this from a WRT300N.

The reason we changed in the first place is because of the same issue, bad wireless signal. Actually, let me rephrase, the signal is okay (he sees the network at around 75% signal strength) but the router speed is only around 2mbps and seems to drop off a lot. It's only a Wireless G router, but it should be at least closer to 54mbps shouldn't it? 

We even thought it was the laptops old wireless card giving out, so we picked up a USB Network Adapter by Belkin. He now uses that but the problem persists. 

The router is as far from my PC, Monitor, and metal as I can possibly put it. And it's pretty well elevated too. Could this just be a case of getting two bunk routers? What would you guys suggest? If a new router is in order, I was thinking of the WRT400N as it is Dual Banded.

---

### Post by Literati on 2009-10-20
Bumptruck.

---

### Post by t0mppa on 2009-10-20
> **Literati said:**
> The reason we changed in the first place is because of the same issue, bad wireless signal. Actually, let me rephrase, the signal is okay (he sees the network at around 75% signal strength) but the router speed is only around 2mbps and seems to drop off a lot. It's only a Wireless G router, but it should be at least closer to 54mbps shouldn't it?

If it's simply a matter of the connection bit rate being only 2Mb/s, then you can manually change it from the terminal with **sudo iwconfig <interface_logical_name> rate <rate>M**. You can see the supported bit rates by doing a **iwlist scan** and check the current bit rate after changing it with **iwconfig**. Note that it takes a while for the change to take effect.

The dropping off a lot part is a bit more tricky, especially if it persist over different interfaces and routers. If you're convinced it's an Ubuntu issue, there's a [long thread]("http://ubuntuforums.org/showthread.php?t=1146367") around with lots of different fixes suggested, but nothing universal found (at least the last time I took a look at it).

---

### Post by cgb on 2009-10-20
If possible I would try connecting a completely separate PC via wireless and see if the same problem occurs.  Sounds more likely that it is a driver/config problem on the laptop and not the router.  Has this laptop ever connected to another outside wireless Router and does the same problem occur?

---

