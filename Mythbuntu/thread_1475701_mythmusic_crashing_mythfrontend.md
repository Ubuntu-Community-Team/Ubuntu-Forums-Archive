---
title: "mythmusic crashing mythfrontend"
date: 2010-05-07
forum: Mythbuntu
---

### Post by wolowina on 2010-05-07
hi,

I have major problems with mythmusic... Got this with 0.23 latest ppa version, but exaclty the same behaviour i remember with 0.22 version (stable)

I can go to music plugin, but once i select 'playlist' or play music or go back (esc key), mythmusic crashes mythfrontend..

And nothing valuable for me can be found in log files...
```
2010-05-07 11:30:07.653 Loading menu theme from /usr/share/mythtv/music_settings.xml
2010-05-07 11:30:27.295 Loading menu theme from /home/mythtv/.mythtv/library.xml
2010-05-07 11:30:29.270 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
mythfrontend.real: malloc.c:4628: _int_malloc: Assertion `(unsigned long)(size) >= (unsigned long)(nb)' failed.

```

When i executed 'mythfrontend -v audio' i have :
```
2010-05-07 11:33:49.193 Connected to database 'mythconverg' at host: 127.0.0.1
2010-05-07 11:33:49.209 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
mythfrontend.real: malloc.c:3096: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
Aborted

```

well, it was only one in time when i was able to play some music... only once.

i got ape, mp3, flac file types there...

---

