---
title: "ARDOUR - startup issues"
date: 2011-06-17
forum: Multimedia Software
---

### Post by sanjeevpunj on 2011-06-17
I installed ARDOUR GTK2 and started the application. I get this message-

ARDOUR could not start jack.

There are several possible reasons:

1) You requested audio parameters that are not supported..
2) JACK is running as another user.

Please consider the possibilities, and perhaps try different parameters.

I then tried to start JACK. I get this-

16:16:06.696 Patchbay deactivated.
16:16:06.711 Statistics reset.
16:16:06.734 ALSA connection change.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:16:06.742 ALSA connection graph change.
16:17:10.086 JACK is starting...
16:17:10.086 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot create thread 1 Operation not permitted
16:17:10.123 JACK was started with PID=3999.
Cannot create thread 1 Operation not permitted
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver ICE1712 running on card 0 - M Audio Audiophile 24/96 at 0xa000, irq 20
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:17:10.207 JACK was stopped with exit status=255.
16:17:12.131 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:20:05.262 Patchbay deactivated.
16:20:36.065 ALSA connection graph change.
16:20:36.105 ALSA active patchbay scan...
16:20:36.106 ALSA connection change.
16:20:36.307 ALSA active patchbay scan...
16:23:28.216 ALSA connection graph change.
16:23:28.408 ALSA active patchbay scan...
16:23:41.051 JACK is starting...
16:23:41.051 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:23:41.072 JACK was started with PID=4110.
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver ICE1712 running on card 0 - M Audio Audiophile 24/96 at 0xa000, irq 20
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:23:41.209 JACK was stopped with exit status=255.
16:23:43.229 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

So anyone facing this when running ARDOUR?

Oh I must delete this thread! Reason I could get ARDOUR running, by simply turning off ALSA PLAYER which was already running.

---

