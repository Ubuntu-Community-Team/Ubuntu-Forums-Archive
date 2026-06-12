---
title: "microsoft wireless card"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by dubsential on 2009-06-14
Hi,
could anyone be so kind as to explain how I can use ndis wrapper to install drivers for a Microsoft mn-730 broadcom wireless pci card that I have in my desktop I am using jaunty 9.04 also I have kde repositories installed. I'm aware that what the wrapper does just unsure what files it needs, I have drivers saved on the computer for windows.
Any help would be much apreciated.

---

### Post by superprash2003 on 2009-06-14
post output of **lshw -C network** from the terminal

---

### Post by dubsential on 2009-06-14
00:08.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)
10ec:8139


me@me-desktop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM43xG 802.11b/g
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0d:3a:71:64:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: b2:4e:93:95:4e:e5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



Just so you know the full story my computer has no onboard ethernet which i am using now it seems i have to use the same blue pci slot for the wireless so basicaly. I'm interchanging the cards just so you know why it may take a little while if i need to read some more info from the wireless card etc im not messing about. The windows driver is a networking program also i have extracted the exe file to see if there was a driver i could use in there it seems its not that easy. i have ndis wrapper installed the gui to make it easier.Ive searched high and low for correct driver
thanks for helping.

---

### Post by superprash2003 on 2009-06-15
read this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by dubsential on 2009-06-15
Ok thanks I will give it a go

---

