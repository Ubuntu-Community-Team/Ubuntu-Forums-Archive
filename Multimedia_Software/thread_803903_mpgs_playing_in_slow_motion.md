---
title: "mpgs playing in slow motion"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Dai777 on 2008-05-22
what's missing as all my mpgs wmv's are playing in slow motion with no sound.

---

### Post by NilsE on 2008-05-22
> **Dai777 said:**
> what's missing as all my mpgs wmv's are playing in slow motion with no sound.
I am not sure which player you are using but most of the players have a speed option for looking at videos and listening to audios in slow motion.  Check to see if the one you are using is one that has that option.

---

### Post by Dai777 on 2008-05-22
mplayer won't play an mpg  vlc plays normal speed no sound and totem plays in slow motion with no sound.

all settings seem to be default.

---

### Post by Dai777 on 2008-05-23
I have sorted mpgs with xine extras but still having problems with watching wmv files in a web page.

[http://dai-videotutes.blogspot.com/2007_05_01_archive.html](http://dai-videotutes.blogspot.com/2007_05_01_archive.html)
some of my blog videos have sound but no video

---

### Post by exquest on 2008-08-05
I seem to have a similar problem.  Earlier today I was able to watch a downloaded .wmv file but when I tried to show it to my girlfriend I was unable to watch it.  The video is in slow motion with no sound.  This is also true for the same video in .mov format.  It's not the video.  I can boot up into windows and watch it.  Even VLC shows the video with no sound.  What gives?

---

### Post by drraf on 2008-08-27
In my case I had .MOV files which were played in slow motion.
I've noticed it was just after installation of mplayer. Removal of mplayer fixed my problem immediatelly.
I am using Totem to play videos and it meets all my requirements as a movie player.
--
Rafal

---

### Post by razany on 2008-10-19
Had the same problem.
Found the solution here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/221488/comments/7](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/221488/comments/7)

"...was able to resolve using the "Sound Preferences" accessed via System -> Preferences -> Sounds.

All options were originally set to Autodetect. After changing all to ALSA, I was able to play videos that previously had been extremely slow."

---

### Post by shlicshlac on 2008-10-20
Razany your solution fixed my problem too. Thanks!

---

### Post by soho2014 on 2009-06-14
My son-in-law has the same problem with Ubuntu 9.04 playing videos in slow motion. I'm going over there today to try out your solution.

---

