---
title: "Why does this fix the no sound problem in Flash under Firefox for 8.04"
date: 2008-05-29
forum: Multimedia Software
---

### Post by ubnewbie2 on 2008-05-29
I have not had sound from flash in 8.04, nor the previous version 7.10, and even on a brand new install of 8.04 tonight, I still had no sound, from flash, playing videos on youtube.

Searching around, I found this post

[http://ubuntuforums.org/showthread.php?t=780961&highlight=flash+sound](http://ubuntuforums.org/showthread.php?t=780961&highlight=flash+sound)

and a little way down in the second message there are some instructions about installing OSS 4 from a deb package, with a note (Addendum 2) about sound in flash. 

```
ADDENDUM2: Sound in Flash
1. Run:
Code:

file /usr/lib/libflashsupport.so

If this returns info on the file, skip ahead to step 4. If the file isn't found...
2. Save the attached libflashsupport.so.gz to your Desktop
3.
Code:

cd ~/Desktop; gunzip libflashsupport.so.gz; sudo mv libflashsupport.so /usr/lib

4. create symbolic links to /usr/lib/firefox/plugins & /usr/lib/mozilla/plugins:
Code:

sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins; sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins

```

Well libflashsupport.so was missing from my install, so I grabbed the file and followed the instructions, restarted Firefox, and presto - sound finally from flash/firefox.


Seems very very odd that I had to manually add something like this, but I am sure glad it worked.

I am posting this message because I'd like to know why it works and how it was missed in 8.04, but also, it might help someone else with these problems.

---

### Post by kostkon on 2008-06-05
> **ubnewbie2 said:**
> I am posting this message because I'd like to know why it works and how it was missed in 8.04, but also, it might help someone else with these problems.
Check this [blog post]("http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/") for some explanations.

---

### Post by ubnewbie2 on 2008-06-05
> **kostkon said:**
> Check this [blog post]("http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/") for some explanations.

Ah yes, and I've been doing more reading since I posted my original message.  Even though it gave me sound, there were stability problems.  FF crashed very often when flash tried to play.

Since then, I found instructions to get the latest from the Flash 10 download on Adobe's site.  This is more stable - although not perfect.  On my system, you can play lot's of flash, but it sometimes crashes as you exit the page with the flash content.

Still it's an improvement.

---

