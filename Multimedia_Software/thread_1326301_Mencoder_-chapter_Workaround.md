---
title: "Mencoder -chapter Workaround?"
date: 2009-11-14
forum: Multimedia Software
---

### Post by dealcorn on 2009-11-14
The code:

mencoder dvd://1 -chapter 1-40 -o out.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4 -vf spp,scale -stereo 2

works if a dvd has 40 chapters but either fails or loses chapters if the dvd has fewer or more chapters.  I am not aware of a "-chapter all" option.  Is there a function that returns the number of chapters on a dvd so I can set a variable with the correct chapter end count?

---

### Post by dealcorn on 2009-11-14
Once I realized I wanted data from VIDEO_TS.IFO, I realized:

5300:~$ lsdvd
libdvdread: Using libdvdcss version 1.2.10 for DVD access
Disc Title:   
Title: 01, Length: 06:18:49.320 Chapters: 40, Cells: 41, Audio streams: 01, Subpictures: 00

Longest track: 01


Also, the dvd has as many titles as the count of the word Title in the output.

---

