---
title: "Network issues"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by Linuxisgod! on 2008-12-16
Guys 
i am a unix linux bod by trade but i am a little stumped has anyone seem the following issue before.
i have just installed a fresh install of 8.10 on a hp pavillion D7-1103ea laptop but it will not connect at home to my wired network it tries ok but then just disconnects, but i get to work and it works perfectly, but it seems everywhere else it will not connect.
also my wireless is unable to be turned on manually as well as from the touch panel.
regards 
    A

---

### Post by Iowan on 2008-12-16
Are home and work both DHCP, static, or a combination?
Post results of **ifconfig** at home.

---

### Post by cmnorton on 2008-12-17
Is there anything tell-tale in your logs? /var/log/syslog, /var/log/messages, or the output of dmesg?

---

