---
title: "No HDMI output on 11.04 nVidia GeForce GTX 465"
date: 2011-07-30
forum: Multimedia Software
---

### Post by vdubs on 2011-07-30
Hey all,

I've seen a lot of threads on this issue and combed through most of them trying to diagnose my problem and I've gotten REALLY close but with no complete success yet.

I have a nVidia GeForce GTX 465 and I'm running HDMI out to my monitor.  I have video but no audio.  I can see the device in the Hardware tab of Sound Preferences but for the life of me I can't get it to play any audio (aside from testing with white noise).

Output from aplay -l:
```
*** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```To figure out which device it is:
```
corey@ubuntu:~$ grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid        0
/proc/asound/NVidia/eld#1.0:eld_valid        1
/proc/asound/NVidia/eld#2.0:eld_valid        0
/proc/asound/NVidia/eld#3.0:eld_valid        0
```I can hear white noise when I run:
```
 speaker-test -c 2 -r 48000 -D hw:2,7
```I made sure that all of the devices in alsamixer were unmuted.

Does anyone have any idea what could be going on here?  It's super frustrating to be able to hear white noise but not my music through my speakers :confused:

Thanks in advance fro any assistance!

---

### Post by markstun77 on 2011-08-01
no but I am having this problem in windows vista home 64 AND windows 7 ultimate 64 with 2 GTX 465's (one flashed to a 470 but they use the same drivers)! I can't get any HD audio playback devices to appear in sound manager... do you know how to make it work in windows?

---

### Post by tjones00 on 2011-08-04
```
aplay -D plughw:2,7 /usr/share/sounds/alsa/Front_Center.wav 
```

doesn't work?  If it does just change your pulseaudio alsa sink to plughw:2,7 or plughw:NVidia,7

---

