---
title: "Audigy SE refuses to work"
date: 2009-05-20
forum: Multimedia Software
---

### Post by AzizLight on 2009-05-20
Hi everybody,
Please don't run away, I'm using #!CrunchBang Linux (which is a modified minimalist ubuntu install). I've been trying to get sound to work for the past two days.
I have a installed pulseaudio but have no clue how to use it. I found [that thread]("http://ubuntuforums.org/showthread.php?t=997506") in the forums but it's useless for me since I don't use gnome..
The volume control doesn't detect pulseaudio, it just detects HDA Inter (Alsa Mixer), CA0106 (Alsa Mixer) and Realtek ALC883 (OSS Mixer). For all the devices, I selecect all the tracks and set the volume to the maximum (and insured that it is not muted).
If I type lspci in a terminal I get those two lines referring to audio devices:

```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
05:01.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

From here I don't really know what to do...
Can somebody help me please?

---

