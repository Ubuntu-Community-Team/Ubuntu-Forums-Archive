---
title: "Ndiswrapper? Does it work?"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by LinXNut on 2011-07-30
Hi I have a Belkin 54g wireless network card. The Info about it is below.

```
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Belkin F5D7011 v1000 High-Speed Mode Wireless G Notebook Card
    Flags: bus master, fast devsel, latency 64, IRQ 19
    Memory at 28000000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
```The internet connection manager says "Firmware Missing". I have had this problem before, but I dont remember how I fixed it. 
:confused:

Thanks

---

### Post by wildmanne39 on 2011-07-30
Hi, you do not need ndiswrapper remove it and open synaptic and type in broadcom and remove all of the ones in that section that are installed.
Then run these commands
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
Then disconnect your wired connection and restart your computer.

---

### Post by LinXNut on 2011-07-30
Solved! Thank you. I remember it was something I had to install, but I just wanted to make sure I would install the right thing.

---

### Post by wildmanne39 on 2011-07-30
Hi, your welcome!!! would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by lasaleds on 2011-08-26
hi - newbie here installing ubuntu on a d610 with a belkin wireless pcmcia plugin. I  have exactly the same problem as described above ... when I try & follow the instructions above I get ...

ubantulaptop@ubuntu:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer Reading package lists... Done Building dependency tree        Reading state information... Done b43-fwcutter is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. Reading package lists... Done Building dependency tree        Reading state information... Done The following NEW packages will be installed   firmware-b43-installer 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. Need to get 3,632 B of archives. After this operation, 49.2 kB of additional disk space will be used. Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/multiverse firmware-b43-installer all 4.150.10.5-5   Could not resolve â€˜gb.archive.ubuntu.comâ€™ Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-installer_4.150.10.5-5_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-installer_4.150.10.5-5_all.deb)  Could not resolve â€˜gb.archive.ubuntu.comâ€™ E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

any suggestions please..?

---

### Post by wildmanne39 on 2011-08-26
Hi, were you connected to the internet by a wired connection when your tried to install the driver? Please post the results of these commands.
```
lspci -nn | grep 0280
```
```
sudo lshw -C network
```
```
iwconfig
```
```
rfkill list all
```
Thank you

---

### Post by praseodym on 2011-08-26
Try:

```
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Do you have any internet connection?

---

### Post by lasaleds on 2011-08-26
Thanks for offers of help you guys. 

I got it working okay  - I followed a set of instructions here ... 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Steve

---

### Post by wildmanne39 on 2011-08-26
Hi, I am glad you got it working.

---

