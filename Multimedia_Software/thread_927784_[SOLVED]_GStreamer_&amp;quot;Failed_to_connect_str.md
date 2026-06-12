---
title: "[SOLVED] GStreamer &amp;quot;Failed to connect stream: invalid argument&amp;quot;"
date: 2008-09-23
forum: Multimedia Software
---

### Post by Doopydoo22 on 2008-09-23
I noticed a similar thread earlier, but it had no responses so I made one with a more straightforward title.

This error occurs in some form or another in any program that uses gstreamer (tested totem, rhythmbox, songbird) while the same media files will work just fine in VLC.

A  gst-launch-0.10 playbin uri="file://[...]" command in the terminal returns:

```
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
ERROR: from element /playbin0/abin/audiosink/audiosink-actual-sink-pulse: Failed to connect stream: Invalid argument
Additional debug info:
pulsesink.c(411): gst_pulsesink_prepare (): /playbin0/abin/audiosink/audiosink-actual-sink-pulse
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
FREEING pipeline ...

```

Other programs, when run in the terminal, bring up identical errors (though formatted differently).

Has anyone found a solution for when this occurs?  Sadly I haven't written down what changes I may have made between when it was working and now.  My gut reaction is to say I didn't change anything, and that's how I remember it, but I must've changed something.  Any thoughts?

---

### Post by markbuntu on 2008-09-23
What do you have setup in System/Preferences/Sound?
System/Preferences/Multimedia Systems Selector?

---

### Post by Doopydoo22 on 2008-09-26
I feel like an idiot.  All I did was switch the options in System>Preferences>Sounds to ALSA from Autodetect and that fixed it.  Videos now work in GStreamer-based apps as well.

Thanks for prompting me to check back there.

---

### Post by carolinason on 2008-09-30
I had to choose OSS for my C-Media CMI8738 to get media working. How this is solved I dunno, it's a bug. Work Around is more like it.

---

### Post by markbuntu on 2008-09-30
More like a faulty default installation configuration than a bug. You should not be having any problems with that card. For general help with sound troubleshooting:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by wykedengel on 2009-01-02
I can say that this tip also worked for me as I spent 2 hours trying to figure out what was going on when I tried to play a DVD.

---

### Post by michinobu_zoned on 2009-01-11
I actually remember mostly what happened between from when my Banshee and Totem apps were working and when they couldn't due to a GStreamer issue.  What had happened was that I saved some movie files, which I downloaded from the internet in Windows Vista and played them in my Linux OS, onto my Linux partition.  

When I was playing the movies, the videos worked and I could watch the movies and then I saved a playlist for those movies.  However, when watching the movies, I did notice that Totem started acting funny - by not showing the list when I was not in full-screen mode.

After watching my movies, I turned off my computer for a while.  Later, I then booted up my machine and tried to watch the movies again, but they didn't work.  Something similar happened had happened when I tried to listen to my music on banshee-1.  I had to start banshee-1 from the console to see what the errors were.

The movies' file types were .flv, .avi, .mpg, and .wmv.  I don't know if the movies' file-type had anything to do with the GStreamer problem, it seems to me that if I didn't change any system settings in order for the problem to have occurred then I shouldn't have to change them in order for the problems to be solved.  However, we might all learn more of this issue if more people report of their experiences dealing with GStreamer.

---

