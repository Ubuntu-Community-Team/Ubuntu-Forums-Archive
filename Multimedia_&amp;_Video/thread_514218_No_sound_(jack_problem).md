---
title: "No sound (jack problem?)"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by theted on 2007-07-31
**PROBLEM FIXED!**

Hi! I've just set up a brand new install of Ubuntu (Feisty) on my buddy's computer. Everything was working fine until we installed the ubuntu studio (ubuntustudio.org) packages. Sound disapeared and I know no way to fix it since i am completely new to Jack. Jack Control (I suppose that's the right program?) outputs this:

> 
18:37:30.894 Patchbay deactivated.
18:37:30.917 Statistics reset.
18:37:30.970 Startup script...
18:37:30.970 artsshell -q terminate
18:37:30.979 MIDI connection graph change.
can't create mcop directory
Creating link /home/daniel/.kde/socket-danne-desktop.
18:37:31.203 Startup script terminated with exit status=256.
18:37:31.203 JACK is starting...
18:37:31.203 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2 -m -i2 -o2
18:37:31.205 JACK was started with PID=6192 (0x1830).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|2|2|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
18:37:31.349 JACK was stopped successfully.
18:37:31.349 Post-shutdown script...
18:37:31.349 killall jackd
jackd: ingen process avslutad
18:37:31.406 MIDI connection change.
18:37:31.556 Post-shutdown script terminated with exit status=256.
18:37:33.446 Could not connect to JACK server as client. Please check the messages window for mor

The soundcard is a Realtek ALC888 that we had no problems installing. Any ideas? Sound is quite a vital part of his studio setup ;)
[B]
PROBLEM FIXED![/B]

---

### Post by timmahhny on 2007-07-31
You have to run command line to restart the sound. I found it these forums a few months ago, and forgot to print it out. I will post link to it, when I find it again. 
Timmahhny

---

### Post by timmahhny on 2007-07-31
[http://ubuntuforums.org/showthread.php?t=502880&highlight=audigy+sound+card+feisty]("http://ubuntuforums.org/showthread.php?t=502880&highlight=audigy+sound+card+feisty")

 This should do the trick.
Good luck
Timmahhny

---

