---
title: "Using two ethernet cards"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by spiritech on 2010-04-08
i have just installed an extra gigabit ethernet card into both my computers and connected them upto a gigabit ethernet switch.

how can explain to my computer to use the extra eth cards and gigabit switch for remote viewing and FTP, and to use the onboard eth cards connected to my modem for internet access???

i configure the cards fine.

thank you

---

### Post by Iowan on 2010-04-08
A little out of my domain - but I suspect **iptables** rules could help. **route** might be another option (check **man route)**) - at least for default gateway (internet access).

---

### Post by spiritech on 2010-04-09
> **Iowan said:**
> A little out of my domain - but I suspect **iptables** rules could help. **route** might be another option (check **man route)**) - at least for default gateway (internet access).

ok thanks for your reply. is iptables terminal based command line. i was hoping there was a software suite that could do this. something that displays the traffic devices connected to my computer and then assign what goes where. 

if not and iptables is the only option i guess i'l have to leave it for now.

spiritech

---

### Post by chiwi on 2010-04-09
If I understood correctly, you want your Gbit card for LAN access (I suppose you have some other computers you FTP from) and the onboard device to internet surfing.

What yuo need to do is configure /etc/network/interfaces file. There you tell Ubuntu to configure one card facing the internal network, and the other one to the outside.



[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

[http://ubuntuforums.org/showthread.php?t=105764](http://ubuntuforums.org/showthread.php?t=105764)

---

