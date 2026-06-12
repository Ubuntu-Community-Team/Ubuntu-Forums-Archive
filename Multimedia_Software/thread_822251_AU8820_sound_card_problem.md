---
title: "AU8820 sound card problem"
date: 2008-06-08
forum: Multimedia Software
---

### Post by KB1LQC on 2008-06-08
Ok,

So I followed the sticky guide as best as possible and still do not have a sound output.  I am using:

```
card 0: au8820 [Aureal Vortex au8820], device 0: AU88x0 ADB [adb]
```

and when I try "play" with sox I get the following error:

```
bryce@kb1lqc:~$ play sine.wav
ALSA snd_pcm_hw_params_set_buffer_time_near error: Invalid argument
play ao: Could not open default device: error 5
play soxio: Failed writing `default':
``` 

I am using Ubuntu 8.04 Server Edition (non-GUI).  Any suggestions to get my sound working?


[RIGHT]

Sincerely,

KB1LQC[/RIGHT]

---

