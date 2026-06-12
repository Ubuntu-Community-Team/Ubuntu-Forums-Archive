---
title: "ICE1712 – Terratec DMX 6 FIRe PCI"
date: 2014-02-21
forum: Multimedia Software
---

### Post by Caddydaddy57 on 2014-02-21
Good day,

I'm a really old win user, but about 6 month ago I change it to Ubuntu. I'm really happy with this system, but now I'm in treble. I bought a DMX 6 Fire soundcard and it is not working. I tried to find the solution on forums, google etc... but still not working. 

Now Ubuntu shows only this card I disabled the onboard soundcard.

If I'm trying to use ALSA output in Audacious it has the following error:
ALSA error: No suitable mixer element found.
 ALSA error: snd_mixer_find_selem failed.

When I changed to PulseAudio nothing happens. Audacious starting to play only 1 second and stop it.

sudo aplay -l
**** PLAYBACK hardvereszközeinek listája ****
kártya 0: DMX6Fire [TerraTec DMX6Fire], eszköz 0: ICE1712 multi [ICE1712 multi]
  Aleszközök: 1/1
  0 számú aleszköz: subdevice #0
kártya 1: HDMI [HDA ATI HDMI], eszköz 3: HDMI 0 [HDMI 0]
  Aleszközök: 1/1
  0 számú aleszköz: subdevice #0

UPDATE:

Audi. now playing and pulseaudio volume control graph shows output signal, but still no sound

Many thanks for your help, if you need more info just write here.

---

### Post by Caddydaddy57 on 2014-02-23
I tried it with Fedora 18, but same problem with Ubuntu

---

### Post by Thee on 2014-02-23
See the last post of this thread, maybe it helps:
[http://ubuntuforums.org/showthread.php?t=1628570](http://ubuntuforums.org/showthread.php?t=1628570)

---

