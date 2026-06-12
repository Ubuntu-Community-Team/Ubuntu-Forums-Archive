---
title: "Low Wireless to Wireless transfer speed on home network"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by VVoodstock on 2010-06-14
I have:
D-Link DIR-655 router

Laptop running Lucid 10.04 with Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)using Broadcom B43legacy wireless driver

Desktop running Lucid 10.04 with Network controller: RaLink RT2561/RT61 802.11g PCI

I setup a local network at home and when attempting to transfer a 1.4 gig file the rate was a steady 220 Kbps. Both wireless cards have good/full signal strength. Someone suggested I try an ftp server situation but the result was the same, approx 240 Kbps. How can I determine where my network bottleneck is? I have router set to use 802.11g only, as although it supports 802.11n my computers still only have g nic cards. Am I wrong in thinking this speed should be quite a bit higher? 
Thanks in advance for any help! I am a bit of a newbie but Ubuntu and Linux have stolen me away from Windows! Great support and OS!!

---

### Post by derrick81787 on 2010-08-05
I just installed that same wireless card and I'm having the same problems.  My local network is so slow that when I attempt to access an NFS share that is on the computer containing the wireless card, the other computer freezes.  It is also causing the internet to be extremely slow on the computer that contains the card.

I haven't found a solution that has worked yet.  However, I saw somewhere that a guy claimed to fix it by installing ndiswrapper and using it to install the Windows drivers for this card.  I think I'm going to attempt to do that tonight, and hopefully that will work out.

- Derrick

---

