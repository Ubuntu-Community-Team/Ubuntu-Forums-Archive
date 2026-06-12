---
title: "Question about Linksys Wireless USB"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by Dural on 2006-07-13
After searching through the forums, I got my WUSB11 v 2.8 adapter to work in Dapper Drake, which makes me very happy. However, whenever I do lshw -C network, this displays:

 description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:58:2b:f6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.100 wireless=IEEE 802.11-DS
Is this normal, or do I have to install additonal drivers for this adapter?

---

### Post by gratefultux on 2006-07-13
I get the same output when i run it as a normal user.
Try using sudo you should get some more info.

---

### Post by Dural on 2006-07-14
Allright. I'll try as soon as I can repair my other problem with Ubuntu. Thanks for the tip. :)

---

