---
title: "1176x664 resolution"
date: 2012-02-21
forum: Multimedia Software
---

### Post by jespo4 on 2012-02-21
Trying to get a HTPC with a nvidia Geforce 7300 to connect to a Magnavox 37 inch LCD via a DVI to HDMI cable. I'm dual booting and in windows 7 screen is right size and identified as 1176x664 60hz. Lubuntu overscans the screen at 1366x768 when I drop down to 1024x768 it puts in a 4:3 format and puts black space on both sides. was able to modify xorg.conf to get 1176x664 to show up in monitor settings, but its still overscanned and jumpy. Can anybody tell me what windows 7 is doing that lubuntu isnt? like I said 1176x664 is what windows calls it and it fills screen perfect.

---

### Post by roelforg on 2012-02-21
Try installing nvidea drivers, those things are known for their problems.

Google will tell you how.

---

### Post by tnicewicz on 2012-02-21
Try under restricted drivers.  May be listed there as well.

---

### Post by jespo4 on 2012-02-26
Turns out 1024x768 will work ok, the screen was in a 4:3 format because the TV was set to that mode for HDMI input. Changed it to widescreen and GUI filled screen, still not as sharp as when I boot into Windows 7 though. So this tells me that my hardware and TV are compatible in the Microsoft world. I downloaded the latest linux 64 bit driver from nvidia (295.20) but when I went to run the file message popped up saying X server must be closed. Tried to switch to a virtual console to accomplish this but screen is white with garbled text, this must be the reason why on boot up before getting the log in screen there a white screen with large garbled text in the center, it must be the lubuntu splash screen. Found a net post about running 3 commands to update to the latest nvidia proprietary drivers:
 
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
 
Ran this and Nvidia x server settings now shows driver updated from 288.13 to 294.20 but why still the white screen with garbled text on boot and vitual consoles? What other tweaking do I need to do to the Nvidia driver? Is it time to give Fedora a try?

---

### Post by BicyclerBoy on 2012-02-26
The nVidia driver is an X server driver only.

The nVidia driver is not running/loaded/involved during grub boot/greeter screen or console use.

When you switch to console screens, the X server driver (if running) is halted.

Some other framebuffer driver is used during boot.
You could try to set the screen resolution in grub..

Your old video card does not benefit from the latest driver but I think it is still supported.
The nVidia 7000 series cards are a bad choice for HTPC, the chipset mobo 6000 & 8000 families are better.

---

