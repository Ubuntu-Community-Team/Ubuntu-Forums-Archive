---
title: "Tool To Add An ID3 Tag To Music Without Any Tag At All"
date: 2011-09-03
forum: Multimedia Software
---

### Post by dniMretsaM on 2011-09-03
Apparently ripping audio from a video with FFmpeg removes any ID3 tags. I like my music to be very organized so I always go in and check the tags and change whatever needs to be done (add pictures, fix spelling, whatever). I recently got some new music so yesterday and today I went through all my music's ID3 tags and fixed everything (a lot more were off than I realized), but I noticed three songs that had no tag (not just empty). When I tried to add one with Kid3-qt, it gave me an error. So anybody know of a tool that will allow me to add an ID3 tag, preferably version 2.4, to those songs? It doesn't have to be able to edit them. Also, I would really like a CLI tool if possible.

---

### Post by andrew.46 on 2011-09-03
Mind you a new enough copy of FFmpeg should be able to copy meta tags across with the following option:

```

-map_metadata outfile[,metadata]:infile[,metadata]  set metadata information of outfile from infile

```

although be aware that there are several different permutations of this command depending on the version of FFmpeg you are using. I would strongly suggest the most recent version:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

You should also be able to manually add meta data using the following syntax:

```
-metadata string=string  add metadata
```

This info extracted using *ffmpeg -h | grep -i meta*...

---

### Post by dniMretsaM on 2011-09-03
I think I figured out the problem. When I did the transcoding I didn't specify a codec and it came out as "Ogg FLAC Audio" instead of the normal "Ogg Audio."

---

### Post by dniMretsaM on 2011-09-04
Posting to confirm that that was the problem. I re-encoded them correctly by specifying the libvorbis codec and all is well. Marking as solved.

---

