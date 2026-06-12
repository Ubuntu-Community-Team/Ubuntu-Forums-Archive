---
title: "How to find out my microphone device under /dev/..."
date: 2011-01-16
forum: Multimedia Software
---

### Post by mcc1975 on 2011-01-16
Dear forum members

I have this software I want to use to extract data from a Polar heart rate monitor. Everything related to sound is working flawlessly. I just need to know the device name of the front microphone ("microphone" 2" in sound properties) so that I can insert it in the following cli command for a script: "rs200_decode -m /dev/XXX -b -o /home/user/dumb.bin"

I checked the forums but I only see references to /dev/dsp, /dev/audio, etc. I don't have any of those but rather /dev/snd/controlC0, hwC0D2, pcmC0D0c, pcmC0D0p, pcmC0D1p and pcmC0D2c.

I'm using Ubuntu 10.10 32-bit. The sound card is a generic HDA Intel audio chip. Lspci  outputs: Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller.

Any hint is greatly appreciated.

Thanks

Regards
Marcio

---

### Post by mcc1975 on 2011-01-17
No answer? Either too simple a question or too difficult :-)

---

### Post by ebedebe on 2012-10-30
Standard rs200_decode uses OSS
ubuntu uses ALSA and PulseAudio

rs200_decode version supports PulseAudio is here: 
[http://urmet.cjb.net/blog/?page_id=66](http://urmet.cjb.net/blog/?page_id=66)
For compiling the source, you’ll need to install the libpulse-dev package.

---

