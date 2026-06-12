---
title: "No sound in some applications please help!"
date: 2010-11-25
forum: Multimedia Software
---

### Post by Eremis on 2010-11-25
Hi everyone,

I got a new sound issue that I can't solve...

First of, in order to get my sound working I had to manually download new alsa drivers and compile + install them (for this I used a script).

My original post: [http://ubuntuforums.org/showthread.php?t=1467628](http://ubuntuforums.org/showthread.php?t=1467628)
used this script to fix: [http://ubuntuforums.org/showpost.php?p=9136618&postcount=2](http://ubuntuforums.org/showpost.php?p=9136618&postcount=2)

The problem is I had to recompile the drivers every time I got a new kernel update. Now after I updated to the newest one (.26 i believe) and redid everything again, I noticed that only half of my applications can play sound.

For example Firefox can play sound from youtube, etc... When I open a mp3, I can play it with audacity, amarock but not audacious2, or vlc..

Why???

Is there a permanent fix to this problem? Why doesn't Ubuntu give an update so the entire alsa will update to the same ver. as in 10.10???

---

### Post by Eremis on 2010-11-25
I figured it out, It turs out the applications (vlc, audacious2) were using pulseaudio as the default output not alsa... 

The only problem now is Pithos (pandora client) it does not have settings so I cant really configure the output stream...

Does anyone know how to solve this?

---

