---
title: "How to sync audio on a already badly out of sync video"
date: 2011-07-09
forum: Multimedia Software
---

### Post by fixitdude on 2011-07-09
You want to use ffmpeg and the -async command. Something like this...

ffmpeg -async 1 -sameq -i infile.avi outfile.avi

Here's what the man page says:

-async samples_per_second
Audio sync method. "Stretches/squeezes" the audio stream to match
the timestamps, the parameter is the maximum samples per second by
which the audio is changed.  -async 1 is a special case where only
the start of the audio stream is corrected without any later
correction.

Searching the net makes one believe that this command is just some sort of magic !

People just put it in the line and it just works. Isn't that nice?

It says nothing about how to change the TIME the audio starts syncing. Like do I want it to start 5 seconds delayed? Or what about 5 seconds sooner?

What if the audio gets more out of sync as the video goes on? Can I slip it a little at a time? What? No magic?

No one mentions a file that already has badly synced audio.

So what -async 1 really does is simply start the audio at the beginning of the file. LIKE AS IF THAT ISN'T STANDARD PROCEDURE?

So what is the exact solution to syncing a messed up video? And why can't it just do the proper "timestamp" sync in the first place?

No docs, no info and you are left out in the cold.

---

### Post by An Sanct on 2011-07-09
How about using VLC and sync audio with that? It also supports saving to stream, so you can save the file as you are looking at it, making a more sync version.

---

### Post by BicyclerBoy on 2011-07-09
Part of your problem could be using the avi container.
The avi container can not properly support modern video codecs etc.

---

### Post by fixitdude on 2011-07-10
The original is already out of sync.

---

### Post by An Sanct on 2011-07-10
You can 'move' the sound track in VLC for as many milliseconds you want in any direction...

---

