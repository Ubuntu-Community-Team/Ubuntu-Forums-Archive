---
title: "help with reliance zte ac8710"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by sri chandan on 2009-08-28
[SIZE=2]hai,
     i am a newbie to linux and am trying to connect to internet using my reliance zte ac8710 evdo card. can anyone help????
i modified the boot/grub/menu.lst file and inserted usbserial.vendor=0x19d2 usbserial.product=0xfff1..afterwards i rebooted the system and ran usb_modeswitch. however i found nothing of use... pl help


root@chandu-ubuntu:/# usb_modeswitch

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.3 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 002 on bus 002 ...
Using endpoints 0x09 (out) and 0x89 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
 Could not send INQUIRY message (error -2)

Device description data (identification)
-------------------------
Manufacturer: ZTE, Incorporated
     Product: USB Storage
  Serial No.: 000000000002
-------------------------
Sending Huawei control message ...
 OK, Huawei control message sent
Note: ignoring MessageContent. Can't combine with special mode

Checking for mode switch (max. 3 times, once per second) ...
 Original device can still be accessed. Hmm.
 Original device can still be accessed. Hmm.
 Original device can still be accessed. Hmm.


root@chandu-ubuntu:/# tail -f var/log/messages
Aug 28 16:35:18 chandu-ubuntu kernel: [  175.897448] sr: Sense Key : No Sense [current] 
Aug 28 16:35:18 chandu-ubuntu kernel: [  175.897454] sr: Add. Sense: No additional sense information
Aug 28 16:35:18 chandu-ubuntu kernel: [  176.564325] sr: Sense Key : No Sense [current] 
Aug 28 16:35:18 chandu-ubuntu kernel: [  176.564330] sr: Add. Sense: No additional sense information
Aug 28 16:35:18 chandu-ubuntu kernel: [  176.571323] sr: Sense Key : No Sense [current] 
Aug 28 16:35:18 chandu-ubuntu kernel: [  176.571328] sr: Add. Sense: No additional sense information
Aug 28 16:35:18 chandu-ubuntu kernel: [  176.578319] sr: Sense Key : No Sense [current] 
Aug 28 16:35:18 chandu-ubuntu kernel: [  176.578323] sr: Add. Sense: No additional sense information
Aug 28 16:35:18 chandu-ubuntu kernel: [  176.599311] sr: Sense Key : No Sense [current] 
Aug 28 16:35:18 chandu-ubuntu kernel: [  176.599315] sr: Add. Sense: No additional sense information

[/SIZE]

---

### Post by GeorgeVita on 2009-08-28
Hi **sri chandan**, welcome to this forum!
As I do not have your h/w I can give you just some ideas, stating that ZTE and ubuntu/linux means ... 'under construction'!

I think the solution for your problem is at:
[http://ubuntuforums.org/showthread.php?t=1185452](http://ubuntuforums.org/showthread.php?t=1185452)
[http://travisneotyler.blogspot.com/2009/07/back-on-wireless-web.html](http://travisneotyler.blogspot.com/2009/07/back-on-wireless-web.html)

As described there, the initial state of AC8710 is the virtual CDROM (19d2:fff6) and after switching to 'real modem' state (19d2:fff1) can be usbserial-ised to get the /dev/ttyUSBx ports.

FIRST try to get 19d2:fff1 to **lsusb** terminal command:
The switch from CDROM to modem can be done with various methods but as you are close to make it with usb_modeswitch just check configuration file and [latest info]("http://www.draisberghof.de/usb_modeswitch/"). Alternative to check: [udev-extras]("http://ubuntuforums.org/showthread.php?t=1211787")

SECOND: get the /dev/ttyUSBx ports and connect using (usually) /dev/ttyUSB2
you probably have 9.04 with usbserial encapsulated into kernel (that's why you modified boot/grub/menu.lst). Later when you make the connection and update to a new kernel you will use the 'standard' way to do that: 'sudo modprobe usbserial ...'

Test the state of AC8710: ```
lsusb | grep 19d2
``` and system activity about creation of /dev/ttyUSBx ports ```
dmesg | grep ttyU
```

Regards,
George

---

### Post by kharesam on 2009-08-31
Hi Sri Chandan,
  I am using the same evdo card. I have got it working on my laptop. In case you still have not got it working, I am attaching the usb_modeswitch.conf file. Hope it helps you.

Regards,
Sameer

---

