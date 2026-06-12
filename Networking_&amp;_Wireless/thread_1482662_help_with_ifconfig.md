---
title: "help with ifconfig"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by thejakeman on 2010-05-13
When I type in the ifconfig command in terminal all I get are eth0, eth1 and lo. This is a problem, because I'm running on wifi. I have Broadcom bcm4311 on a Dell. Is there a patch or something I need?

Thanks in advance!

PS. I will provide further info if necessary.
PPS. All I know about eth0 and eth1 is that they're LAN stuff. I dont' know what lo is though.

---

### Post by nevle on 2010-05-13
Try iwconfig
should list wifi connectiion--am at work on windows so can't give you any more info about it

---

### Post by Iowan on 2010-05-13
**ifconfig -a** *should* show all interfaces. **sudo lshw -C network** will provide more details - including if your wireless card has an alias (wlan0, etc.) My laptop uses eth1 for the wireless.

ifconfig should have provided a line similar to:```
lo        Link encap:Local Loopback  

```[Here]("http://en.wikipedia.org/wiki/Loopback") is probably more information than you wanted about the loopback device.

---

### Post by thejakeman on 2010-05-13
```
jake@jake-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:201  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

vboxnet0  no wireless extensions.
```
Is something wrong here?

---

