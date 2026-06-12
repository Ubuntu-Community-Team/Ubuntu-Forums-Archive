---
title: "gnome sound recorder crashes - alsa misconfig?"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by bschiett on 2007-07-16
hi,

gnome sound recorder has been working ok on my ubuntu 7.04 amd64 install. I have been using skype also without any problems (32 bit version and libs)

last week i tried installing a bluetooth headset and the bluetooth-alsa package.

since then i have the impression alsa is confused, and there are some devices still hanging around after uninstalling all the bluetooth stuff (which I never got to work properly). 

how do I get alsa to re-detect and re-configure everything so i can record sound again?

thanks,
Bert

These are in my device list when I am in audacity : 

playback

OSS: /dev/dsp
ALSA: NVidia CK804 : Nvidia CK804 (hw:0,0)
ALSA: NVidia CK804 : Nvidia CK804 - IEC958 (hw:0,2)
ALSA: front
ALSA: iec958
ALSA: spdif

recording

OSS: /dev/dsp
ALSA: NVidia CK804 : Nvidia CK804 (hw:0,0)
ALSA: NVidia CK804 : Nvidia CK804 - MIC ADC (hw:0,1)
ALSA: front

when i try to record or playback in audacity I also have problems.

---

### Post by fredj on 2007-07-16
Try choosing each one in turn (but forget the OSS option) and see if any of them work.
Choose the same one for record and playback.

---

### Post by bschiett on 2007-07-18
> **fredj said:**
> Try choosing each one in turn (but forget the OSS option) and see if any of them work.
Choose the same one for record and playback.

that didn't do anything...

i think bluetooth somehow screwed up my alsa settings which were working fine when i upgraded to 7.04. 

is there a way to let ubuntu redect the sound card and config it ?

---

