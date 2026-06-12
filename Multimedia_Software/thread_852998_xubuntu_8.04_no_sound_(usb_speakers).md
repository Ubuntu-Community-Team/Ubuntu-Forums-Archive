---
title: "xubuntu 8.04 no sound (usb speakers)"
date: 2008-07-08
forum: Multimedia Software
---

### Post by wongtop on 2008-07-08
Hi - I upgraded from Xubuntu 6.06 where sound worked fine (out of the box) - now in Xubuntu 8.04 I have no sound.

The pc has no onboard sound so I am using USB speakers.

aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 cat /proc/asound/cards gives
 1 [Audio          ]: USB-Audio - USB Audio
                      C-Media INC. USB Audio at usb-0000:00:1f.2-1, full speed

alsamixer gives;

alsamixer: function snd_ctl_open failed for default: No such file or directory

Any help / hints as to what to try next would be great.

Thanks

---

### Post by rasec_spain on 2009-06-11
Hi, I have the same problem with 9.04. Did you solve your problem?

I´m searching for solution...

---

### Post by wongtop on 2009-06-12
No sorry - I didn't get it sorted.  I think a reviewer on distrowatch had a similar problem and managed to get things going.  I've since retired the PC with the USB speakers (it was a P3).

---

### Post by rasec_spain on 2009-06-20
Hi! I find my solution. The first time after install xubuntu i was update to ubuntu, for test something... and sound works perfect after init gnome session.

How I don't want run gnome, I was install again xubuntu and too install a audiopulse packets. this solve the problem of my usb speakers...

Now I have a problem with sound, because every time that i reboot my system the sound turn off and is necesary search an tool configuration for up level sound... maybe tomorrow will be work :P


I have a Mac Cube 450Mhz (yes, ppc!!:oD) with 416MbRam I'm trying convert into a htpc...
(I have a lot of work...)

Bye!!

---

### Post by hmagoo on 2009-06-25
Hi,
For some reason the USB Audio sound "cards" are getting put on the back burner, they are not getting /dev/dsp (In most cases) but are getting /dev/dsp1 (or something), even though there is _NO_ other sound device installed. 

I had the same problem, and had to change the order that the system assigns them to /dev/dsp...

[http://ubuntuforums.org/showthread.php?t=205449&highlight=modprobe+usb+audio]("http://ubuntuforums.org/showthread.php?t=205449&highlight=modprobe+usb+audio")

should work for you, or at least help you start googling.  Find the name of your sound device and change it so that it is seen by the system as /dev/dsp... with no number!

---

