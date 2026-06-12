---
title: "Simple way to record TV?"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by phossal on 2007-01-10
Can anyone suggest a very simple way to record TV from my TV tuner? I don't care if the *commands* are difficult, as long as the installation is simple. For example, MythTV won't just "fit in", and I don't want to take the time to install it properly. Can't I just pipe something to something, and convert some stuff, and... can you help?

---

### Post by majoridiot on 2007-01-10
assuming it's where the video tuner is located...
```
cat /dev/video0 > filename.mpg
```
should record the output to an mpg file for manipulation, etc. you can use ivtv (assuming that
is the driver you are using) to change inputs, etc.

---

### Post by kebes on 2007-01-10
Well, if you have a video capture card, and it's configured properly, you can just go:

cat /dev/video > test.mpg

And it will dump the MPEG video data stream to a file, assuming your card does MPEG compression on-card. (You'll have to go Ctrl+C to stop it!) So yes you can dump video fairly easily... Then you can use commandline programs like "mencoder" and "mplayer" to re-encode it or play it or whatever. Everything can be put into bash scripts and run via cron or whatever.


However normally getting the video capture card to work is the hard part of mythTV! If you've got the video capture card working, then installing MythTV should be pretty easy.

---

### Post by phossal on 2007-01-10
Exactly what I was looking for, guys, thank you both. :D

---

### Post by bodymind on 2007-01-25
and video with audio? :|

---

### Post by phossal on 2007-01-25
Depending on what you're doing, you may really be looking for MythTV.

---

