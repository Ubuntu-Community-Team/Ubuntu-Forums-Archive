---
title: "burning mkv to dvd"
date: 2008-11-28
forum: Multimedia Software
---

### Post by kaston on 2008-11-28
relative noob here.  i'm looking for an easy, ideally GUI-based method of burning mkv files to DVD.  couldn't find one using the search.  i know that mkv is just a container for different video types.  does this mean that a universal mkv to dvd tool doesn't exist?

---

### Post by andrew.46 on 2008-11-30
Hi kaston,

An mkv file can be burned to DVD with the standard burning tools available to Ubuntu such as k3b. Is this what you mean? My apologies if I have misunderstood :-).

**Edit:** Or are you referring to something like ffmpeg's conversion:

```
ffmpeg -i infile.mkv -target dvd outfile.mpg
```

Commandline though... A full description of this and  few other techniques can be seen here:

[http://atomized.org/2005/03/converting-divxxvid-avi-to-dvd-with-ffmpeg/](http://atomized.org/2005/03/converting-divxxvid-avi-to-dvd-with-ffmpeg/)

  Andrew

---

### Post by tgpraveen on 2008-11-30
i guess he wants to make a movie dvd. u know the kind which we can playback on standard dvd video players.

---

### Post by kaston on 2008-11-30
> **tgpraveen said:**
> i guess he wants to make a movie dvd. u know the kind which we can playback on standard dvd video players.yeah.  sorry, i should have specified this.  i want to be able to play the dvd in my standalone dvd player connected to my tv

---

