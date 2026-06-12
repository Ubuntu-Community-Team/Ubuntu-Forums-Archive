---
title: "Setting USB audio sample rate"
date: 2008-06-09
forum: Multimedia Software
---

### Post by steevc on 2008-06-09
I'm using a Zoom H4 as a audio input device via USB. It gets recognised automatically and I can use it as an input for Skype, Audacity or Jack, but the recorded sound was pitch shifted up. I found that if I set the H4 to sample at 48kHz rather than the default of 44.1, then all was well. So it looks like ALSA or something assumes that the device will use 48.

I would prefer to use 44.1KHz as this is more standard for audio recording and is also the default on the H4, so I would not have to change it every time I plug in.

So where can I configure the sample rate?

In addition, I do not see the H4 as an input in Kmix or alsamixer. I do not hear the input signal over my speakers, so I guess that it is not enabled for that. Can this be changed somewhere?

Thanks

---

