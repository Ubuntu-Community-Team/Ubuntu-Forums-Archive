---
title: "FIX: Audio only played from one application at a time"
date: 2008-09-12
forum: Multimedia Software
---

### Post by Sparky222B on 2008-09-12
I see a lot of threads posted about only being able to hear audio output from a single application at a time. This is due to limitations in ALSA, however, using PulseAudio fixes this problem. Unfortunately, many applications only support ALSA and OSS.

Here's how to solve this issue:
Follow the steps at [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) under Installation, even on 8.04. Assuming you run the apt command and edit asound.conf correctly, go to System -> Preferences -> Sound and change your output sound system to PulseAudio. All ALSA applications should now be routed through alsa-pulse to PulseAudio.

You can now hear audio from multiple applications at the same time, even if they don't natively support Pulse.

Enjoy.

---

