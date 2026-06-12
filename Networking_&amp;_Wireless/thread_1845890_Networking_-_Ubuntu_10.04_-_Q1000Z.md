---
title: "Networking - Ubuntu 10.04 - Q1000Z"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by brett- on 2011-09-17
I solved this problem but thought I would post in case someone had a better solution.

I recently "upgraded" to VDSL and was required to change modem to Q1000Z.  Modem installation went fine and no trouble connecting to internet.  Had three other Linux machines with Samba set up to share folders before installing Q1000Z modem.  After modem change out Samba did not work.

Fix - 

1.  Assigned static IP addresses in modem for each connected device (192.168.0.XX).

2.  Added assigned static IP address and device names to /etc/hosts (192.168.0.XX device_name).

Why did I have to go through this mess?  Now if another device joins the share, that devices /etc/hosts file must be modified as above.

I can't figure out the difference between the old ADSL modem and the new Q1000Z ADSL modem (no fire wall used in Ubuntu or modem).

---

