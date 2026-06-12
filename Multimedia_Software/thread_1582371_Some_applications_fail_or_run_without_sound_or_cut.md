---
title: "Some applications fail or run without sound or cut out sound for others"
date: 2010-09-26
forum: Multimedia Software
---

### Post by Glace on 2010-09-26
Something is weird with my sound, I've tried the sound debugging threads but failed, so I hope an overview here will give you enough to give me a fix, you don't have to read them all but I'm just hoping you might previously know some of these problems =)

I'm actually running studio, but these same problems occurred in the past running regular ubuntu. I'm running ubuntu 10.04 and ALSA (I believe).

[LIST]
[*]Many applications fail to run with sound. Vlc player is the only one that works, qmmp and audacious don't let me actually play files but they will run.
Trying to play in qmmp gives: ```
OutputALSA: Error opening PCM device default

```
[*]Running applications that go without sound from terminal show: ```
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM “surround51&#8243;

```
[*]Flash content in a browser either completely takes over the sound output (nothing else will play with sound) or has no sound (if another sound app is running at the time it begins loading) or allows nothing to have sound. I just run this a hundred times a day to get what I need ```
sudo alsa force-reload
```
[*]Vlc sometimes cuts the sound completely out but continues as if nothing has happened, then works again once restarting playback. The computer will make that loading noise right before this happens.
[/LIST]

---

