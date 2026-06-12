---
title: "Jack error message"
date: 2011-01-26
forum: Multimedia Software
---

### Post by matjaz_pirnovar on 2011-01-26
HI,

Can't get jack to work.
Installed from synaptic (running ubuntu 10.10, 64bit).

WHen ckicking "start" in qjackctl (jack control) I keep getting this message:

19:27:58.615 Patchbay deactivated.
19:27:58.616 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
19:27:58.722 ALSA connection graph change.
19:27:58.915 ALSA connection change.
19:28:01.244 Startup script...
19:28:01.245 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
19:28:01.647 Startup script terminated with exit status=32512.
19:28:01.647 JACK is starting...
19:28:01.647 /usr/bin/jackd -dalsa -d/dev/dsp -r44100 -p1024 -n2 -Xseq
19:28:01.650 JACK was started with PID=4831.
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
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
audio_reservation_init
Acquire audio card Audio-1
creating alsa driver ... /dev/dsp|/dev/dsp|1024|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
19:28:01.748 JACK was stopped with exit status=255.
19:28:01.749 Post-shutdown script...
19:28:01.749 killall jackd
jackd: no process found
19:28:02.163 Post-shutdown script terminated with exit status=256.
19:28:03.723 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
19:28:10.369 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started


It's been going on for a while.
WHat should I do or check?

Thanks!
M

---

### Post by cchhrriiss121212 on 2011-01-27
Open the setup window and select your card from the drop down list under interface. The one you have specified does not exist.

---

### Post by matjaz_pirnovar on 2011-01-27
Thanks. This did the trick.

Sound card was unselected, so as channels.

Cheers.

---

