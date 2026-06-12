---
title: "How to rotate/split cam on skype?"
date: 2013-12-13
forum: Multimedia Software
---

### Post by ivan.ujhelji on 2013-12-13
[COLOR=#000000]Hello there... I am a new user of ubuntu 12.04 and have installed skype version 4.2.0.11 and have integrated camera (Bus 002 Device 003: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]). Everything works fine only thing is that my cam is rotated and couldn't find the way how to rotate to normal. Have installed Cheese and there is everything ok. [/COLOR]

[COLOR=#000000]Thnx very much for helping and if its not a problem explain me everything in details bcs as I mention, I'm new user. [/COLOR];)[COLOR=#000000] cheers[FONT=arial black][/FONT][FONT=comic sans ms][/FONT][/COLOR]

---

### Post by mikewhatever on 2013-12-13
It says **[B110 Optical USB Mouse]**. Are you sure that's a webcam? Can you post all of **lsusb** output as is.

---

### Post by ivan.ujhelji on 2013-12-13
When I put **lsusb **in terminal, it reply this: 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 002 Device 003: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]

Or did I put wrong something?

---

### Post by mikewhatever on 2013-12-13
Hm..., I don't see a webcam. The " Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. " is, apparently a wireless device. 
Is it a removable one? Was it plugged in? Do you have any info at all about it? If not, perhaps info about the computer will help.

---

### Post by mörgæs on 2013-12-13
The camera is [COLOR=#000000]13d3:5130

A mirrored /upside down picture is a classical error for this camera in Skype, but I can't point to a solution, sorry. Other packages like Cheese and Guvcview are seldom affected.[/COLOR]

---

### Post by ivan.ujhelji on 2013-12-14
I have installed also "v4l2ucp" - app that lets you change various settings with the camera and everything is working properly when I try to change brightness, saturation, sharpness...and also there is options for vertical & horizontal flip but only that 2 options is not working at all, like others. I have ASUS K52J notebook. I had "many cam" but that is working only for windows. It seems a little problem but at the end its not. :)

---

### Post by vvozar on 2013-12-21
Check this post: [http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210) :)

---

