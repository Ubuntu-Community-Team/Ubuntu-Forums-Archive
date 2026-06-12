---
title: "Kino Firewire No AV/C compliant cam connected or not switched on?"
date: 2014-11-25
forum: Multimedia Software
---

### Post by troy7 on 2014-11-25
Hello,

Trying to do some DV caputre from my Sony HandyCam TRV320 using Kino.  Initially, I got the error "WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!".  I 'fixed' this by doing

sudo ln /dev/fw0 /dev/raw1394

since I read /dev/fw0 is what I need to use, but kino is lookign for /dev/raw1394.  Doing this and running kino now give me a new error "No AV/C compliant cam connected or not switched on?".  Been reading and reading - not sure what to do.  Some forums suggested unplugging/plugging - rebooting - etc.  Tried all those.  Other forums refer to the Xubuntu kernel not supporting 1394 - but no real suggestions for how to add this to the kernal.  I did so some commands, like

lspci | grep FireWire and get 

05:05.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller

I guess this shows the hardware is detected.  Any suggestions/test I should try?  Thanks.

---

### Post by troy7 on 2014-12-31
I kinda solved this - see my thread titled 
[h=3][SOLVED] 						 					 					[I want to capture Video from Sony HandyCam - Firewire - need new Kernel?]("http://ubuntuforums.org/showthread.php?t=2254409")[/h]

---

