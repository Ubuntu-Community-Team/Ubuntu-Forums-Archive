---
title: "Listen music player crashes"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by insaneidiot on 2007-10-31
I'm running Gutsy and I recently downloaded the Listen music player, which is probably the best music player I've found for Ubuntu.  Only problem is that it hangs and crashes all the freakin' time.  Why is that?

---

### Post by ThrobbingBrain66 on 2007-10-31
Open it using a terminal and post any output that it gives.

```
listen
```

---

### Post by insaneidiot on 2007-10-31
I tried launching it from the terminal and it still hangs.  It's greyed out as we speak.  I also noticed this when I launched it in the terminal:

No musicbrainz support (musicbrainz2 missing)
No iPod support
No Audio cd support (musicbrainz2 missing)
Exception in thread Thread-11:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 460, in __bootstrap
    self.run()
  File "/usr/lib/python2.5/threading.py", line 440, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/listen/widget/context.py", line 112, in thread
    songs = pl.get_songs()
  File "/usr/lib/listen/library/__init__.py", line 520, in get_songs
    return [self.library.songs[uri] for uri in self.songs]

---

