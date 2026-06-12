---
title: "Jack2 will not start"
date: 2012-06-01
forum: Multimedia Software
---

### Post by sselt on 2012-06-01
Jack2 used to work. One day it stopped working.
Qjackctl output:

jackdmp 1.9.8
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
14:22:41.624 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot read socket fd = 14 err = Success
JackSocketClientChannel read fail
Cannot create new client
Cannot open qjackctl client
14:22:44.379 JACK is stopping...
jack main caught signal 15
14:23:20.455 JACK is stopping...
14:23:21.047 JACK is stopping...
14:23:21.094 JACK was stopped successfully.
14:23:21.095 JACK has crashed.

The last four lines is from repeated clicks of Stop in Qjackct.

---

### Post by sselt on 2012-09-14
Found this solution a while back. The capture channel had to be on in alsamixer. ;)

---

