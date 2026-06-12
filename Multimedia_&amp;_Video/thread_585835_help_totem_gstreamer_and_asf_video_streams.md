---
title: "help totem gstreamer and asf video streams"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by cor2y on 2007-10-21
I haven't much experience with the gstreamer backend.
But seeing as when i upgraded to Gutsy a quick  install of all the dependancies worked i decided to use that and not go with the normal xine backend.
Well now i have discovered the first chink in the armor of gstreamer.
Totem its plugins and player are the only player i have installed and so  far via the web it played everything now i have discovered i can't see asf video streams with the plugin for firefox or with the player and just using the mms or http stream address .
Totem says buffering then the window will stay black and there will be no audio or video after it buffers.
Any help on what could be wrong would be appreciated.
Ubuntu Gutsy
totem 2.20 with gstreamer backend all plugins installed
msg from terminal with totem when attempting to play the stream
```
totem
JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Total Unfree 60 bytes cnt 1 [(nil),0]

```
I don't know what that means, note i can play other video streams in the  player or the plugin for firefox, real media and quicktime works but for some reason asf refuses to work.
I have tried setting the gstreamer video setting s to use x11 to see if that was the problem it didn't work.

---

