---
title: "[SOLVED] Presonus Firepod issues"
date: 2008-02-19
forum: Multimedia Production
---

### Post by Stochastic on 2008-02-19
So I've had my Firepod working for a while now, but it's gone and stopped connecting through Jack.  I really can't afford to go buy a new soundcard so I'm forced to troubleshoot.  Can anyone offer any suggestions?  Here's what I get when I start jack from either qjackctl or straight from command line:
```
loading driver ..
Freebob using Firewire port 0, node -1
new client: freebob_pcm, id = 1 type 1 @ 0x806f768 fd = -1
new buffer size 512
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.3
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 44100
LibFreeBoB MSG:   Period Size              : 512
LibFreeBoB MSG:   Nb Buffers               : 3
LibFreeBoB MSG:   Directions               : 0
send oops
send oops
send oops
send oops
send oops
send oops
send oops
send oops
send oops
send oops
send oops
no response
[31mError (bebob_light/bebob_light_avdevice.cpp)[1104] enumerateSubUnits: Subunit info command failed
[0m[31mError (bebob_light/bebob_light_avdevice.cpp)[96] discover: Could not enumarate sub units
Root node has no children!
Root node has no children!
FreeBoB ERR: FREEBOB: Error creating virtual device
[0mcannot load driver module freebob
starting server engine shutdown
freeing shared port segments
17:14:21.388 JACK was stopped successfully.
17:14:21.388 Post-shutdown script...
17:14:21.388 killall jackd
jackd: no process killed
17:14:21.605 Post-shutdown script terminated with exit status=256.
17:14:23.063 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]
```


EDIT**** I plugged the firewire cable into the second port of the Firepod and now I'm off to the races.

---

