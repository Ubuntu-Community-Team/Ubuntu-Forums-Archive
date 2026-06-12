---
title: "only stereo but no sorround on HDMI"
date: 2010-12-28
forum: Multimedia Software
---

### Post by Ubuntliinux on 2010-12-28
Hello.

I have a Sony Vaio VPCEC1M1E with ATI and Ubuntu 10.10

My problem:

I want to watch a video with my home theater, but can't select HDMI (I'm on System->Preferences->Sound->Hardware). I can only select Stereo and not Surround. Stereo works perfect but I want to use Surround.
aplay -l gives me following (in German):
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC269 Analog [ALC269 Analog]
Sub-Geräte: 1/1
Sub-Gerät #0: subdevice #0
Karte 1: Generic [HD-Audio Generic], Gerät 3: ATI HDMI [ATI HDMI]
Sub-Geräte: 1/1
Sub-Gerät #0: subdevice #0

Thanks for your help!

Ubuntliinux

---

### Post by BicyclerBoy on 2010-12-28
Probably need to post your video hardware & which driver you are using.
Can imagine that hdmi audio with amd/ati hardware is still evolving..

---

### Post by lidex on 2010-12-29
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1466111&page=2](http://ubuntuforums.org/showthread.php?t=1466111&page=2)
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

---

