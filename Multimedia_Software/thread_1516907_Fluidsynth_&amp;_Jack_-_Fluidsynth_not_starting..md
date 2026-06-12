---
title: "Fluidsynth &amp; Jack - Fluidsynth not starting."
date: 2010-06-24
forum: Multimedia Software
---

### Post by Tootler on 2010-06-24
I have just upgraded to 10.04 and Fluidsynth will not start. It used to start previously but now it tries to call Jack which it did not do before and there are a load of errors with Jack and then it throws me out. Here is the terminal output I get.

```

FluidSynth version 1.1.1
Copyright (C) 2000-2009 Peter Hanappe and others.
Distributed under the LGPL license.
SoundFont(R) is a registered trademark of E-mu Systems, Inc.

lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
fluidsynth: warning: Ignoring sample *KPianoB5: can't use ROM samples
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
all 32 bit float mono audio port buffers in use!
cannot assign buffer for port
cannot deliver port registration request
all 32 bit float mono audio port buffers in use!
cannot assign buffer for port
cannot deliver port registration request
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
fluidsynth: warning: Jack sample rate mismatch, expect tuning issues (synth.sample-rate=44100, jackd=0)
./fsynth: line 2:  3435 Bus error               fluidsynth -C0 -R1 /usr/share/sounds/sf2/Unison.SF2

```

It seems in some way that the necessary resources cannot be made available, but I have no idea how to resolve this. I have had a good hunt around and cannot find anything similar to base an attempt to solve the problem on.

I used to get something similar to the "lash open socket" error in 9.04, but fluidsynth would still run.

Any help and suggestions appreciated.

Geoff

---

### Post by Tootler on 2010-07-02
I think I have sorted it.

I set fluidsynth to run without lash and to use alsa so that jack does not try to load.

The full command I use is

```
fluidsynth -C0 -R1 -l -a alsa /usr/share/sounds/sf2/Unison.SF2
```

Geoff

---

