---
title: "/etc/network/interfaces not booting on startup?"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by nateuni on 2010-09-23
Hi,

When I boot into Ubuntu with the Xfce desktop then proceed to terminal to check my IP it is always some random IP as provided via DHCP by the router. If I then go to the cmdline and type sudo /etc/init.d/networking restart then the wifi correctly connects to the router to the one static network address that I have specifically provided for it - as stated in my interfaces file.

Why is this not happening on startup?  And how do I fix this?

Regards,
Nate

---

### Post by Iowan on 2010-09-23
I presume there's an "auto" line for the wireless interface in */etc/network/interfaces*.

---

### Post by BkkBonanza on 2010-09-24
Also if you have Network Manager (little icon top right desktop) then it will "take over" control and default to DHCP, unless you specifically configure it for static. It "rewrites" the interfaces according to it's needs.

---

