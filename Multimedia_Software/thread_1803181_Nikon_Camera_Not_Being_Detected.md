---
title: "Nikon Camera Not Being Detected"
date: 2011-07-12
forum: Multimedia Software
---

### Post by pravsemilo on 2011-07-12
Ever since I have upgraded to Ubuntu 10.04, my USB devices don't seem to be detected automatically.

I plug in camera or an MP3 player but that is not detected. However I see them when I run the command lsusb.

My USB mouse is however detected.

Following is the output of lsusb

Bus 002 Device 005: ID 0471:20a2 Philips 
Bus 002 Device 004: ID 064e:a103 Suyin Corp. 
Bus 002 Device 003: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04b0:0181 Nikon Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Phillips is my MP3 player and Nikon is my camera. 

Should I manually mount my camera? I don't see my camera under the /dev folder to mount it.

---

### Post by handy on 2011-07-13
I run Arch/Openbox, so I've got a system that is basically a custom built job (as Arch systems are), to I can't give you any Ubuntu specifics.

What I can say, is that I have a Nikon D90, which uses SD cards for memory. Even though external USB HDDs & flash memory can be mounted & read (automatically) my Nikon is not seen by my Linux system.

So, as you've probably guessed already, I just stick the SD memory into a card reader & all is well.

I hope your Nikon has removable memory as that will make your job so much easier, card readers are so cheap they are practically giving them away these days.

Another thing that I have read & been told about at the local camera house, is that you really are better off to not connect your camera to a computer as there is the potential for problems to arise in the camera. This advice would be appropriate for the more sophisticated cameras such as DSLR I suspect.

Anyway, that's all I can offer on the subject. I hope you find a quick solution.

---

