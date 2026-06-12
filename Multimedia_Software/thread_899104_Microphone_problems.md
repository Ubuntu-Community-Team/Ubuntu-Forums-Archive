---
title: "Microphone problems"
date: 2008-08-24
forum: Multimedia Software
---

### Post by xaenyx on 2008-08-24
Sound in linux.. is my Achilles heal.

Anyway, I plugged in my microphone, and if I blow or talk into it, I hear the sound coming out of the speakers--however, both trying to record a video on youtube or using the "sound recorder" program, I don't hear anything when I play it back.  Can someone help me out?

Here's the output of amixer:

```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 6 [86%] [on]
Simple mixer control 'PCM',0
  Capabilities: volume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 31 [100%] [12.00dB] Playback [on] Capture [on]
  Front Right: 31 [100%] [12.00dB] Playback [on] Capture [on]
Simple mixer control 'PCM',1
  Capabilities: volume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 25 [81%] [0.00dB] Playback [on] Capture [on]
  Front Right: 25 [81%] [0.00dB] Playback [on] Capture [on]
Simple mixer control 'Line',0
  Capabilities: volume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 0 [0%] [-50.00dB] Playback [off] Capture [off]
  Front Right: 0 [0%] [-50.00dB] Playback [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: volume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 25 [81%] [0.00dB] Playback [on] Capture [off]
  Front Right: 25 [81%] [0.00dB] Playback [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: volume volume-joined pswitch pswitch-joined cswitch
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Mono: 31 [100%] [12.00dB] Playback [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+30dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Bypass',0
  Capabilities: cswitch
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Aux',0
  Capabilities: volume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Front Left: 0 [0%] [-50.00dB] Playback [off] Capture [off]
  Front Right: 0 [0%] [-50.00dB] Playback [off] Capture [off]
Simple mixer control 'Mono',0
  Capabilities: volume volume-joined pswitch pswitch-joined cswitch
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Mono: 0 [0%] [-50.00dB] Playback [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mono1 Bypass',0
  Capabilities: cswitch
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mono2 Bypass',0
  Capabilities: cswitch
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mono',1
  Capabilities: volume volume-joined pswitch pswitch-joined cswitch
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: 0 - 31
  Mono: 0 [0%] [-50.00dB] Playback [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'AD Input Select',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

---

### Post by xaenyx on 2008-08-24
bump

---

### Post by eggdeng on 2008-08-24
First, to record from utube, there is a neat little app called utube ripper.
Download & How-to at
[http://maketecheasier.com/ubuntu-how-to-extract-audio-from-youtube-video/2008/06/30]("http://maketecheasier.com/ubuntu-how-to-extract-audio-from-youtube-video/2008/06/30")
For the rest, let's assume for the moment your drivers are working OK & step through configuring the Sound Recorder application.

Start with Applications -> Sound & Video -> Sound Recorder
The Sound Recorder interface shows two options buttons. 
For **Record from Input** choose Capture
For **Record as** for the moment, choose Voice, Lossless (Wav Audio)

Now go to the File menu and click Volume Control
On the Volume Control interface, you want to see 3 tabs. (If you are missing any tabs or options, go to Edit -> Preferences. You will see a list of devices with checkboxes for you to tick which will make the relevant tabs / items appear.)
**Playback**	with sliders for Master, PCM, Front, Line-In, Microphone & Internal Mic
This is not relevant for recording.
**Recording**		with at least one (usually three) Capture option(s)
If you have chosen Capture as your Record from Input option, make sure the capture slider is set to max.
**Options** with at least one (usually three) Input source(s)
If you are recording from a microphone, set mic as your input source (If you have more than one Input source options buttons on this tab, you might as well set it on all of them). 

Try to record some sound through the microphone. If you get nothing, go back & click the File Menu (still on the Volume Control dialogue box). Here you will be able to select different devices /drivers to do some trial and error with.

---

### Post by Stochastic on 2008-08-24
My first reaction would be to turn on all your mixer elements listed as 'capture' (I see many are turned off).  My second reaction would be to try recording in Audacity.  My third reaction would be to open System->Sounds and select the soundcard as the capture device.

---

