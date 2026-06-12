---
title: "Reliance Broadband Netconnect Devices"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by raunhar on 2010-10-19
I am planning to get a Reliance Broadband wireless internet for laptop.
The device options are:
ZTE and Huawei.

Which device is compatible with Ubuntu 10.04 and higher. Main thing is that the device should be easily recognised by the Network Manager without any hip-hops.

---

### Post by imol on 2010-10-19
My Huawei E182E is recognized without any issues

IMoL

---

### Post by gyussz on 2010-10-19
ZTE worked fine for me (now I use my phone as a modem).

---

### Post by lisati on 2010-10-19
My ZTE mobile phone works nicely as a modem with Ubuntu 10.04 on my laptop.

---

### Post by raunhar on 2010-10-19
Is ZTE AC2736 compatible. How to configure the modem with ubuntu 10.04

---

### Post by dineshs on 2010-10-20
raunhar,
with ref to your post [here ]("http://ubuntuforums.org/showthread.php?t=1599306")
> [ 2280.321188] usb 6-1: generic converter now attached to ttyUSB0
I believe you can make it work following any of the methods suggested [in this guide]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html")
Since wvdial and gnome-ppp are not available in 10.04 by default first try to configure the connection using```
sudo pppconfig
```follow instructions and when it asks for modem port type  [COLOR="Blue"]/dev/ttyUSB0[/COLOR]  and proceed.
To connect use```
pon
```
If you have any difficulty post back.[URL="http://ubuntuforums.org/showthread.php?t=1466490"]
Note:Here[/URL] is a guide by alexfish

---

### Post by raunhar on 2010-10-20
I was able to get the device work with Ubuntu. Now it works under network manager--Mobile Broadband.
But, i am not sure, if it is working as High speed (3.1MBps) or simply 1x speed.

I there any way to find it out.

---

