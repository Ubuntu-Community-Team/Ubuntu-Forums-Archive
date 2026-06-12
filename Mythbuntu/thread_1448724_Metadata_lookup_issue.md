---
title: "Metadata lookup issue"
date: 2010-04-07
forum: Mythbuntu
---

### Post by dannysauer on 2010-04-07
I have a few videos for which myth just doesn't seem to be able to fetch metadata, even if I enter the IMDB number.  Specifically, here's a couple of examples:

[http://www.imdb.com/title/tt0500148/](http://www.imdb.com/title/tt0500148/)
[http://www.imdb.com/title/tt0430334/](http://www.imdb.com/title/tt0430334/)
[http://www.imdb.com/title/tt0117217/](http://www.imdb.com/title/tt0117217/)

Now, ignoring the opinions of people on the videos themselves, what's up with the metadata grabber?  It gets hundreds of other videos just fine.  For the first one, I actually renamed the file
```
Saturday Night Live: The Best of Phil Hartman.iso
```
and, thinking that it needed to be forced to TV, I tried this:
```
1x01 Saturday Night Live: The Best of Phil Hartman.iso
```

I tried just download metadata, look up TV based on title/subtitle, and entering the IMDB number - both as 0500148 and t0500148.  None of those have worked.  For Mosquito Man (aka mansquito), I actually went to the trouble of correcting the IMDB alternate entry with the missing space a few weeks back, and it still won't look up right (though I can find it through IMDB's web interface using the two word version now). :)

Anywho, I'd appreciate any tips people have.  It's really annoying having these black spots in my otherwise awesome list-o-videos, and I hate having to enter all of the metadata manually for things where the automatic system should be working. It's mostly the principle of the thing, but also because it's apt to happen again.  I'm not planning to stop accumulating bad movies. :D

PS, it's done this in Karmic and continues in the current Lucid (I still wish they'd chosen "Lumpy") beta.

---

### Post by iamlindoro on 2010-04-07
Do your films exist at TheMovieDB?  Myth's metadata source is not IMDB.  In .22, you use the IMDB number as the reference (meaning it only worked with the subset of films at TMDB that had an IMDB number set.  In .23, the TMDB number is the reference, meaning you should be using the TMDB number when entering the reference number.  If it doesn't exist at TMDB, then no amount of cajoling will make a metadata grab succeed-- you can, however, add it to TMDB, wait a few days for their cache servers to refresh, and then pull in the data, thus helping the whole community.

---

### Post by dannysauer on 2010-04-10
Well, that would explain it.  I thought that since it was using IMDB numbers it looked up with IMDB. :D

---

### Post by nickrout on 2010-04-10
> **dannysauer said:**
> Well, that would explain it.  I thought that since it was using IMDB numbers it looked up with IMDB. :D

imdb do not allow automated lookups. the imdb numbers are an historical artifact from the time mythtv did use imdb by default.

I suggest you add these movies to themoviedb - it's a collaborative effort, if people like you don't add the entries, it will never get in there.

---

### Post by singedwings on 2010-05-24
Just as a side note you should read [http://www.mythtv.org/wiki/MythVideo_File_Parsing]("http://www.mythtv.org/wiki/MythVideo_File_Parsing") for valid ways to name your files, makes life a lot easier.

---

