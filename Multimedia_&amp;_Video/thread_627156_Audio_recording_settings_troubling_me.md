---
title: "Audio recording settings troubling me"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by fululian on 2007-11-29
when i try to use the audio-recording features of ubuntu, as in trying to use skype oder the gnome-sound-recorder 2.20.1, i am only able to record something if i scream as loud as i can, and even then it isn't much. after several hours of playing with the settings on gnome-volume-control 2.20.1, gnome ALSA and gamix, i actually was able to make it work a couple of times, but the very next day, everything was back as it was before.

if i see "system" - "settings" - "audio", everything is set to "ALSA", but i can't get a testing-sound (only using "test"), and instead i get this:

> coudn't establish test-forwarding for »gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat«

(sorry, translating from german). could anybody tell me how to solve this? maybe by updating or changing the driver?

infos regarding the audio-device:

```
cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x80000000 irq 16
```

```
lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
```

```
lsof | grep snd
mixer_app  5777   fululian   19u      CHR      116,6                14308 /dev/snd/controlC0
```

thanks.

---

