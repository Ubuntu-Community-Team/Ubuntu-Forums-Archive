---
title: "how to enable my network adapter"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by a7med93 on 2009-08-03
hi i am dual booting windows 7 & ubuntu 9.04
my problem doesn't make any sense if i run ubuntu it doesn't connect to my wireless but if i run windows and connect to the wireless network then restart the pc boot ubuntu it find's the network and connects with no problem's :confused:
Thx :D

---

### Post by xc3RnbFO8P on 2009-08-03
Do you have a Networks Icon on the panel?

---

### Post by a7med93 on 2009-08-03
yes

---

### Post by xc3RnbFO8P on 2009-08-03
If you left click on it, can you see your router?

---

### Post by a7med93 on 2009-08-03
of course i can that's how i connect to the network but only if i boot windows first then restart and boot linux

---

### Post by xc3RnbFO8P on 2009-08-03
do:
> sudo lshw -C network
check the name of the wireless card ***-network** (something like rt2870)

---

### Post by a7med93 on 2009-08-03
OK I Did it Here is What i got :
> 
    description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.


---

### Post by xc3RnbFO8P on 2009-08-03
I found this Bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/354548]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/354548")
You could try to install Backports:
> sudo apt-get install linux-backports-modules-jaunty

---

### Post by a7med93 on 2009-08-03
thx am gonna try it
and sorry i posted the thread in the wrong sect

---

