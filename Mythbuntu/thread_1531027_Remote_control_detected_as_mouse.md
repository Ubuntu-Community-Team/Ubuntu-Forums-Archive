---
title: "Remote control detected as mouse"
date: 2010-07-14
forum: Mythbuntu
---

### Post by alsalgado on 2010-07-14
Hello. :razz:

I'm having problems with remote control, first tried to do the work that comes with the Hauppauge WinTV-GO PLUS, but had no success so I bought the VCR-1100 Vista MCE of Ortek Technology, but ubuntu is seeing it as a mouse (mouse2 ) and so it does not work properly, almost no key works.
Help

Mythbuntu 10.04

Hardware
CPU: AMD  2.6 Ghz
Motherboard : M4a785td
RAM: 2.0 gb ram
Remote: VRC-1100 Ortek Technology / HAUPPAUGE WINTV-GO PLUS SILVER
HD: 60 gb hard drive
Tuners:
HAUPPAUGE WINTV-GO PLUS


cat /proc/bus/input/devices

I: Bus=0003 Vendor=05a4 Product=9881 Version=0110
N: Name="HID 05a4:9881"
P: Phys=usb-0000:00:13.1-3/input1
S: Sysfs=/devices/pci0000:00/0000:00:13.1/usb6/6-3/6-3:1.1/input/input6
U: Uniq=
H: Handlers=kbd mouse2 event6 
B: EV=17
B: KEY=1f0000 2020000 3878d801d001 1e000000000000 0
B: REL=103
B: MSC=10

salgado@htpc:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 05a4:9881 Ortek Technology, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

salgado@htpc:~$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root    140 2010-07-14 11:50 by-id
drwxr-xr-x 2 root root    160 2010-07-14 11:50 by-path
crw-r----- 1 root root 13, 64 2010-07-14 11:50 event0
crw-r----- 1 root root 13, 65 2010-07-14 11:50 event1
crw-r----- 1 root root 13, 66 2010-07-14 11:50 event2
crw-r----- 1 root root 13, 67 2010-07-14 11:50 event3
crw-r----- 1 root root 13, 68 2010-07-14 11:50 event4
crw-r----- 1 root root 13, 69 2010-07-14 11:50 event5
crw-r----- 1 root root 13, 70 2010-07-14 11:50 event6
crw-r----- 1 root root 13, 63 2010-07-14 11:50 mice
crw-r----- 1 root root 13, 32 2010-07-14 11:50 mouse0
crw-r----- 1 root root 13, 33 2010-07-14 11:50 mouse1
crw-r----- 1 root root 13, 34 2010-07-14 11:50 mouse2

salgado@htpc:~$ irw
^[[D^[[E^F^[[^C

---

### Post by itlarson on 2010-07-14
Go into mythbuntu control center and make sure the infrared device is set to "windows MCE remote".  If you have already done this, Someone who's much more of a hacker than I am needs to help you.

---

### Post by larsolav on 2010-07-14
The remote is behaving the way it was designed. It should actually show up as a mouse and a keyboard. So when you use the mouse pad and two mouse buttons that is the mouse part. The other buttons are actually mapped to emulate keyboard entries. That is the reason you probably only have the up,down,left,right, and OK(enter) buttons working off the bat. It does not work in the normal sense with LIRC, so even if the infrared device is set to "windows MCE remote" it will not work without doing some extra stuff.
I spent a few days searching for ways to make the remote work, but gave up. I am too much of a novice. This is the closest to a solution I could find:
[http://ubuntuforums.org/showthread.php?t=876874&page=3](http://ubuntuforums.org/showthread.php?t=876874&page=3)
Maybe you will have more luck

PS: you had a little typo in the model name. It should read "VRC-1100", not VCR...

---

### Post by alsalgado on 2010-07-14
Thank  itlarson, I had already configured as windows MCE.
Thank you also  larsolav, but I think it also will not have much luck as you. rss And you're sure the same model and VRC-1100, is  my fault.
Again thanks for the  responses.

---

### Post by itlarson on 2010-07-16
I ebayed a windows mce remote for $30, and it works without doing a thing except choosing it in the control center.  Maybee you just need different hardware.

---

