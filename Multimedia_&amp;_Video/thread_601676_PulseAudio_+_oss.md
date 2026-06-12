---
title: "PulseAudio + oss"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by tribunal on 2007-11-03
Hi all!
I have Kubuntu 7.10 installed
When I have installed PulseAudio, I have found a new problem
all applications, that need oss have stopped working :(
alsa-oss is installed

---

### Post by tribunal on 2007-11-03
found a new detail:
after stopping pulseaudio (killall pulseaudio), but not alsa (snd-drivers) alsa-oss starts working again
But I cannot make them work together and I don't know why :(

The problem is half-solved using padsp

---

### Post by staham on 2007-11-12
Have a look at:
[http://www.pulseaudio.org/wiki/FAQ](http://www.pulseaudio.org/wiki/FAQ)

And:
[http://forums.debian.net/viewtopic.php?t=12497](http://forums.debian.net/viewtopic.php?t=12497)

And also:
[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

