---
title: "USB Headset doesn't work in games"
date: 2008-05-03
forum: Multimedia Software
---

### Post by sqrlking on 2008-05-03
Hi, 

My headset works fine when I play music via rhythmbox, but i installed steam (via wine) and ETQW, and neither of them recognize the usb headset.  I don't have speakers, so this is my only option for sound.  

in system>pref>sound I've selected USB audio for everything.

I tried following a couple of the sounds guides, but no help so far.  Here's some more info on my system.

cat /proc/bus/input/devices:
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Generic Explorer Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=0d8c Product=000c Version=0100
N: Name="C-Media USB Headphone Set  "
P: Phys=usb-0000:00:0b.0-6/input3
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.3/input/input7
U: Uniq=
H: Handlers=kbd event2 
B: EV=13
B: KEY=e0000 0 0 0
B: MSC=10

```
 
And asoundconf list:
```
Names of available sound cards:
NVidia
default

```

As you can see, no headset shows up in asoundconf.  

Appreciate all help. 

Thanks!

---

### Post by sqrlking on 2008-05-04
Anybody have this trouble?  or have a working usb headset, so they can share their settings with me?

Headset is gigaware, if that makes any difference

---

### Post by sqrlking on 2008-05-05
final bump.  Any help?

---

### Post by error420 on 2008-07-20
I'm having a similar problem however i'm using a Bluetooth headset. Works great for music with Amarok but the problem in wine lies in selecting the default alsa device. Does anyone know how to tell wine to use a secondary device as the default sound card?

---

### Post by erikthedrink on 2009-09-08
If you don't have speakers, then why is NVidia showing up.:confused:  Try this
In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb headphones, your laptop speakers will take over.  In order to re-establish contact with the usb headphones, you will need to (plug them back in) restart the system.  If this doesn't work, substitute a 2 in place of the 1.:popcorn:

---

