---
title: "Wireless not remaining stable"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by kmrkushal on 2012-10-07
Hi all,

For past 2 days, for some reason my Wifi is not remaining stable.(but my roomates are not facing a problem, so problem in router is gone).
I have ubuntu 12.04 and it has been working fine for past 1 month, but suddenly this problem started

Could you guys help me in debugging?

lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

---

### Post by kmrkushal on 2012-10-08
Still waiting? Anyone

---

### Post by varunendra on 2012-10-10
Hi Kushal, welcome to the forums!

Please run the following command (just copy-paste it in a terminal):
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will automatically download and run a script, and create a "**netinfo.txt**" file in your home directory. Copy-paste the contents of that file here. It will give us almost all the info required for troubleshooting.

---

