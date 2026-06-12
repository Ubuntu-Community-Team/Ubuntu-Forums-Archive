---
title: "SIIG Vista MCE Remote detected as keyboard...?"
date: 2010-12-09
forum: Mythbuntu
---

### Post by mnelson100 on 2010-12-09
Hi... I'm trying to get my new SIIG Vista MCE Remote setup and I'm having some trouble.  I'm running 10.10 and it seems to detect it as a keyboard... which wouldn't be a big deal, but many of the buttons don't work.  If it were found as a lirc_mceusb device, I think I'd have better luck...

lsusb returns:
Bus 004 Device 002: ID 147a:e031 Formosa Industrial Computing, Inc.

dmesg | grep Formosa returns:
[    1.830821] input: Formosa21 IR603 HID MCE as /devices/pci0000:00/0000:00:11.2/usb4/4-1/4-1:1.0/input/input2
[    1.831661] generic-usb 0003:147A:E031.0001: input,hiddev96,hidraw0: USB HID v1.11 Keyboard [Formosa21 IR603 HID MCE] on usb-0000:00:11.2-1/input0

Thanks for your advice!

---

