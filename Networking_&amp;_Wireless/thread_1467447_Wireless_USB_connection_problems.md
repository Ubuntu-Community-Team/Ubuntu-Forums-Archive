---
title: "Wireless USB connection problems"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by sicp on 2010-04-30
I installed Ubuntu (10.04) today and it has gone smoothly except for the  fact that I can't connect to the Internet when in Ubuntu (connection  works fine in Windows XP). I am using a wireless USB card (Linksys  WUSB600N) to connect.

The weird thing is that the card detects all the local networks, asks me  for a password to my network, and it even says it is connected to my  network after I put the password in -- but when I open Firefox no pages  will load.

There is another weird quirk as well: Ubuntu will not restart or shut  down properly (it hangs around indefinitely with the little white /  orange dots going across the screen) unless I first remove the wireless  card from the USB slot. But that doesn't bother me as badly as the lack  of Internet.

---

### Post by sicp on 2010-04-30
Okay, I solved this problem using a fix I found in another thread (not too long after posting this one, of course):

1. From terminal:
sudo gedit /etc/modprobe.d/blacklist.conf 
 
2. Paste the following into that file:
blacklist rt2800usb 
blacklist rt2x00usb 
blacklist rt2x00lib

3. Save file and restart.

^ For the benefit of anyone else who has this same problem.

---

### Post by M4xC4v413r4 on 2010-05-01
> **sicp said:**
> Okay, I solved this problem using a fix I found in another thread (not too long after posting this one, of course):

1. From terminal:
sudo gedit /etc/modprobe.d/blacklist.conf 
 
2. Paste the following into that file:
blacklist rt2800usb 
blacklist rt2x00usb 
blacklist rt2x00lib

3. Save file and restart.

^ For the benefit of anyone else who has this same problem.

Thanks m8, was having the same problem, now it's fixed :D

---

### Post by ncbb on 2010-05-01
> **sicp said:**
> Okay, I solved this problem using a fix I found in another thread (not too long after posting this one, of course):

1. From terminal:
sudo gedit /etc/modprobe.d/blacklist.conf 
 
2. Paste the following into that file:
blacklist rt2800usb 
blacklist rt2x00usb 
blacklist rt2x00lib

3. Save file and restart.

^ For the benefit of anyone else who has this same problem.

I upgraded to 10.04 from 9.10 (where I had the wusb600n working at N speeds, Bit Rate=130 Mb/s). On 9.10 my interface was ra0, on 10.04 it is wlan0 and I can only get A/G speeds, Bit Rate=54 Mb/s. Is there something else I need to do to get full N working?

lsusb
Bus 005 Device 002: ID 091e:0003 Garmin International GPSmap (various models)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000
Bus 001 Device 002: ID 1737:0071 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

dmesg | grep rt2
[   24.705986] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   24.717881] usbcore: registered new interface driver rt2870

---

