---
title: "Problem: Could not connect to JACK server as client."
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by CapnWhizBang on 2006-10-15
I HAD it working with the Intel chip on the motherboard, well, I could only capture MONO but..... Hey, it was working.

So I bought an M-Audio Audiophile USB thingy. It took quite some time to get it working to the point that I could select it from System/Preferences/Sound and get stuff to play through it. I can now switch between the intel(laptop speakers) and the Audiophile USB and play stuff with Rhythmbox Music Player.

But, what I want to do is record in "Stereo". So when it didn't work initially I started downloading and installing all the latest and greatest versions of 
alsa - 1.0.13
jack audio connection kit - 0.102.20
qjackctl 0.2.21

Now I keep getting errors, not even the Intel configuration works...
Here's what I get when trying to start the setup preset for the Intel chip

11:44:08.327 Patchbay deactivated.
11:44:08.770 Statistics reset.
11:44:09.151 Startup script...
11:44:09.152 artsshell -q terminate
11:44:09.252 MIDI connection graph change.
11:44:09.539 Startup script terminated with exit status=256.
11:44:09.540 JACK is starting...
11:44:09.541 jackd -R -p128 -t2000 -dalsa -dhw:0 -r44100 -p64 -n2 -Phw:0 -S
11:44:09.548 JACK was started with PID=15933 (0x3e3d).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|-|64|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
11:44:09.771 Could not connect to JACK server as client. Please check the messages window for more info.
11:44:11.671 MIDI connection change.
11:44:12.079 Could not connect to JACK server as client. Please check the messages window for more info.
11:44:13.793 JACK is stopping...
jack main caught signal 15
no message buffer overruns
11:44:14.081 JACK was stopped successfully.

here's what I get when trying to launch the Setup Preset for the USB...

11:46:41.112 Startup script...
11:46:41.116 artsshell -q terminate
11:46:41.546 Startup script terminated with exit status=256.
11:46:41.551 JACK is starting...
11:46:41.555 jackd -R -p128 -t2000 -dalsa -r48000 -p256 -n2 -D -Chw:1 -Phw:1
11:46:41.580 JACK was started with PID=16208 (0x3f50).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
11:46:41.647 Could not connect to JACK server as client. Please check the messages window for more info.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|256|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 256 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 24bit big-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit big-endian
ALSA: use 2 periods for playback
11:46:44.285 Could not connect to JACK server as client. Please check the messages window for more info.
11:46:45.695 JACK is stopping...
jack main caught signal 15
no message buffer overruns
11:46:46.004 JACK was stopped successfully.

I can't even get it to connect to a dummy...

11:47:07.670 Startup script...
11:47:07.673 artsshell -q terminate
11:47:08.100 Startup script terminated with exit status=256.
11:47:08.105 JACK is starting...
11:47:08.109 jackd -p128 -ddummy -r44100 -p1024
11:47:08.136 JACK was started with PID=16262 (0x3f86).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
creating dummy driver ... dummy_pcm|44100|1024|23219|2|2
11:47:10.226 Could not connect to JACK server as client. Please check the messages window for more info.
11:47:12.074 JACK is stopping...
jack main caught signal 15
no message buffer overruns
11:47:12.276 JACK was stopped successfully.

Does anyone see what the problem is? Thanks...

---

### Post by brummer on 2006-10-16
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian

maybe your soundcard cant work with this settings try a higher frames/period from 256 or 512 frames and a sampelrate 96000 an go step by step down to get the limit from your soundcard you can do this with the setup button in the mainwindo and read the message with the messages button
              brummer

---

