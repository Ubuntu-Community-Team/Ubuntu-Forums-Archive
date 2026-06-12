---
title: "Yet another HDMI/Nvidia thread"
date: 2011-10-29
forum: Multimedia Software
---

### Post by Psyael on 2011-10-29
This time with additional Xubuntu Oneiric.

So, I've played around with trying to make an MP3 play in VLC and my GTX 460. As soon as I switch to ALSA and "HDA NVidia: HDMI 0 (hw:1,3)", I get wonderful music.

The system, however, doesn't seem to be aware of this in any other applications. It seems my hardware is working, but I need to figure out how to configure my system to use this device by default. I've tried a bunch of "edit this file with this string" style instructions around here with no luck at all.

This is a clean install, so I'm willing to start over if my futzing about with the sound system has messed things up good, but I think I've settled on the actual problem. How do I make it force hw:1,3?

---

### Post by Psyael on 2011-10-30
Solved with the app mentioned in the second post of [this thread](http://ubuntuforums.org/showthread.php?t=1864436). I simply turned internal audio off.

---

### Post by mörgæs on 2011-10-30
Good, then please mark the thread 'solved' using 'thread tools'.

---

