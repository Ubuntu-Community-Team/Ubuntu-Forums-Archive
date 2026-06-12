---
title: "xbox360-gamepad doesn'r work with xpad or xboxdrv"
date: 2015-09-09
forum: Multimedia Software
---

### Post by Michael_Richardsso on 2015-09-09
hi,

i've tried to use my xbox360-controller on my lubuntu machine. i tried both, xpad and xboxdrv.

_xpad_
connected the controller to the machine, 'sudo modprobe joydev' and 'sudo modprobe xpad' (i could find the xbox360 receiver with lsusb), but the controller doesn't connect to the receiver. on my windows machine and when i use xboxdrv the controller connects very fast. maybe xpad doesn't work with my receiver/gamepad?

_xboxdrv_
installed xboxdrv and set xpad to blacklist. after connecting the receiver to my machine and start xboxdrv the controller connected without any problem to the receiver and i could use them. i set an autoload of the driver in /etc/rc.local (xboxdrv --config file --silent). but when i didn't use the controller for some hours or disabled it manually and rebooted the machine the receivers led doesn't shine. when ubuntu is booted it seems that xboxdrv isn't loaded because it couldn't find the receiver (when the controller is on during the boot process the receiver doesn't go out). so i have the problem: to driver loading because the receiver is off and no receiver start because the driver isn't loaded?

i've tried several usb ports, thats not the problem.

michael

---

