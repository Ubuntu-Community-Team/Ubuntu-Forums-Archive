---
title: "Computer freezes with ifconfig ra0 up"
date: 2006-05-20
forum: Networking &amp; Wireless
---

### Post by Quatrerwin on 2006-05-20
I have a Belkin F5D7000 PCI card which is showing up as a Rt2500 (rev 01) cardbus.  I can connect just fine with the Network GUI, but I am trying to install the computer as a server since it only has 64 MB ram and so I will not have that Network GUI.

When I do ifconfig -a, it shows an ra0 device and when I do iwconfig ra0, it shows the device.  when I do iwlist ra0 scan, it returns no results.  So then I try an ifconfig ra0 down then an ifconfig ra0 up and then my computer freezes.

Anyone know why it's freezing?

---

### Post by Quatrerwin on 2006-05-20
The computer actually freezes with any attempt to use the wireless adapter.  It used to work with the Networking GUI about a year ago, but it no longer works.

---

