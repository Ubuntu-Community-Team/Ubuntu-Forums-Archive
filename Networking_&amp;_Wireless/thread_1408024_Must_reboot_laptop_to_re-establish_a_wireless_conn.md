---
title: "Must reboot laptop to re-establish a wireless connection"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by Sredni Vasthar on 2010-02-15
Hi All,

I have a problem with the Ubuntu 9.10 wireless connection to my router, that IF the router is reset (power on reset) during an active connection, I have to reboot my laptop to re-connect to the router. I did not have this problem with the previous Ubuntu (JJ) version. It does happen quite often for me because the router is installed in another room and the brat in the house gets immense pleasure in playing with it's power switch :D. However, the strange thing is that disconnect - reconnect works if I do it from the Ubuntu software interface (without resetting the router).

It's probably some simple issue, but I am quite new to Ubuntu and do not know the ropes well...

S

---

### Post by ant2ne on 2010-02-15
next time try 
```
sudo ifconfig wlan0 down &&  sudo ifconfig wlan0 up
```
assuming that your wifi device is on wlan0. It could be (and often is) eth1. you can do a iwlist scanning, and the device that succeeds at a scan is the device we are looking for.

WHY You have to power off and on the device I can't tell you.

---

### Post by zaphod777 on 2010-02-16
I had tons of wireless issues until I did a clean install of 9.04 and then upgraded to 9.10. Now I am a happy camper with a rock solid wireless connection.

---

### Post by Sredni Vasthar on 2010-02-20
Thanks for the replies guys, but the problem still persists. When I do a iwlist scanning (while I am connected say now), I get a reply with 4 ports - eth0, eth1, irda0, lo. All of these "Interface does not support scanning"... But by looking at the statistics in Network Tools, I'm sure that the connection is on eth1.

I did in fact start with 9.04, which I then upgraded to 9.10. And I didnt have this problem in 9.04..

---

