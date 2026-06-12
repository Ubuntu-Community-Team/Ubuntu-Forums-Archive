---
title: "GStreamer Volume Control"
date: 2008-06-08
forum: Multimedia Software
---

### Post by mastermindg on 2008-06-08
I accidentally muted my sound today while configuring my remote (lircrc). The issue was that I had muted PulseAudio rather than my sound card. The Gnome Volume Applet showed all outputs as ok, volume full, no mute.

Luckily, I installed the PulseAudio Tools and went into the volume controls there. It showed that it was in fact muted. I un-muted it and now have sound.

To get a PulseAudio playback entry in Gnome Volume Control, open gstreamer-properties and select Pulseaudio Sound Server as your default output. 

I'm not sure how PulseAudio got setup as my default output, though this is preferable in hindsight, this leads to a nice little extra, I now have the option of muting a single device or ALL sound:

To mute all audio with PulseAudio as your default:
**amixer set Master 0% unmute**

To mute your first device:
**amixer -c 0 Master 0% unmute**

To mute your second device:
**amixer -c 1 Master 0% unmute** 

.... and so on

Just an idea :)

---

