---
title: "webcam not working with xubuntu 12.04"
date: 2012-08-12
forum: Multimedia Software
---

### Post by stevemasterson on 2012-08-12
webcam on dell inspiron 910 netbook not working in ubuntu or xubuntu. I installed cheese and it gives me a no device found error. Any help would be very much appreciated.

Thank You

---

### Post by papibe on 2012-08-12
Hi stevemasterson.

Usually built-in webcam are internal usb devices.

Could you post the result of this command?
```
lsusb
```
Regards.

---

### Post by stevemasterson on 2012-08-13
stephen@stephen-Inspiron-910:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:a118 Suyin Corp. 
Bus 002 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
stephen@stephen-Inspiron-910:~$

---

### Post by gordintoronto on 2012-08-13
Puzzling. This page: [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)
says that webcam should work. (ID 064e:a118)

Can you paste uname -a output?

You might try camorama, but that's a long shot.

---

### Post by stevemasterson on 2012-08-13
No Luck. Thanks for trying, much appreciated

---

### Post by gordintoronto on 2012-08-13
Another person who had difficulty with that computer's webcam discovered it was an intermittent connection of the internal cable. That shouldn't be the case, since it shows up in lsusb. But you never know.

---

### Post by arkhan101 on 2012-10-08
Hi, 
I encountered the same problem on Asus eee pc but after installing cheese when i restarted the system and turned off the 'OS installation' to finished in BIOS (advance settings) then the cam worked properly. hope it will also work for:)

---

