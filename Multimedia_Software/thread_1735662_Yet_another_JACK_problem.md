---
title: "Yet another JACK problem"
date: 2011-04-21
forum: Multimedia Software
---

### Post by netro_grant on 2011-04-21
I did a search on this problem and couldn't find a solution but I apologise in advance if there is one kicking about there on the forum. I recently downloaded hydrogen drum machine and am currently trying to get it working, but before I even start on that I need to get jack up and running. It won't start! I have no idea what I'm doing in this area but here is a screen dump of the error message I get when runnin "qjackctl":

```
21:39:26.387 Patchbay deactivated.
21:39:26.456 Statistics reset.
21:39:26.478 Startup script...
21:39:26.478 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
21:39:26.486 ALSA connection graph change.
sh: artsshell: not found
21:39:26.897 Startup script terminated with exit status=32512.
21:39:26.897 JACK is starting...
21:39:26.898 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
21:39:26.913 JACK was started with PID=3148.
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
21:39:27.104 ALSA connection change.
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver CA0106 running on card 0 - Audigy SE [SB0570] at 0xdce0 irq 18
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
AcquireSelfRealTime error
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
.....REPEATS THIS FOR FRICKIN AGES.....
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
21:39:34.115 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
.....AND AGAIN REPEATS FOR FRIKIN AGES!!.......
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::Pro
21:39:34.245 JACK was stopped successfully.
21:39:34.246 Post-shutdown script...
21:39:34.246 killall jackd
21:39:34.264 JACK has crashed.
cessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
......AND AGAIN BUT EVEN LONGER THIS TIME........
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackSocketClientChannel read fail
Cannot open qjackctl client
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
jackd: ../common/JackGraphManager.cpp:45: void Jack::JackGraphManager::AssertPort(jack_port_id_t): Assertion `port_index < fPortMax' failed.
jackd: no process found
21:39:34.703 Post-shutdown script terminated with exit status=256.
21:39:40.299 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
21:39:50.665 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
```

I cut the massive repetitions out to save space.
Does anyone know what's going on here and how I can fix it?

Thanks in advance x

---

### Post by netro_grant on 2011-04-21
It appears to make several attempts at starting, but fails to read something, over and over again and so eventually times out and cannot start JACK. So I'm guessing it's perhaps something to do with JACK's access to memory?

---

### Post by netro_grant on 2011-04-21
Never mind I managed to find a solution when I googled "Cannot lock down memory area (Cannot allocate memory)"

---

### Post by KegHead on 2011-04-21
Hi!

Congrats!

Please mark your thread as "solved".

KegHead

---

