---
title: "Can't see available wireless networks - T60p (8.10)"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by jcw5002 on 2009-03-16
Hi!

About a month ago I installed Ubutnu 8.10 on a Thinkpad T60p laptop. When I first installed the OS, i recall seeing a list of all available wireless networks to choose from. I can no longer find this list.

I can connect to my wireless network at home, but not at work. I can't see any of the other networks available around my apartment on my Ubuntu laptop, but I can see nearly 10 networks on my mac. 

Can anyone help me get this functionality working? I would like to be able to see a list of available networks and connect to them.

---

### Post by nixscripter on 2009-03-17
What wireless card and driver does the Thinkpad have? Run ```
lshw -C network
``` in a terminal and post the output (in [code] forum tags, please).

---

