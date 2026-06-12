---
title: "USB-Headset with Feisty Fawn"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by anon66 on 2007-10-15
Hi there!

I'd like to use my USB-Headset with Ubuntu Feisty Fawn. Is there a way to get it working?

My headset has a CMedia chipset if it matters.

Currently it is not even recognised by
aplay -l


Best regards anon66

---

### Post by anon66 on 2007-10-16
for now i found out that that my /var/log/messages contain the following:

Oct 16 19:39:53 ubuntu kernel: [ 6926.909460] input: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-sb_02-2.2

Oct 16 19:39:53 ubuntu kernel: [ 6926.909406] input: C-Media USB Headphone Set   as /class/input/input2

is there a way to use it with any application ?


Best regards

---

### Post by anon66 on 2007-10-19
hi there!

fixed my problem. it is caused by my custom kernel.

---

