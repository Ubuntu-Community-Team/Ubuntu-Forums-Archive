---
title: "[SOLVED] Skipping/miscoloured video."
date: 2008-06-01
forum: Multimedia Software
---

### Post by yatesl on 2008-06-01
Hey everyone.  I'm having a bizarre problem.

In VLC Media Player, if I play a video file, it seems to skip.  Not in the sense that it misses out frames, but it seems to continuously jump back and forth.  For example, it seems to be going frame 1, frame 3, frame 2, frame 4, frame 6, frame 5 etc.  Hopefully that gives you an idea.

When running it in (Totem?) Movie Player, the colour's all wrong.  No matter how much I play with the hue, contrast and whatnot, I always have a green or blue tint to it.

I'm running on a X1400 ATi card, with the restricted drivers.  Has anyone else had this problem?

---

### Post by Ichido on 2008-06-01
I'm having trouble with the colors when playing DVDs.
I've been working through this post:
[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+player](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+player)

It is helping with some problems, but the Contrast & Color Balance is still off.

I'm testing:
gxine -Good
MoviePlayer-Totem - OK
MPlayer Movie Player - = Not Good
SMPlayer - Good & Controls = Good
VLC Media Player _ Best Player, Controls & DVD Menus features! = Best
Hope this helps you.

UPDATE:

I did the following and now my VLC and SMPlayer do NOT work,but gxine and Totem Movie Player now WORK and I can now CONTROL the COLOR Balance, Contrast & Brightness :)

1. Open a terminal window. 

2. Execute the following terminal command to install the necessary packages (make sure to approve any prompts):
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

3. Execute the following terminal command:
sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by yatesl on 2008-06-14
Just trying what you said now.  I'll update as it happens.  

For reference, this is the miscolouring I'm talking about:
[IMG]http://i32.tinypic.com/jhrolc.png[/IMG]

That's how it looks.  It should look like:
[IMG]http://i29.tinypic.com/10pa5jl.png[/IMG]

As you can see, big difference, no matter how much I fiddle.


Update:  Unfortunately, that didn't work.

```
liam@liam-laptop:~$ sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
[sudo] password for liam:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
The following extra packages will be installed:
  libpulse0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1
Suggested packages:
  pulseaudio libxine1-plugins xine-ui gxine
Recommended packages:
  libxine1-doc libxine-doc
The following packages will be REMOVED
  totem-gstreamer
The following NEW packages will be installed
  libpulse0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1
  libxine1-ffmpeg libxvmc1 totem-xine
0 upgraded, 9 newly installed, 1 to remove and 6 not upgraded.
Need to get 4888kB of archives.
After unpacking 7205kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://security.ubuntu.com gutsy-security/main libpulse0 0.9.6-1ubuntu2.1 [104kB]
Get: 2 http://archive.ubuntu.com gutsy/main libxcb1 1.0-3 [41.6kB]
Get: 3 http://archive.ubuntu.com gutsy/main libxcb-shape0 1.0-3 [14.6kB]
Get: 4 http://archive.ubuntu.com gutsy/main libxcb-shm0 1.0-3 [14.1kB]
Get: 5 http://archive.ubuntu.com gutsy/main libxcb-xv0 1.0-3 [17.7kB]
Get: 6 http://archive.ubuntu.com gutsy/main libxvmc1 2:1.0.4-2ubuntu1 [19.2kB]
Get: 7 http://archive.ubuntu.com gutsy/main libxine1 1.1.7-1ubuntu1 [2490kB]
Get: 8 http://archive.ubuntu.com gutsy/universe libxine1-ffmpeg 1.1.7-1ubuntu1 [446kB]
Get: 9 http://archive.ubuntu.com gutsy/main totem-xine 2.20.0-0ubuntu3 [1740kB]
Fetched 4888kB in 11s (417kB/s)                                                
dpkg: totem-gstreamer: dependency problems, but removing anyway as you request:
 totem-mozilla depends on totem-xine (>= 2.20.0-0ubuntu3) | totem-gstreamer (>= 2.20.0-0ubuntu3); however:
  Package totem-xine is not installed.
  Package totem-gstreamer is to be removed.
 totem depends on totem-gstreamer (>= 2.20.0-0ubuntu3) | totem-xine (>= 2.20.0-0ubuntu3); however:
  Package totem-gstreamer is to be removed.
  Package totem-xine is not installed.
(Reading database ... 100764 files and directories currently installed.)
Removing totem-gstreamer ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libpulse0.
(Reading database ... 100522 files and directories currently installed.)
Unpacking libpulse0 (from .../libpulse0_0.9.6-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package libxcb1.
Unpacking libxcb1 (from .../libxcb1_1.0-3_i386.deb) ...
Selecting previously deselected package libxcb-shape0.
Unpacking libxcb-shape0 (from .../libxcb-shape0_1.0-3_i386.deb) ...
Selecting previously deselected package libxcb-shm0.
Unpacking libxcb-shm0 (from .../libxcb-shm0_1.0-3_i386.deb) ...
Selecting previously deselected package libxcb-xv0.
Unpacking libxcb-xv0 (from .../libxcb-xv0_1.0-3_i386.deb) ...
Selecting previously deselected package libxvmc1.
Unpacking libxvmc1 (from .../libxvmc1_2%3a1.0.4-2ubuntu1_i386.deb) ...
Selecting previously deselected package libxine1.
Unpacking libxine1 (from .../libxine1_1.1.7-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxine1-ffmpeg.
Unpacking libxine1-ffmpeg (from .../libxine1-ffmpeg_1.1.7-1ubuntu1_i386.deb) ...
Selecting previously deselected package totem-xine.
Unpacking totem-xine (from .../totem-xine_2.20.0-0ubuntu3_i386.deb) ...
Setting up libpulse0 (0.9.6-1ubuntu2.1) ...

Setting up libxcb1 (1.0-3) ...

Setting up libxcb-shape0 (1.0-3) ...

Setting up libxcb-shm0 (1.0-3) ...

Setting up libxcb-xv0 (1.0-3) ...

Setting up libxvmc1 (2:1.0.4-2ubuntu1) ...

Setting up libxine1 (1.1.7-1ubuntu1) ...

Setting up libxine1-ffmpeg (1.1.7-1ubuntu1) ...
Setting up totem-xine (2.20.0-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
liam@liam-laptop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
--16:39:56--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb
           => `/tmp/dvdcss-wN6808/libdvdcss.deb'
Resolving www.dtek.chalmers.se... 129.16.29.100
Connecting to www.dtek.chalmers.se|129.16.29.100|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:39:57 ERROR 404: Not Found.
```


Double Update:  I updated to 8.04 (or whatever it is), and they both seem to work.  Ho hum.

---

