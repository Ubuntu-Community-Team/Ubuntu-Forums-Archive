---
title: "Headset Mic Receiving Headphones Pulse, Alsa"
date: 2020-05-13
forum: Multimedia Software
---

### Post by isidoreagricola on 2020-05-13
Hello,

My headset is quite finicky with Ubuntu 20.04. Sometimes it works perfectly. At other times the microphone seems to pick up the headphones instead. Both "Headset mic" and "Headset speaker" are shown in audio settings, however I've found that if I tap my mic, there is little response whereas if I tap my headphones, the input level spikes (it also does when I have my computer makes an output sound). The headset has separate speakers and mic jacks that go through a combining wire to go into my laptop's one jack. Sometimes this happens, but other times it works and I have not been able to figure out why. I have a USB mic that works well and the built in mic works fine. I've never had a problem with the headset's headphones either.

I think I have both pulseaudio and alsa installed and running, so maybe that has something to do with it. Oddly, the headset mic remains as an option in sound settings even when I unplug it (whereas the headphones disappear from the outputs list).

---

### Post by CatKiller on 2020-05-13
I can't help that much with the issue itself, other than to note that headphones-being-used-as-a-microphone sounds like a wiring issue, but

> **isidoreagricola said:**
> I think I have both pulseaudio and alsa installed and running, so maybe that has something to do with it.

This is what you want. ALSA handles the interface with the hardware and PulseAudio handles the audio streams. PulseAudio replaced ALSA's (somewhat limited) software mixer, not ALSA as a whole.

---

