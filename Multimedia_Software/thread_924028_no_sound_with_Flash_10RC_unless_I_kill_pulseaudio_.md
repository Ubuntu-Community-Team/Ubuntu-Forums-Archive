---
title: "no sound with Flash 10RC unless I kill pulseaudio (x64)"
date: 2008-09-19
forum: Multimedia Software
---

### Post by carpeme on 2008-09-19
So I've been looking around and noticing that a number of people are having issues with pulseaudio and sound in flash. The best tip I've seen (outside of simply deleting pulseaudio, which doesn't seem awesome) is to install Flash 10 RC. I followed the [instructions to install Flash 10 RC on AMD64]("http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/") to the letter, thinking I'd be all set. Well, Flash seems to work -- I right-click on a Flash video, it says I'm using Flash 10 -- but I don't get any sound. BUT if I do a `killall pulseaudio`, sound works fine.

Am I missing something? As far as I can tell, in my sound preferences, everything is pointing at ALSA anyway, pulseaudio is just around for system sounds (and whatever else it does in the background).

---

