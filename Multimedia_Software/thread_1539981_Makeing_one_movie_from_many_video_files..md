---
title: "Makeing one movie from many video files."
date: 2010-07-27
forum: Multimedia Software
---

### Post by irv on 2010-07-27
I have 13 ogv file and I would like to make one seamless movie from them. Does Ubuntu have a program that will do this? Right now I am trying to do it with DeVeDe, but I am not sure this is the best way to go?
Any ideas would be appreciated.  Thanks

---

### Post by ron999 on 2010-07-27
Hi irv
Try using **mkvmergeGUI**.
It's part of the package **mkvtoolnix**.
You 'add' the first file then 'append' the other twelve.
You should end up with one mkv file.
No re-coding is done.
I don't know whether the result will be 'seamless', there's only one way to find out.

(By the way, DeVeDe is a program that's used for making playable DVDs from files.)

---

### Post by irv on 2010-07-27
> **ron999 said:**
> Hi irv
Try using **mkvmergeGUI**.
It's part of the package **mkvtoolnix**.
You 'add' the first file then 'append' the other twelve.
You should end up with one mkv file.
No re-coding is done.
I don't know whether the result will be 'seamless', there's only one way to find out.

(By the way, DeVeDe is a program that's used for making playable DVDs from files.)
I'll give it a shot. I did end up with a iso file after using DeVeDe, and burned a DVD which should work, but I am still going to try mkvmergeGUI from mkvtoollnix. Thanks for the tip.

---

### Post by irv on 2010-07-27
T> ry using mkvmergeGUI.
It's part of the package mkvtoolnix.
OK I tried these packages, but they do not support ogv file format. It is not listed in the file format list. I force the format, but it comes up with an error when run.

---

### Post by ron999 on 2010-07-27
OK
If you still want to try mkvmergeGUI change the suffix of those ogv files into **ogg** or **ogm**.

Also when you use add and append, only import the audio and video tracks. If there's any 'unknown' tracks then un-tick their boxes.

Then '**Start muxing**'.

---

### Post by irv on 2010-07-27
> **ron999 said:**
> OK
If you still want to try mkvmergeGUI change the suffix of those ogv files into **ogg** or **ogm**.

Also when you use add and append, only import the audio and video tracks. If there's any 'unknown' tracks then un-tick their boxes.

Then '**Start muxing**'.

Ok, I gave it a try but even though it worked, everything was off. The voice (audio) was not right with the video. What I did before with DeVeDe will work for what I want, I don't think mkvmergeGUI is going to work for what I am trying to do. Thanks again for your input on this thread.

---

