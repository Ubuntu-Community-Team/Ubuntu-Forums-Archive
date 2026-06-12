---
title: "Webcam image upside down"
date: 2009-05-22
forum: Multimedia Software
---

### Post by bawig1 on 2009-05-22
Hi,

I am running the 9.04 Disk as a Live CD to test all my hardware. I was testing my webcam with Ekiga and it works, the only problem is the image is upside down. Why would the image be upside down? Is there any way to 'flip' the image?

Brett.

---

### Post by bawig1 on 2009-05-27
I'm still having problems with this..I had a look at [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
 
and was looking for EasyCam2 but am still unable to find it. ```
lsusb
``` produces

```
Bus 002 Device 003: ID 04f2:b106 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1164:1f08 YUAN High-Tech Development Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 147e:1000  
Bus 005 Device 002: ID 0b05:1751 ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```and I'm pretty sure my camera is the Chicony Electronics Co., Ltd device. How do I find out which driver I am using? Is there any other places I can look for for info to flip the webcam image.... echo 1 > vflip doesnt work either.

thanks,

Brett.

---

### Post by bawig1 on 2009-05-27
according to [http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices) my device is supposed to be supported.

---

### Post by JUMmi on 2009-05-27
Hi,

have you tried: echo 0 >/sys/class/video4linux/video0/vflip
that works for me.

Jarmo Uusi-Maahi
Finland

---

### Post by bawig1 on 2009-05-27
Hi Jarmo,

I try that and get the same result as echo 1 > vflip

```
sudo echo 0 > /sys/class/video4linux/video0/vflip
bash: /sys/class/video4linux/video0/vflip: No such file or directory

```then if I try

```
sudo touch /sys/class/video4linux/video0/vflip
```I get

```
touch: cannot touch `/sys/class/video4linux/video0/vflip': No such file or directory

```and I have tried to use chmod but it doesnt work.

thanks anyway Jarmo,

Brett.

---

