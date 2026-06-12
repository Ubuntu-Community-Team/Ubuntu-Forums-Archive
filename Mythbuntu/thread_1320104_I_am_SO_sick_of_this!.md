---
title: "I am SO sick of this!"
date: 2009-11-08
forum: Mythbuntu
---

### Post by Shockwav on 2009-11-08
:frown:

Mythbuntu 9.10 with Myth 0.22 and I get this after “sudo make install” of driver wis-go7007-linux-0.9.8-5 and a reboot.

mythbox@mythbox:~$ lsusb
Bus 002 Device 003: ID 093b:a004 Plextor Corp. ConvertX TV402U XLOADER

No /dev/video device exists. “sudo mount -t usbfs none /proc/bus/usb” works and this is the result
mythbox@mythbox:~$ lsusb
Bus 002 Device 005: ID 093b:a104 Plextor Corp. ConvertX PX-TV402U/NA

I added “ACTION==”add”, ATTRS{idVendor}==”093b”, ATTRS{idProduct}==”a104&#8243;, RUN+=”/usr/sbin/go7007_firmware_load”" to /etc/udev/rules.d/91-wis-ezusb.rules and I am now able to set up the device.

It does not appear to survive a reboot and I have to “sudo mount -t usbfs none /proc/bus/usb” to reacquire the device.

I’m also getting the “green screen” from the device as it connects and if I change channels it goes black, then kicks out with an “Unrecoverable recorder error”

Any ideas? Device works fine in Mythdora 4.

---

