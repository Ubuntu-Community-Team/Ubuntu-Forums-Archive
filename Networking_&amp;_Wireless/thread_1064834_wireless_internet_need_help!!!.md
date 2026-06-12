---
title: "wireless internet need help!!!"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by lulumara on 2009-02-09
HI I need help  to put wireless internet, I had Linksys wireless usb usually when I installed the Ubuntu last time there's an internet right away I did reinstalled the Ubuntu along side with Window XP,the Window XP had an internet but the Ubuntu nothing even I put the the WEP password can even to work? I even had installed Fedora core 1 the old edition in my second hard drive but doesn't have also an internet can you help me pls?

---

### Post by lulumara on 2009-02-09
Any one knows about it I been playing around but can't figure it out I spend one  day yesterday just to solve this problem?

---

### Post by lulumara on 2009-02-10
is anyone knows the anwers to my question?

---

### Post by juan234 on 2009-02-10
does the machine reconize the usb, example;

$ lsusb
Bus 003 Device 005: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

---

### Post by lulumara on 2009-02-10
Yap, there's a LInksys Usb54 wireless that's connected , Last time when i installed the Ubuntu it recognized it then I did uninstalled the Ubuntu because the cpu is not working properly, but now it's working ok but no wireless at all.

---

### Post by pdtpatrick on 2009-02-10
output sudo iwconfig or sudo ifconfig 

also dmesg | grep -i linksys

---

