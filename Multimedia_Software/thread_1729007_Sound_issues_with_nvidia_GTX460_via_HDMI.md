---
title: "Sound issues with nvidia GTX460 via HDMI"
date: 2011-04-14
forum: Multimedia Software
---

### Post by earthwormgym on 2011-04-14
Hi,

I'm trying to get sound working in ubuntu 10.10 via the HDMI connection in my nvidia GTX 460

Currently when I first boot up I get no sound at all but I can manually sort this by:

1) Using alsamixer to unmute "S/PDIF 1" on the nvidia card
2) Play a sound through the card with 
```
aplay -Dplughw:1,7 /usr/share/sounds/alsa/Front_Center.wav
```

From here on the sound works but there is some form of tinny distortion.

Therefore I have two issues
1) How to make the card work automatically on boot up
2) Solve the sound distortion I'm getting


For issue 1 I believe that this is because the nvidia card is not the default sound device. The way I have seen to fix this is to put an option on the module loaded in /etc/modprobe.d/alsa-base.conf as below...
```
options snd-C index=0
options snd-A index=1
```
However as you can see from the configuration information attached they both use the same driver so I don't think this will work.

I know very little about sound on Linux but I have read many posts and can't find any solutions to my issues. Any help is greatly appreciated.

Attached is a dump of information about my system.

---

### Post by earthwormgym on 2011-04-18
OK I think I have solved both my problems. It looks like it was to do with the way pulse and alsa were working together. For the record this is what I did...

Run aslamixer
Using F6 switch to the nvidia output
Unmute all 
Run: sudo alsactl store

sudo vi /etc/pulse/default.pa

Put in the following line:
load-module module-alsa-sink device=hw:1,7

(The numbers were worked out in trial and error from aplay -l)

Reboot

Open up the sound preferences GUI and go to the Output tab
Select the device called "GF104 High Definition Audio Controller"

Reboot


Now i just have to remember how you turn off that annoying ubuntu login noise ;-)

---

