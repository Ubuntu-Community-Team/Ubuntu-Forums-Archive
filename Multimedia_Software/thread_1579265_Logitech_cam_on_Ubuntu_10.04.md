---
title: "Logitech cam on Ubuntu 10.04"
date: 2010-09-21
forum: Multimedia Software
---

### Post by hanslammerts on 2010-09-21
Hi,
 
Just found my old Logitech webcam again, and tried to get it to work on 10.04. Somehow this doesn't work. I tried searching the forum, but did not get an answer to my situation.
Here is what i can see:
After connecting (or rebooting), dmesg shows the following lines
 
uvcvideo: Found UVC 1.00 device <unnamed> (046d:08cc)
input: UVC Camera (046d:08cc) as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input5
usbcore: registered new interface driver uvcvideo
 
And that's it. No message that cam was registered to /dev/video<x>.
 
I should add that I already have another cam (Philips) that works and is registered to /dev/video0, and I also installed a Hauppauge PVR350 card that also gets registered to various /dev/video<y> files.
 
Does anyone have any clue why the Logitech cam won't register ?
I'm guessing I can't do anything until this cam has its own /dev/video<x>, right ?
 
Much obliged,
 
Hans

---

### Post by no2498 on 2010-09-21
is both cams plugged in at the same time ?

---

