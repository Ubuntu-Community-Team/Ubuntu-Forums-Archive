---
title: "Pulseaudio not working properly with two displays"
date: 2009-03-15
forum: Multimedia Software
---

### Post by amw72 on 2009-03-15
I have been trying to set up Ubuntu 8.10 to play videos on my tv, following the instructions [here]("http://en.wikibooks.org/wiki/NVidia/TV-OUT").

Everything works fine when I try to play a video on the monitor, using: ```
DISPLAY=:0 mplayer film.avi
``` but when I try to play it on the tv, using: ```
X :1 -layout tv
``` and ```
DISPLAY=:1 mplayer film.avi
``` mplayer opens up, but the video won't start and the following message is written to /var/log/syslog: > Mar 14:07:43 desktop pulsaudio[5287]: module-alsa-sink.c: Error opening PCM device front:0: Invalid argument

It all works again if I use sudo to start mplayer, so I'm guessing that there is some permissions issue that I need to fix. My user name is in all the groups pulse, pulse-access and pulse-rt.

Any help will be appreciated.

---

