---
title: "Sound completely dead"
date: 2008-09-01
forum: Multimedia Software
---

### Post by Imashinu on 2008-09-01
So earlier today I was trying to get sound to work in wine and in the process my computer locked up so I had to restart. When the computer came back online no sound in any application but flash in firefox worked. The computer is recognizing my sound card but no audio is playing.

I tried to go test my sound in the preferences and it is giving me this error.

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```

I tinkered around for a while and cannot find a solution. Does anyone have any ideas?

Note: I'm using Ubuntu 8.04

---

### Post by minky311 on 2008-09-01
Try pressing alt f2 and typing in gstreamer-properties. Under default ouput change it to Alsa and try different devices until you find one that works if any. Also make sure in system->preferences->sound that under music and movies it is set to alsa.

---

