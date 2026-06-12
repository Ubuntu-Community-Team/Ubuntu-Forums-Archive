---
title: "Help!!"
date: 2010-03-30
forum: Multimedia Software
---

### Post by evanct on 2010-03-30
When I try to play anything in banshee it crashes with the error:

```
=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

Same thing happens with Listen and Rhythmbox, but with a segmentation fault. 

Amarok doesn't even get past the splash screen, but that's more or less okay because I'd rather stick with gnome.

Guayadeque is the only decent music player that works, and even it isn't without its issues. Audacious also works, but I don't like Audacious(the whole "one big playlist" system... ew). 

Of course if I had my way I'd skip gnome music players entirely and go with foobar2000, but wouldn't you know it, that doesn't work either. [http://ubuntuforums.org/showthread.php?t=1442002](http://ubuntuforums.org/showthread.php?t=1442002)

I'm using 10.04 beta, but these problems were present on 9.10 too.

Why have the gods forsaken me?

---

### Post by lidex on 2010-03-31
Did you "upgrade" from karmic?

---

### Post by evanct on 2010-03-31
Yeah. And I upgraded 9.10 from 9.04. The original install was 8.04.

---

### Post by evanct on 2010-03-31
hmm, i'm getting some different behavior today from banshee and listen.

Listen doesn't crash, but still can't play songs, and gives me this when I try:

```
WARNING  listen.player.fadebin.StreamBin     stream "file:/path/to/song" already blocked
ERROR    listen.player.fadebin.PlayerBin   0x9993b6c  Failed start output
```

Banshee meanwhile doesn't crash immediately, but I tried playing several songs and each time i got this:

```
[Warn  14:06:20.670] Seem to be stuck loading file:/path/to/song, so re-trying

(Banshee:7277): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed
```

and then it crashed:

```
Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
at Banshee.GStreamer.PlayerEngine.OnAboutToFinish (intptr) <0x00011>
at (wrapper native-to-managed) Banshee.GStreamer.PlayerEngine.OnAboutToFinish (intptr) <0x00048>
```

---

### Post by lidex on 2010-03-31
I don't know what's going on. There's another thread with same type of issues but Listen for me works great (no banshee install). There were some recent mono updates and Banshee is a mono app. Something in those errors about gstreamer. My guess is something didn't upgrade properly and, yes, you asked for that by upgrading to a beta release. You say you had those problems in Karmic, looks like they carried over. Try purging Banshee and Listen and gstreamer codecs, all of them. Re-install listen and see what happens. Don't mess with banshee yet, mono may be an issue.

---

