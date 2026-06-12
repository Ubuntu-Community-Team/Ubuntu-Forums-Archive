---
title: "Output Jack works, Speakers dont, then Speakers work, and output jack doesn't"
date: 2010-09-17
forum: Multimedia Software
---

### Post by fysicsandpholds on 2010-09-17
I have an intel mac with an ICH8 hda-intel Realtek ALC889A sound card.
When I first installed Ubuntu (10.04), I could not get sound to come out of the built in speakers. Sound did work on external speakers, but it was oddly low (much lower than same speakers on mac partition).
I fixed the built-in speakers by adding the line:
options snd-hda-intel model=imac24 
to the end of 
/etc/modprobe.d/alsa-base.conf
As instructed by the guide [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
However this made any external speakers stop working and on top of that, the sound comes out of the built-in speakers really thin for some reason so when I want to listen to music with quality speakers, I have to remove the options snd-hda-intel model=imac24 line and reboot my system. It is a real pain in the *** and I would love it to just use the built in jack detection

---

### Post by lidex on 2010-09-17
What model is this?
```

  macpro    MacPro support
  mb5        Macbook 5,1
  macmini3    Macmini 3,1
  mba21        Macbook Air 2,1
  mbp3        Macbook Pro rev3
  imac24    iMac 24'' with jack detection
  imac91    iMac 9,1
```

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags (the # in toolbar)

---

### Post by fysicsandpholds on 2010-09-19
```
uname -a
Linux spocklinux 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A
```

---

### Post by lidex on 2010-09-19
> **fysicsandpholds said:**
> ```
uname -a
Linux spocklinux 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A
```

When was the last time you updated your install? I believe lucid kernel is up to at least 2.6.32-24
Also what is the PC model?

---

### Post by fysicsandpholds on 2010-09-20
I have the newest kernal, and if I don't then it's cause I just reinstalled ubuntu from scratch. I had the exact same probablem on my last install which was definitely kernal .23.
I have an intel mac desktop computer

---

### Post by lidex on 2010-09-21
> **fysicsandpholds said:**
> I have the newest kernal, and if I don't then it's cause I just reinstalled ubuntu from scratch. I had the exact same probablem on my last install which was definitely kernal .23.
I have an intel mac desktop computer
And model number?

---

