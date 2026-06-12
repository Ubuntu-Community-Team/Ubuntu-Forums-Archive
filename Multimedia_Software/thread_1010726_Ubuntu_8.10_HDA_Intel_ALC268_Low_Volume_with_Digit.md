---
title: "Ubuntu 8.10 HDA Intel ALC268 Low Volume with Digital"
date: 2008-12-14
forum: Multimedia Software
---

### Post by noelsusman on 2008-12-14
I have been searching for a solution to this problem for months, and I seem to have hit a dead end.  Here's my situation.

Under default settings my sound works perfectly.  Audio is a good volume, and everything is crisp and clear.  The only problem is that my HDMI audio does not work.  In order to fix that, I added this line to my /etc/modprobe.d/alsa-base file according to [this site]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
```
options snd-hda-intel model=auto
```
This fixed my HDMI problem, but unfortunately it has caused my speaker/headphone volume to be dramatically cut.  The audio still works, but I have to put everything up to 100% just to be able to barely hear it.  I have checked alsamixer and the gnome volume control panel, and everything is set to 100% (front, PCM, etc.).  When I take that line out of my alsa-base file, my audio returns back to normal.

I am running Ubuntu 8.10 on a HP Dv6700 Special Edition laptop.
lspci:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```
aplay:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
When I add that line to my alsa-base file, the only thing that changes in my aplay is another entry identical to the first entry except it says "Digital" where it says "Analog".

Right now I just run normally without that line in my alsa-base file, and I have to edit that file and reboot every time I want to use my HDMI port.  It's not horrible, but obviously I would like everything to work properly.

Any ideas?

---

### Post by noelsusman on 2008-12-15
Bump.

---

### Post by markbuntu on 2008-12-15
Have you filed a bug report because that is surely a bug in the driver.

---

### Post by noelsusman on 2008-12-16
[Done.]("https://bugs.launchpad.net/bugs/308339")

Hopefully it won't be ignored and somebody will take a look at it.

---

### Post by jacobisreal on 2009-07-26
Was there ever a resolution to this?  If so, please inform me of what to do.  I have the same issue with an Acer Extensa 5420.

---

### Post by Javier Tapia on 2009-08-01
Hello, I have:

HP TouchSmartPC tx2 - 1025dx
HDA ATI DB Realtek ALC268
Ubuntu 9.04

and works fine with:

options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1



Thanks

---

