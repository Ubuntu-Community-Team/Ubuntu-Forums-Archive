---
title: "Can't record and playback in audacity at the same time"
date: 2010-01-26
forum: Multimedia Software
---

### Post by Aszasz on 2010-01-26
Hi,

I'm trying to record with my webcam in audacity. The quality is fine and i also can play it. But when i check the box "Play other tracks while recording new one" i get the standard error message (check sample rate etc.). However, I can record multiple tracks when the box is not checked. Would love to make it work since I prefer to work with several tracks.
When I start audacity form the terminal and try to use the playback while recording, I get this output:
Expression 'ioctl( component->fd, SNDCTL_DSP_SETFRAGMENT, &frgmt )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1024
Expression 'PaOssStreamComponent_Configure( component, sampleRate, framesPerBuffer, StreamMode_Out, master )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1135
Expression 'PaOssStream_Configure( stream, sampleRate, framesPerBuffer, &inLatency, &outLatency )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1232

Would be grateful if anyone has an idea on this one or has managed to find a workaround...

---

