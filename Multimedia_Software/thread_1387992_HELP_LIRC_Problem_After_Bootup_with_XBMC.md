---
title: "HELP LIRC Problem After Bootup with XBMC"
date: 2010-01-22
forum: Multimedia Software
---

### Post by stpfarms on 2010-01-22
Running:
Ubuntu/Mythbuntu 9.10
XBMC 9.11

I am having a problem with LIRC and my Antec Veris and XBMC. On a fresh boot, I have to initiate a "sudo /etc/init.d/lirc start" or XBMC will not pick up any commands even though IRW records all my buttons pressed. When I run XBMC in DEBUG mode I see no LIRC commands, but after I start LIRC it will. LIRC_IMON is definitely being assigned to my Antec Veris on boot. I accomplish this by having the following UDEV rule to make sure USBHID doesn't take it over:


cat /etc/udev/rules.d/99-imon.rules

SYSFS{idVendor}=="15c2", SYSFS{idProduct}=="0043", MODE="0666", PROGRAM="/bin/sh -c 'echo -n $id:1.0 >/sys/bus/usb/drivers/usbhid/unbind;\
echo -n $id:1.1 >/sys/bus/usb/drivers/usbhid/unbind'"



One thing I notice is after a fresh boot I do an LS /dev and I get lirc0 in yellow and lircd in pink, but after I "sudo /etc/init.d/lirc start" lircd turns to light blue. Any ideas?

---

### Post by stpfarms on 2010-01-25
Bump... any ideas?

---

