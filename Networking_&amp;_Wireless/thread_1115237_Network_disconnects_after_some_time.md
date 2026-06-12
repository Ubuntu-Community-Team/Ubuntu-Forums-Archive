---
title: "Network disconnects after some time"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by Manu311 on 2009-04-03
Hi,

I got a strange problem since I reinstalled my Debian Squeeze.
It also happens once while I installed Debian Lenny (no squeeze cd yet).
I cant reproduce it, nor can I find it in logs. But it happens always in the wrong moment and very often.
My Network totaly crashs. eth0 is still in ifconfig and ips are as well. But I can't ping my own ip! I can ping 127.0.0.1 but not my network ip, nor those of others like my router or the internet.
The only fix is restarting. But if I restart the pc crashes at "shutdown portmap". I can type, change screen, but I can't execute anything (can't write on other screens then screen 1 and there's no login screen or sth). It happens as well if I "sudo killall portmap" before I should down. An other error is "killing all processes: failed".
No Log file in /var/log has any informations about it and if I check my (passive) switch: the network is still connected (light is on and blinking). Also the other members of the network have no problems (but they can't ping me either after it crashes).

Maybe there are similar problems, but I have no idea for good search strings and didn't find something yet.

---

### Post by Manu311 on 2009-04-04
push

---

