---
title: "Using a using a behringer uca 202 as main soundcard"
date: 2009-03-06
forum: Multimedia Software
---

### Post by 04pban on 2009-03-06
There is no problem for this little device to work with Recording programs and musiceditors, just plug and play, but the problem is that my phones minijack on my laptop i broken, so i also want to be able to play youtube, vlc, amarok, and movieplayer with this soundcard, but is that possible?

i have tried to change the configurations in sound in the system menu, and there is one option called USB Audio CODEC USB Audio (ALSA) and i thought that it was the one, but it does not work. i hope someone can help.

My os is intrepid ibex.

---

### Post by 04pban on 2009-03-09
Bump

---

### Post by cmay on 2009-03-09
if it can play those program like audacity and such it should be able to play other sound sources such as xine totem youtube and so on. maybe play around wiht the alsa settings for a while and if get stuck then try post the mixer settings here . maybe i can or someone else can check that out for you if its completely undoable to make it give sound output from the programs you need.

---

### Post by amor0fati on 2009-04-27
I have the same problem, though my sound card works fine.  I thought I'd be able to simply run an 1/8" to RCA into it from my soundcard so as to temporarily pipe the sound through the device's optical out (this is what runs to my reciever), since that works with the headphone port but no luck.  I imagine that the optical out only pipes through signals directly from the USB.  The device works fine for Rhythmbox and Audacity, but not VLC or Flash; somehow, they don't seem to recognize USB sound devices.

Not sure if this info will help or not:

> ~$ cat /proc/asound/cards
 0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xd5106000/0xd5000000, irq 17
 1 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:02.0-6, full s


> ~$ lsusb
Bus 002 Device 008: ID 05ac:1209 Apple, Inc. iPod Video
Bus 002 Device 005: ID 13fd:1040 Initio Corporation 
Bus 002 Device 004: ID 059f:0651 LaCie, Ltd 
Bus 002 Device 003: ID 059f:0951 LaCie, Ltd 
Bus 002 Device 002: ID 059f:0651 LaCie, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 014: ID 03f0:4511 Hewlett-Packard Photosmart 2600
Bus 001 Device 003: ID 08bb:2902 Texas Instruments Japan 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by Minishark on 2009-05-23
I'm having the same issue on Jaunty Jackalope. I think this article may be the solution, but I've yet to try it out:
[https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)

---

