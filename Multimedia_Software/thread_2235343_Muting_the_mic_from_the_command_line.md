---
title: "Muting the mic from the command line"
date: 2014-07-20
forum: Multimedia Software
---

### Post by cpdondo on 2014-07-20
Is there any way to mute the mic from the CLI?  The only way seems to be to move the sliders to 0% gain.  The mute button in alsamixer doesn't do anything (at least the mic still seems functional in pavucontrol).  amixer says it's muted but pavucontrol says different.

pacmd lets me toggle the mute, but again, pavucontrol still shows the mic picking up sound.

How do I turn off the mic?

---

### Post by tgalati4 on 2014-07-21
It's a little tricky, but use *pacucontrol* and mute and unmute the microphone then detect changes in amixer:

> tgalati4@Mint14-Extensa ~ $ amixer | grep Capture
  Capture channels: Front Left - Front Right
Simple mixer control 'Capture',0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
[B]  Front Left: Capture 12 [39%] [1.50dB] [off]
  Front Right: Capture 12 [39%] [1.50dB] [off][/B]
Simple mixer control 'Capture',1
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [off]
  Front Right: Capture 0 [0%] [-16.50dB] [off]
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
  Capture channels: Front Left - Front Right
tgalati4@Mint14-Extensa ~ $ amixer | grep Capture
  Capture channels: Front Left - Front Right
Simple mixer control 'Capture',0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
[B]  Front Left: Capture 12 [39%] [1.50dB] [on]
  Front Right: Capture 12 [39%] [1.50dB] [on][/B]
Simple mixer control 'Capture',1
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [off]
  Front Right: Capture 0 [0%] [-16.50dB] [off]
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
  Capture channels: Front Left - Front Right


I have Intel HDA motherboard sound card.  When I unmute the microphone, the channel "Capture" goes "off" to "on".

But, it looks like you are correct:  Pulseaudio seems to have priority over mute.  Regardless of the amixer level that I set, mute does not change it.

> tgalati4@Mint14-Extensa ~ $ amixer sset 'Capture' 15 off
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 15 [48%] [6.00dB] [on]
  Front Right: Capture 15 [48%] [6.00dB] [on]
tgalati4@Mint14-Extensa ~ $ amixer sset 'Capture' 16 mute
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 16 [52%] [7.50dB] [on]
  Front Right: Capture 16 [52%] [7.50dB] [on]
tgalati4@Mint14-Extensa ~ $ amixer sset 'Capture' 18 unmute
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 18 [58%] [10.50dB] [on]
  Front Right: Capture 18 [58%] [10.50dB] [on]
tgalati4@Mint14-Extensa ~ $ amixer sset 'Capture' 7 off
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 7 [23%] [-6.00dB] [on]
  Front Right: Capture 7 [23%] [-6.00dB] [on]
tgalati4@Mint14-Extensa ~ $ amixer sset 'Capture' 7 on
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 7 [23%] [-6.00dB] [off]
  Front Right: Capture 7 [23%] [-6.00dB] [off]
tgalati4@Mint14-Extensa ~ $ amixer sset 'Capture' 7 unmute
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 7 [23%] [-6.00dB] [off]
  Front Right: Capture 7 [23%] [-6.00dB] [off]


You can set the level to "0" but you can't mute or unmute it with *amixer*.  It appears that *pavucontrol* has total control over the muting function.  This is either a bug or a feature.  I would file a bug (and one probably already exists) against *pulseaudio* for this behavior.

I don't know if there is a commandline way to send a mute signal directly to *pulseaudio*.

---

