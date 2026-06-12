---
title: "After installed WinTV-HVR-950, Webcam does not work"
date: 2008-07-09
forum: Mythbuntu
---

### Post by rqliang on 2008-07-09
After installed WinTV-HVR-950, Webcam does not work
I followed this instruction ([http://u32.net/MythTV/WinTV-HVR-950/](http://u32.net/MythTV/WinTV-HVR-950/)). I successfully get it works using mplayer. But my integrated webcam cannot work now. Before installation of WinTV card, /dev/video0 is the webcam. After that, it turns to be the TV. How can get my webcam works? Thank you!

My laptop model: Acer Extensa 4620Z.
uname -r: 2.6.24-19-generic

lsusb

Bus 007 Device 003: ID 2040:6513 Hauppauge 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 064e:a101 Suyin Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 15d9:0a37  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by superm1 on 2008-07-10
The easiest solution is to compile uvcvideo (the webcam driver) from scratch against those V4L headers.

---

### Post by rqliang on 2008-07-10
But the driver for WinTV HVR 950 is based on V4L2. I think, on my laptop, the V4L is substituted by V4L2 now. And must I to compile the driver? I think maybe just need a command to link my webcam to a device like /dev/video1. But how to do it? 

> **superm1 said:**
> The easiest solution is to compile uvcvideo (the webcam driver) from scratch against those V4L headers.

---

### Post by superm1 on 2008-07-10
> **rqliang said:**
> But the driver for WinTV HVR 950 is based on V4L2. I think, on my laptop, the V4L is substituted by V4L2 now. And must I to compile the driver? I think maybe just need a command to link my webcam to a device like /dev/video1. But how to do it?
Well here's a quick summary of what happened...

The uvcvideo driver and the v4l-dvb stuff all use a common videodev module and possibly others.  They were both compiled against the same headers when shipped so they both worked.  The moment you introduced the new v4l-dvb stuff, you need to recompile anything else that was using it's headers for the common modules.

---

### Post by rqliang on 2008-07-10
Very good summary. Now I know why. But how to do it? Any clue?

Thank you!

> **superm1 said:**
> Well here's a quick summary of what happened...

The uvcvideo driver and the v4l-dvb stuff all use a common videodev module and possibly others.  They were both compiled against the same headers when shipped so they both worked.  The moment you introduced the new v4l-dvb stuff, you need to recompile anything else that was using it's headers for the common modules.

---

### Post by superm1 on 2008-07-11
> **rqliang said:**
> Very good summary. Now I know why. But how to do it? Any clue?

Thank you!
Checkout from here: [http://linux-uvc.berlios.de/#documentation](http://linux-uvc.berlios.de/#documentation)

Build like this:
[http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS](http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS)

---

### Post by rqliang on 2008-07-11
Oh. I just know copy, paste, and make. Can you show me how to?

Thank you very much!

Actually I tried the following:

   1.  Enter the check-out Linux-UVC folder
      cd trunk
   2. Open the Make file in this directory
      sudo nano Makefile
   3. Edit Makefile to change the modules path from
      INSTALL_MOD_DIR := usb/media
      to
      INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo
   4. make
   5. sudo make install
It doesn't work.

I then tried change this in Makefile
[INDENT][/INDENT]KERNEL_DIR	:= /home/ruqiang/uvcvideo/v4l-dvb
And it cannot be compiled.


> **superm1 said:**
> Checkout from here: [http://linux-uvc.berlios.de/#documentation](http://linux-uvc.berlios.de/#documentation)

Build like this:
[http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS](http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS)

---

