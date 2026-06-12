---
title: "Songbird only plays songs as root"
date: 2008-05-01
forum: Multimedia Software
---

### Post by shoofy on 2008-05-01
I installed Songbird 0.5.1 from getdeb.net. When I try to play songs in it as a normal user, it says error and the terminal says:

(songbird:462): GStreamer-CRITICAL **: 
Trying to dispose element fakesink, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

If I run it as root it plays fine.

I'm running Hardy.

Anyone know what this error means or how to run it as a normal user?

---

### Post by beoba on 2008-06-04
I'm getting this for all gstreamer applications (totem, banshee, quodlibet). Non-gstreamer apps (vlc, mplayer) are fine. Is there a solution?

---

### Post by beoba on 2008-06-04
Looks like I was able to fix it by removing gstreamer0.10-pulseaudio

Not really a fix, but this problem is sufficiently irritating that I don't really care.

---

