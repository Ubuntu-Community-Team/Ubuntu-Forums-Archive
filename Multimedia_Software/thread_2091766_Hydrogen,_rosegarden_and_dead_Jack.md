---
title: "Hydrogen, rosegarden and dead Jack"
date: 2012-12-06
forum: Multimedia Software
---

### Post by vector on 2012-12-06
HI all,
Having some real weird troubles here.
I have never been able to get rosegarden running on this pc.
Seems to be a low level Jack problem. I have read ooddles of posts tried many things over the months but generally give up. Can some one please help me.

3.0.0-28-generic #45-Ubuntu
hydrogen start up from terminal but gives a jack memory error
Hydrogen 0.9.5
jackd 0.121.0
```

JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
cannot lock down memory for RT thread (Cannot allocate memory)
jackd watchdog: timeout - killing jackd
cannot continue execution of the processing graph (Broken pipe)
zombified - calling shutdown handler

```

thanks id really like to get this to work

---

### Post by vector on 2012-12-06
ok I had to add 

```
sudo gedit /etc/security/limits.d/audio.conf

and added these two lines
@audio - rtprio 95
@audio - memlock unlimited

```

now rosegarden works and plays midi.

hydrogen still wont start jack server tho
```
jackd 0.121.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
jackd watchdog: timeout - killing jackd
cannot continue execution of the processing graph (Broken pipe)
zombified - calling shutdown handler

```

qjackctl als produces errors if I try to run it.
```
21:46:48.018 Patchbay deactivated.
21:46:48.073 Statistics reset.
21:46:48.097 ALSA connection change.
21:46:48.137 ALSA connection graph change.
21:47:03.010 Startup script...
21:47:03.011 artsshell -q terminate
sh: artsshell: not found
21:47:03.414 Startup script terminated with exit status=32512.
21:47:03.414 JACK is starting...
21:47:03.415 /usr/bin/jackd -v -r -u -doss -r44100 -p1024 -n3 -w16
jackd 0.121.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_net.so
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_oss.so
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_firewire.so
21:47:03.432 JACK was started with PID=2659.
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_alsa.so
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_dummy.so
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
new client: oss, id = 1 type 1 @ 0x8b50f30 fd = -1
21:47:03.482 JACK was stopped successfully.
21:47:03.483 Post-shutdown script...
21:47:03.484 killall jackd
21:47:03.485 JACK has crashed.
jackd: no process found
21:47:03.895 Post-shutdown script terminated with exit status=256.
21:47:05.607 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by silverhaze06 on 2012-12-06
I'm not much of an expert with this stuff, but have you installed the ubuntu studio controls? I was having the same kinds of problems with hydrogen before I installed all the extra ubuntu studio packages from the software center.

---

