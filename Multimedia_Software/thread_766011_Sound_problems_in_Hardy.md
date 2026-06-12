---
title: "Sound problems in Hardy"
date: 2008-04-24
forum: Multimedia Software
---

### Post by diwakergupta on 2008-04-24
I had been using PulseAudio in Gutsy since several months and everything worked peachy. I had Alsa going through Pulse as well. Since upgrading to Hardy, things are breaking down.

- ALSA works just fine on its own
- When I start pulseaudio using the default config, I get:
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
(note that the server doesn't die though)
- After starting pulseaudio and setting Alsa go use it (asoundconf set-pulseaudio), I run speaker-test. It crashes with this:
*** PULSEAUDIO: Unable to create stream.
Unable to set hw params for playback: Input/output error
Setting of hwparams failed: Input/output error
speaker-test: pcm_pulse.c:115: pulse_stop: Assertion `pcm->stream' failed.
Aborted

I have searched the forums as well as Google, but nothing turned up. Any ideas?

Thanks!

---

