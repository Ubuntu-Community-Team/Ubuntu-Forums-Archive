---
title: "lirc device not loading"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by TallEddie on 2007-07-07
I am kind of new to linux, and I just got mythtv up and running.  I followed the giude online and everyting went smooth.  I had the remote working perfectly.  I shut down the computer, then the next day the remote no longer worked, and I can get it to work.  here is the problem:

running irw kills the lirc dameon.

I did a lot of searching, and I have not found a way to fix this.

the output of cat /proc/bus/input/devices is: 
I: Bus=0003 Vendor=413c Product=2005 Version=0105
N: Name="DELL DELL USB Keyboard"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=0461 Product=4d15 Version=0200
N: Name="USB Optical Mouse"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=40001
B: SND=6

and the output of ls -l /dev/lirc* is:

srw-rw-rw- 1 root root 0 Jul  7 09:07 /dev/lircd

when the remote was working, it was using /dev/lirc0.  However, based on the previous outputs it looks as though the lirc device is not loading.  Any ideas on how to fix this?

Thank you

---

### Post by TallEddie on 2007-07-07
Also, I am running Dapper, and have a pvr 150 tuner card

---

