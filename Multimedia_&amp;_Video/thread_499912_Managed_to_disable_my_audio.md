---
title: "Managed to disable my audio"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by chamstar on 2007-07-13
Hello, while trying to upgrade the ALSA driver to the newest version because my microphone does not work I have managed to completly disable the audio playback!

How do I rollback the drivers so I can get audio playback again?

I looked in Synaptic and it still lists the old version, I tried doing a re-install but no luck.

The audio icon in the top toolbar has a cross (as if muted) and when I click it it gives an error:

"No volume control GStreamer plugins and/or devices found."

If I run alsamixer I get:
alsamixer: function snd_ctl_open failed for default: No such device

And finally if I run lspci I can see the entry for the soundcard (which is built in to the motherboard):

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

Any assistance would be really helpful!


The upgrade guide I was following was: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
I did the entire section called: Update to the latest version of alsa, the section after that I could not do.

---

### Post by Sonicgoo on 2007-07-28
I'm having this same problem after messing up my groups.

---

### Post by darrenm on 2007-07-28
Ah groups.... Me too. I'll have this figured in a mo :)

---

### Post by darrenm on 2007-07-28
Aha. You need to be a member of the audio group:

```
sudo adduser $USER audio
``` should fix it.

---

### Post by chamstar on 2007-08-15
I solved this by just installing all the latest updates...

---

