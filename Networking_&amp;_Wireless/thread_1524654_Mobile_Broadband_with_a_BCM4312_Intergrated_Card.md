---
title: "Mobile Broadband with a BCM4312 Intergrated Card"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by DalaiFarma on 2010-07-05
Hello everyone,

This is my first ever Attempt at Linux so please be kind ;)

Here are my Specs:

Netbook: HP Mini 210-1012EZ
Network Card: Broadcom Corporation BCM4312 802.11b/g (rev 01
Ubuntu: 10.04 Netbook Remix
CPU: 32Bit

Wired and Wireless Networks work perfectly the only issue is the Mobile Broadband.

When I try to setup my Mobile Broadband connection manualy using the Network Connections Manager the device drop-down is grayed out and it doesn't seem like my network card is being recognized as a Mobile Broadband Card.

When I had Windows 7 installed and started ubuntu over a USB Drive the connection worked great.

I've followed the steps at [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) too and it all checked out.

I found another idea in a thread here and I've tried that too:

I added the following line to my /etc/modules:

echo b43 | sudo tee -a /etc/modules

I've also tried using the Broadcom STA drivers that ubuntu offers but it doesn't seem to make any difference.

Nothing did any good.

Please feel free to yell at me for probably forgetting the one piece of info you actually needed to help me :)

---

### Post by ieee488 on 2010-07-05
mobile broadband?

do you even understand what that term means?

you can't get mobile broadband with a network card with BCM4312 chipset

---

