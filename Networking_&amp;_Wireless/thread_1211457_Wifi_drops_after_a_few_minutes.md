---
title: "Wifi drops after a few minutes"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by Domoconnor on 2009-07-12
Hey, I have just installed Ubuntu 9.04. To start with I can connect to my wireless network fine but after a few minutes it just drops. The network manager still says I am connected but I can't access any sites of or ping anything. I have installed the driver for my wireless card( RTL8187B Wireless Adapter) using ndiswrapper but it still drops after about 5 minutes. I would be very grateful for any help.

Thanks in advance,
Dom

---

### Post by Crafty Kisses on 2009-07-12
When the connection drops, try to reconnect by running:
```
ifconfig wlan0 down
ifconfig wlan0 up
```
See if that reconnects. I will help you further, but I just want to see if you can reconnect by running the above commands.

---

### Post by Domoconnor on 2009-07-12
Nope. That doesn't work for me.

---

### Post by Crafty Kisses on 2009-07-12
Here's a couple of things I want you to try. First when the wireless is up, run the following command:
```
lsmod
```
Then when the wireless drops, run the exact same command, and post the results.

---

### Post by superprash2003 on 2009-07-13
take a look at this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by Domoconnor on 2009-07-13
All fixed now. I just installed Wicd and it seemed to work.

---

