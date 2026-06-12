---
title: "no sound with &quot;new&quot; soundcard"
date: 2009-01-12
forum: Multimedia Software
---

### Post by therob on 2009-01-12
hello everyone!

i just "replaced" my c-media onboard soundcard with a soublaster live (emu10k1). the onboard sound is disabled in bios. the sblive is detected and the driver is loaded. but i have still no sound. i also checked the alsamixer and gnome-volume control. if i set the output device to "Multichannel Output (ALSA)" in the audio setting i can hear the test sound but there is still no sound in the system. i created a new user to test the default setting but this was no help. with the ubuntu 8.10 livecd works the sound out of the box. my speakers are over coax connected.

any suggestions are welcome
rob

---

### Post by sisco311 on 2009-01-12
try to set it as default sound card.

open a terminal and type:
```
asoundconf list
```
this will display a list of available sound cards

set the default sound card with:
```
sudo asoundconf set-default-card *<type-the-name-here>*
```

---

### Post by therob on 2009-01-12
i tried this. "asoundconf list" lists only one soundcard calld "Live" and i started "sudo asoundconf set-default-card Live" and rebooted the system. still no sound.

how can i reset the complete audio configuration? maybe it helps because the sound with the livecd works just fine.

---

### Post by markbuntu on 2009-01-12
What is most likely is that you need to change the default output device in the pulseaudio volume control, pavucontrol. If you do not have pavucontrol, you should get it.

---

### Post by therob on 2009-01-12
ok, i have 2 devices in the pulseaudio volume control. "alsa pcm on front:0" and "simultaneous output to alsa pcm on front:0". i tried both as default device but still no sound. i wonder why both devices are "front". i think there should be a "rear"?

---

### Post by therob on 2009-01-12
i just discovered a new phenomenon. if i play ac3 audio stream with vlc and spdif activated in vlc the sound works. still no sound with stereo mp3 :(

---

