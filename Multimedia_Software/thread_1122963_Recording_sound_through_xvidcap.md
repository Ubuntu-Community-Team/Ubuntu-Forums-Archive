---
title: "Recording sound through xvidcap"
date: 2009-04-11
forum: Multimedia Software
---

### Post by jnbr on 2009-04-11
OK everytime I try to record the sound through xvidcap I get the sound from the microphone and not from the source I'm playing, which works but badly.

Now I had thought it was an oddity with xvidcap alone and that audacity was working but now I can get neither to work (or rather both use the microphone). I use pulseaudio to try to redirect the sound streams to dev/dsp but at that point I get confused about what I am doing.

As far as I can see the problem has something to do with managing the mix of sound sources but how do I control these, what devices should I be setting where. The pulse audio volume control seems to indicate that the output from the falsh video I am playing is being redirected to the 'monitor source of ALSA PCM' and xvidcap is set to use /dev/dsp as it's source. I thought padsp was meant to then redirect the current output to the dev/dsp device which many be what it's meant to be doing but doesn't seem to be what I'm getting.

Is there a trick to launching padsp (some parameter I'm missing perhaps?) or a numpty's guide to understanding linux audio somewhere?

---

