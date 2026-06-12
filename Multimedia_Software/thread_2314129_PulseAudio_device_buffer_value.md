---
title: "PulseAudio device buffer value"
date: 2016-02-18
forum: Multimedia Software
---

### Post by claudia-alvarado on 2016-02-18
Hello! I have come across a strange problem and have no clue how to go about fixing it. We are using PulseAudio to send audio over wifi using RTP. We were having buffering issues and started going through the error logs to see if we could pinpoint the problem. We noticed that in the sink.c file, where device specifics are pulled (i.e. sound card characteristics), the development version of PulseAudio pulls a different value from the natively installed version of pulse for only the device buffer size and the device fragment size. I think that this may be the root of our problem.. when we should be seeing values of 64000 and 32000 respectively, the dev version is giving 352,800 and 176,400.


Has anyone else encountered this issue? Thanks in advance!

---

