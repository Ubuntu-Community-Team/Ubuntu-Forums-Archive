---
title: "Real-time audio equalizer problems whit alsa"
date: 2008-11-26
forum: Multimedia Software
---

### Post by Nollapiste on 2008-11-26
I need to get VoIP program Mumble to work with extraordinary  setup. I have a bad soundcard(I remember that it was quite bad card in windows times too). When I record from microphone, speak is guit normal, but in background you can hear high-frequency noise. Well, i installed alsaequal from sourcecode, and eliminated the most highest frequency(10.16k) and I can't hear noise anymore. In Skype I can choose "equal" from input devices list, and its working great! But in Mumble, it doesn't work. Mumble's alsa devices list doesn't include "equal" at all. I think that Mumble's alsa device list has been pre-written so program doesn't recognize new inputs at all.

Is there any trick to wrap "equal" output to "plughw:0,0" output or are there any way to edit mumble's alsa devices list?

Sorry about my bad English, my mother language is not English because I am from Finland. :)

---

### Post by psyke83 on 2008-11-26
> **Nollapiste said:**
> I need to get VoIP program Mumble to work with extraordinary  setup. I have a bad soundcard(I remember that it was quite bad card in windows times too). When I record from microphone, speak is guit normal, but in background you can hear high-frequency noise. Well, i installed alsaequal from sourcecode, and eliminated the most highest frequency(10.16k) and I can't hear noise anymore. In Skype I can choose "equal" from input devices list, and its working great! But in Mumble, it doesn't work. Mumble's alsa devices list doesn't include "equal" at all. I think that Mumble's alsa device list has been pre-written so program doesn't recognize new inputs at all.

Is there any trick to wrap "equal" output to "plughw:0,0" output or are there any way to edit mumble's alsa devices list?

Sorry about my bad English, my mother language is not English because I am from Finland. :)

If you're using PulseAudio, you can get an idea how to get system-wide equalized audio from Appendix D of [this]("http://ubuntuforums.org/showthread.php?t=789578") guide (though it uses a statically configured ladspa plugin). All programs that are PulseAudio-compatible will have equalized output.

If you don't care about PulseAudio at all, then you should look [here]("http://wiki.archlinux.org/index.php/ALSA#System-Wide_Equalizer") - pay attention to the "pcm.!default" definition, as you'll need to define something similar that applies to alsaequal.

---

### Post by Nollapiste on 2008-11-28
Thank you! I changed appendix D becouse I wanted to equalize input, not output. So I simply changed this:
```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=equalized
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
```
To this:
```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
load-module module-alsa-source device=equalized
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
```

That was most simplest thing I ever done whit sound systems so thank you again, everything works now.

---

