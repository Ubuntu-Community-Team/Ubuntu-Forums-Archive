---
title: "How to play stereo sound on surround speaker?"
date: 2009-05-28
forum: Multimedia Software
---

### Post by pongtawat on 2009-05-28
How could I config PulseAudio to play stereo sound on all surround speakers? I.e. front left and right sound are duplicate to rear left and right speaker.

I found a guide for ALSA here:
[http://alsa.opensrc.org/index.php/Playing_stereo_on_surround_sound_setup_(Howto](http://alsa.opensrc.org/index.php/Playing_stereo_on_surround_sound_setup_(Howto))

and a guide to config PulseAudio for surround sound here:

[http://ubuntuforums.org/showthread.php?t=795525&highlight=Playing+stereo+surround+sound+setup](http://ubuntuforums.org/showthread.php?t=795525&highlight=Playing+stereo+surround+sound+setup)

Is there any way to config just PulseAudio to do the same as in ALSA guide above?

Thank you in advance.

---

### Post by xzero1 on 2009-05-28
Install padevchooser.  Select Sound and video->Pulse audio volume control->Configuration and select the proper profile.

---

### Post by pongtawat on 2009-05-28
I have already installed padevchooser.

In PA Volume Control, I can't find anything about duplicating stream to all output.

I also look at many settings in PA Dev Chooser, but I don't know how to config it to duplicate front left and right to rear left and right. :cry:

---

### Post by xzero1 on 2009-05-29
But you already have surround in alsa right? Post the output of "aplay -L".

---

