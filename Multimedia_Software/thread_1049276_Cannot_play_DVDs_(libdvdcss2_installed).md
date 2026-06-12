---
title: "Cannot play DVDs (libdvdcss2 installed)"
date: 2009-01-24
forum: Multimedia Software
---

### Post by Luke Dunstan on 2009-01-24
Hi,

I am unable to play a DVD (Life of Brian) using either Totem, Totem-Xine or VLC, though I have been successful with a different DVD. Attached is the output of:

$ export DVDCSS_VERBOSE=2
$ vlc > vlc_output.txt 2>&1

As you can see from the messages, libdvdcss is installed (version 1.2.10-0.2medibuntu1).

My DVD drive is region 4 (verified using regionset), and the DVD is region 4. I am running Ubuntu 8.10 Intrepid Ibex on x86_64.

Please help.

---

### Post by akash2008 on 2009-01-24
As you can see from the messages, libdvdcss is installed (version 1.2.10-0.2medibuntu1).

My DVD drive is region 4 (verified using regionset), and the DVD is region 4. I am running Ubuntu 8.10 Intrepid Ibex on x86_64.

---

### Post by mc4man on 2009-01-24
Unfortunately I'm in totally different region so can't help as to whether there is some structure protection on your title.

What you could try is going into home folder -> .dvdcss and deleting the folder (cache) associated with that title (DVD_VIDEO-2003041609453100-9b9c9e0e6e

That will force vlc to reacquire the keys.

If/when that doesn't work, delete the folder again and start vlc like this (assumes disk is in vlc's default drive - /dev/scd0

```
export DVDCSS_METHOD=title && vlc dvd://
```

This will force vlc to use 'title key' method to reacquire the keys (assuming you deleted the cache folder in .dvdcss as before

---

### Post by Luke Dunstan on 2009-01-24
It is working now, which is very strange because I didn't do anything except try to play a different DVD and then try the original DVD again.

---

### Post by mc4man on 2009-01-24
One of linux's little mysteries I guess.
it would be interesting to output another vlc.txt from same disc and run a diff on that and the orig. one to see if anything changed.

---

