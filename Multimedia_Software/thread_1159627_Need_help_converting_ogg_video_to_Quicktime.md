---
title: "Need help converting ogg video to Quicktime"
date: 2009-05-14
forum: Multimedia Software
---

### Post by jakev383 on 2009-05-14
Hey all - I have a video conversion question if anyone would like to answer it for me.
I recorded some video using gtk-recordmydesktop and want to convert the video to Quicktime. I have both ffmpeg and mencoder installed, but need to options I need to use for either/or to convert the video. 
The original videos are in ogg format:
```

[theora @ 0x9f4cba0]544 bits left in packet 81
[theora @ 0x9f4cba0]7 bits left in packet 82
Input #0, ogg, from 'part1.ogg':
  Duration: 00:13:56.66, start: 0.000000, bitrate: 848 kb/s
    Stream #0.0: Video: theora, yuv420p, 1280x1024,  9.00 tb(r)
    Stream #0.1: Audio: vorbis, 22050 Hz, mono, s16, 66 kb/s

```

How can I convert this file to Quicktime (.mov) while retaining the quality? I used a framerate of 9 (maybe 8?) when recording since it's not an action movie or anything, so a similar framerate for the output is fine.
I tried to convert it with no options used and while it did convert it, the quality was rather horrible.
Thanks in advance!

---

### Post by andrew.46 on 2009-05-14
Hi jakev383,

> **jakev383 said:**
> 
```


Input #0, ogg, from 'part1.ogg':
  Duration: 00:13:56.66, start: 0.000000, bitrate: 848 kb/s
    Stream #0.0: Video: theora, yuv420p, 1280x1024,  9.00 tb(r)
    Stream #0.1: Audio: vorbis, 22050 Hz, mono, s16, 66 kb/s

```

How can I convert this file to Quicktime (.mov) while retaining the quality? 

By default FFmpeg converts to mpeg4 video and aac sound and [the documentation]("http://ffmpeg.mplayerhq.hu/compat.html") claims that this means the files will be able to be played with Apple QuickTime Player v6.5.2. If you are happy with this you could simply try:

```
ffmpeg -i part1.ogg -vcodec mpeg4 **[COLOR="Red"]-sameq[/COLOR]** -acodec libfaac output.mov
```

Hopefully your copy of FFmpeg is set for aac? If not have a look at:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

This conversion is pretty basic but may be all you are after? The encoding can be a lot more adventurous depending on what software / hardware you are planning to play these files back on, and with more pleasing results as well I suspect. Any particular reason for the quicktime thing?

All the best,

Andrew

---

### Post by jakev383 on 2009-05-15
Thanks for the answer!
I'll give that a shot later today.

Why Quicktime? I'm making some videos targeted for a combination of Windows and Mac users and Quicktime (or mpeg) seems like the most common codec denominator between the two. Linux seems to install it by default on a lot of distros (or at least make it very easy to get) these days.
Thanks again!

---

### Post by andrew.46 on 2009-05-15
Hi jakev383,

> **jakev383 said:**
> Why Quicktime? I'm making some videos targeted for a combination of Windows and Mac users and Quicktime (or mpeg) seems like the most common codec denominator between the two. Linux seems to install it by default on a lot of distros (or at least make it very easy to get) these days.

Well perhaps the 'lowest common denominator' approach might be the best one then :-). If it all works out you might want to have a look at the following:

3.14 Which are good parameters for encoding high quality MPEG-4?
[http://ffmpeg.mplayerhq.hu/faq.html#SEC26](http://ffmpeg.mplayerhq.hu/faq.html#SEC26)

I personally use the following with mpeg4 transcoding, drawn from the reference above,:

```
-mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300
```

and this gives the image quality a *huge* boost. And of course consider 2 pass encoding: lots of room for experimentation!

Andrew

**Edit:** I have corrected a few glaring errors in the the encoding details above...

---

### Post by FakeOutdoorsman on 2009-05-15
> **andrew.46 said:**
> 
I personally use the following with mpeg4 transcoding, drawn from the reference above,:

```
-mbd rd -flags +4mv+aic -trellis 2 -cmp 2 -subemp 2 -g 300
```

and this gives the image quality a *huge* boost. And of course consider 2 pass encoding: lots of room for experimentation!

Andrew
More recent revisions of FFmpeg use *+mv4* instead of *+4mv*.  I'm not sure when that change occurred, but you can find out which one to use with:
```
ffmpeg -h | egrep "4mv|mv4"
```
Also, I believe *-subemp* is a typo for *-subcmp*.

---

### Post by andrew.46 on 2009-05-15
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> More recent revisions of FFmpeg use *+mv4* instead of *+4mv*.  I'm not sure when that change occurred, but you can find out which one to use with:
```
ffmpeg -h | egrep "4mv|mv4"
```

Glad you caught that one, I have a couple of scripts to alter now :-).

> Also, I believe *-subemp* is a typo for *-subcmp*.

Sigh.... in fact that is a fairly inglorious typo..... thanks for catching my errors! I have altered the original post to protect anybody who has not read down this far.

Andrew

---

