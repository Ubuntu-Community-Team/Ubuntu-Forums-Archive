---
title: "Unable to record from &quot;what you hear&quot; - device missing?"
date: 2009-04-22
forum: Multimedia Software
---

### Post by murri on 2009-04-22
Hi all!

I want to be able to record audio from "what you hear" for entirely legal non-youtube-related purposes.
I have 8.10 Intrepid Ibex and a Sound Blaster Audigy 2 ZS soundcard.

Tried to use arecord and Audacity, with no luck:
All my recordings complete without errors, but also **no sound** (some devices give a bit of clicks and fuzzing, like static electricity).

These are the available recording devices in Audacity:
[LIST]
[*]OSS: /dev/dsp
[*]OSS: /dev/dsp1
[*]ALSA: Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback (hw:0,0)
[*]ALSA: Audigy 2 ZS [SB0350]: Mic Capture (hw:0,1)
[*]ALSA: Audigy 2 ZS [SB0350]: Multichannel Capture/PT Playback (hw:0,2)
[*]ALSA: Audigy 2 ZS [SB0350]: p16v (hw:0,4)
[*]ALSA: PnP Audio Device: USB Audio (hw:1,0)
[*]ALSA: spdif
[/LIST]

I tried every single one of these, most just gave the same silence; the OSS ones didn't work and "p16v" gave some loud noise to playback, messed up and forced me to reboot..!

I did try opening alsamixer, selecting capture, and enable it.
alsamixer says "Card: PulseAudio / Chip: PulseAudio" on the top.

I've also tried fooling around in Volume Control, jumping through devices and enabling any control that reven remotely resembles any type of recording.

In Volume Control, there are several devices not displayed in Audacity, here are all of them:
[LIST]
[*]Audigy 2 ZS [SB0350] (Alsa mixer)
[*]PnP Audio Device (Alsa mixer)
[*]SigmaTel STAC9721,23 (OSS Mixer)
[*]Playback: ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA (PulseAudio Mixer)
[*]Playback: ALSA PCM on front:1 (USB Audio) via DMA (PulseAudio Mixer)
[*]Capture: Monitor Source of ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA (PulseAudio Mixer)
[*]Capture: ALSA PCM on hw:0 (ADC Capture/Standard PCM Playback) via DMA (PulseAudio Mixer)
[*]Capture: Monitor Source of ALSA PCM on front:1 (USB Audio) via DMA (PulseAudio Mixer)
[*]Capture: ALSA PCM on front:1 (USB Audio) via DMA (PulseAudio Mixer)
[/LIST]

(I believe the PnP Audio Device is my unused motherboard built-in soundcard).

I have a feeling that the "PCM Capture" control under the "Audigy 2 ZS [SB0350] (Alsa mixer)" device sounds like what I need (I may be way off here). Still, I'm not sure how to specify that device and control for arecord, Audacity or anything else for that matter.
Here are the controls for that device in Volume Control: _[http://murray.sysrq.no/controls.png](http://murray.sysrq.no/controls.png)_

I'm (obviously) no expert in sound systems. I just want this to work - do **you** have any idea what I'm missing?

Thanks in advance :)

---

### Post by murri on 2009-04-23
Oh, another thing, here are the devices that's available under [_[color="blue"]"Sound Preferences" -> "Audio Conferencing"[/color]_]("http://murray.sysrq.no/soundpref.png"):
(I was unable to do a screenshot while the select bar was open!)

[LIST]
[*]Audigy 2 ZS [SB0350] (rev.4, serials:0x20021102) p16v (ALSA)
[*]Audigy 2 ZS [SB0350] (rev.4, serials:0x20021102) Multichannel Capture/PT Playback (hw:0,2)
[*]Audigy 2 ZS [SB0350] (rev.4, serials:0x20021102) Mic Capture (ALSA)
[*]Audigy 2 ZS [SB0350] (rev.4, serials:0x20021102) ADC Capture/Standard PCM Playback (ALSA)
[*]PnP Audio Device USB Audio (ALSA)
[*]Audigy 2 ZS [SB0350] (rev.4, serials:0x20021102) ADC Capture/Standard PCM Playback (OSS)
[*]PnP Audio Device USB Audio (OSS)
[*]Alsa - Advanced Linux Sound Architecture
[*]OSS - Open Sound System
[*]PulseAudio Sound Server
[*]Test Sound
[*]Silence
[/LIST]
I don't know if maybe the fact that this list differs slightly from the one in Audacity should tell me anything?

---

### Post by markbuntu on 2009-04-23
First, set your sound up according to this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If after that you are having trouble controlling all your devices go here

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

To record with Audacity go here

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

To record what is playing in your speakers you need to use the "Monitor....." of the device playing the sound which you can choose in the pulse volume control

---

### Post by murri on 2009-04-26
That was just what I needed - I finally made it work, and learned a lot in the process.

Thanks a bunch :)

---

