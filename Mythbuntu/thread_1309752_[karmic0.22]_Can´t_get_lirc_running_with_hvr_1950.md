---
title: "[karmic/0.22] Can´t get lirc running with hvr 1950"
date: 2009-11-01
forum: Mythbuntu
---

### Post by deadland on 2009-11-01
Dear all,

I can´t get my Hauppauge HVR-1950 work with lirc! 

I ran  "sudo dpkg-reconfigure lirc" and chose the hvr-1300 as remote configuration, which produced the following hardware.conf:

```
 # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1300"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

```

but if I run "irw" or "mode2 -d /dev/lircd" nothing happens. If I open the battery case I get this model-id: "A415 OH/S 1-3".

Additional infos:

```
lsmod | grep lirc
lirc_i2c                7136  0 
lirc_dev               10804  1 lirc_i2c

```

```
mesg | grep lirc
[   16.280348] lirc_dev: IR Remote Control driver registered, major 61 
[12447.886947] lirc_dev: IR Remote Control driver registered, major 61 
[14764.173728] lirc_dev: IR Remote Control driver registered, major 61 
[14986.500859] lirc_dev: IR Remote Control driver registered, major 61 
```

```
mesg | grep pvrusb2
[    9.041222] usbcore: registered new interface driver pvrusb2
[    9.041237] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[    9.041246] pvrusb2: Debug mask is 31 (0x1f)
[    9.433638] cx25840 2-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[    9.434739] pvrusb2: Attached sub-driver cx25840
[   10.000549] tuner 2-0042: chip found @ 0x84 (pvrusb2_a)
[   10.000576] pvrusb2: Attached sub-driver tuner
[   13.414902] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
[   13.414920] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
[   13.414930] pvrusb2: Setting up 6 unique standard(s)
[   13.414941] pvrusb2: Set up standard idx=0 name=PAL-M
[   13.414949] pvrusb2: Set up standard idx=1 name=PAL-N
[   13.414957] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   13.414966] pvrusb2: Set up standard idx=3 name=NTSC-M
[   13.414974] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   13.414982] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   13.414992] pvrusb2: Initial video standard (determined by device type): NTSC-M
[   13.415028] pvrusb2: Device initialization completed successfully.
[   13.415218] pvrusb2: registered device video1 [mpeg]
[   13.415230] DVB: registering new adapter (pvrusb2-dvb)

```

It would be great if someone could provide me his working hardware.conf or any other advice.

Thanks in advanced

---

### Post by deadland on 2009-11-01
test

---

### Post by deadland on 2009-11-04
There is something totally wrong with lirc on Karmic. It doesn't even create an input-device:

```
cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus EeePC extra buttons"
P: Phys=eeepc/input0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=rfkill kbd event7 
B: EV=3
B: KEY=100000 0 0 0 400b 400 0 1300000 e0000 0 0 0

I: Bus=0003 Vendor=eb1a Product=2761 Version=1212
N: Name="UVC Camera (eb1a:2761)"
P: Phys=usb-0000:00:1d.7-8/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse1 event9 
B: EV=b
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0001 Vendor=10ec Product=0662 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: EV=40001
B: SND=6

```

Really I need help, I already have weeks with this problem.

---

### Post by kelvinelk on 2009-11-05
your problem is likely that lirc has moved its socket from /dev/lircd to /var/run/lirc/lircd. you can change where the frontend looks for the socket in setup>general on the frontend itself

---

### Post by deadland on 2009-11-06
Thanks alot for your advice! I will test it when I get home.

---

