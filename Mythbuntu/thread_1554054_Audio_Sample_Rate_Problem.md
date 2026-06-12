---
title: "Audio Sample Rate Problem"
date: 2010-08-16
forum: Mythbuntu
---

### Post by texklemer on 2010-08-16
I'm using a NVIDIA HDMI audio source and it will only play audio that is at 48000 and not 44100.  I'm sure there is a way to make the sound card upconvert on the fly but I've got no clue how to do it, any ideas?

---

### Post by texklemer on 2010-08-16
Any Ideas?

---

### Post by Neon Dusk on 2010-08-17
Some more info would help

What version of MythTV?

What do you have set for 'Audio output device' & 'Digital Output device' in Setup -> General -> Audio System?

What do the frontend log files say when you try to play 44100 audio?

In MythTV 0.23 I have 'Audio output device:' ALSA:hdmi (digital output device: Default) and this works fine.

In previous version of MythTV I set 'Audio output device:' to ALSA:default and created a /etc/asound.conf file with
```

pcm.!default {
     type plug
     slave.pcm "hdmi"
  }

```

N.B. One of my frontends has integrated Nvidia on the motherboard and a Nvidia graphics card so I need to use 'hdmi:1' to get the sound to go though the separate card.

---

