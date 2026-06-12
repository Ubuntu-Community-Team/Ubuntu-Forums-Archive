---
title: "kwrold dvb-t not working"
date: 2010-02-21
forum: Multimedia Software
---

### Post by aivoonu on 2010-02-21
lsusb

Bus 001 Device 004: ID 1b80:e383 Afatech 


dmesg

[   16.068941] AF901X: af901x_module_init
[   16.068969] usbcore: registered new interface driver dvb_usb_af901x

how i can install dvb-t card in ubuntu

---

### Post by laceration on 2010-02-21
You probably need some firmware.  The best source for dvb setup instructions + whether cards are supported(most kworlds are) is
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

---

### Post by aivoonu on 2010-02-21
lsmod | grep dvb
dvb_usb_af9015         61576  0 
dvb_usb                16741  1 dvb_usb_af9015
dvb_core              102897  1 dvb_usb

i put firmware /lib/firmware/uname -r/firmware.fw 

sudo modprobe firmware

but nothing

no dev/dvb/ working

---

### Post by laceration on 2010-02-21
You do realize that it is not literally "uname -r", but the result of uname -r typed int the command line??  It will return your kernel version.

Anyways the best place to put it is in
/lib/firmware/
That way it will still work when the kernel is upgraded.

---

### Post by aivoonu on 2010-02-21
i put /lib/firmware firmware but still nothing 

something is wrong but i dont know how find

---

### Post by laceration on 2010-02-21
Where did you get your firmware?
I did a little digging at linuxtv.org and found:
[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/)

try that one.
Do you have a relatively recent version of Linux?  The kernel only supports your device as of 2.6.28.

What program are you using to tune/watch with?

---

