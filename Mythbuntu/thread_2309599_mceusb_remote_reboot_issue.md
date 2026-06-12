---
title: "mceusb remote reboot issue"
date: 2016-01-11
forum: Mythbuntu
---

### Post by mraggie on 2016-01-11
It seems I am suffering the dreaded remote works until I reboot issue.  I have seen people post part of the solutions but I am not getting it.   I would like to create a udev rule to make sure that the mceusb is selected on reboot.   I need to get this fix for the wife an kids.

This is the what I see as the remote now IS Currently working

mythbox@mythbox:~$ ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event2) with:
	Driver mceusb, table rc-rc6-mce
	Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other 
	Enabled protocols: LIRC 
	Extra capabilities: <access denied>
Found /sys/class/rc/rc1/ (/dev/input/event4) with:
	Driver cx88xx, table rc-hauppauge
	Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other 
	Enabled protocols: LIRC 
	Extra capabilities: <access denied>
mythbox@mythbox:~$ 

and udevadm info -a /dev/lirc0

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.2/1-4.2:1.0/rc/rc0/input5/event2':
    KERNEL=="event2"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.2/1-4.2:1.0/rc/rc0/input5':
    KERNELS=="input5"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)"
    ATTRS{phys}=="usb-0000:00:1d.7-4.2"
    ATTRS{uniq}==""
    ATTRS{properties}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.2/1-4.2:1.0/rc/rc0':
    KERNELS=="rc0"
    SUBSYSTEMS=="rc"
    DRIVERS==""
    ATTRS{protocols}=="rc-5 nec rc-6 jvc sony sanyo mce_kbd [lirc]"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.2/1-4.2:1.0':
    KERNELS=="1-4.2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="mceusb"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{supports_autosuspend}=="0"



Can I get some help on making a udev rule to make sure the remote always works.  Thanks.

---

