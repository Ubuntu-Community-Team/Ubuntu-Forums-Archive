---
title: "line-in works but Jack only hears mic-in"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by raydar on 2008-02-16
I recently freshly installed Ubuntu Studio Gutsy on a machine w/ Asus mobo, Intel onboard sound (fancy surround outputs etc.), and am running the realtime kernel.

Regular system sound has always worked fine, but I haven't been able to get Jack-based sound working right yet (or MIDI, but I doubt that's directly related).  I'll fire up the Jack Control and start Jack, then run Creox, Ardour, or both, and plug a guitar in (usu. through a compressor pedal, sometimes straight in).

I can hear the clean line-in sound just fine, but no matter what I try in a mixer, Jack's connections and settings, Creox's settings, or Ardour's settings, I cannot get that line-in input processed--Creox doesn't mangle it and Ardour doesn't record it.  But if I reach over and plug the guitar plug into the mic input instead, it works.   But there's an annoyingly noise-gatey effect, like mic voice activation or something, in Creox (not an intentional effect as far as I can tell), and whatever's causing that, I really I ought to be able to use line-in too.

This seems tantalizingly close to being just an audio port configuration change of some kind, but I'm just clueless enough not to know precisely where to prod; none of my experiments have yielded the right result. Does this sound like a symptom anyone else has had?

Jack settings are as follows:
realtime
soft mode
priority = 0
frames/pd. = 1024
sample rate = 48000
periods/buffer = 3
port max = 256
timeout ms = 500
interface = default
dither = none
audio = duplex
input device = default
output device = default
input channels = 2
output channels = 2
input latency = 0
output latency = 0
(I'm showing latency of 64ms, but Jack goes xrun crazy on me and it's the best I've been able to do so far.)

Hardware wise, I'm showing, under High Definition Audio Controller,
ALC880 Analog ALSA Capture Device
ALC880 Analog ALSA Capture Device
HDA Intel ALSA Control Device
ALC880 Analog ALSA Playback Device
ALC880 Analog OSS Control Device
ALC880 Analog OSS PCM Device
ALC880 Analog OSS PCM Device

Thanks for any help!

---

### Post by raydar on 2008-02-24
SOLVED:  The Intel on-board sound hardware on my Asus motherboard was not fully supported.  Opening QAMix (ALSA mixer), I found no combo boxes to select between mic and line input on the Capture tab.  On good advice from D. Michael McIntyre on the Ubuntu Studio mailing list, I installed a few-years-old PCI sound card to see what different hardware would do, and I immediately found combo boxes in QAMix and was able to select line in and get processing of the line input signal (instead of just mic) in Creox.  After some Jack & Patchage shennanigans, I got the Creox-processed line-in sound going into Ardour for recording.

---

