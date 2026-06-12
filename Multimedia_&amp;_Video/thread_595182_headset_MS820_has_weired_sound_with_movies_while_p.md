---
title: "headset MS820 has weired sound with movies while plays mp3 fine"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by andrei.kouznetsov on 2007-10-28
I'm running Ubuntu gutsy. Recently I've found a blue-tooth headset of my cell phone and connected it to my laptop.
I used instructions from [http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

When I play mp3 files with mplayer using the command
```

mplayer -ao alsa:device=bluetooth music.mp3

```
It plays fine (unless I select text in the console with my usb mouse)

when I try to play a video file with the same command
```

mplayer -ao alsa:device=bluetooth video.avi

```
It starts crackling, there are some intervals of time when it's playing sound well.
mplayer says
```

alsa-play: write error: Broken pipe0.115 1268/1268  5%  0%  2.7% 0 0 
alsa-play: trying to reset soundcard

```
Any ideas?

---

### Post by andrei.kouznetsov on 2007-10-28
More info
If I run the same video with "no video" with the command
```

mplayer -vo null -ao alsa:device=bluetooth video.avi

```
it does not play the sound well either.

It plays everything fine if the sound output is my speakers

---

