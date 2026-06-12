---
title: "How to convert .mov to mp4"
date: 2015-08-22
forum: Multimedia Software
---

### Post by satimis on 2015-08-22
Hi all,

I have .mov files download from IPhone.  Please advise the easy way converting them to .mp4

Thanks

Regards
satimis

---

### Post by andrew.46 on 2015-08-22
> **satimis said:**
> I have .mov files download from IPhone.  Please advise the easy way converting them to .mp4

Easy enough to do with FFmpeg as it is *probably* a simple container change however much depends on:

[LIST=1]
[*]The audio and video codecs in the existing mov container
[*]Your reason for changing the container
[*]
[/LIST]

The simplest commandline would be:

```

ffmpeg -i input.mov -map 0 -c copy output.mp4

```

Change the names and paths of input and output files to match your needs...

---

### Post by monkeybrain20122 on 2015-09-23
use ffmpeg 
```
ffmpeg -i file.mov -c copy out.mp4
```

Or you can use a gui called winff, available in the repo.

---

### Post by danielfed on 2016-07-28
Great! it worked.

---

