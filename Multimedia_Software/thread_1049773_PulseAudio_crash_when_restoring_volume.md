---
title: "PulseAudio crash when restoring volume"
date: 2009-01-24
forum: Multimedia Software
---

### Post by Dr. Kylstein on 2009-01-24
This happens with both Audacious and VLC, possibly others:
I open the program and start playback, then change the output device in pavucontrol. I close the program, re-open it, and start playback again. PulseAudio crashes: 
> 
E: sink.c: Assertion 'PA_SINK_OPENED(s->thread_info.state)' failed at pulsecore/sink.c:424, function pa_sink_render(). Aborting.

I restart PulseAudio and start playback again: it works. I close and reopen the program and restart playback: PulseAudio crashes again.

If I delete the stored volume table, it happens all over from the beginning.

---

### Post by 2hot6ft2 on 2009-01-24
Here's the thread for fixing PulseAudio.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)
Hopefully you'll find the fix for yours there.

---

### Post by Dr. Kylstein on 2009-01-24
This is *after* following the how-to.

I've noticed that the crash also happens after playback has been stopped for a while, or if I change to a different file in Audacious.

Edit: The pattern seems to be everytime a program starts an audio stream for the second or later time since PulseAudio was started.

---

### Post by Dr. Kylstein on 2009-01-25
This isn't something I can ignore. If there's any way I can make my problem clearer, I'd like to know. I have to open a new media file before the previous one stops to avoid crashing!

---

