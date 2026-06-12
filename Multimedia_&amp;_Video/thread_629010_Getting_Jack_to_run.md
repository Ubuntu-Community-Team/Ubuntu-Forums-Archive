---
title: "Getting Jack to run"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by bakaeigo on 2007-12-01
I'm having trouble running JACK, and none of the other threads seem to be helping.  I've tried qtjack as well as running it from the command prompt.

If this helps, here's the section of the text that's related to Jack when I try to run ardour:

> JACK tmpdir identified as [/dev/shm]
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the capture device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
ardour: [ERROR]: Unable to connect to JACK server
ardour: [ERROR]: Could not connect to JACK server as  "ardour"
ardour: [ERROR]: Could not connect to JACK server as  "ardour"

Any suggestions?

Thanks in advance!

---

### Post by Unterseeboot_234 on 2007-12-02
Try this link:

**[http://lau.linuxaudio.org/jack/]("http://lau.linuxaudio.org/jack/")**

jack needs a "server" to connect audio streams. That is, I found I had to have alsa-player or timidity running first, then jack, then ardour or rosegarden. I blew up my Dapper forcing a lib that Rosegarden requires... is the last advice I can give you. (I use Gusty now for artwork, video, scripting and mean to get back, to serious audio one day).

---

