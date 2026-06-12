---
title: "Sound applications interfere with each other"
date: 2010-07-07
forum: Multimedia Software
---

### Post by e64462 on 2010-07-07
A friend of mine is having a problem where one application will cut off another application when playing sounds.

For example, if he has amarok playing music and pidgin beeps on a new message, amarok stops.

If he has vlc playing music, and then has amarok play something simultaneously, vlc stops.

Has anyone else experienced this behavior?

The only related bug I've been able to find is
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/444950](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/444950)

But I cannot even confirm that this is a pulseaudio problem. He's using an updated 10.04 installation, any advice is welcome.

---

### Post by e64462 on 2010-07-08
bump

---

### Post by e64462 on 2010-07-08
bump

---

### Post by lidex on 2010-07-10
This may help:
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

---

### Post by e64462 on 2010-07-12
Wow, completely missed that you had replied. We found this bug report, which I'm 98% sure is what's causing the behavior. 

[https://bugs.launchpad.net/ubuntu/+source/phonon-backends/+bug/554147](https://bugs.launchpad.net/ubuntu/+source/phonon-backends/+bug/554147)

No quick progress is being made in that bug, so I had him completely remove pulse with:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
and set everything to use alsa directly with:
```
gstreamer-properties
```

This solved the problem, but obviously it's not the preferred solution. If you still think that those lines in /etc/asound.conf might be the culprit, I'll have him reinstall pulse.

---

### Post by martiniuuus on 2010-07-12
Try a complete re-install. That often helps many problems. Or, un-install as many of the sound programs as possible and that way try to find out whioch ones that cause problems.

---

### Post by e64462 on 2010-07-12
Well, like I said we've already found a much more simple solution than formatting. But before we tried that, he completely reinstalled 10.04, and experienced the exact same behavior. Also, it's not so much sound applications which are the problem. Any program which makes a sound generates the bug; from aplay to gnome-mplayer, amarok, and vlc. Sound applications just don't seem to share pulseaudio/alsa well.

---

