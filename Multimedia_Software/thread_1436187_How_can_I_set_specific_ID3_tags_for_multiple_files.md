---
title: "How can I set specific ID3 tags for multiple files?"
date: 2010-03-22
forum: Multimedia Software
---

### Post by KIAaze on 2010-03-22
How can I set specific ID3 tags for multiple files?

For example, I would like to set all files in a directory to the same album. (directly setting the album tag for files in a directory to the directory name would be even better)

Command-line solutions are also welcome.

---

### Post by l.billon on 2010-03-22
Hi!
If you use KDE, Kid3 does great job when working on a 1folder-1ablum scheme.
Easy TAG also per-folder batch id3 tagging.
I don't know any command line solution.

---

### Post by KIAaze on 2010-03-22
Thanks, I used kid3 in the end.

The problem was that rhytmbox seems to use the ogg vorbis tag instead of the ID3 tags, so id3 and id3v2 didn't work.
easytag seemed unable to set the album for multiple files.

Also, is there any way to get rhytmbox or amarok to search through music by filenames instead of tags? (the original reason why I'm even starting to change the tags ^^)

P.S.:
CLI way to change the album tag for all files in a directory to the directory's name:
```

id3 -A "$(basename "$(pwd)")" *
id3v2 -A "$(basename "$(pwd)")" *

```

---

