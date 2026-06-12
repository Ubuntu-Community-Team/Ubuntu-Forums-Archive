---
title: "Huawei E160 Problems (Possible workaround)"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by astrilae on 2009-09-13
After using one of these devices for a while now, I have naturally come across the problem, upon the tail of dmesg, to see a bunch of connects/disconnects.

My way of dealing with this is as follows.

1. Remove dongle.
2. Enter:```
sudo rmmod option
sudo rmmod usbserial
sudo rmmod usb_storage
```
3. Insert dongle. -Do not click nm-applet-
4. Keep checking dmesg. This works for me around 85/90% of the time, rather than constantly like it does at times.

Hopes that helps some people.

---

