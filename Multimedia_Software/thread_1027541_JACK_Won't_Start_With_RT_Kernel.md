---
title: "JACK Won't Start With RT Kernel"
date: 2009-01-01
forum: Multimedia Software
---

### Post by kamlapati on 2009-01-01
I need some help with my first attempts to make a Linux powered recording studio.

I have installed Ubuntu Studio, including the real time kernel. When I start JACK with the RT option enabled, I get the following failure message:

10:28:21.514 Startup script...
10:28:21.515 artsshell -q terminate
10:28:22.349 Startup script terminated with exit status=256.
10:28:22.351 JACK is starting...
10:28:22.352 /usr/bin/jackd -R -p128 -t5000 -dalsa -dhw:0 -r44100 -p512 -n2 -m -S -i2 -o2
10:28:22.360 JACK was started with PID=7308.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 326649568, from thread 326649568] (1: Operation not permitted)
cannot create engine
10:28:22.476 JACK was stopped successfully.
10:28:22.477 Post-shutdown script...
10:28:22.478 killall jackd
10:28:22.567 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
jackd: no process killed


If I disable the RT option, JACK starts OK. Any help understanding this behavior would be appreciated!

Thanks.

---

### Post by ccx1138 on 2009-01-09
Have same issue. Checked user in audio group.  Set memlock and nice with studio controls.  Using rt kernel 2.6.27-3.  Pulse audio shut off.  jackd starts with rt disabled but gives error when started with rt. 

"cannot use real-time scheduling (FIFO at priority 10) [for thread 326649568, from thread 326649568] (1: Operation not permitted)
cannot create engine"

Please help!

---

### Post by bruhja on 2009-02-17
Same here. 

cannot use real-time scheduling (FIFO at priority 10) [for thread -1210784080, from thread -1210784080] (1: Operation not permitted)
cannot create engine

Installed realtime kernel booting -rt kernel in grub edited my security.conf file. hell i cant even get it to run as root.

This is really killing my Linux experience. I am running Ubuntu studio thinking "hey its the studio edition".

I am finding my switch to linux a real pain in the but. So far i have been unable to author a DVD because of the Brasero bug nor have i been able to create menus for said DVD and to top it all off i am unable to get my EMU-0404 soundcard to work @ all and cant get realtime processing on my soundcard that does work.

Nice studio edition:(

ANY!!!! help would be greatly appreciated as i really dont want to have to turn back to winblowz for anything other than games

---

