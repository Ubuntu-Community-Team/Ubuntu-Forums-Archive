---
title: "Lost Wired Network after Update"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by hobo on 2010-06-24
I have not been able to connect to my network after a recent update to 2.6.32-23. I can however connect via this PC to my network using another OS.
The problem is that I never get an IP address.
Any help would be welcome.

btw...reverting to the last kernel does not help.

---

### Post by VH-BIL on 2010-06-24
Have you tried setting a static IP?

---

### Post by hobo on 2010-06-24
I just tried but apply is always 'grayed out'

---

### Post by VH-BIL on 2010-06-24
You need to add a netmask and gateway.

Example: (If your router IP is 192.168.0.100)
You can set your IP to 192.168.0.10 (You can change the last number)
Set the subnet to 255.255.255.0
Set the gateway to 192.168.0.100 (Your router IP).

---

### Post by hobo on 2010-06-24
Looks like my router is goin' south. I booted to W7 and had the same problem. I assigned a static IP and all is well with W7. I then booted back to 10.04, did the network setup again and Apply. But the static address never shows in network tools even after a reboot.
Anyway the UPDATE has nothing to do with my problem.

tks

---

### Post by VH-BIL on 2010-06-24
Try reboot your router, if that doesn't work and your router doesnt work, try flash the rom.

---

### Post by hobo on 2010-06-25
Well I finally got 10.04 to connect and resolve by using the CL...sudo dhclient eth0.
I really don't know what happened but it is all working now.

---

