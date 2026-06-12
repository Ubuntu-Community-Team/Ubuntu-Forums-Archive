---
title: "USB video capture"
date: 2010-06-14
forum: Multimedia Software
---

### Post by pmla on 2010-06-14
The Story:
My friend bought an Manhattan HI-SPEED USB 2.0 Audio/Video grabber.
Basically we have a bunch of VHS that we would like to get into DVD. He plugged usb video capture dongle into is win7 and it worked out of the box without installing any drivers and using VLC as capture software.

MY Mistake:
I thought, if it works with WIN7 it will surely work with ub 10.04 d64 .... BIG MISTAKE :p

Could someone help me:
#lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 004 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0572:262a Conexant Systems (Rockwell), Inc. 
Bus 002 Device 002: ID 041e:406b Creative Technology, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


**This is what is being recognized Bus 002 Device 005: ID 0572:262a Conexant Systems (Rockwell), Inc. **

#dmesg
[ 5993.570014] usb 2-2: new high speed USB device using ehci_hcd and address 5
[ 5993.980275] usb 2-2: configuration #1 chosen from 1 choice
[ 7743.950387] usbcore: registered new interface driver em28xx
[ 7743.950389] em28xx driver loaded

after going a google search for usb "572:262a" only 9 results pop, like persons crying for help.


What to do? can someone help?



EDITED: In win7 it's works great in VLC » Open Capture Device » DirectShow » **VC500 video**

---

### Post by pmla on 2010-06-14
Ubuntu and it's community! uffff

---

### Post by linux-hack on 2010-06-14
If you don't get an answer that means that may be no one has a right answer for the moment.We'll not give you an answer juste to give one (like me LOL) if someone has an answer for you, you'll have 'it .. non need to get aggressive :D

---

### Post by pmla on 2010-06-14
lol... aggressive ... I think it's more like](*,):confused:#-o8-[
basically crying and sad ... lol

---

