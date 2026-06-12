---
title: "MythTV running choppy when seeking (fast forwarding/rewind or stepping through frames"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by Yoooder on 2007-02-15
My mythbox has suffered several disasters (admittedly at my hand) included loss of the video files and database corruption.

I've since done a complete uninstall and reinstall of mythtv (including wiping the mythconverg database) and it's not acting quite right.

Before the data losses if I paused either LiveTV or playback of a video and stepped through frame by frame it worked beautifully, each frame was clear and it would step smoothly through.  When fast forwarding or rewinding the screen would show me where I was at in the recording.

Since the data losses I occassionally get "No seektable" errors on the OSD when trying to edit recordings, and stepping through frame by frame doesn't work--instead it jumps maybe 1 second and then plays for a fraction of a second.  The result is an inprecise and somewhat sloppy effect.

FYI: I did backup my pooched database and re-used it's keybindings and channel tables in the reinstall, and I'm not certain I purged the original 100%.

Thanks!

---

### Post by bnuytten on 2007-02-15
I remember coming past a forward/rewind option to have them act to the exact frames. Not "far away" from the sticky keys option I believe.  If it is enabled, it will be more CPU intensive. Just a guess...

---

### Post by Yoooder on 2007-02-22
I re-enabled this option, as well as something to do with letting OpenGL sync things.

It makes a difference for the better, but still shows some playback while stepping through frames and such.

---

### Post by wjston on 2007-02-22
> **Yoooder said:**
> 
Since the data losses I occassionally get "No seektable" errors on the OSD when trying to edit recordings, and stepping through frame by frame doesn't work--instead it jumps maybe 1 second and then plays for a fraction of a second.  The result is an inprecise and somewhat sloppy effect.

Go to post #5 using the following URL. I have explained how to repair mythconverg using a web browser.
[http://www.ubuntuforums.org/showthread.php?t=357927&highlight=MYTHTV](http://www.ubuntuforums.org/showthread.php?t=357927&highlight=MYTHTV)

Your database is more than likely corrupt and needs to be repaired.

---

### Post by Yoooder on 2007-02-23
Thanks for the suggestion, but it didn't resolve my issues.

Here's a scenario that really emphasizes the behaviour that I'd like to resolve:  When watching a previously recorded program I pause it then go into "edit recording."  Once there I reduce it's time-steps to 1 frame, and hit my over button just once (to move one frame).  At this point it very slowly plays 2 or 3 frames and their associated audio in a loop.

Before my database/data losses moving 1 frame was very crisp and smooth, and definately resulted in a single frame and no audio.

---

### Post by OldGaf on 2007-09-09
I also "suddenly" have an issue with fast forward and rewind. I hear sound while doing both (didn't before) and it has become VERY choppy and often does not take you to where you think you should be, or gets stuck and will not return to normal play.

---

### Post by Balachmar on 2007-09-15
I am experiencing the same problems als OldGaf.
Quite annoying really. And as far as I know I didn't really change anything...
OK, solved this one. It has to do with the database and you should run optimize_mythdb.pl
Which is a script that has been installed by mythtv already. (just do a locate to find it)
After this all my troubles where gone

---

