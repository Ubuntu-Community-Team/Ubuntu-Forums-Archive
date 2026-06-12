---
title: "No sound after install jack"
date: 2011-02-18
forum: Multimedia Software
---

### Post by rrrobles on 2011-02-18
I had sound. My sound stops working after install jack. Jack server starts well, and the jack log shows no error messages. If I run Muse, it recognizes jack and show no error messages, but I have no sound output. Where should I start investigating?
I'm using Karmic.

---

### Post by garyjmellor on 2011-02-18
Ensure your system is based entirely on ALSA, with no extra non-ALSA servers or daemons, such as ESD, artsd or PulseAudio. You can disable these components through the Sound Preferences application (System > Preferences > Sound). Try this and check back.

---

