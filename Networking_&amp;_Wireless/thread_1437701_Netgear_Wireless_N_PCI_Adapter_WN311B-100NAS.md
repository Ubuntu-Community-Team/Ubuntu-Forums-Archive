---
title: "Netgear Wireless N PCI Adapter WN311B-100NAS"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by isutrout on 2010-03-24
I just bought a Netgear N PCI wireless network card and was hoping Ubuntu 9.10 would recognize it. I installed the card and was using XP on the machine (Dell Dimension 2400) and decided to install 9.10 on this computer instead (XP = slow!!!). I'm not sure how to get Ubuntu to recognize it. I'm relatively new to Ubuntu, so any help would be appreciated! I was hoping this would be a 'plug and play' install :)

---

### Post by chili555 on 2010-03-24
Let's get started by opening Applications > Accessories > Terminal and please post:```
lspci -nn
iwconfig
```Thanks.

---

### Post by jeff.nitt on 2010-04-09
I am having the same problem with the same WN311B
05:02.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet [14e4:1696] (rev 03)
05:09.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
jeff@jeff-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   

I installed a driver for BCM43xg
It works ok but keeps dropping the connection and is slow
I also need to reenter the wep key often

Can you help me set it up?

---

### Post by andy341 on 2010-04-09
I did the following in a previous posting in the forum:
Go:

System > Administration > Hardware Drivers

Activate the one that was not activated. It now works! Yes!

---

### Post by jeff.nitt on 2010-04-11
Which driver did you install?
I seem to be having problems with mine

---

