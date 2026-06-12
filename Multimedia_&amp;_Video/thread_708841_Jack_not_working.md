---
title: "Jack not working"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by parrosa on 2008-02-26
Hi,

i tried several settings, read several posts, but till now nothing works. 

I'm runnig Ubuntu studio 7.1 Gutsy gibbon.have a realtek & driver. 

error message:

02:15:19.892 Patchbay activated.
02:15:19.951 Statistics reset.
02:15:19.985 Startup script...
02:15:19.987 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]
02:15:20.002 MIDI connection graph change.
can't create mcop directory
Creating link /home/paulo/.kde/socket-vivo.
02:15:20.366 Startup script terminated with exit status=256.
02:15:20.366 JACK is starting...
02:15:20.366 /usr/bin/jackd -v -dalsa -ddefault -r22050 -p256 -n2 -P
02:15:20.367 JACK was started with PID=4996 (0x1384).
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 22050
creating alsa driver ... default|-|256|2|22050|0|0|nomon|swmeter|-|32bit
configuring for 22050Hz, period = 256 frames, buffer = 2 periods
[B]ALSA: final selected sample format for playback: 32bit little-endian
You appear to be using the ALSA software "plug" layer, probably
a result of using the "default" ALSA device. This is less
efficient than it could be. Consider using a hardware device
instead rather than using the plug layer. Usually the name of the
hardware device that corresponds to the first soun[/B]
ALSA: cannot set period size to 256 frames for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x805b858 fd = -1
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
02:15:20.428 JACK was stopped successfully.
02:15:20.428 Post-shutdown script...
02:15:20.428 killall jackd
jackd: no process killed
02:15:20.568 MIDI active patchbay scan...
02:15:20.568 MIDI connection change.
02:15:20.645 Post-shutdown script terminated with exit status=256.
02:15:20.772 MIDI active patchbay scan...
02:15:21.601 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

And what does that message in bold means?

BTW, i'm quite new to linux.. 

downloaded and tried to update alsa and jack drivers, but because my linux machine isn't connected to the net, i have to install with usb pen. how can i update the drivers this way?

---

