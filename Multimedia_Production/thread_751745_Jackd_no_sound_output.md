---
title: "Jackd no sound output"
date: 2008-04-10
forum: Multimedia Production
---

### Post by whitewizardcoder on 2008-04-10
Hi,

I am trying to get jack to work as I use it for running ardour and hydrogen, however when I run it I get no audio output.  There doesn't appear to be any errors when starting jackd, although when I use qtjackctl to start it, the dsp load displays a constant 0%.

My audio card is an Intel HDA audio:

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

and this is the output from jackd when trying to start it with the alsa backend:

> getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
new client: alsa_pcm, id = 1 type 1 @ 0x8068898 fd = -1
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
new buffer size 1024
registered port system:capture_1, offset = 4096
registered port system:capture_2, offset = 8192
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
7357 waiting for signals

I am able to run jackd on my other computer with what I assume is the same sound card, and I was able to run it on this computer a few months ago on gutsy (although it stopped working on gutsy too).  Any help is greatly appreciated!

Thanks,
WhiteWizardCoder

---

