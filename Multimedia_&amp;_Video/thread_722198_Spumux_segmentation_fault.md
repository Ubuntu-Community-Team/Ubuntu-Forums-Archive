---
title: "Spumux segmentation fault"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by survient on 2008-03-12
ok, I'm in the middle of authoring a dvd, I've got the primary streams created and muxed, I just need to add subtitles to the mix using spumux. When I run the command like so:
```

$ /usr/bin/spumux -m dvd -s 0 "/tmp/test/test/subtitle_1.xml" < "/tmp/test/test.mpeg2" > '/tmp/test/test/subtitles.vob'
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

Segmentation fault (core dumped)

```
well you can see the end result. Is there a known issue with spumux? I tried finding the source for it but it came of no avail... any help on this would be appreciated

---

