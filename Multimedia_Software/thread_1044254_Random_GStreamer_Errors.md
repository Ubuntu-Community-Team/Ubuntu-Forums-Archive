---
title: "Random GStreamer Errors"
date: 2009-01-19
forum: Multimedia Software
---

### Post by version7x on 2009-01-19
I've been having an on and off error when trying to play mp3's in banshee...

After a fresh reboot, the problem usually goes away, but I can't always reboot and would like to be able to figure out what is really going on.

About every third or fourth session, I'll launch banshee and attempt to play any mp3.  Banshee will freeze up and show the X box that it shows when I don't have the correct codec installed.

I reboot and poof... there's the codec!!

When trying to track down the cause of these errors, I started banshee in debug mode and got this output...

```
[Debug 09:47:35.606] Player state change: Idle -> Loading

(Nereid:15552): GStreamer-CRITICAL **: 
Trying to dispose element playbin, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

[Debug 09:47:35.751] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL
[Debug 09:47:35.752] Player state change: Loading -> Idle
[Error 09:47:35.753] GStreamer resource error: Failed
[Debug 09:47:35.754] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL
[Error 09:47:35.755] GStreamer core error: StateChange
[Debug 09:47:35.755] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL
[Error 09:47:35.756] GStreamer resource error: Failed
[Debug 09:47:35.756] (libbanshee:player) bp_stop: setting state to GST_STATE_NULL
[Error 09:47:35.756] GStreamer core error: StateChange
[Debug 09:47:36.260] Querying model for track to play in Song:Next mode
```

I've done some unsuccessful digging around, but can't find a cause or a cure.  

Any suggestions?

Thanks in advance!

---

