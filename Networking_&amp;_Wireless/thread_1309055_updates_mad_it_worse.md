---
title: "updates mad it worse"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by shiggydiggy on 2009-11-01
I'm running 9.10 Krazy Koala. The only way i can get on the net is a huawei e169 and Koala didn't want to talk to my little huawei

i was refered to a work around:
"safely remove" the virtual CD and SD card reader on the dongle
then run

sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x1001
sudo pppd ttyUSB0

and that worked untill i installed today's updates.
It's like the e169 is not detected anymore
:(
it's not a bug, it's a feature right ;)

any help greatly appreciated

---

### Post by shiggydiggy on 2009-11-01
bump?

---

