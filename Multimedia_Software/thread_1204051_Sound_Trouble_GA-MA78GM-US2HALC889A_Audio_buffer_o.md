---
title: "Sound Trouble GA-MA78GM-US2H/ALC889A Audio buffer overflow - lost!"
date: 2009-07-04
forum: Multimedia Software
---

### Post by mgarl10024 on 2009-07-04
Hi,

I'm running Mythtv 0.21.0+fixes19961-0ubuntu8 on Ubuntu 9.04, however I seem to have persistent issues with the audio, and I'd really appreciate some direction as I really don't know what to try next. I suspect that this is someone wrong with my machine setup and not a mythtv issue - but I hope someone might know the answer or the best setup for mythtv.
Audio hardware wise, I have a Gigabyte GA-MA78GM-US2H motherboard that comes with onboard ALC889A audio, and I'm just using standard analogue speakers.

The audio and system will work fine for a couple of days, then randomly I'll get "NVP::AddAudioData():ps: Audio buffer overflow, audio data lost!", during which time the machine will completely lock for 2-3 minutes.
When I say 'completely lock' - no processes run. Backend recording skips, and the machine wont respond over the network.
Afterwards, everything continues as if nothing had happened.

Removing PulseAudio (default with Ubuntu) helped.
Changing from Alsa to /dev/dsp and /dev/mixer in the mythtv setup options also helped.
Enabling 'Aggressive Sound Card Buffering' in the mythtv options also helped.

If honest, I'm a little lost with sound in Linux and especially what's best for my hardware and mythtv.
Can anyone please point me in the right direction? Hours of googling have just confused me more!

Thanks in advance,

MG

---

### Post by mgarl10024 on 2009-07-04
Hi all,

Please see the attachment I have from running the ALSA diagnostic script 
- does this help anyone?

Thanks in advance,

MG

---

