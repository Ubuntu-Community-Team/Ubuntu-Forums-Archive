---
title: "wireless permanence"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2006-07-08
I can get my usb wireless dongle activated with insmod/ifconfig
How do I make thes commands permanent from one boot to another

---

### Post by stupidkid on 2006-07-08
Add 
wireless-essid <essid> 
wireless-key <key>
to your /etc/networking/interfaces under you wireless interface.

---

