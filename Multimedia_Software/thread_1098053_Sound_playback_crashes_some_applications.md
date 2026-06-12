---
title: "Sound playback crashes some applications"
date: 2009-03-16
forum: Multimedia Software
---

### Post by short4lif2 on 2009-03-16
For the longest time, sound playback has been crashing some of the multimedia applications.  When I try to play a song in Banshee or Exaile, or a video in totem, they crash, however vlc, mplayer and flash all work perfectly fine.  When  went into my sound preferences, (all set to autodetect) and click on Test, I get the following error.

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

When I click on Close in the error dialogue, it crashes and I have to force quit.  I have tried to get output from exaile and banshee, however, they stop writing output the instant I try to play a song.  What could be causing this?

---

### Post by markbuntu on 2009-03-16
System/Preferences/Sound. change the settings from automatic to either alsa or pulseaudio.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by short4lif2 on 2009-03-16
Thanks! Everything works properly.

---

