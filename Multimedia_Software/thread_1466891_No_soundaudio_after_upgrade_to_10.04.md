---
title: "No sound/audio after upgrade to 10.04"
date: 2010-04-30
forum: Multimedia Software
---

### Post by OobNosferatu on 2010-04-30
Can someone help me please? I recently upgraded to Ubuntu 10.04 and my sound is not working. I have a gateway p-6860FX. i've had this trouble since 9.04 and also in 9.10, but I worked around it by adding the following to my alsa-base.conf with 

```
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
# alias snd-card-0 snd-hda-intel
```

Sound worked fine after that, but it doesn't work with 10.04


here are the results of aplay -L

```
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```

PS: yes, i went in to alsamixer and turned everything up. it didn't work.

---

### Post by OobNosferatu on 2010-04-30
Alright this is weird... I checked the alsamixer again and found that the speaker volume was lowered yet again.

So I increased the volume and tried to play an mp3. IT WORKED!

However, after every reboot the speaker volume is reset to zero.

How do I get around this!? 

I'm assuming I'll have to make a script/command for increasing the volume and put it in the start up menu... the thing is, I don't know what that command would have to be...

---

### Post by mikemn84 on 2010-05-03
I have the same problem after upgrading to 10.04.  Try

```
amixer set Speaker 100%
```

Does anyone know what causes this and how to stop it other than issuing a command to reset the volume all the time?

---

### Post by OobNosferatu on 2010-05-03
Yeah I now use a script to automatically set the speaker volume. What sucks about this method though is that it doesn't store the settings after each reboot, not even using the amixer store command (or something).

---

### Post by Yellow Pasque on 2010-05-03
> **OobNosferatu said:**
> Yeah I now use a script to automatically set the speaker volume. What sucks about this method though is that it doesn't store the settings after each reboot, not even using the amixer store command (or something).
Put your script/command in /etc/rc.local so it runs at every boot. You can also try to install linux-backports-alsa-modules (or something like that) to upgrade ALSA and see if the mute bug got fixed.

---

### Post by kingpin_uy on 2010-05-03
Worked for me on Lenovo Ideapad Y530 + Ubuntu 10.04 64 bits
It only worked the 2 main speakers, not the small ones and sub-woofer
Solution:
add:
options snd_hda_intel model=lenovo-sky
on:
/etc/modprobe.d/alsa-base.conf

I found the solution here -> [http://www.linlap.com/wiki/lenovo+ideapad+y530](http://www.linlap.com/wiki/lenovo+ideapad+y530)
I added only this line. Maybe you should try with another model value.

Or try this->

[http://translate.google.com.uy/translate?hl=es&sl=ru&tl=en&u=http%3A%2F%2Flenih-nix.blogspot.com%2F2010%2F02%2Falsa-gateway-p-6860fx-snd-hda-intel.html](http://translate.google.com.uy/translate?hl=es&sl=ru&tl=en&u=http%3A%2F%2Flenih-nix.blogspot.com%2F2010%2F02%2Falsa-gateway-p-6860fx-snd-hda-intel.html)

(check for the console lines on the original blog because the translator changes them too)

---

