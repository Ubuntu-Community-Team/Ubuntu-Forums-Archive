---
title: "BCM 4313 lots of problems. HELP"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by slokenafk on 2013-03-04
Hello all,

I am currently running a HP g6 with the broadcom bcm 4313 wifi card. (on ubuntu 12.04)  Believe me when I tell you that for days I have been trying everything possible to connect to wifi.  I have tried numerous drivers, I have tried blacklisting my way, and nothing has worked.  Currently it will not even connect to the signal, It will just keep trying.

---

### Post by Hadaka on 2013-03-04
Hi, please copy and paste the following commands 
and post the output.

```
arch
 lspci -n | grep -v 8086 | egrep '0200|0280' |  awk '{print$2,$3}'
lsmod | egrep 'b43|ssb|wl'
```
thanks

---

### Post by drphysic on 2013-04-08
I did not see any further information on this thread, but since I am experiencing the same issues with a BCM4311 in a Compaq Presario V6105NR that I am moving (I hope) from XP to Xubuntu 12.04; here is the output from the commands provided:

$ arch
i686

$  lspci -n | grep -v 8086 | egrep '0200|0280' |  awk '{print$2,$3}'
0280: 14e4:4311

$ lsmod | egrep 'b43|ssb|wl'
wl                   3032542  1 
cfg80211              178877  1 wl
lib80211               14040  1 wl

drphysic

---

### Post by Hadaka on 2013-04-08
Hi drphysic
try this..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree 
sudo modprobe b43
```
thanks.

---

