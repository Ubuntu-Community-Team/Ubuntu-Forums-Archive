---
title: "Convert AAC to mp3 and keep tags"
date: 2009-10-09
forum: Multimedia Software
---

### Post by Jssizzle on 2009-10-09
I need to convert a good 2000 tracks or so into .mp3 format from .m4a, and haven't found a simple way to do it that keeps the same tags I already have on the files.

I'd rather not have to retag all of them . . . I've never seen a program that does it well.

Any ideas? Sound converter can work, but is awfully slow going about it - it freezes up whenever I drop too many tracks into it.

---

### Post by StuartN on 2009-10-09
> **Jssizzle said:**
> I'd rather not have to retag all of them . . . I've never seen a program that does it well.

There is a Python script here [http://pragmattica.wordpress.com/2008/01/17/convert-itunes-m4a-files-to-mp3-on-linux/](http://pragmattica.wordpress.com/2008/01/17/convert-itunes-m4a-files-to-mp3-on-linux/) that saves the tags and re-inserts them after the conversion. I have not tried it.

---

### Post by andrew.46 on 2009-10-10
Hi Jssizzle,

> **Jssizzle said:**
> I'd rather not have to retag all of them . . . I've never seen a program that does it well.

There is an option in the latest svn FFmpeg which I will admit I have not investigated *fully* to map tags from an input file to an output file. For example:

```
ffmpeg -i infile.m4a **[COLOR="Red"]-map_meta_data outfile.mp3:infile.m4a[/COLOR]** outfile.mp3
```

In the small usage I have made of this option it has worked well enough and I suspect it will be worth exploring for your purposes. Details concerning the svn FFmpeg can be seen here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

All the best,

Andrew

---

