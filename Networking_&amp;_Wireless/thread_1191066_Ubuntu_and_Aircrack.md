---
title: "Ubuntu and Aircrack"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by Mariogeo on 2009-06-18
I installed Ubuntu and aircrack inside it and when i try to enable monitor mode it writes that ndiswrapper's driver is not support monitor mode. I installed my windows cd's wifi adapter
driver with ndiswrapper to get ubuntu regognize my adapter. What add-on driver i must use that supports monitor mode in linux and where can be obtained? Also i have no
access to the internet thru ubuntu but detects wireless networks. It is atheros chip and
i think is ar5008 because is 802.11n adapter. Also is it a better and easier live cd to
get that will work with my card? I have two adapters. One is tp-link wln951n pci card 
and the other is buffalo and i think the other has marvell chip and it works too.
Ubuntu is very driver friendly but i'm in bad luck that i have many problems capturing packets with my hardware and trying for days to make it work and i need better programs.

---

### Post by synapsys on 2009-06-18
First of all, this should probably be in the wireless section.

Second of all, ndiswrapper DOES NOT support monitor mode. You must use a different driver. You will need to find out which driver will work with your ar5008. It will probably be ath5k or madwifi-ng.

---

### Post by t4thfavor on 2009-06-18
The buffalo should be a Broadcom chip, which you can get a driver for, you just have to get the Firmware out of the windows driver. 


There are plenty of people out there using Aircrack under Ubuntu with a Broadcom chip (Myself included). 


If you want an easier method without spending alot of cash, buy a PCMCIA senao cb3054 card off of ebay, I think I got mine new for like $20USD.


If you need PCI, I have had good success with $10USD pci -> PCMCIA adapters and the above mentioned card.

If you want a really good card (you'll pay for it) find a Cisco cb21AG and you will not have anymore problems.

---

### Post by Mariogeo on 2009-06-18
> **synapsys said:**
> First of all, this should probably be in the wireless section.
 
Second of all, ndiswrapper DOES NOT support monitor mode. You must use a different driver. You will need to find out which driver will work with your ar5008. It will probably be ath5k or madwifi-ng.
 
Where should i download the drivers? Should it be the regular linux drivers from the
manufacturer's site or should it be ubuntu made drivers? Can you give me the link?

---

### Post by synapsys on 2009-06-18
[http://linuxwireless.org/en/users/Drivers/ath5k](http://linuxwireless.org/en/users/Drivers/ath5k)

---

### Post by Mariogeo on 2009-06-18
> **synapsys said:**
> [http://linuxwireless.org/en/users/Drivers/ath5k](http://linuxwireless.org/en/users/Drivers/ath5k)
 
Also my buffalo usb adapter uses Marvell 88w8360 topdog when i searched the internet. I'm not sure if it needs
ath5k or ath9k the card. Do you have links for those also?

---

### Post by synapsys on 2009-06-19
The ath** drivers are only for atheros chipsets, hence the 'ath' Not sure about marvell chipsets, you will probably have to end up using ndiswrapper for that. Check link here:

[http://ubuntuforums.org/showthread.php?t=1103837](http://ubuntuforums.org/showthread.php?t=1103837)

---

### Post by carcar1 on 2009-06-20
Try backtrack it uses some weird driver and works amazingly backtrack is really far ahead of ubuntu in wireless drivers.

---

### Post by adi_luk on 2010-03-22
Hello to everyone, i have a little problem using aircrack.For cracking a WPA i need the handshake protocol and i can get it by deconnecting an client of the AP.My question is, how do i get the mac address of an active client? Thank you very much!

---

