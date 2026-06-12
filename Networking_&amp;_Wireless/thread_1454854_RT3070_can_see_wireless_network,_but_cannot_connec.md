---
title: "RT3070 can see wireless network, but cannot connect"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by Cobra_MX5 on 2010-04-15
Hello,

I have a "Planet WNL-U554" wifi usb stick, which uses the Ralink 3070 chipset. I am trying to make it work on my 9.10 laptop, as well as a 10.04 b2 desktop pc. I have seen some topics in this board and managed to make the stick work up to the point that I see wireless networks in NetworkManager.

I have blacklisted rt28xx etc drivers, the module loads properly and I can see the interface (ra0) in iwconfig and ifconfig. iwlist scan also works and I can see the networks in my area. Network manager also shows all available networks, but I cannot actually connect to anyone of them. I have tried creating a wireless network on my ubuntu laptop and connect to it via the rt3070 stick on the desktop pc but it goes on trying to connect, but never makes it.

Any ideas what the problem can be?

P.S. I have also tried installing windows drivers via ndiswrapper, but some files are shown as invalid (why?) and with the one that can get loaded from ndiswrapper, iwconfig and ifconfig etc do not show the interface.

---

### Post by Cobra_MX5 on 2010-04-15
FWIW, the windows driver in the disc that came with it are named "rt2870.inf"...

---

### Post by 5BallJuggler on 2010-04-26
I have rececently (Today) had a similar issue, 

go to network configuration settings and check the IPv6 settings tab, make sure that the method is set to "Ignore"

Hope this helps

---

### Post by xXx8004 on 2010-07-29
i have the same problem
rt3070

---

