---
title: "Audio Mixer(s) in ubuntu"
date: 2009-05-06
forum: Multimedia Software
---

### Post by bigheart on 2009-05-06
Hello,

i am not very familiar with Linux audio so i few questions on it.
i  have a laptop installed ubuntu 9.04.

1. in Volume control i found OSS mixer, ALSA mixer and PulseAudio mixer, why there are so many? what they are doing in the system?

2. i want to know the digital output format (44.1k, 16bit something like that) how can i check and change it?

i read some ALSA, OSS document but still can't get a clear idea.

thanks!

Joseph

---

### Post by bigheart on 2009-05-08
Hello All,

seems no one interested in this queston, anyway, i think i can answer part of the question myself after further study.

the OSS mixer should be an on a emulated device which provide backward compitabilty for some "old" programe which use OSS.

the PulseAudio mixer can act as one of the channel in ALSA mixer.

ALSA mixer wrap up add the mixers, while ALSA and PulseAudio can direct access to the device. of course OSS also but access to a emulated device.

correct me if i am wrong.

Joseph

---

