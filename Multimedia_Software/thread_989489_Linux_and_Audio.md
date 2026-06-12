---
title: "Linux and Audio"
date: 2008-11-21
forum: Multimedia Software
---

### Post by efeurich on 2008-11-21
Can someone explain to me why linux and audio devices work so poorly together? I have installed Ubuntu Studio for a while now and it works fine. After some time of adjusting Jack Controls and the ALSA driver settings it works fine. But still i have a annoying thing and it seems to be generally excepted within the Linux community. 

When I run an music file MP3 with movieplayer and i want to run a movie with MPlayer the sound stops or you don't hear anything from one or both of the running applications.

Is there anyone out here that can explain that to me. Why the sound device can't handle 2 audio streams. For my work i have to use Windows and Windows doesn't have this problem.

Thanks in advanced.

EIF

---

### Post by Yellow Pasque on 2008-11-21
> Can someone explain to me why linux and audio devices work so poorly together?
[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

As for your problem, are you using PulseAudio, and do you have your apps and/or gstreamer (System -> Preferences -> Sound) set to output to pulseaudio?

---

### Post by markbuntu on 2008-11-21
Go here, it will tell you how to set up pulseaudio and jack.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

