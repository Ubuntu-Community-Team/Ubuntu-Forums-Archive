---
title: "Piping audio between applications"
date: 2010-05-30
forum: Multimedia Software
---

### Post by PowerRanger on 2010-05-30
Greetings.  I would like to know if it is possible to pipe audio between applications.  I am running 10.04.  The applications I am interested in are Teamspeak2 and mumble.  I would like to link the input of the 1st to the output of the 2nd, and the output of 1st to the input of the 2nd.  This would create a 'bridge' between these application that would allow all users of one application (Teamspeak)connected to one server to communicate with the users of the other application (Mumble)on another server.  I do not need to monitor the bridge.  I think what I want to use is called qjackctl, but I can't seem to get it to work.  Running it from the command line it flashes up for a second, then quits.  The terminal output is:

```
qjackctl
Suspending PulseAudio
WARNING: Child process terminated by signal 11
Failure to resume: Invalid argument

```

Teamspeak uses oss and mumble can use alsa, oss, or pulse.

My questions are; 
1. Am I on the right track using qjackctl, or is there an easier/better way?
2. Does qjackctl/pulse work out-of-the box with 10.04?
3. Do I have something mis-configured?

My .jackdrc contains:
```
/usr/bin/jackd -v -r -dalsa -dhw:0 -r44100 -p1024 -n2
```

The only way I could get it to start at all was to un-enable realtime.

The qjackctl.log before qjackctl disappearing is:

```
01:34:11.402 Logging started --- Sun May 30 01:34:11 2010 ---
01:34:11.423 Patchbay deactivated.
01:34:11.491 Statistics reset.
01:34:11.508 ALSA connection graph change.
01:34:11.705 ALSA connection change.
01:34:15.319 Startup script...
01:34:15.320 artsshell -q terminate
sh: artsshell: not found
01:34:15.726 Startup script terminated with exit status=32512.
01:34:15.727 JACK is starting...
01:34:15.728 /usr/bin/jackd -v -r -dalsa -dhw:0 -r44100 -p1024 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
getting driver descriptor from /usr/lib/jack/jack_firewire.so
01:34:15.740 JACK was started with PID=2521.
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_net.so
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x838f580 fd = -1
start poll on 3 fd's
new buffer size 1024
registered port system:capture_1, offset = 4096
registered port system:capture_2, offset = 8192
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
registered port system:playback_3, offset = 0
registered port system:playback_4, offset = 0
registered port system:playback_5, offset = 0
registered port system:playback_6, offset = 0
registered port system:playback_7, offset = 0
registered port system:playback_8, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
2521 waiting for signals
load = 0.0633 max usecs: 27.000, spare = 21306.000
01:34:17.923 Server configuration saved to "/home/flip/.jackdrc".
01:34:17.925 Statistics reset.
01:34:17.928 Client activated.

```

 
I then must killall jackd else I can't restart qjackd.






Any help or input is appreciated.

---

