---
title: "ALTERNATE INSTALL: Gettign wireless"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by malangbaba on 2010-01-07
SEMI-NOOB

Installing Ubuntu through the alternate install cd (which i got onto a bootable USB).  

Did a basic command line install.

Spent an hour to get the wireless turned on.

Now I am tryign to connect to my wireless network, but iwconfig or iwlist is not installed
It is an open network (no WEP key or pass)

What do I do?
Is iwconfig ob the alternate install cd? if so, how do i install it off the usb?

Oh, installing KARMIC on a HP 5310m

My etc/network/interfaces:
auto wlan0
iface wlan0 inet static
address 193.162.10.103
netmask 255.255.255.0
network 193.162.10.0
broadcast 193.162.10.255
gateway 193.162.10.1
wireless-essid doobieDo
wireless-channel 10

lspci:
02:00.0 Net Controller: Intel Corp PRO/Wireless 5100 AGN [Shiloh] Network Connection

---

### Post by malangbaba on 2010-01-07
^^^

---

### Post by malangbaba on 2010-01-07
1. Is there a reason the installer wouldnt install iwconfig? Im pretty sure it should be availble on the alternate installer and installed by default
2. The CLI does tell me which packages i need. Is there a manual way for me to get the packages on there? maybe download and copy them into a folder through a live distro

---

### Post by malangbaba on 2010-01-08
SOLVED!

Went and got the wireless-tools, libc6 (udev), libiw29 packages from packages.ubuntu.com

installed them on CL through dpkg

got wireless-tools on

now wireless works!

---

### Post by Project PWNED on 2010-01-08
Edit your thread and choose [Solved], this will help others out

---

### Post by malangbaba on 2010-01-08
i was looking for it earlier, but under post editing.

thanks!

---

### Post by Project PWNED on 2010-01-08
No, thank you for saying you solved something because someone will eventually find this thread and your solution, so it will help someone out rather than just saying thank you and not editing the thread to show it was solved. 

Thankfully all my wireless cards work out of the box. I've got a TP-Link card (in my signature) and a D-Link WDA-1320 PCI card (ath5k). I ran MadWifi drivers for the D-Link and wasn't pleased with the performance.

---

