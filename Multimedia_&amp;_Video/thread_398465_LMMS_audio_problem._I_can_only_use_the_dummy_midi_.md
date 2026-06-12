---
title: "LMMS audio problem. I can only use the dummy midi client."
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by tee2 on 2007-04-01
Among other output I get "Couldn't create MIDI-client, neither with ALSA nor with OSS. Will use dummy-MIDI-client." Here's the full output FWIW:

```
tee@tee-laptop:~/.wine/drive_c/Program Files/World of Warcraft$ lmms
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
history size: 1
history size: 2
history size: 3
history size: 4
history size: 5
jackstart: cannot get realtime capabilities, current capabilities are:
           =ep cap_setpcap-ep
    probably running under a kernel with capabilities disabled,
    a suitable kernel would have printed something like "=eip"

back from read, ret = 1 errno == Success
jackstart: could not give capabilities: Operation not permitted
jackd 0.101.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|512|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 512 frames, buffer = 2 periods
Note: audio device hw:0 doesn't support a 32bit sample format so JACK will try a 24bit format instead
Note: audio device hw:0 doesn't support a 24bit sample format so JACK will try a 16bit format instead
nperiods = 2 for capture
nperiods = 2 for playback


**** alsa_pcm: xrun of at least 7.502 msecs

configuring for 48000Hz, period = 512 frames, buffer = 2 periods
nperiods = 2 for capture
nperiods = 2 for playback
Couldn't create MIDI-client, neither with ALSA nor with OSS. Will use dummy-MIDI-client.
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave


**** alsa_pcm: xrun of at least 625.161 msecs



**** alsa_pcm: xrun of at least 3.493 msecs



```

Because of this I can't get any sound and LMMS basically just goes through the motions of playing back what I've made. 

Any ideas are appreciated.

---

### Post by tee2 on 2007-04-02
bump

---

