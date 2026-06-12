---
title: "need help with broadcom"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by kcallstar7 on 2006-06-17
iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

why would  it show my wireless set under my eth1 does this make any sense at all please n e help is good help, i just want to get my wireless up and running with unbuntu some please help

---

### Post by x64Jimbo on 2006-06-17
Looks like it's already up and running. All you should need to do now is connect it to the network. For more info on that, run this command:
man iwconfig

---

### Post by lois on 2006-06-17
I had the same problem.

This post from Phaeton77 worked for me:
[http://ubuntuforums.org/showthread.php?t=135921&highlight=trouble+broadcom](http://ubuntuforums.org/showthread.php?t=135921&highlight=trouble+broadcom)

---

### Post by noname101 on 2006-06-17
It doesn't matter if it shows up as eth1. Also you can configure the wireless in System | Administration | Networking.

---

