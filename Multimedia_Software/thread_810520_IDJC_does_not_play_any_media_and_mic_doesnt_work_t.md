---
title: "IDJC does not play any media and mic doesnt work too"
date: 2008-05-28
forum: Multimedia Software
---

### Post by Cobra_Fast on 2008-05-28
Well today i purchased a Soundcard (its from "Trust") cause my onboard sound-chip is quiet bad and i got sick of it and my microphone did not work poperly with it.

Well then i tried to start playing music with IDJC (all packages installen) but when i press play nothing happens. the music counter does not even start counting. 

i can add tracks into the playlist, but noch play them.

when i hit the stop button then IDJC probably crashes for 30 secs (stuck, hung up, whatever).

```

$ idjc
### ln_text.py: warning, attribute autopause does not appear in the canonical list en_GB
Internet DJ Console Version 0.7.5
Copyright 2005-2008 Stephen Fairchild
Released under the GNU General Public License V3.0

Language translation: de_DE
JACK tmpdir identified as [/dev/shm]
JACK compiled with System V SHM support.
loading driver ..
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
unknown destination port in attempted connection [idjc-sc:lt_in]
unknown destination port in attempted connection [idjc-sc:rt_in]
shout_initialiser: shout_init called
JACK tmpdir identified as [/dev/shm]
started 6 encoders, 6 streamers, 2 recorders
threads initialised
jack sample rate is 48000
Restoring previous session
Toggle ON recieved for signal: Play
song title: TipTop - TipTop

updated metadata successfully
Seek time is 0 seconds
Configuring resampler
player context id is 1

Player has started
Toggle OFF recieved for signal: Play
player shutdown code was called
watchdog timer frozen for one of the media players -- possible bad media file
shutting down the mixer in one second
Mixer reports a segmentation fault
*** Mixer has likely crashed ***
JACK tmpdir identified as [/dev/shm]
Sample rate is 48000
attempting to sync
got sync
threads_shutdown commencing
Mixer module has closed
threads_shutdown finished

```

Thanks for help!!

---

### Post by Cobra_Fast on 2008-05-28
Well i fixed playing by selecting OSS for jack ... but the microphone has still problems.

---

### Post by Cobra_Fast on 2008-05-28
well thanks to all who were thinking about this :p

i figured out myself by playing with the OSS-Mixer options.

kinda stupid, i could have noticed earlier :>

---

