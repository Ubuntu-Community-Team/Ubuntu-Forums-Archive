---
title: "HDMI: Soundchip of Nvidia GeForce 8600M GT isn't recognized --&gt; no sound with HDMI"
date: 2010-02-21
forum: Multimedia Software
---

### Post by greten on 2010-02-21
Hi. I'm trying to get my Sound working with HDMI-connection. Got an Nividia 8600M GT on Ubuntu 9.10.
Here is what aplay -l says:


```
$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC1200 Analog [ALC1200 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC1200 Digital [ALC1200 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
```As you can see, you can see nothing (concerning Nvidia HDMI).


Here is what i tried so far:
Nvidia drivers: 185, 175, 190.43, 195.30 (beta)

ALSA: 1.0.20.3, 1.0.22, 1.0.22.1


System right now: Nvidia 195.30 (beta) with Alsa 1.0.22.1


Anybody here who got it working?

Thanks a lot.

---

### Post by i531qooq on 2010-02-23
I am having the same problem...same video card, Ubuntu 9.10 64 bit.  Nvidia driver version: 173.14.20

---

### Post by the hoplite on 2010-06-22
Same problem, any news?

---

### Post by the hoplite on 2010-07-20
Ok guys, I got it working! I have your same graphic card on a Ubuntu 10.04. So this is what I did:

1. In /etc/modprobe.d/alsa-base.conf put this line
```
options snd-hda-intel model=auto
```

2. Under system-preferences-sound, hardware tab, select Internal audio, 1 output / 1 input, profile: Digital stereo (IEC958) Output + Analog input.

3. Reboot. Should work now. Let me know. Bye.

---

### Post by J_Luukvg on 2010-09-16
This solution has worked for me. I have the Nvidia GeForce 8600m GT on a XPS m1530 running Ubuntu 9.10, and now I can confirm that it is possible to send both video and audio signals by using an HDMI cable with this computer (by doing what was mentioned in the previous post).

Thanks!

---

