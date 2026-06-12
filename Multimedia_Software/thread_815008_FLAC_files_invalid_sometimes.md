---
title: "FLAC files invalid sometimes?"
date: 2008-06-01
forum: Multimedia Software
---

### Post by insane_alien on 2008-06-01
i've been using a script to convert my flacfiles to ogg

found here: [www.buberel.org/linux/batch-flac-to-ogg-converter.php](www.buberel.org/linux/batch-flac-to-ogg-converter.php)

this works for the large majority of my music collection (about 95%) but a few hundred files come up with the error

```
ERROR: Input file "/path/to/track/example.flac" is not a supported format
```

now i've double checked that these files are infact flacs. media players play them as flacs, the mime types say they are flacs and so on.

these flacs were obtained in the same way as the rest of them, by ripping off my CD collection.

anyone any ideas how to fix this or another method of convertion?

---

### Post by ajgreeny on 2008-06-01
Install and try either soundconverter or soundkonverter from the repos.  I've used both, sometimes have found that soundconverter makes a mess of producing ogg files, but soundkonverter has done those OK.  No idea why, just one of those things.

If you want a terminal application, try sox, also in the repos, and easy to use, though not as easy as those with a gui if you have lots of files to batch convert.

---

