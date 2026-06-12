---
title: "Evo Broadband Not Working???"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by MIRAAN Baloch on 2012-02-20
Hi,

I am new in Ubuntu, I have installed Ubuntu 11.10 All Others working Good But Evo 3G USB Modem Not working plz any one help me to solve this problem? 


**My Device: ZTE CDMA TECH**


I am waiting for your reply!

---

### Post by roelforg on 2012-02-20
Most of my network exp. is in wired net's but i'm gonna give it a shot.
Find out what kernel module it's using (google is your best friend) and load it with modprobe.
exec /etc/init.d/networking restart
and try configuring it, if it works, add the module to /etc/modules

I've got a Eminent USB Nic, it's module (pegasus2) always needs to be manually loaded (e.g. solved be adding pegasus2 to /etc/modules).

---

