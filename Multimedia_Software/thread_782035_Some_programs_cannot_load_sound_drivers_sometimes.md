---
title: "Some programs cannot load sound drivers sometimes"
date: 2008-05-04
forum: Multimedia Software
---

### Post by bunnyfly on 2008-05-04
Hello, since my upgrade to Hardy, I am having a continual problem with audio. Typically things will work. I open up Skype fine, Fakenes (NES emulator), Firefox etc and all sound is great. But sometimes I'll open things up and no sound.

Fakenes won't even load and says "Possible code fault at line 94 of "src/audio.c" then "Failed to initialize audio interface at line 218 of src/main.c"

Skype will load, but no sound and from the commandline has about ten of these thrown out:
"ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave"

Typically, it seems to be caused by Firefox. Sometimes, if I've been watching youtube videos, this will happen, and nothing else will load with sound, but then I exit Firefox and they'll suddenly load fine. Then I can reload Firefox alongside them. Sometimes they WON'T though, and the audio is just gone until I restart or logout/in.

The only guess I have is that it might be PulseAudio, but I'm not even sure that's new to Hardy? Can I delete it? Or maybe it's something else. But either way, I never had the issue before Hardy...and actually I don't think it happened in the Hardy betas either...but I'm not certain.

ANY help is greatly appreciated. Just ask if any info about my computer would help. Thanks!
[chloe]

---

### Post by bunnyfly on 2008-05-06
Anybody?

---

### Post by bunnyfly on 2008-05-17
Bump

---

### Post by Gunman1982 on 2008-05-17
PulseAudio seems to make some problems in hardy, you can try to set every program to use alsa directly and uninstall PulseAudio with synaptic (or apt-get if you want).

---

