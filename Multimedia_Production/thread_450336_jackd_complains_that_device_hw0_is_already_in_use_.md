---
title: "jackd complains that device hw:0 is already in use but all my sound apps are dead."
date: 2007-05-21
forum: Multimedia Production
---

### Post by the_it on 2007-05-21
I am running festy and I want to take a look at our sound apps here.  I'm trying to get rosegarden and ardour to work but I read they run on jack and I can't get jack to start.

> markd@trixie:~$ jackd -d alsa
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns


the thing is, I already killed my music player and i can't see any esd using my sound card.  And besides, can't it share sound access?

> markd@trixie:~$ ps aux|grep esd
markd    21822  0.0  0.0   5020   812 pts/0    R+   20:06   0:00 grep esd

What should I kill/install/config or try out to stop whatever is using my soundcard?  Is it possible to start jack and have my desktop sounds still running as normal?

---

### Post by eric71 on 2007-05-22
try installing Qjackctl and using that to start jack.  Choose Alsa as the driver in the settings, rather than OSS. If you are using the normal Feisty kernel, you won't be able to select the realtime option in the Qjackctl settings without receiving an error. It looks as if your command line entry should do all of this, so I'm not sure if it will help. With Feisty I haven't had any problems with ESD running and Jack running as in older Ubuntu varieties.

---

### Post by the_it on 2007-05-22
qjackctl has the same problems as command-line startup.

```
07:44:22.932 Patchbay deactivated.
07:44:22.959 Statistics reset.
07:44:22.977 Startup script...
07:44:22.978 artsshell -q terminate
07:44:23.010 MIDI connection graph change.
can't create mcop directory
Creating link /home/markd/.kde/socket-trixie.
07:44:23.237 Startup script terminated with exit status=256.
07:44:23.237 JACK is starting...
07:44:23.237 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
07:44:23.240 JACK was started with PID=12381 (0x305d).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
07:44:23.262 JACK was stopped successfully.
07:44:23.262 Post-shutdown script...
07:44:23.262 killall jackd
jackd: no process killed
07:44:23.441 MIDI connection change.
07:44:23.474 Post-shutdown script terminated with exit status=256.
07:44:25.460 Could not connect to JACK server as client. Please check the messages window for more info.
```

[http://img511.imageshack.us/img511/4192/qjackctlcg9.png](http://img511.imageshack.us/img511/4192/qjackctlcg9.png)

What's happening is that it's complaining that it can't use the soundcard, since the soundcard is in use. :s

btw, I probably should mention this, but I'm running on Feisty 64bit.

lspci results for my soundcard.
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

---

### Post by theorem_hunter on 2007-05-28
i am running Edgy 64bit & i am getting the same errors when running Qjackctl. i want to run lives.

lspci gives
```

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

```

this is what i get when i run lives:

```

$ lives

LiVES 0.9.8.4
Copyright 2002-2007 Gabriel Finch (salsaman@xs4all.nl) and others.
LiVES comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.

jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

```

---

### Post by tomjennings on 2007-06-06
This may be related to a hibernate/suspend sound driver bug:
    [http://ubuntuforums.org/showthread.php?p=2665766](http://ubuntuforums.org/showthread.php?p=2665766)
    [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

(The fix in one of the posts on the first one didn't fix it for me.)

$ uname -a
Linux qx 2.6.20-16-lowlatency #2 SMP PREEMPT Wed May 23 01:49:41 UTC 2007 i686 GNU/Linux

I installed ubuntustudio 7.04

jackd and sound works just fine for me (after much initial wrangling) -- until I suspend or hibernate. Then I get either /the playback device "hw:0" is already in use...cannot load driver module alsa/ error and segfaulted jackd, or I get bad noises and weird behavior out of the sound card. I can't seem to determine why I get one symptom vs. the other, though mostly I get the weird noises. It probably depends on what was done last or what was running at suspend time. 

No sound program is running of course.

/etc/init.d/alsa-utils {restart or force-reload} has no effect.

jackd invokation (from qjackctl's .jackdrc) is
/usr/bin/jackd -v -R -dalsa -dhw:0 -r48000 -p1024 -n3 -P

A normal reboot solves it.

---

### Post by Uber_Rage on 2008-05-08
Found the solution to the "hw:0 already in use":

All you have to do is "restart" ALSA 

sudo /sbin/alsa force-reload

The next time you start Jack, it should give you no problems.

As a side note, its really becoming frustrating to read blogs these days...there were days of Gentoo that I miss...I always found the answer to questions that loomed me for days. People talking about restarting their linux boxes as a solution is beyond me.... One might as well go back to Windows...

---

