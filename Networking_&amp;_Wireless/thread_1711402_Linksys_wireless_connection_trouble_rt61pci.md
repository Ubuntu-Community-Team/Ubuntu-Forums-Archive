---
title: "Linksys wireless connection trouble rt61pci"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by Gary Heinl on 2011-03-21
Had a perfect running wireless network card with driver rt61pci all of a sudden I have no wireless applet and no wire less connection. With mn-tool I get:

Type:802.11 WiFi
Driver:rt61pci
State:disconnected
Default:no
HW Address: 00:1a:70:b0:47:a1
WEP WPA WPA2 yes

how can I get the wireless applet back and the wireless connection working

---

### Post by Hippytaff on 2011-03-21
Can you post the output of these comands in a terminal (CTRL+ALT+T to open a terminal)
```

iwconfig
```
```
lsmod | grep -i rta
```
 
Have you updated recently or upgraded the kernel? Have you tried right clicking on the top panel and -> add applet and choosing the notifications applett (Ithink...not at my ubuntu box at themoment to check if thats totally correct)

---

### Post by Gary Heinl on 2011-03-21
Thanks I got the applett notification up and running and the wireless was showing. I deleted my old wireless setup and started fresh and low and behold it is now working great. Thanks I consider this closed.

---

### Post by Hippytaff on 2011-03-21
Glad you got it sorted - rmember to mark the thread as solved in thread tools at the top of the page :-)

---

