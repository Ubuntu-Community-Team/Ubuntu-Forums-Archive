---
title: "Wireless card won't work after fresh install"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by colinireland on 2009-08-13
Hey,

I am just after doing a fresh install of 9.04 and now my wireless card isn't working properly. ifconfig and iwconfig show the card but when I go to see available wireless networks the icon near the clock is four empty vertical bars and a small white X on a red background. Its says no network connection when I run te mouse over it.

 I have a Dell Inspiron 1545.

lspci | grep BCM gives:
0c:00.0 Network contoller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I would grately appricate any help resolving this. I have no idea what to do. I have also made sure that the card is in managed mode and that the wireless switch is in the on position

Colin

---

### Post by rlzyoner on 2009-08-13
I've that same wireless card.

Usually, one of 2 things works for me.

First, enable restricted drivers.
System->Administration->Restricted Drivers (I think, unfortunately I'm on the girlfriends linuxless machine :(  )

If no luck, if you have a wired connection, connect the laptop with a cable and vist [http://www.linuxwireless.org](http://www.linuxwireless.org).
Grab the necesary drivers and follow the steps to build them.

Best of luck

---

