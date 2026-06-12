---
title: "Mplyaer too slow when disabling screensaver"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by wisam on 2007-11-01
Mplayer takes a lot of time to disable the screensaver.
It detects the container format then displays this message
[CODExscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled][/CODE]
This message is displayed for 6 seconds or so then mplayer detects the codecs and starts playing.

The thing is that when I first installed Gutsy, I didn't have this problem. Mplayer started quickly and didn't disable the sceensaver but the screensaver started while mplayer running. 
I don't even have stop-xscreensaver=1 in my mplayer config file.

---

### Post by muphry on 2008-01-10
This should fix it:

echo "stop-xscreensaver=0" >> ~/.mplayer/config

---

