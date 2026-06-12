---
title: "Why is Rhythmbox freezing on me?"
date: 2009-08-19
forum: Multimedia Software
---

### Post by JohneG on 2009-08-19
When i go to play some audio files it freezes. I'm assuming this is cause it doesn't support the file format? Is there a way of expanding the formats that Rhythmbox supports if thats the problem? I have tried Banshee and while i like it i prefer Rhythmbox for one main reason. . . it seems to be lighter. If i could get this one problem solved then i would have my mind made up. Anyone able to help?

---

### Post by Stochastic on 2009-08-19
Moved to Multimedia & Video.

---

### Post by heluani on 2009-08-19
try running ```
$rhythmbox -d
``` on a terminal, that might help. Also you can try something like ```
$rhythmbox -d 2>&1 | tee my-rhymbox-stalls.log
``` and then take a look at the file "my-rhythmbox-stalls.log". Finally you might want to run ```
$gdb rhythmbox
``` do whatever you do to freeze rhythmbox and get a stacktrace. Posting here (or in Rhythmbox's mailing list) that info might be useful.

R.

EDIT: as for your original question regarding formats, Rhythmbox uses gstreamer so any format that your gstreamer understand can be played with Rhythmbox. You might want to install gst-plugins-{base,good,bad,ugly,ffmpeg}... etc.

---

### Post by Wanas on 2009-09-06
> **JohneG said:**
> When i go to play some audio files it freezes. I'm assuming this is cause it doesn't support the file format? Is there a way of expanding the formats that Rhythmbox supports if thats the problem? I have tried Banshee and while i like it i prefer Rhythmbox for one main reason. . . it seems to be lighter. If i could get this one problem solved then i would have my mind made up. Anyone able to help?

Try to increase the Network Buffer | Edit > Preferences > playback
It fixed the same problem that I was having

---

