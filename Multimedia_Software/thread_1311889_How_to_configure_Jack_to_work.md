---
title: "How to configure Jack to work"
date: 2009-11-02
forum: Multimedia Software
---

### Post by hellocatfood on 2009-11-02
I have installed Ardour on Karmic, which brings with it Jack. Whenever I start Jack it automatically kills itself, with the following error
```
00:09:07.762 Patchbay deactivated.
00:09:07.838 Statistics reset.
00:09:07.893 ALSA connection graph change.
00:09:08.114 ALSA connection change.
00:09:10.773 Startup script...
00:09:10.773 artsshell -q terminate
sh: artsshell: not found
00:09:11.175 Startup script terminated with exit status=32512.
00:09:11.175 JACK is starting...
00:09:11.177 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1217055040, from thread -1217055040] (1: Operation not permitted)
cannot create engine
00:09:11.215 JACK was started with PID=23530.
00:09:11.225 JACK was stopped successfully.
00:09:11.225 Post-shutdown script...
00:09:11.226 killall jackd
jackd: no process found
00:09:11.634 Post-shutdown script terminated with exit status=256.
00:09:13.354 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```
I have jack installed but yet it still doesn't start. Does anyone know what settings I need to have in order to start jack?

---

### Post by hellocatfood on 2009-11-11
*bump*

Am I the only one with this problem?

---

### Post by markbuntu on 2009-11-12
If you have not also installed the rt kernel (linux-rt) then you cannot run jack in rt mode. You can deselect rt in the jack control setup.

FYI. The multimedia production forum is a better place for questions about ardour, jack, recording. production, etc.

---

### Post by LightEngineer007 on 2009-11-12
You will have to disable or stop Pulse Audio for Jack to be able to start. The two both fight for use of ALSA devices and Jack just gives up. There are also some permissions that need to be setup that are listed in the Jack documentation.  

I managed to get Jack to work on Intrepid last year with a stock kernel (no RT). It will run fine like that for playing around but you will want the RT for any real performance type applications. I will go down that road again soon with Karmic (if it ever becomes a stable release like Intrepid is). 

In theory there is a way to get Jack and Pulseaudio to work together. There is a plugin for Pulse that allows it to interface to Jack. Ubuntu doesn't supply this but Debian does and it will install into Ubuntu. Google around with keywords Jack and Pulseaudio and it will come up. I tried this plugin but was never able to get them to work reliably together. For now I just kill the Pulse dameon if I need to use Jack.

---

### Post by werpumukl on 2013-03-04
I use Ubuntu Studio 10 or 12

To start jack you must run it in a terminal with root-privileges:

**CTRL & ALT & T**
(opens the terminal)

type:
**sudo -i**
(gets you root-privileges to your computer; be careful what you do, it could destroy a lot!!! Do nothing now, of what you are ABSOLUTELY sure!!!!)

then type:
**qjackctl**
(starts jack. Now you can start it and it gets a connection)

:guitar:

---

### Post by wildmanne39 on 2013-03-05
Old thread closed!

---

