---
title: "help detecting built-in irda receiver port in analog tuner using saa7130/4 chip"
date: 2009-09-22
forum: Multimedia Software
---

### Post by jaikat on 2009-09-22
hello everyone

i bought a "epro" analog tv tuner card with fm a few days ago which works just fine, the card was autodetected as "sabrent sbttvfm" with a saa7130/4 philips semiconducter. i check and turns out the autodetection was correct.

yet my problem lies with the irda receiver supplied with the card, which connects to the cards rear end, through a 2.5 mm jack.

i know for a fact that activating the irda port in the card must come through detection of an "event" in /proc/bus/input/devices which the system recognized, and here is mine:

=============
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=045e Product=0752 Version=0111
N: Name="Microsoft Wired Keyboard 400"
P: Phys=usb-0000:00:13.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb1/1-2/1-2:1.0/input/input2
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input3
U: Uniq=
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input4
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0
================

as you can see, there's nothing indicating detection of the irda receiver port...

after spending a few days probing the internet i realized that the problem lies in the driver used to detect the card. the driver "is" the one meant for this card, but it doesn't provide support for the card's irda input.. there's even some guy who wrote a patch for the driver in order to add support for the card's irda input port, but its too old (2005 maybe), plus i don't know how to apply patches at all in linux, the patch is also provided as text, so i don't even know where to start..

i searched this and other forums, blogs, howtos, tutorials, reviews..etc.. but to no avail..

i really much appreciate it if someone could be of help here..

---

### Post by jaikat on 2009-09-23
just a small bump, nothing to be afraid of :lolflag:

---

### Post by jaikat on 2009-09-25
nobody!!?:(

---

### Post by jaikat on 2009-09-29
one more bump..come'on guyz

---

