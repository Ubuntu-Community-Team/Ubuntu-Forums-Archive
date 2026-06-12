---
title: "Propellerhead Reason wont read SoundRecorder wave files"
date: 2010-09-04
forum: Multimedia Software
---

### Post by Lutshow on 2010-09-04
Hi everyone.
I'm facing a particular problem here.

What I want to do : play a Wave file under Propellerhead Reason using wine.
Reason, although it has a few graphical glitches, works fine under wine.
So what I do is loading a wave file into a sampler.
It works fine with all the wave files I recorded back in the days on WinXP...

However, when I record a wave file using Ubuntu 10.4 Sound Recorder, Reason keeps telling me "Unsupported format", and won't load the file. Besides, the file seems OK to me, it plays normally under VLC and totem.

I checked two files with audacity, one from sound recorder, and one from XP. The details are the same : Mono 22050Hz, 32-bit float.

I can't see any format difference. 


Any idea someone ?

---

### Post by Lutshow on 2010-09-04
Well, I found a workaround.
I open my wave file in audacity, and then i export it, choosing the "WAV (Microsoft) signed 16 bit PCM"...

I still can't tell the difference between the files, but well, Reason accepts it...

---

