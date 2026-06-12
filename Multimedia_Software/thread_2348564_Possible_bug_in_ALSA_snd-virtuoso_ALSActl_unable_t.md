---
title: "Possible bug in ALSA snd-virtuoso: ALSActl unable to store settings for ASUS XONAR"
date: 2017-01-04
forum: Multimedia Software
---

### Post by bcschmerker on 2017-01-04
On the Hot Rod gPC, I found that the gain settings for ALSA snd-virtuoso consistently have Aux In muted, off record/stream, on every start for the ASUS® XONARESSENCESTX/A (C-Media® CMI-8788 DSP) with any Aux setting prior to shutdown.  Attempting sudo alsactl store returned the following error:
```
alsactl: get_control:256: Cannot read control '2,0,0,Mic Capture Volume,0': Invalid argument
```
This error did not occur with snd-emu10k1 on either the Creative Laboratories® SB0350 (Creative Technology CA0102 DSP) or SB1550 (Creative Technology CA10300-IAT DSP).  How does one isolate the correct package for filing at Launchpad&#8480;?

---

### Post by Yellow Pasque on 2017-01-05
```
apport-bug audio
```

---

### Post by bcschmerker on 2017-01-07
The hardware is not at fault; apport-bug audio had all recording and playback tests complete without issue.  The problem is failure to read a specific parameter from the CMI-8788 due to an invalid argument, so that settings fail to save properly.

---

