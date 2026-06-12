---
title: "DWL-650 not working in Dapper"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by klaas on 2006-06-06
Hi all,

My wireless network does not work in Dapper (in Breezy it did!). My card is a D-Link DWL-650 and it is detected by UBUNTU. I can configure it but it does not get an IP from my router. The strange thing is that it has worked when I installed Dapper but after the first reboot this problem occurred!

Does anyone have this same problem and a solution?

Thanx,
Klaas

---

### Post by edwing on 2006-06-06
add the following line in the wlan0 section in /etc/network/interfaces:

wireless-mode = managed


I have the DWL-650+ and that line made it work for me. You can try specifiying the channel number if you're having difficulties:

wireless-channel = x

---

### Post by klaas on 2006-06-07
Thanx for the reply! I added "wireless-mode managed" and "wireless-channel x" to "etc/network/interfaces" but it still does not work. 

Any other sugestions?

---

