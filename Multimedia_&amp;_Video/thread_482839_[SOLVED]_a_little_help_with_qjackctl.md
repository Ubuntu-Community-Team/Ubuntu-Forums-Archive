---
title: "[SOLVED] a little help with qjackctl"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by unebaguettesvp on 2007-06-24
so i had qjackctl working fine with 0.2.21 (current package under ubuntu feisty). then i compiled successfully 0.2.22, the latest version, and now i'm getting an error:

Could not connect to JACK server as client. Please check the messages window for more info.

```

02:03:45.181 Patchbay deactivated.
02:03:45.332 Statistics reset.
02:03:45.507 MIDI connection graph change.
02:03:45.549 MIDI connection change.
02:03:47.397 Startup script...
02:03:47.397 artsshell -q terminate
02:03:47.695 Startup script terminated with exit status=256.
02:03:47.695 JACK is starting...
02:03:47.696 jackd -v -R -P1 -dalsa -dhw:2 -r48000 -p1024 -n2
02:03:47.700 JACK was started with PID=7334 (0x1ca6).
getting driver descriptor from /usr/local/lib64/jack/jack_alsa.so
getting driver descriptor from /usr/local/lib64/jack/jack_dummy.so
getting driver descriptor from /usr/local/lib64/jack/jack_oss.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:2|hw:2|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:2
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
7334 waiting for signals
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x612700 fd = -1
new buffer size 1024
registered port alsa_pcm:capture_1, offset = 4096
registered port alsa_pcm:capture_2, offset = 8192
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
load = 0.0234 max usecs: 10.000, spare = 21323.000
02:03:49.812 Could not connect to JACK server as client. Please check the messages window for more info.
load = 0.0445 max usecs: 14.000, spare = 21319.000
load = 0.0504 max usecs: 12.000, spare = 21321.000
load = 0.0393 max usecs: 6.000, spare = 21327.000
load = 0.0524 max usecs: 14.000, spare = 21319.000
load = 0.0567 max usecs: 13.000, spare = 21320.000
02:03:54.547 JACK is stopping...
jack main caught signal 15
starting server engine shutdown
stopping driver
unloading driver
freeing shared port segments
stopping server thread
stopping watchdog thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 14.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
02:03:54.880 JACK was stopped successfully.
02:03:54.881 Post-shutdown script...
02:03:54.882 killall jackd
jackd: no process killed
02:03:55.115 Post-shutdown script terminated with exit status=256.

```

i'm very new to jack. so, am i forgetting to do something? what would cause a "Could not connect to JACK server as client" error?

---

### Post by unebaguettesvp on 2007-06-24
strange. but when i type this in a terminal:

jackd -v -R -P1 -dalsa -dhw:2 -r48000 -p1024 -n2

i get no errors. no "Could not connect to JACK server as client. Please check the messages window for more info." errors.

however, when i run qjackctl and use those values listed above, everything looks fine. it's in verbose mode, so, i get a bunch of:

load = 0.0625 max usecs: 13.000, spare = 21320.000
load = 0.0617 max usecs: 13.000, spare = 21320.000
load = 0.0590 max usecs: 12.000, spare = 21321.000
load = 0.0576 max usecs: 12.000, spare = 21321.000
load = 0.0640 max usecs: 15.000, spare = 21318.000
......

but every so often i get an error box that gives me that could not connect to JACK server as client.

either way, i still cannot get fluidsynth (qsynth) to connect to JACK.

i don't get it! this was working an hour or two ago! i even deleted the qjackctl configuration files in my home directory and started with the defaults all over again and it still doesn't work!

please help! thanks!

---

### Post by unebaguettesvp on 2007-06-24
sorry for the bump. any ideas?

---

### Post by unebaguettesvp on 2007-06-24
so, i know now that jackd never actually starts. in qjackctl, it always says starting and not started. this worked before but i don't know what happened. any ideas?

---

### Post by unebaguettesvp on 2007-06-24
*******. finally. fixed. it.

so, i initially installed jackd from synaptic. that was version 102. then, i tried compiling 103 and was successful. that was the time when jackd stopped working.

so, to fix it... first, i uninstalled 102 from synaptic. then, i did a sudo make uninstall for version 103. then, i reinstalled version 102 from synaptic.

that's it. hope this helps someone.

---

