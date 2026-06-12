---
title: "Looking for a Good Streaming Audio Player like Xmms"
date: 2009-03-13
forum: Multimedia Software
---

### Post by kwabena39 on 2009-03-13
Hi, I'm using Ubuntu 8.10 and I listen to a lot of talk shows on the internet, and I am looking for a good, stripped down audio streaming player (mp3, shoutcast pls, etc.)

I have Alsaplayer, and I like it, but whenever I go to use Blender or other graphics programs, Alsaplayer causes the system to freeze/crash.  I like to listen to talk shows while I'm working on graphics projects.

I didn't used to have this problem when I ran Ubuntu 8.04, but now I'm having it in 8.10.

Alsaplayer seems to have conflicts with Blender, and Xmms is not included in the distribution.

So is there any other lightweight player out there like Alsaplayer or Xmms that I can use?

---

### Post by linuxwizard on 2009-03-13
Look at Audacious. It is in the repo.
[http://audacious-media-player.org/index.php?title=Main_Page](http://audacious-media-player.org/index.php?title=Main_Page)

---

### Post by markbuntu on 2009-03-13
If you miss your xmms (not xmms2) and would like to have it back, (this should work on Intrepid also):
i386:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

Change the output plugin to alsa and you should be good to go.

---

