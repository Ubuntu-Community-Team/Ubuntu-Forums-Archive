---
title: "Logitech Quickcam S7500"
date: 2008-11-08
forum: Multimedia Software
---

### Post by YoungCthulhu on 2008-11-08
I am having problems recording sound on my Logitech Quickcam S7500. Video works alright but I have to use a microphone plugged into the mic jack to record sound.  I use the Quickcam for Skype.  

In all other respects it works just fine, it is just that I suspect the quality of the Quickcam's built in mic would be superior to my plug-in mic which doesn't produce clear sound for those at the other end of my Skype sessions.

Here is the resuslts of lsusb:

> :~$ lsusb
Bus 004 Device 004: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 004 Device 003: ID 046d:09a2 Logitech, Inc. 
Bus 004 Device 002: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 1058:1000 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 056a:0016 Wacom Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

Has anybody got any ideas?

Many thanks:)

---

### Post by YoungCthulhu on 2008-11-08
Hello all,

I think I sorted it out for myself already.  It was just one of the many combinations that are possible on "Media Sound Selector", alsamixer, and "Sound Recorder".

For those of you who may be having similar problems with this webcam I found the following settings worked for me:

i) System>Preferences>Media Systems Selector:  
Plugin: ALSA
Device: Default

ii) alsamixer or "Gnome Alsamixer": 
Capture and capture 1 set to max and with record box ticked
USB set to max, with record box ticked

iii) Applications>Sound&Video>Sound Recorder (to test function)
"Record from input" set to "Master"

That's all.  Best of luck! :D

PS: some of these settings are irrelevant, I suspect.  If anyone could point me towards a good tutorial that explains how all of these controls fit together, or what they actually do on a basic level I would be much obliged.

Cheers:guitar:

---

### Post by alabwab on 2009-01-03
i am using logitech quickcam s7500. unfortunately it does not work in ubuntu 8.4. is there a how-to that could help me. looking at the hardware-datenbank i thought this model would work out-of-the-box.

thanks

---

### Post by Spartanis on 2009-06-04
Hi, I bought the same webcam.. plug it in.. cam working. Same sound recording problem. 

Followed your steps.. now BOTH Sound and cam recording not working.. SOmething about error connecting to dev/video0

:|

---

