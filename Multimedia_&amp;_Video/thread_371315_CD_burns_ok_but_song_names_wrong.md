---
title: "CD burns ok but song names wrong"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by rfrestedt on 2007-02-26
Burning an audio CD works fine but the wrong tracknames, artist names, album names are bizzarely incorrect.  The information seems to be retrieved randomly as I have burned the same several MP3 songs 4 times finding different name information on each.  It is always the information from some random album completely unrelated to the songs I have.  

Could the program that is run by the user application (cdrecord?)be going out to some CDDB and getting the wrong information?

I have tried 3 user applications and the result is the same.  I have used:  Serpentine, Rhythmbox and K3b (configured to use cdrskin/libburn).

Any explanation as to how the naming info thing works would be appreciated.

Thanks

---

### Post by kevinlyfellow on 2007-02-26
Well, it seems to be a problem with gstreamer (Rhythmbox and Serpentine are practically the same program when burning).  Tell me, in Rhythmbox does it give the correct idv2 and/or idv3 tags?  I doesn't really have much to do with cddb, but maybe I'm wrong.  Try disconnecting yourself from the internet first.  (also, if you haven't already, pick up a cd-rw so you don't become a coaster factory!).  Another thing, try a program to rename your mp3s, I like Audio Tag Tool... (sudo aptitude install tagtool)

---

### Post by kevinlyfellow on 2007-02-26
Oh, the best explaination I can give on these tags is that at the begining of each mp3 file there is a special section where all that information is written.  CDDB takes a look at the cd, and queries a server on the internet that will provide info on the cd.  Actually, come to think of it, I'm not sure if your cd would have any information about what it is on it!  I think it should give you track 1 track 2 ... because cds do not have files, only tracks.  I still should not be giving you funny names though.

---

### Post by rfrestedt on 2007-02-26
I would be quite happy with tracknames of 1 and 2 and unknown artist etc.  No information is better than the wrong information- in a variety of languages too.

---

### Post by kevinlyfellow on 2007-02-27
What I suggest, is to download xine-ui and see if that program gives you wrong names.  If it does I know how to shut down its ability to retrieve cddb info from the web (which I will help you with).  It may be a weird coincidence, but it is possible that someone mixed an album, and posted it onto freedb.org and for whatever reason, it thinks that it matches your disk.

---

