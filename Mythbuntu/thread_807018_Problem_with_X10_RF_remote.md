---
title: "Problem with X10 RF remote"
date: 2008-05-25
forum: Mythbuntu
---

### Post by hfl on 2008-05-25
Hello,

I've got a strange problem with getting a remote to work properly.
I'm using Mythbuntu 8.04 and have a OR22V RF remote that shipped with my Hauppauge PVR-150 TV card.

The good thing is that the remote is being recognised in Mythbuntu Control Centre by selecting the ATI/Nvidia X10 RF (Userspace) driver. By selecting this driver, and restarting the mythtv frontend, I was able to use my remote quite well.

However, every time after rebooting my machine, the system doesn't recognise the remote anymore. After manually re-selecting the X10 RF Userspace driver in Mythbunu Control Centre, and restarting the frontend, the remote works again.

Does anyone have any ideas what causes this behaviour?

This is my dmesg output, related to lirc

```

me@mediacenter-tv:~$ dmesg | grep lirc
[  145.274035] lirc_dev: IR Remote Control driver registered, at major 61 
[  145.299588] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[  145.299594] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[  145.304567] lirc_dev: lirc_register_plugin: sample_rate: 0
[  145.319051] lirc_atiusb[2]: X10 WTI RF receiver on usb2:2
[  145.334386] usbcore: registered new interface driver lirc_atiusb
[  145.385392] lircd[6511]: segfault at 000000f3 eip 08050500 esp bfc49340 error 4
[  145.415631] lircd[6517]: segfault at 000000f3 eip 08050500 esp bfc7fa50 error 4
[  168.745109] usbcore: deregistering interface driver lirc_atiusb
[  168.745199] lirc_atiusb[2]: usb remote disconnected
[  227.674929] lirc_dev: IR Remote Control driver registered, at major 61 
[ 1253.085781] lirc_dev: IR Remote Control driver registered, at major 61 
[ 1253.101541] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[ 1253.101547] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[ 1253.109853] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 1253.124588] lirc_atiusb[2]: X10 WTI RF receiver on usb2:2
[ 1253.143602] usbcore: registered new interface driver lirc_atiusb
[60023.114067] usbcore: deregistering interface driver lirc_atiusb
[60023.114140] lirc_atiusb[2]: usb remote disconnected
[60023.938225] lirc_dev: IR Remote Control driver registered, at major 61 
[60023.982569] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[60023.982575] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[60023.989181] lirc_dev: lirc_register_plugin: sample_rate: 0
[60024.005035] lirc_atiusb[2]: X10 WTI RF receiver on usb2:2
[60024.018963] usbcore: registered new interface driver lirc_atiusb
[60024.077803] lircd[16847]: segfault at 000000f3 eip 08050500 esp bff56e50 error 4
[60024.139746] lircd[16859]: segfault at 000000f3 eip 08050500 esp bff650f0 error 4
[60044.934164] usbcore: deregistering interface driver lirc_atiusb
[60044.934250] lirc_atiusb[2]: usb remote disconnected

```

Here's my lsusb output
```

me@mediacenter-tv:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 002: ID 046d:c310 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0bc7:0006 X10 Wireless Technology, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Thanks for any help.

---

### Post by volkswagner on 2008-05-25
You may need a udev rule.

---

