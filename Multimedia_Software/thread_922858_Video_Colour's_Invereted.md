---
title: "Video Colour's Invereted"
date: 2008-09-17
forum: Multimedia Software
---

### Post by zapperzen on 2008-09-17
Hey All,  So I've installed my restricted packages, setup my codec's but I must have messed something up.
I followed this guide to install everything here.   [http://ubuntuforums.org/showthread.php?t=766683&highlight=color](http://ubuntuforums.org/showthread.php?t=766683&highlight=color)

My issue is that every time I play a video, regardless of how it's encoded it plays just fine, I can hear it just fine, however all the colors are inverted. 

Has anyone else run into this? If so how would I go about fixing it ? If you need anymore info just let me know and I'll get it out when I can.

---

### Post by mc4man on 2008-09-17
read thru here, if that doesn't post work back for additional solutions 
[http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white](http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white)
post 2

---

### Post by zapperzen on 2008-09-17
Thanks, I'll give it a shot now.  I'll post back if it works or not.

---

### Post by zapperzen on 2008-09-18
Ok I tried a few steps in that post you linked for me and they seemed to fix it.  For me I first I tried 

sudo apt-get purge gxine

well not only did that not fix the video, it killed sound.   So I reinstalled that and moved on.  I tried the trick with the nvidia-settings, it wasn't installed so I installed it with the terminal.  Then trying to reset the settings to default and that seemed to fix it.  

If anyone else happens to be using this info I do use VLC for a media player, but I did try adjusting the hue in the default player of Totem too.  Now video seems to be working in both.

---

