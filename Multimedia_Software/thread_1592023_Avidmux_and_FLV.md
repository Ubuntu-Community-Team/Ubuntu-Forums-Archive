---
title: "Avidmux and FLV"
date: 2010-10-10
forum: Multimedia Software
---

### Post by GrouchyGaijin on 2010-10-10
Hi,

I'm running Ubuntu 10.4.

I'm able to use Avidemux to put subtitles on a video file although I had to go through a lot of trial and error before I found settings that would actually encode.  Most settings resulted in immediate failure.

After I got the subtitles on my video I was able to use WinFF to convert that video (a form of an mpeg) into flv.

My question is I see that Avidemux lists flv as one of it's options.  It would be nice if I could use it to make the flash file instead of having to open another program.  The problem is that the configure box is grayed out under flv and the job fails instantly if I try to run it.

How can I figure out what is missing from Avidemux and how can I enable Avidemux to create flv files?

---

### Post by pixideps on 2011-10-14
wow - exactly the same issue with me ... avidemux opens flv files but cannot encode into flv?!?!
However, I've noticed that I did not have such problem with 2.5.2 version where I could have auto flv options ... while in 2.5.4 I cannot find flv encoder though I have installed it through ffmped ... wierd ...

---

### Post by GrouchyGaijin on 2011-10-14
I gave up and do it from the cli.  I added this to my bash_aliases file:
```

alias flv='ffmpeg -i foo1.avi -b 400000 -s qvga -acodec libmp3lame -ar 22050 bar.flv'

```

---

### Post by GrouchyGaijin on 2011-10-14
I gave up and do it from the cli.  I added this to my bash_aliases file:
```

alias flv='ffmpeg -i foo1.avi -b 400000 -s qvga -acodec libmp3lame -ar 22050 bar.flv'

```

---

