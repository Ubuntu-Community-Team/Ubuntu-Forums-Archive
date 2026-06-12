---
title: "Pulse Audio not working on 15.10 Mate"
date: 2016-01-26
forum: Multimedia Software
---

### Post by MZ250Supa5 on 2016-01-26
I was on 15.04 Mate, and until the day before yesterday sound was working fine. I plugged in some headphones, and for a short while all was fine. I then needed to reboot, and when the system booted up I not only did not have any sound, but also noticed that the sound applet in the system tray had gone - the UI had also become very sluggish and unresponsive.  I decided to upgrade to 15.10, and that solved the sluggish UI issue, but I still have no sound. I've tried so many of the suggested remedies, sadly in vain.  I'm just hoping someone on these forums has some idea.

It's pretty amazing that we're still having these issues with sound on Linux, or more particularly, Ubuntu.  It seems to be a bit of a re-play of the 9.04, (or was it 9.10) when pulse was a mess on Ubuntu and often needed intense intervention to solve the issue. I don't know what happened to make the sound on my computer completely disappear, much less make the UI sluggish and unresponsive, (though I do have a faint recollection of having that issue previously)

---

### Post by QDR06VV9 on 2016-01-26
Have you tried this yet..
```
sudo alsa force-reload
```
Here is a link that i use alot..[http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)
Hope that helps
Regards

---

### Post by yoshii on 2016-01-26
Maybe use synaptic package manager and do a re-install of PulseAudio.  And then after that, go into PulseAudio Volume Control and get everything configured.  And edit the system preferences files for Pulse if needed too.  (buffer sizes if you have too much latency).

---

