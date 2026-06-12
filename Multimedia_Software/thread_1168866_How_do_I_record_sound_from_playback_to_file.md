---
title: "How do I record sound from playback to file?"
date: 2009-05-24
forum: Multimedia Software
---

### Post by ALIENDUDE5300 on 2009-05-24
This might seem like an odd question, but I'm trying to figure out how to record the sound that plays through the speakers to a file. So far, I have only been able to record what's played through my microphone using the following command:
```
dd if=/dev/dsp of=~/testfile.wav bs=4
```
And I have been able to play that sound back using:
```
dd if=~/testfile.wav of=/dev/dsp
```
This works perfectly for recording high quality microphone audio. However, in my case, I don't want to record what sound is recorded with the microphone. Instead, I want to record what sound is coming out of the speakers. For example, if I were to start a call in Skype, play a CD, or watch a video, I would want to have the sounds that I hear recorded to a .wav file. Does anyone know how to do this?

---

### Post by ajgreeny on 2009-05-24
You can certainly do it with audacity, and perhaps also sound recorder, though I do not use that.  You may need to configure your alsa-mixer channels in the preferences for that by opening Volume control, choosing Preferences and setting the channels you want to show.  You will need Capture and Mix, but can also enable things like Line in, Mic, CD, and even Mic boost (+20db).  Play around a bit and see what can be done.

I do not know how you can, or even if you can do this with a terminal command, but I would be very surprised if it is not possible.

---

