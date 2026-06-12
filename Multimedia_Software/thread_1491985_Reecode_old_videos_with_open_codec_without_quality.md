---
title: "Reecode old videos with open codec without quality loss possible?"
date: 2010-05-24
forum: Multimedia Software
---

### Post by blaster32 on 2010-05-24
Hi,

I have a lot of old video footage around that, I am ashamed to say, I encoded with heavily proprietary codecs like DivX and such during the dark ages (aka. the Windows Times).

Now, I would like to redeem myself from the mistakes of my past by re-encoding everything into open formats.
Since those videos are often not of the best quality (poor camera, poor codecs, poor knowledge), I do not want to loose more quality in the process.

So, to avoid any more mistakes in the future, I would be glad if someone could answer me some of the following questions:
1. Is it even possible to re-encode those movies into something like x264/vp8/theora without loosing any more quality?
2. What tools should I use for that? Command line is actually preferred.
3. What would be the most desirable format to have? I'm thinking about x264 in Martroska with ogg Auto. Is there anything better suited?

Thanks,
Markus

---

### Post by Detonate on 2010-05-24
See 
```
man ffmpeg
```

and 

```
ffmpeg -formats
```

to see the supported formats

---

### Post by andrew.46 on 2010-05-25
Hi Markus,

> **blaster32 said:**
> 
1. Is it even possible to re-encode those movies into something like x264/vp8/theora without loosing any more quality?

Personally I would leave the old movies as they are and make a decision about a suitable format for your new movies. Even with the most skilled transcoding there are compromises.

> 2. What tools should I use for that? Command line is actually preferred.

The best choice here is FFmpeg and for Ubuntu this is the best guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

> 3. What would be the most desirable format to have? I'm thinking about x264 in Martroska with ogg Auto. Is there anything better suited?

There is an interesting article here:

Google Open Sources VP8 Codec
[http://alien.slackbook.org/blog/google-open-sources-vp8-codec/](http://alien.slackbook.org/blog/google-open-sources-vp8-codec/)

which speaks at some length about how 'free' x264 actually is. My own thought is that if you are after the most open of codecs theora is what you need and the easiest transcoder is ffmpeg2theora. Many will disagree :).

All the best,

Andrew

---

