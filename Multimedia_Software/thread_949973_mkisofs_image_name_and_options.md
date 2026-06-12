---
title: "mkisofs image name and options"
date: 2008-10-16
forum: Multimedia Software
---

### Post by maeks84 on 2008-10-16
If I run the command
```
mkisofs -dvd-video -udf -R -o D005.iso DVD/
```
Then mount the resulting iso file.  The name of the mounted image has the title CDROM.

Is there a way to change this to a specific name (D005) or am I stuck with CDROM as the name?

Also, are the -udf and -R options needed if I'm planning on burning the image to DVD later?  (It's a video DVD.)  I've seen the command with and without them and I don't really understand what the man page has to say about them.

Many Thanks,
maeks84

---

### Post by maeks84 on 2008-10-17
Another issue I've discovered...

If I mount the resulting .iso image on another computer, (Running Mac OS X 10.5) the mounted image has no files in it.  Yet is has 4.21 GB space used and if I open it from inside of VLC it plays.

I've tried it without the -UDF and -R.  As well as with just -r.

I'll continue looking, but some help would be great.  Maybe I should be using something other than mkisofs?  I'm just trying to get VIDEO_TS and AUDIO_TS folders to an image for later burning.

---

### Post by maeks84 on 2008-10-17
Okay, further research lead me to this [List of ISO image software]("http://en.wikipedia.org/wiki/List_of_ISO_image_software") at Wikipedia.  Using that I've found and started to use [DVD Imager]("http://lonestar.utsa.edu/llee/applescript/dvdimager.html") for Mac OS X.  Files appear everywhere I've tried and I can specify the name I want.

So, I've currently abandoned the research on getting mkisofs to work.  Yet, if anyone knows what I was doing wrong with it, I would still be interested in hearing it...

---

### Post by J-Hutchinson on 2009-09-19
If anyone is wondering how to do this still, -V is the switch to set the volume ID for the disk.
Cheers,
John

---

