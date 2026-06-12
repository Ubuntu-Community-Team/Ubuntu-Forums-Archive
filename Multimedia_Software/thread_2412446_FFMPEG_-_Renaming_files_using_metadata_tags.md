---
title: "FFMPEG - Renaming files using metadata tags"
date: 2019-02-13
forum: Multimedia Software
---

### Post by Alan5127 on 2019-02-13
Hi All,

I am trying to work out whether it is possible to use a metadata tag to change the output filename from ffmpeg.

For example, an MKV file can contain a 'title' tag.

I would like to do something like this:

```
ffmpeg -i InputFile.mkv -vcodec copy -acodec mp3 OutputFile-$TITLE.mkv
```

where $TITLE is taken from the tag.

I have read the ffmpeg manual / online docs (and searched more broadly), but I cannot work out if this is possible.

I can find lots of discussions about adding a metadata tag to a file, but none about going the other way as I want to.

Any suggestions gratefully received.

Thanks,

Alan.

---

### Post by Holger_Gehrke on 2019-02-13
I don't think you can do that directly, but you can use ffmpeg to get all the metadata and use awk to extract the tag you need and use command substitution to use the result as (part of) the output file name. Something like:
```

ffmpeg -i InputFile.mkv -vcodec copy -acodec mp3 **"$(ffmpeg -hide_banner -loglevel quiet -i InputFile.mkv -f ffmetadata -|awk -F'=' -- '/^title/ {print $2}' -)"**.mkv

```
Holger

---

### Post by Alan5127 on 2019-02-14
Hi Holger,

That works perfectly!

Thanks,

Alan.

---

### Post by Alan5127 on 2019-02-15
Hi Holger (or anyone else reading this),

I have posted a new, follow-on question to this one, asking how to apply to multiple files, without resorting to a script (a one-line solution).

That question is here:

[https://ubuntuforums.org/showthread.php?t=2412682](https://ubuntuforums.org/showthread.php?t=2412682)

Thanks for any (additional) assistance you can provide :-)

Alan.

---

