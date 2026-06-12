---
title: "Anyone know of a good ffmpeg guide?"
date: 2008-05-24
forum: Multimedia Software
---

### Post by YAOMTC on 2008-05-24
The --help for ffmpeg is overwhelming, and the documentation isn't thorough enough. Does anyone know of a good ffmpeg guide? There's a lot I can do with it, I know, but it's not at all newbie-friendly.
> **"YAOMTC"]Well, I've come up with this.

```
ffmpeg -i benny_lava.avi -s 72x54 -t 14 -r 25 -pix_fmt rgb24 benny_lava.gif
```

The problem, though, is that somehow the GIF ends up being 7 seconds instead of 14 said:**
> http://www.hotlinkfiles.com/files/1378072_stle9/benny_lava.avi[/url]
[http://www.hotlinkfiles.com/files/1378073_joppz/benny_lava.gif](http://www.hotlinkfiles.com/files/1378073_joppz/benny_lava.gif)

---

### Post by FakeOutdoorsman on 2008-05-25
It also doesn't help that the option names change often between revisions.  I have a few good resources available:
[ffmpeg doc]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html")
[ffmpeg faq]("http://ffmpeg.mplayerhq.hu/faq.html")
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")
[Encode Video for iPod with ffmpeg]("https://wiki.ubuntu.com/iPodVideoEncoding?highlight=%28ipod%29")
[iPod video guide]("http://rob.opendot.cl/index.php/useful-stuff/ipod-video-guide/")

What are you trying to do with ffmpeg?

---

### Post by warp99 on 2008-05-25
Here's a guide to some of the advanced features of ffmpeg:

[http://www.itbroadcastanddigitalcinema.com/ffmpeg_howto.html](http://www.itbroadcastanddigitalcinema.com/ffmpeg_howto.html)

---

### Post by YAOMTC on 2008-05-25
Well, I've come up with this.

```
ffmpeg -i benny_lava.avi -s 72x54 -t 14 -r 25 -pix_fmt rgb24 benny_lava.gif
```

The problem, though, is that somehow the GIF ends up being 7 seconds instead of 14; thus, double the speed.

Also, how does the GIF, which is much smaller in frame size than the ~650KB AVI and without audio, end up 1.5MB?

[http://www.hotlinkfiles.com/files/1378072_stle9/benny_lava.avi](http://www.hotlinkfiles.com/files/1378072_stle9/benny_lava.avi)
[http://www.hotlinkfiles.com/files/1378073_joppz/benny_lava.gif](http://www.hotlinkfiles.com/files/1378073_joppz/benny_lava.gif)

---

### Post by gandaran on 2008-05-25
there is a frontend gui for ffmpeg, have a look
[http://www.winff.org/](http://www.winff.org/)

---

### Post by YAOMTC on 2008-05-25
> **gandaran said:**
> there is a frontend gui for ffmpeg, have a look
[http://www.winff.org/](http://www.winff.org/)
Thanks. Good for future use.

Unfortunately, useless for this. It doesn't convert to GIF.

The problem listed in my previous post still remains.

---

### Post by FakeOutdoorsman on 2008-05-28
> **YAOMTC said:**
> Well, I've come up with this.

```
ffmpeg -i benny_lava.avi -s 72x54 -t 14 -r 25 -pix_fmt rgb24 benny_lava.gif
```

The problem, though, is that somehow the GIF ends up being 7 seconds instead of 14; thus, double the speed.

I'm not sure why it does this, but this would be a good question to ask on the [ffmpeg-user mailing list]("http://ffmpeg.mplayerhq.hu/mailinglists.html").  There are very knowledgeable users there, but they may ignore your question if you don't follow proper protocol: use the latest svn version of ffmpeg, show your full ffmpeg command (like you did above), show the full response of ffmpeg, don't "top-post", and don't hijack threads.  If you need help compiling ffmpeg, this thread should help: [HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095").

> **YAOMTC said:**
> Also, how does the GIF, which is much smaller in frame size than the ~650KB AVI and without audio, end up 1.5MB?

GIF isn't optimized as a movie codec such as mpeg4.  You can compare them to a butterknife and a sword in terms of video encoding compression efficiency.

---

