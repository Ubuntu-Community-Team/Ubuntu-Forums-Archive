---
title: "MythArchive Fails to burn DVD (Intrepid)"
date: 2008-11-07
forum: Mythbuntu
---

### Post by funkydan2 on 2008-11-07
Hi,

Since upgrading to Intrepid, MythArchive has been failing to create DVDs.

The error message from the log is
```
ERROR: Failed while running ffmpeg to re-encode video.
Command was ffmpeg -threads 2 -v 1 -i "/myth/tmp/work/5/newfile.mpg" -r pal -target dvd -b 2344k -s 352x576 -acodec copy -copyts -aspect 16:9 "/myth/tmp/work/5/newfile2.mpg" -map 0:0 -map 0:1 

```
and when I run that command directly from the command line the error message is
```
error, non monotone timestamps 23765903 >= 23763023
av_interleaved_write_frame(): Error while opening file
```

I think this may result from there not being a version of ffmpeg in medibuntu for intrepid at the moment, but I'm keen to find out if there's a solution to this other than waiting for the medibuntu team to compile ffmpeg (if that's something that they're going to do).

---

### Post by dvhart on 2009-07-02
Did you find a solution to this?

---

### Post by funkydan2 on 2009-07-02
I can't remember!

I upgraded to jaunty, and came across some sort of problem that caused lots of crashing. I've since downgraded to hardy, which has improved the crashing, but not completely - I'll have to track down the hardware problem I think.

Anyway, I think it may have had something to do with burning recordings that had lots of errors in them (as in digital TV recordings where the reception was poor) and I just gave up on burning them.

---

### Post by funkydan2 on 2009-11-15
Hi,

Sorry for this bump, but I went to burn a DVD on the weekend, and it seems that this problem is still alive and well in Karmic (9.10)

With some research online, I thought maybe installing ProjectX (apt-get install project-x), and enable the use of that might change things, but it doesn't make any difference (maybe ProjectX gets called later in the script?).

Any ideas on what I need to do to be able to burn DVDs with the recordings that fail with this error - it doesn't happen with all recordings, just some, but all the recordings I'm wanting to burn to disc playback fine (but with a different number of skipped frames due to poor reception).

Thanks

---

