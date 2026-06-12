---
title: "Cannot burn audio CDs with Serpentine"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by jgb2185 on 2008-01-28
I burned a number of audio CDs in Serpentine (under 6.06 LTS) a week ago with no problem. Now, when I try to do so, I get the error:

"Converting files failed -- Writing to disc didn't start so it is still usable"

This occurs whether I run Serpentine under my own ID or as root, so it does not seem to be a permissions issue. When I run Serpentine from the command line, no error appears when I attempt to burn a CD.

I've searched ubuntuforums and the Net in general, and cannot find anything that is relevant to these circumstances. Can anyone suggest a solution, or at least some more diagnostics?

Many thanks...

JGB

---

### Post by disturbed1 on 2008-01-28
> **Converting files failed**

Check that you have the correct GStreamer codecs installed to playback the files you're attempting to burn. As long as you still have the default Totem installed, and not Totem-xine, this can be confirmed by playing the file back with that application. Totem uses GStreamer, Totem-xine does not.

---

### Post by newagelink on 2008-05-30
> **disturbed1 said:**
> Check that you have the correct GStreamer codecs installed to playback the files you're attempting to burn. As long as you still have the default Totem installed, and not Totem-xine, this can be confirmed by playing the file back with that application. Totem uses GStreamer, Totem-xine does not.[COLOR="Indigo"]I'm having the same error as OP; I use Ubuntu 7.10 and Serpentine 0.9. How do you play files with Serpentine? I think my GStreamer is working correctly; Rhythmbox is my default jukebox and I can play .wav files in MPlayer.[/COLOR]

---

