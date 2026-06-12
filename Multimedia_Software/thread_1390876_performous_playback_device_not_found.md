---
title: "performous: playback device not found ???"
date: 2010-01-26
forum: Multimedia Software
---

### Post by /\/\@/\/ |_| on 2010-01-26
performous is not able to autodetect any playback device...
following is the output when i run it from terminal
```


ALSA capture devices:
  alsa:hw:SB,0   HDA ATI SB (ALC883 Analog)
  alsa:hw:SB,2   HDA ATI SB (ALC883 Analog)
ALSA playback devices:
  alsa:hw:SB,0   HDA ATI SB (ALC883 Analog)
  alsa:hw:SB,1   HDA ATI SB (ALC883 Digital)

Parsing /usr/share/games/performous/config/performous.xml
Skipping /etc/xdg/performous/performous.xml (not found)
Skipping /home/manish/.config/performous.xml (not found)
>>> Trying recording device alsa:hw:default
ALSA lib pcm_hw.c:1435:(_snd_pcm_hw_open) Invalid value for card
Capture device mics=channels=2@alsa:hw:default failed and will be ignored:
  alsa::pcm::pcm: snd_pcm_open failed: No such device
>>> Trying recording device alsa
-!- alsa::hw_config::set: snd_pcm_hw_params_set_access failed: Invalid argument
>>> Trying recording device jack
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
cannot connect ports owned by inactive clients; "libda_jack_record" is not active
cannot connect ports owned by inactive clients; "libda_jack_record" is not active
    Device:       jack:libda_jack_record
    Channels:     2
    Rate:         44100 Hz
    Buffer size:  1024 frames
>>> Trying playback device alsa:hw:0
Playback device pdev=alsa:hw:0 failed and will be ignored:
  alsa::pcm::pcm: snd_pcm_open failed: Device or resource busy
No playback devices could be used. Please use --pdev to define one.
>>> Not scanning: /home/manish/.ultrastar/songs/. (no such directory)
>>> Not scanning: /usr/local/share/games/ultrastar/songs/. (no such directory)
>>> Scanning /usr/share/games/ultrastar/songs/.

```

---

