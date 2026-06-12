---
title: "Make /dev/video/tv, /dev/video/webcam is not working"
date: 2008-12-05
forum: Multimedia Software
---

### Post by giorgosc61 on 2008-12-05
Hello,

I have Intrepid Ibex and 3 video sources:

1) Creative Webcam
```
giorgos@giorgos-desktop:~$ lsusb | grep Creative
Bus 002 Device 004: ID 041e:4034 Creative Technology, Ltd WebCam Instant

```

2) Conexant TV Card and

3) Avermedia TV Card

```
giorgos@giorgos-desktop:~$ lspci -vnn
03:05.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
	Subsystem: Avermedia Technologies Inc Device [1461:f11d]
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

03:07.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
	Subsystem: Conexant Systems, Inc. Device [14f1:ea3d]
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

03:07.1 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8811] (rev 05)
	Subsystem: Conexant Systems, Inc. Device [14f1:ea3d]
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88_audio
	Kernel modules: cx88-alsa

```

I have modified

```
giorgos@giorgos-desktop:~$ sudo nano /etc/udev/rules.d/95-perso.rules
SUBSYSTEMS=="pci", SYSFS{vendor}=="0x14f1", SYSFS{device}=="0xea3d", SYMLINK+="video/vcapture"
SUBSYSTEMS=="pci", SYSFS{vendor}=="0x1002", SYSFS{device}=="0x4397", SYMLINK+="video/webcam"
SUBSYSTEMS=="pci", SYSFS{vendor}=="0x1131", SYSFS{device}=="0x7133", SYMLINK+="video/tv"

```

I have added

```
giorgos@giorgos-desktop:~$ sudo nano /etc/udev/rules.d/40-permissions.rules
SYSFS{vendor}=="0x14f1", SYSFS{device}=="0xea3d", GROUP="video"
SYSFS{vendor}=="0x1002", SYSFS{device}=="0x4397", GROUP="video"
SYSFS{vendor}=="0x1131", SYSFS{device}=="0x7133", GROUP="video"

```

Now i have
/dev/video/webcam
/dev/video/vcapture
/dev/video/tv

When I do xawtv -c /dev/vcapture i get

```
giorgos@giorgos-desktop:~$ xawtv -c /dev/vcapture
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-9-generic)
xinerama 0: 1680x1050+0+0
xinerama 1: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/vcapture: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/vcapture: No such file or directory
v4l2: open /dev/vcapture: No such file or directory
v4l: open /dev/vcapture: No such file or directory
no video grabber device available

```

But with xawtv -c /dev/video0 (which corresponds to /dev/vcapture) i get the correct picture from the camera.

What am I doing wrong?

---

### Post by sisco311 on 2008-12-05
the symlink is in the /dev/video directory.

try:
```
xawtv -c /dev**/video/**vcapture
```

---

### Post by giorgosc61 on 2008-12-08
giorgos@giorgos-desktop:~$ xawtv -c /dev/video/vcapture
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-9-generic)
xinerama 0: 1680x1050+0+0
xinerama 1: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video/vcapture: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video/vcapture: No such file or directory
v4l2: open /dev/video/vcapture: No such file or directory
v4l: open /dev/video/vcapture: No such file or directory
no video grabber device available
giorgos@giorgos-desktop:~$ 

giorgos@giorgos-desktop:~$ ls /dev/video
tv  webcam

The /dev/video/vcapture was not created...why?

---

### Post by giorgosc61 on 2008-12-11
Can someone please help me with my problem?:confused:

---

