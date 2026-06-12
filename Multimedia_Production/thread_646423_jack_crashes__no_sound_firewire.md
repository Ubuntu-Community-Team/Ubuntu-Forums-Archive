---
title: "jack crashes / no sound firewire"
date: 2007-12-21
forum: Multimedia Production
---

### Post by thomasbas on 2007-12-21
Hi

I just installed Ubuntu Studio on an AMD 2600+ with an asrock motherboard. Cant make my Edirol fa-101 firewire audio interface to work and jack control makes the computer freeze when I open setup.
Anyone got ideas?

I see on the freebob page it should be possible..

---

### Post by Stochastic on 2007-12-23
well do you have freebob installed? can you start jack from the command line with ```
jackd -R -d freebob
``` I know for my firewire device I had to go into /etc/udev/rules.d/40-permissions.rules and change the line that says something like "raw1334" group="disk" to say group="audio" to give permissions to a normal user for a firewire device.  I don't know why qjackctl would be crashing on you, that's not right.

---

### Post by thomasbas on 2007-12-23
Thanks for your reply.


This is what I get running your comand:

jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Error (bebob_light/bebob_light_avdevice.cpp)[1666] setSamplingFrequencyPlug: setSampleRatePlug: IsoStreamInput plug 0 does not support sample rate 48000
Error (bebob_light/bebob_light_avdevice.cpp)[1696] setSamplingFrequency: setSampleRate: Setting sample rate failed
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
Segmentation fault (core dumped)

I found out how to get permission to acces the firewire...

Thanks

---

### Post by thomasbas on 2007-12-23
If I change the samplerate on my Edirol soundcard I get this from your comand..

~$ jackd -R -d freebob
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
FreeBoB ERR: Error opening ALSA sequencer.
FreeBoB ERR: -----------------------------------------------------------
FreeBoB ERR: Error creating midi device!
FreeBoB ERR: FreeBob will run without MIDI support.
FreeBoB ERR: Consult the above error messages to solve the problem. 
FreeBoB ERR: -----------------------------------------------------------


libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
jack main caught signal 15
no message buffer overruns
no message buffer overruns

---

