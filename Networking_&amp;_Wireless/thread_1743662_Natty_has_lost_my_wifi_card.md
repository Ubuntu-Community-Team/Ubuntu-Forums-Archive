---
title: "Natty has lost my wifi card"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by glendavee on 2011-04-29
Reading recent posts, it seems that 11.04 has seriously screwed wifi.
I have  an Advent QRC430 laptop which worked perfectly until I upgraded to Natty. Now wifi is broken. The wifi driver is rt73usb.
When I run lspci in terminal, no wifi card is listed. Running rfkill shows wifi hard blocked, but the switch on laptop makes no difference. 
I've installed and run Hardware Lister - this shows wireless interface "has been disabled"
Grateful for any suggestions

---

### Post by glendavee on 2011-05-02
Solved (for now). Solution was to uninstal Network Manager and instal wicd.

---

### Post by andrezgz on 2011-11-14
I've solved the same problem reinstalling all the packages that began with network-manager

---

