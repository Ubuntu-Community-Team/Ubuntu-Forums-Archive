---
title: "Wireless not recognized"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by awiggin on 2009-02-17
Hi.

I updated recently (don't know if it matters, but it's all I can think of).  Now I can't connect to the internet via my wireless.

In the network manager, there is no wireless recognized.  When I type in ifconfig, all I get is info on lo and eth0, no wlan.

It was working fine until about a week ago.

Help?!

P.S.  Can you tell I'm not a computer guy? Not exactly a noob, since I've had ubuntu for over a year, but I still hardly know a terminal screen from a hole in the ground.

---

### Post by trepid666 on 2009-02-17
Plug in your ethernet, update the system, then enable restricted wireless driver

I think the code for wireless is iwconfig

---

### Post by awiggin on 2009-02-17
I will try that.

Meanwhile...I went back to the Grub menu and chose an older kernel and I am able to get online.

Does this tell you anything different?

Thanks in advance for your help.

---

### Post by trepid666 on 2009-02-22
the proper code to see wireless is 

```
iwconfig
```

to see what wireless card you have, type

```
lspci
```

did u manage to get wireless working yet?

---

