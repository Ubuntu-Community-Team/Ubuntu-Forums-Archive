---
title: "USB TV Capture Card Not Working"
date: 2013-03-10
forum: Multimedia Software
---

### Post by srinathnitb on 2013-03-10
Hi,

I have a usb tv capture card and its not working in xubuntu.

I have installed tvtime to view the card output.

My usb is recognised as "Arkmicro Technologies Inc. ". Output of lsusb is below

srinath@srinath-desktop:/usr/sbin$ lsusb
Bus 001 Device 008: ID 18ec:3280 Arkmicro Technologies Inc. 
Bus 001 Device 004: ID 0bc2:3000 Seagate RSS LLC 
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

When I open tvtime , its says "Cannot open capture device /dev/video0".

Please help

Regards
Srinath

---

### Post by sanderj on 2013-03-10
Unplug the USB tv stick, wait 5 seconds, plug it in again, and check the last page of

```
dmesg
```

(which you have to type in a terminal)

And: which *Ubuntu version are you using?

---

### Post by srinathnitb on 2013-03-10
Hi,

Thanks a lot for your reply.

I am using xubuntu and below are the version details and last 10 lines of my dmesg after unplugging and plugging in my capture card.

srinath@srinath-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

srinath@srinath-desktop:~$ dmesg | tail -10
[   30.044013] i915: render error detected, EIR: 0x00000010
[   34.085355] show_signal_msg: 39 callbacks suppressed
[   34.085364] apt-check[2095]: segfault at c14ce500 ip b713bc2c sp bfc07780 error 5 in libapt-pkg.so.4.12.0[b70ee000+11d000]
[   60.162032] usb 1-1: USB disconnect, device number 2
[   66.696023] usb 1-1: new high-speed USB device number 5 using ehci_hcd
[   66.828925] usb 1-1: New USB device found, idVendor=18ec, idProduct=3280
[   66.828931] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   66.828936] usb 1-1: Product: USB3280DEVICE
[   66.828940] usb 1-1: Manufacturer: USBTVBOX
[   95.267089] type=1701 audit(1362909066.262:25): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2217 comm="chromium-browse" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb2f20424 code=0x50000

Regards
Srinath

---

### Post by sanderj on 2013-03-10
I had hoped for some more info in dmesg, for example "firmware not found". Not so. Pity.

Your usb stick's USB-ID does not yield any results in Google. Is it a new product?

Further steps:

If you start tvtime from a terminal, what info do you see in the terminal?  
What's the output of "ls -al /dev/vid*"?
You could download and live boot Ubuntu 13.04, plugin the USB stick, and see what happens. (=long shot)

---

### Post by srinathnitb on 2013-03-10
Its not a new product. I bought it a year ago and its working fine with Windows 7. Just that my system is getting corrupted with Virus , I moved to Ubuntu. I did do some research myself before posting here in this forum but no luck.

The exact model name is "tech-com ssd-126" you can google this and see. Its a usb tv capture card with FM.

There are no video devices listed in /dev/vid*.

Here are the outputs you requested.

srinath@srinath-desktop:~$ ls -al /dev/vid*
ls: cannot access /dev/vid*: No such file or directory

srinath@srinath-desktop:~$ sudo tvtime
[sudo] password for srinath: 
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/srinath/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.
Thank you for using tvtime.

Hope some boarders like you will help me. If it doesnt get resolved for about a week , I will try the upgrade option.

Regards
Srinath

---

### Post by sanderj on 2013-03-10
If there are no /dev/vid* files, I would say Linux does not know how at all how to handle your USB TV-stick hardware. You could have a look at /var/log/syslog if it says anything when you plug in the stick.

Furthermore: did you live-boot Ubuntu 13.04, plug in the stick and checked /dev/vid* ?

FWIW: I only use DVB USB sticks as my my cable provider stopped providing analog TV signal a few years ago. So I have no experience with analog-TV sticks like yours.

---

### Post by sanderj on 2013-03-10
Some more tips

```
sudo apt-get install input-utils
sudo lsinput
```

And:

```
udevadm monitor --udev
```

and then plug in your USB stick.

---

