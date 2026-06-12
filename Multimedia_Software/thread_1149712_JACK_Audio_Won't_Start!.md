---
title: "JACK Audio Won't Start!"
date: 2009-05-05
forum: Multimedia Software
---

### Post by The1Robomaster on 2009-05-05
Whenever I try to start JACK, I get an error message and it won't start. 

 p, li { white-space: pre-wrap; }  [COLOR=#999999]12:10:14.387 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:10:14.467 Statistics reset.[/COLOR]
 [COLOR=#999999]12:10:14.479 Startup script...[/COLOR]
 [COLOR=#990099]12:10:14.480 artsshell -q terminate[/COLOR]
 [COLOR=#66cc99]12:10:14.484 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]12:10:14.897 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]12:10:14.897 JACK is starting...[/COLOR]
 [COLOR=#990099]12:10:14.898 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]12:10:14.911 JACK was started with PID=7281.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1212225856, from thread -1212225856] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]12:10:15.091 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]12:10:15.092 Post-shutdown script...[/COLOR]
 [COLOR=#990099]12:10:15.092 killall jackd[/COLOR]
 [COLOR=#cccc99]12:10:15.109 ALSA connection change.[/COLOR]
 jackd: no process killed
 [COLOR=#999999]12:10:15.499 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]12:10:17.320 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


I've read several topics on other people who have this problem but I still can't fix it! Please help me!

I have a Compaq CQ50 Laptop with 2 GB of RAM, running Ubuntu 9.04. I really need help in this as I can't run Rosegarden without Jack! Please help!

---

### Post by Cordess on 2009-05-06
Same problem here.

---

### Post by gescape on 2009-05-07
Same issue here. 
Message:

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1211341120, from thread -1211341120] (1: Operation not permitted)
cannot create engine
16:14:39.343 JACK was stopped successfully.
16:14:39.344 Post-shutdown script...
16:14:39.345 killall jackd
jackd: no process killed
16:14:39.755 Post-shutdown script terminated with exit status=256.
16:14:41.346 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

gescape@fugazi:~$ jackd -R -d alsa
no message buffer overruns
jackd 0.116.1
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1212127552, from thread -1212127552] (1: Operation not permitted)
cannot create engine
gescape@fugazi:~$
gescape@fugazi:~$ jackd -d alsa
no message buffer overruns
jackd 0.116.1
JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
jack main caught signal 15
gescape@fugazi:~$ 

Message:
16:35:26.152 Patchbay deactivated.
16:35:26.302 Statistics reset.
16:35:26.495 Client activated.
16:35:26.770 XRUN callback (1).
16:35:26.777 JACK connection change.
16:35:26.779 ALSA connection change.
16:35:28.638 XRUN callback (49 skipped).
16:35:30.891 XRUN callback (52 skipped).
16:35:32.895 XRUN callback (46 skipped).
16:35:34.899 XRUN callback (46 skipped).
16:35:36.902 XRUN callback (46 skipped).
16:35:38.907 XRUN callback (46 skipped).
16:35:40.910 XRUN callback (45 skipped).
16:35:42.918 XRUN callback (46 skipped).
16:35:44.924 XRUN callback (46 skipped).
16:35:46.911 Client deactivated.
16:35:46.913 Post-shutdown script...
16:35:46.914 killall jackd
16:35:47.328 Post-shutdown script terminated successfully.

Does anyone went across the solution for this problem?
Thanks.

---

### Post by hortstu on 2009-05-20
I'm having the same problem... anyone solved it yet?

Here's my error message...

Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.

and the result of "messages"

01:07:42.458 Patchbay deactivated.
01:07:42.558 Statistics reset.
01:07:42.580 ALSA connection graph change.
01:07:42.881 ALSA connection change.
01:07:49.252 Startup script...
01:07:49.252 artsshell -q terminate
sh: artsshell: not found
01:07:49.654 Startup script terminated with exit status=32512.
01:07:49.654 JACK is starting...
01:07:49.655 /usr/bin/jackd -v -t2000 -dfreebob -dhw:0 -r96000 -p256 -n3 -D -I1 -O1
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
01:07:49.669 JACK was started with PID=7505.
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
new client: freebob_pcm, id = 1 type 1 @ 0x841a1f0 fd = -1
Freebob using Firewire port 0, node -1
new buffer size 256
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.11
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 96000
LibFreeBoB MSG:   Period Size              : 256
LibFreeBoB MSG:   Nb Buffers               : 3
LibFreeBoB MSG:   Directions               : 0
Ieee1394Service::initialize: Could not get 1394 handle: No such file or directory
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
LibFreeBoB ERR: cannot create libfreebob handle
FreeBoB ERR: FREEBOB: Error creating virtual device
[0mcannot load driver module freebob
starting server engine shutdown
stopping driver
01:07:50.041 JACK was stopped successfully.
01:07:50.041 Post-shutdown script...
01:07:50.041 killall jackd
01:07:50.042 JACK has crashed.
jackd: no process killed
01:07:50.455 Post-shutdown script terminated with exit status=256.
01:07:52.135 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by ruhtranayr on 2009-06-04
I'm having the same error on Debian Lenny (just compiled/installed realtime kernel 2.6.26.4-rt14):

JACK compiled with System V SHM support. cannot use real-time scheduling (FIFO at priority 10) [for thread 147109600, from thread 147109600] (1: Operation not permitted) cannot create engine

Although, it seems to work fine when qjackctl is launched with sudo

And $sudo jackd -R -d alsa works

I think I just need to add user to realtime group...

Back to googling.

---

### Post by tlipfert on 2009-06-05
Add me to the list having this problem. I have a fresh Jaunty install, only trying to run Ardour, and Jack gives me the message:

Cannot Use real time scheduling (Fifo ....)

Any help most appreciated!

Thanks.

---

### Post by ericbarch on 2009-06-07
For the operation not permitted I added myself to the audio group under System >> Administration >> Users and Groups then rebooted. Now Jack is running great with RT support. Hope that helps.

---

### Post by tlipfert on 2009-06-07
> **tlipfert said:**
> Add me to the list having this problem. I have a fresh Jaunty install, only trying to run Ardour, and Jack gives me the message:

Cannot Use real time scheduling (Fifo ....)

Any help most appreciated!

Thanks.


Hi again,

Got my Jack running with some great help at the Ardour forum. The steps were:

1. run a small diagnostic program to check a bunch of audio settings

2. follow the links in the file output by the diagnostic program

3. make changes one at a time  to test if Jack could launch without either the "broken pipe" or the "cannot use real time scheduling (fifo ...) errors. 

If you read through my conversation top to bottom, you should be able to recreate what worked for me. Here is the link:

[http://ardour.org/node/2733](http://ardour.org/node/2733)

Good luck!

Theo

---

### Post by jdieter on 2010-06-30
I could NOT get jack working. Ardour would not start. I got all kinds of errors and hangs including "bus error", "jack has crashed". Removing pulseaudio and /dev/shm rm * fixed it!

sudo apt-get remove pulseaudio
sudo rm /dev/shm/*

---

