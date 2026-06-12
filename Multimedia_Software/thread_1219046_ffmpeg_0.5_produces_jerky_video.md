---
title: "ffmpeg 0.5 produces jerky video"
date: 2009-07-21
forum: Multimedia Software
---

### Post by hazelnut on 2009-07-21
I already posted this ti the ffmpeg users list, but thought I'd try here as well.

I never had a problem until upgrading my ubuntu box from 8.10 to 9.04 and now ffmpeg produces jerky video when I encode from a progressive scan dvd source.

My command line:

    nice -n 15 ffmpeg -i "$filename" -vcodec libx264 -vpre max \
    -b 1200k -maxrate 1500k -r 23.976 \
     -s 640x352 -f mp4 -async 800 \
    -acodec libfaac -ab 192k -ar 48000 -ac 2 \
    -y $outfilename

The older version of ffmpeg produced very smooth results.  The latest version produces jerky results.  Anyone have any ideas? Or anyone experience similar results?

Thanks.

---

### Post by FakeOutdoorsman on 2009-07-22
Show the full FFmpeg output.  Why are you declaring a frame rate (-r 23.976)?

---

### Post by hazelnut on 2009-07-22
I specify -r 23.976 because if I don't, ffmpeg will try to encode as 29.97 and that's not what I want.  I'm encoding an NTSC progressive scan DVD.  

I realize ffmpeg has no ivtc option, but I have always had good results with the aforementioned command line.

Anyway, I have traced the problem to the difference between SVN-r18958 and SVN-r18959.  I am about to post a message to the developer mailing list.

---

### Post by FakeOutdoorsman on 2009-07-22
These may be of interest to you:

```
$ svn log -r 18959 svn://svn.mplayerhq.hu/ffmpeg/trunk
------------------------------------------------------------------------
r18959 | bcoudurier | 2009-05-26 16:14:32 -0800 (Tue, 26 May 2009) | 3 lines

Fix off by one offset with fetch_timestamps, pts_parser_problem.mpg.
Patch by Wolfram Gloger, wmglo at dentm dot med dot uni-muenchen dot de.

------------------------------------------------------------------------
```

[[FFmpeg-devel] [PATCH] change parser to fetch timestamps in correct order](http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2009-May/069799.html)

---

