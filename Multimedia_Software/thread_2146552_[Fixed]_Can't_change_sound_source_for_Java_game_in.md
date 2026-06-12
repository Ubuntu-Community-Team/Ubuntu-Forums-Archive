---
title: "[Fixed] Can't change sound source for Java game in pavucontrol [pulseaudio]"
date: 2013-05-18
forum: Multimedia Software
---

### Post by Elite6809 on 2013-05-18
**FIXED**. It's an issue with OpenAL, not pulseaudio. The solution for me was to put the config file at [http://repo.or.cz/w/openal-soft.git/blob_plain/HEAD:/alsoftrc.sample](http://repo.or.cz/w/openal-soft.git/blob_plain/HEAD:/alsoftrc.sample) to ~/.alsoftrc and add the line **allow-moves = true** to the bottom. Thanks to **ohsix** on freenode:#pulseaudio!

Hi,
I have the Microsoft LifeChat LX-3000 USB headphones with my PC and I got them working with pavucontrol by changing the 'Built-in Audio Analogue Stereo' to 'Microsoft LifeChat LX-3000 Analogue Stereo.' YouTube videos play just fine. However when I try and do the same for Java to play Minecraft, if I attempt to select 'Microsoft LifeChat LX-3000 Analogue Stereo' it just does nothing and stays as it is - 'Built-in Audio Analogue Stereo' - which is useless as it doesn't work, so there is no audio output anywhere.
Is there another way to change the sound source, as pavucontrol clearly isn't functioning. I've tried to do it via the terminal with pacmd but that doesn't seem to be useful either. As usual for me, it seems I'm the only person on the entire web to have encountered this issue, and it's winding me up (and has been for the past 4 hours.)
Can anyone give me a solution? Thanks

---

