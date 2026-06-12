---
title: "Rosegarden no audio"
date: 2010-05-24
forum: Multimedia Software
---

### Post by the_waka on 2010-05-24
I recently installed rosegarden, but was disappointed to find that it isn't correctly directing the midi output to ALSA. I went to the detail section under the "midi ok, no audio" message in edit->preferences of rosegarden, and got the output. It appears to not be able to find a usable device, but I'm not sure... here it is:


```
Rosegarden 10.02 - AlsaDriver [ALSA library version 1.0.22, module version 1.0.21, kernel version 2.6.32-22-generic]

JackDriver::initialiseAudio - JACK server not running

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]

Using low-resolution system timer, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

AlsaDriver::setPlausibleConnection: connection like "" requested for device 0
AlsaDriver::setPlausibleConnection: nothing suitable available
AlsaDriver::setPlausibleConnection: connection like "" requested for device 1
AlsaDriver::setPlausibleConnection: nothing suitable available

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99
```]

---

### Post by cchhrriiss121212 on 2010-05-25
You need to install and run jackd (a low latency sound server) which you can find in the repos. You will also need to use Rosegarden with some kind of synth in order to hear things. Zynaddsubfx and phasex are good choices.

---

### Post by the_waka on 2010-05-25
Ah! Thank you very much!:ks

---

