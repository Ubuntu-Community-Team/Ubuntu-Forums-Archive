---
title: "dvd plays, but rippers can't see the disc"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by Coogan on 2006-09-06
Maybe the title's not entirely accurate, but I couldn't think of another way to describe it.  Here's what happened:

I installed Dapper on a box a few months ago.  The system originally had a standard CD burner, and that's what Dapper was installed from.  A few weeks ago I got a new DVD burner for my main desktop to replace my slower one, and last night replaced the cd burner in the Dapper system with my old DVD burner.

At first Totem couldn't read any the disc; it errored out with something about the incorrect plugins.  After doing some searches on this forum, I found a thread with some tips, and after all was said and done, ended up replacing Totem with Totem-Xine, which had no problem reading and playing the DVD.

The rippers are another problem.  I've been using AcidRip, but when I pointed it at /media/cdrom0/, it just produced a single chapter with a time of 00:00:00 in it's list.  I tried k9play (or something like that; I found it in the repos) and it produced the same thing.  I'm guessing it's a problem with the css libs, but I've already run the install-css.sh script and as far as I can tell, the css decrypter is in place and working just fine.

Can somebody point me in the right direction?

Coog

---

### Post by x64Jimbo on 2006-09-06
Try changing the device to /dev/dvd or something similar.

---

### Post by Coogan on 2006-09-06
Thanks, I'll give it a try after I get home from work and let you know what happens.

Coog

---

### Post by Coogan on 2006-09-06
Nope, that didn't work either.  I'm able to open a terminal and cd to /media/cdrom0, and ls shows both the audio_ts and video_ts folders, and all the vob, ifo, etc, files seem to be ok and right where they're supposed to be.  AcidRip automatically detects and fills in the title, but the chapter list still shows the single chapter with a duration of 00:00:00

---

### Post by x64Jimbo on 2006-09-07
Is it just this one dvd or all dvds? have you installed all the necessary libraries?

---

### Post by Coogan on 2006-09-07
> **x64Jimbo said:**
> Is it just this one dvd or all dvds? have you installed all the necessary libraries?


I stand corrected.  Tried another DVD and everything was good.

Huh.  Wonder what the problem with the first one was.

Coog

---

