---
title: "cannot connect unless inches away from router"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by lanruisen on 2009-05-29
I have 64 bit 9.04 on a new asus n20a-x1. The wireless will not connect unless it is very close to the router. Vista works anywhere in the house, so does the linux splashtop os that comes on the asus.
I am using this router for two other linux machines that always connect. I have used ubuntu with this router many times before. I am only using wep encryption. I also tried the 9.04 32bit live cd and it did not connect either. It even shows a good signal, but  will not authenticate unless I'm right in front of the router. Once it fails to authenticate the passphrase, it must restarted in order to connect, otherwise the passkey dialog box keeps repeatedly showing up.
It uses the Intel GM45 chip set.

---

### Post by lanruisen on 2009-05-29
I just tested the 8.10 live cd. and Fedora 10 live cd and the wireless works flawlessly with both. But my sound and video are not supported those two.

---

### Post by lanruisen on 2009-05-30
Anybody got any ideas?

---

### Post by crazybuntu on 2009-05-30
try adding this by doing : sudo gedit /etc/rc.local

rmmod drivername
modprobe drivername

before the last line
then reboot... 

had the same problem but with iwl3945 card, and now works..
Hope it solves your problem

The drivername can be checked with : lshw -C network

---

### Post by lanruisen on 2009-06-01
That did not help, but I did find the solution.

I installed linux-backport-modules-jaunty rebooted and now it works.

---

