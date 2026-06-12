---
title: "MP3 library smart volume music analyser."
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by jbor7755 on 2008-02-09
Ie had a look around at other posts but haven seen one yet on this...

I like to be a ble to run a music analysation program which can equalise the volumes of the various albums/tracks in my music library.  Creative (I have a Zen Vision M) has a feature on their windos based software which can do this and it is quite handy.  It reduces tha amount of volume adjustment you need to do when listening to your music.

Is there something like this out there for linux??

Cheers.

---

### Post by ron999 on 2008-02-09
> **jbor7755 said:**
> 

Is there something like this out there for linux??



Yes, it's called mp3gain.
Here:-[http://mp3gain.sourceforge.net/]("http://mp3gain.sourceforge.net/")
It's in the Ubuntu repo.

---

### Post by jbor7755 on 2008-02-09
Thanks, awesome.

---

### Post by jbor7755 on 2008-02-09
Would there be a graphical front end for this program or something similar with a GUI?  Doing analysis and normailisation on a whole library is going to get a bit cumbersome at the  command line.

---

### Post by ron999 on 2008-02-10
Hi
I don't know whether there is a GUI for mp3gain.

When I use mp3gain from the command line I do this:-

Change directory to the folder where the mp3 tracks are (or create a temporary folder and put the required tracks in).
Then enter:-
**mp3gain -r ***

Then mp3gain works its way through the whole lot and normalizes them individually.

8):guitar::cool:

---

