---
title: "Hauppage nova-t-500 not detected in /dev/dvb"
date: 2008-11-15
forum: Mythbuntu
---

### Post by bemorgan on 2008-11-15
Hi,

I'm trying to get Ubuntu to recogonise a Hauppage nova-t-500 tv tuner card on a 8.10 installation (not mythbuntu). I tried installing the relevant modules and firmware but the device is not registering in /dev/dvb/...

It looks like the device is being picked up as a USB device (as i understand it the pci card actually contains a usb controller):

lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 045e:008a Microsoft Corp. Wireless Keyboard and Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 10b8:0066 DiBcom 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

however it doesn't appear to be mounting this 'DiBcom' device anywhere.

When i check the pci devices i think this is it:

03:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

When i reload the dvb module, it doesn't detect any devices:

sudo modprobe dvb-usb-dib0700
dmesg | grep -i dvb
[ 1136.579563] usbcore: registered new interface driver dvb_usb_dib0700

I've had a look at the various forum and wiki articles:

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)
[http://ubuntuforums.org/showthread.php?t=797525](http://ubuntuforums.org/showthread.php?t=797525)
[http://ubuntuforums.org/showthread.php?t=981131](http://ubuntuforums.org/showthread.php?t=981131)

I think i've installed the correct modules:
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dibusb-mc.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dib0700.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dibusb-mb.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dibusb-common.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/frontends/dib7000p.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/frontends/dib7000m.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/frontends/dib0070.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/frontends/dib3000mc.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/frontends/dib3000mb.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/frontends/dibx000_common.ko

kernel version:
2.6.27-7-generic

A check of the kernel logs reveals that it is not finding anything:
dmesg | grep -i dv

The appropriate firmware is available:
ls /lib/firmware/dvb-usb-d*
/lib/firmware/dvb-usb-dib0700-1.10.fw     /lib/firmware/dvb-usb-dibusb-6.0.0.8.fw
/lib/firmware/dvb-usb-dibusb-5.0.0.11.fw  /lib/firmware/dvb-usb-dtt200u-01.fw

And V4L:
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/v4l2-common.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/v4l2-int-device.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/v4l1-compat.ko

I've added the options to modprobe:
options dvb-usb-dib0700 force_lna_activation=1
options dvb-usb-dib0700 debug=1

And i've tried powering down the computer, waiting and restarting to get a cold update of the firmware.

I've tried the newer version of the firmware (dvb-usb-dib0700-1.20.fw) but that didn't work either.

I tried turning up the log levels for udev but couldn't work out if it was telling me if it found the device.

This device is meant to be supported out of the box. If i re-install Ubuntu with now with the device installed, would that be more likely to pick up the device?

Any help with this would be most welcome.

Ben

---

