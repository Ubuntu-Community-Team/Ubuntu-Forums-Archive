---
title: "Sound works in some programs"
date: 2008-05-31
forum: Multimedia Software
---

### Post by azizzle on 2008-05-31
This morning, I had sound in all of my programs. I had one issue, though, not being able to watch videos online while rhythmbox was playing. I searched around, and found [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739).
So after I followed those instructions, my sound went out in rhythmbox, and in system>preferencces>sound when I press the 'Test' button, there is no sound, but in all my other apps sound works just fine. 

The weird thing, though, is when I'm running these apps, with PulseAudio volume meter open, it shows that both rythmbox and the sound test are producing sound. PA volume meter shows no reading when my other apps are playing, when sound is actually coming out of my speakers. So something is backwards somewhere, any body have this happen?

btw: This is what I get when I start pulseaudio from the terminal:
$ pulseaudio
W: pid.c: Stale PID file, overwriting.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
W: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
W: alsa-util.c: Cannot find fallback mixer control "PCM".
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1

---

