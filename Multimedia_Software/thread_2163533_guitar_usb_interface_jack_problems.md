---
title: "guitar usb interface jack problems"
date: 2013-07-18
forum: Multimedia Software
---

### Post by hagai_sela on 2013-07-18
Hi,
I am trying to connect my guitar to my ubuntu 12.04 PC. I have a chinese USB guitar interface, which I know people used successfully in ubuntu.
I tried connecting it to my speakers using qjackctl and couldn't get any sound, so I downloaded compiled and installed jack 1.9.9.5. This is the output I get when I try running it:

[COLOR=#999999]23:15:58.257 Patchbay deactivated.[/COLOR]
[COLOR=#999999]23:15:58.284 Statistics reset.[/COLOR]
[COLOR=#cccc99]23:15:58.660 ALSA connection change.[/COLOR]
[COLOR=#999999]23:15:58.669 JACK is starting...[/COLOR]
[COLOR=#990099]23:15:58.670 /usr/local/bin/jackd -p128 -t5000 -dalsa -r48000 -p64 -n2 -S -D -Chw:CODEC,0 -Phw:0[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
jackdmp 1.9.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2012 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
creating alsa driver ... hw:0|hw:CODEC,0|64|2|48000|0|0|nomon|swmeter|-|16bit
configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
[COLOR=#66cc99]23:15:59.428 ALSA connection graph change.[/COLOR]
[COLOR=#999999]23:15:59.664 JACK was started with PID=3916.[/COLOR]
[COLOR=#ff0000]23:16:04.670 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
Cannot read socket fd = 25 err = Success
CheckRes error
JackSocketClientChannel read fail
Cannot open qjackctl client
CheckSize error size = -1 Size() = 4
CheckRead error
CheckSize error size = 0 Size() = 12
CheckRead error
[COLOR=#999999]23:16:07.533 JACK is stopping...[/COLOR]
Jack main caught signal 15

---

