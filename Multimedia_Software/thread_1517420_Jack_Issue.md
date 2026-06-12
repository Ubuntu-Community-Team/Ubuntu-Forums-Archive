---
title: "Jack Issue"
date: 2010-06-25
forum: Multimedia Software
---

### Post by MrDelish on 2010-06-25
I've been banging my head against this problem for a couple hours now.

The short version: Jack will record in Ardour and other recording applications, but not play back. I'm on the Lucid Netbook Remix.

The long version: I'm using an M-Audio MobilePre for recording and playback - I've disabled my internal sound card and pulse does very well with it. Everything was working fine and dandy up until a few days ago. Jack wouldn't start from QJackCtl, so I found that I should run the following command from the terminal first:

```
jackd -R -d alsa -r 44100
```

I simply added this as a new startup application, which worked fine at the time. Another day or two (and possibly some updates) later, and although audio works fine in any other application I try, I cannot play back in Ardour. I was able to at one point by starting it with playback only, but that defeats the purpose of using a DAW...

I've also tried editing the /etc/pulse/default.pa file to load module-jack-source and module-jack-sink modules, set up a script for QJackCtl to run after startup that does the same thing, but no joy.

Any suggestions?

---

### Post by cchhrriiss121212 on 2010-06-25
What does jack give you in the message window when starting it through qjackctl?

---

### Post by MrDelish on 2010-06-26
qjackctl with jack started by "jackd -R -d alsa -r 44100" as a startup application:

```
22:05:04.547 Patchbay activated.
22:05:04.592 Statistics reset.
22:05:05.093 Client activated.
22:05:05.307 JACK active patchbay scan...
22:05:05.317 JACK connection change.
22:05:05.525 JACK active patchbay scan...
22:05:36.551 JACK connection graph change.
22:05:36.674 JACK active patchbay scan...
22:05:44.309 JACK connection graph change.
22:05:44.507 JACK active patchbay scan...
22:05:44.573 JACK connection graph change.
22:05:44.718 JACK active patchbay scan...
22:05:44.733 JACK connection change.
22:05:44.937 JACK active patchbay scan...
22:05:50.841 JACK connection graph change.
22:05:50.964 JACK active patchbay scan...
22:05:50.972 JACK connection change.
22:05:51.177 JACK active patchbay scan...
```

All looks well, but still no output in Ardour unless I make it playback only. Here's the log when I try to start jack via qjackctl:

```
22:09:57.521 Patchbay activated.
22:09:57.539 Statistics reset.
22:09:57.654 Startup script...
22:09:57.667 artsshell -q terminate
sh: artsshell: not found
22:09:58.075 Startup script terminated with exit status=32512.
22:09:58.077 JACK is starting...
22:09:58.078 /usr/bin/jackd -v -r -t2000 -dalsa -r44100 -p256 -n4 -D -Chw:1 -Phw:1 -s -S -i2 -o2
22:09:58.090 JACK was started with PID=4804.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
new client: alsa_pcm, id = 1 type 1 @ 0x85c07b8 fd = -1
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|256|4|44100|2|2|nomon|swmeter|soft-mode|16bit
control device hw:1
configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 4 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 4 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 4 periods for playback
new buffer size 256
registered port system:capture_1, offset = 1024
registered port system:capture_2, offset = 2048
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver
cannot start driver
starting server engine shutdown
stopping driver
server thread back from poll
start poll on 3 fd's
server thread back from poll
unloading driver
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
22:09:58.451 JACK was stopped successfully.
22:09:58.454 Post-shutdown script...
22:09:58.456 killall jackd
jackd: no process found
22:09:58.883 Post-shutdown script terminated with exit status=256.
22:10:00.525 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by cchhrriiss121212 on 2010-06-26
Could you post the output of aplay -l?

Try the following setup using qjackctl:
periods/buffer:2
interface: default
all input/output options: default
leave the rest as it is

---

### Post by MrDelish on 2010-06-26
> **cchhrriiss121212 said:**
> Could you post the output of aplay -l?

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: MobilePre [MobilePre], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

> **cchhrriiss121212 said:**
> Try the following setup using qjackctl:
periods/buffer:2
interface: default
all input/output options: default
leave the rest as it is

Same result, sadly...

---

### Post by cchhrriiss121212 on 2010-06-27
So the aplay -l shows that your internal sound is still active, which means that it will be the default for running jack from that terminal command.
Back to qjackctl setup and try this:
interface: hw:1,1
on the left check the realtime option and uncheck all the others

---

### Post by RaumTrug on 2010-06-28
I've just "witnessed" a case where moving the usb-device to another usb-port, removing all other unneeded usb-devices (and also trying different ports for them, use lsusb to check if the audio-device is alone on its hub would be best) plus using a shorter, possibly high quality usb cable eleminated the "broken pipe" error messages & made jack start. seems like something is kind of borked in linux usb.

wish you good luck!

---

### Post by MrDelish on 2010-06-28
> **cchhrriiss121212 said:**
> Back to qjackctl setup and try this:
interface: hw:1,1
on the left check the realtime option and uncheck all the others

Oddly enough, the box for interface is grayed out and shows "default" even after I reenable the built-in sound card. 

[QUOTE=RaumTrug]I've just "witnessed" a case where moving the usb-device to another usb-port [...] eleminated the "broken pipe" error messages & made jack start.[/QUOTE]

After you mentioned this, I realized that I got a hub for my netbook because it feels like I'm going to break the ports off the motherboard if I'm not careful. I switched the plug and jack starts normally now, so that's a step in the right direction.

Sadly, though, the recording part isn't working now. I'll try doing some restarting and unplugging devices and see if that does the trick.

---

### Post by MrDelish on 2010-06-29
No luck so far. I don't have much more time to put into this right now, but I figure I will uninstall Ardour completely in case I messed with the settings a little too much. I'm not sure what else to try at this point.

Thanks very much for the replies so far! Hopefully I get this working soon... :KS

---

