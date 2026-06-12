---
title: "My Jack is unhappy..."
date: 2007-12-03
forum: Multimedia Production
---

### Post by kupo365 on 2007-12-03
I was trying to run Ardour GTK2, and it said jack wasn't running.
So I try to manually run Jack and it doesn't seem to work.
This is what I get when I type: jack

This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *error* Access of CD device /dev/cdrom resulted in error: Input/output error


I'm running on Ubuntu 7.10 Studio 64-bit.

I tried reinstalling in synaptic and rebooting, but that didn't work.

Help please?

---

### Post by Stochastic on 2007-12-04
yeah 'jack' is the command for a little used CD ripper or something like that, 'jackd' is the command for JACK.  Try jackd and let us know how that works.  You may also want to run things through qjackctl, many people prefer this route.

---

### Post by kupo365 on 2007-12-07
Oops, Here's what I get with jackd
> 
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --silent OR -s ]
             [ --version OR -V ]
         -d backend [ ... backend args ... ]
             The backend can be `alsa', `coreaudio', `dummy',
                                `freebob', `oss' or `portaudio'.

       jackd -d backend --help
             to display options for each backend


and when I try to open ardour I get

> There are several possible reasons:

1) JACK is not running.
2) JACK is running as another user, perhaps root.
3) There is already another client called "ardour".

Please consider the possibilities, and perhaps (re)start JACK.

and I try qjackctl and ardour didn't work, then I tried pressing start and got:
> 
23:19:44.833 Patchbay deactivated.
23:19:44.868 Statistics reset.
JACK tmpdir identified as [/dev/shm]
23:19:44.941 MIDI connection graph change.
23:19:45.083 MIDI connection change.
23:22:11.358 Startup script...
23:22:11.358 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/bren/.kde/socket-brendonstudio.
23:22:12.142 Startup script terminated with exit status=256.
23:22:12.142 JACK is starting...
23:22:12.143 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
23:22:12.146 JACK was started with PID=8740 (0x2224).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
23:22:12.169 JACK was stopped successfully.
23:22:12.170 Post-shutdown script...
23:22:12.170 killall jackd
jackd: no process killed
23:22:12.403 Post-shutdown script terminated with exit status=256.
23:22:14.169 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

---

### Post by Stochastic on 2007-12-08
well the first response is a help message describing how you should use jackd, the second is ardour telling you that jackd isn't running yet, the third is qjackctl telling you that your soundcard hw0 is already in use and so it cannot use it until you close the other programs using it (may include background/hidden apps, or be an issue with configuring qjackctl to look for the proper soundcard).

---

