---
title: "Pulseaudio seems to cause youtube videos to play too fast?!"
date: 2013-05-28
forum: Multimedia Software
---

### Post by Cinaed666 on 2013-05-28
[SIZE=2][FONT=arial]Hello,

A while ago I noticed the voices in the youtube videos I often watch were too high pitched.
After checking videos I had watched before, I came to the conclusion that playback was too fast. The time counter didn't match a stopwatch.
I googled around but the only thing I could find was someone suggesting to killall -9 pulseaudio, and relaunching that, and also the browser.
It seems to work, but that breaks my volume hotkeys on my keyboard until I reboot, and the whole process is a bit of a hassle, really, since it happens a couple of times ever day now. My browser is google chrome [COLOR=#303942]Version 27.0.1453.93,  (I use it over chromium because of a plugin that requires the latest chrome version at all times and chromium often lags a version behind. Also for the built-in audio player and pdf reader) and my system is using pulseaudio 3.0. Xubuntu 13.04.

Any idea? I tried a fix where it said that this would happen if you have multiple flash versions in chrome installed, but this didn't seem to be the case as I only had one.[/COLOR][/FONT][/SIZE]

---

### Post by zt14427 on 2013-05-28
I know this guide is geared more towards skype, but the problems sound similar enough that it might help.  As far as I can tell, I have been using this trick for a long time and haven't run into any noticeable speed-bumps. [http://pc-freak.net/blog/how-to-fix-pulseaudio-and-skype-crappy-sound-glitches-choppy-sound-and-crackling-on-debian-gnu-linux/](http://pc-freak.net/blog/how-to-fix-pulseaudio-and-skype-crappy-sound-glitches-choppy-sound-and-crackling-on-debian-gnu-linux/) I have also found that a good restart after doing this trick is better than restarting the daemon.

---

### Post by Cinaed666 on 2013-05-28
I have indeed noticed a severe crackle in the skype startup sound as well, I followed the steps and for now videos play at regular speed, I'm interested to see if it stays that way.
At least the crackle in the skype startup is gone. Thanks!

---

