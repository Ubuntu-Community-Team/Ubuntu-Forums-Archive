---
title: "E-MU 1212m and Wine wrong internal clock rate"
date: 2008-07-25
forum: Multimedia Software
---

### Post by deep-z on 2008-07-25
Hello!

Recently stumbled into a problem with E-MU 1212m sound interface and the game Syberia 2. 
Problem was with internal clock rate (44100 and 48000 setting). When launched, ingame audio sounded pithed up and with winecfg there was no way to change the audio interface clock rate (ALSA mixer setting was set to default - 44100). 
Also selecting OSS driver in Wine, where my built in audio card was listed, didn't work - Wine was picking the default audio interface instead, completely ignoring the built in Ensoniq card.

Solution to the problem was quite simple:

```
deep-z@vista-sux:~$ asoundconf list
Names of available sound cards:
EMU1010
AudioPCI
deep-z@vista-sux:~$ asoundconf set-default-card AudioPCI

```

Afterwards Wine picked as default audio card my built-in sound device and everything was fine.

Hope this helps, if someone is having the same problems with E-MU and games on Wine.

---

