---
title: "command line tool for extracting tags"
date: 2008-05-09
forum: Multimedia Software
---

### Post by Yulquen on 2008-05-09
anyone know of a command line tool that can extract 
specific tags from mp3 and FLAC files? (at least Genre tag is needed)

need this tool for a shell script.

thanks in advance for any help.

---

### Post by girishv on 2008-05-09
Hi,

you can either use mp3info a perl utility or 
id3tool (can also be to edit the tags)
Both the tools are available in the repos

Girish

---

### Post by Yulquen on 2008-05-09
> **girishv said:**
> Hi,

you can either use mp3info a perl utility or 
id3tool (can also be to edit the tags)
Both the tools are available in the repos

Girish

I`m afraid none of them were usable.
they only display genres that is part of some predefined list,
and my genre fields contain both genre and styles, separated
by a ;.so they only say "12", "C" or "other" for my genre fields.

and none support flac, only mp3.

---

### Post by nick_h on 2008-05-09
> and none support flac, only mp3.
for flac files have a look at *metaflac* which is in the *flac* package.

---

### Post by Yulquen on 2008-05-09
> **nick_h said:**
> for flac files have a look at *metaflac* which is in the *flac* package.

metaflac seems to be just right for the flacs!

and I found I could use exiftool for the mp3's, so problem solved.

thanks again for suggestions.

---

