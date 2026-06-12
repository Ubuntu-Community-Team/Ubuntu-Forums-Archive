---
title: "Is there a faster way to convert video formats?"
date: 2011-06-05
forum: Multimedia Software
---

### Post by sofasurfer on 2011-06-05
I am using winff to convert recorded tv shows to mpg. Trouble is that it takes 3 hours or mor to convert a 1 hour show. The shows that I am converting are recorded from kaffeine which makes them .m2t files...what ever the heck that is. I am converting them because when I put them on my flash drive and try to watch them on a particular tv with a usb port, they do not play.
So, am I missing a simpler process or something?

---

### Post by papibe on 2011-06-05
Sadly, video conversion is one the most CPU intensive tasks around. However with more information more solutions would appear.

What's the original format and resolution?
Which formats your TV can play (codecs, container and resolution)?

Regards.

---

### Post by sofasurfer on 2011-06-05
The original format was stated above as .mt2. Don't know anymore than that. But you answered good enough. Video processing takes a long time. Just wanted to make sure the problem was not me.
Thanks.

---

### Post by papibe on 2011-06-05
I believe m2t are either VC1 or h.264.

If your TV plays mp4 for example, you don't need conversion but repack the content in a different container. That could be done in a matter of minutes (10-15 in my experience).

Then, it is relevant to know which formats your TV can reproduce.

Regards.

---

### Post by lovinglinux on 2011-06-05
I use Handbrake. Depending on the configuration, I can convert a 90 min video in 15-20 minutes on a Core 2 Duo with Ubuntu 32bit.

These are the settings I use:

**Video Codec:** MPEG-4 (FFMpeg)
**Constant Quality**: 3

In Picture Settings >> Filters:

**Deinterlace:** Fast

The rest I use pretty much at default.

---

### Post by sofasurfer on 2011-06-05
It appears that the tv can play mp4.
Can you please give me a brief explaination of "repack the content in a different container"? 
Thanks.

---

### Post by papibe on 2011-06-06
It involves extracting the video and audio stream of the m2t into 2 separate files. Then merging them together into a mp4 file. It would be similar to convert mkv to mp4. This is an [example ]("http://ubuntuforums.org/showthread.php?t=879680&highlight=mkv+mp4")of that.

Since it implies using ffmpeg and the command line, I think it would be interesting to try another GUI tools as suggested by lovinglinux. Handbrake is a very good one, so is Arista.

Regards.

---

### Post by sofasurfer on 2011-06-06
I just installed handbrake. The deinterlace option is not to be found in picture settings. I will look further. But for right now I am going to go convert. I will let you know how it goes.

---

### Post by sofasurfer on 2011-06-06
I just converted a 2 hour show with handbrake. It seems to have done it in about 2 hours. About the same time to convert it as the length of the show. A bit faster than winff. And at least you have a ata (approx time of arrival) for when it will be done.
I like it. Thanks.

---

### Post by Thewhistlingwind on 2011-06-06
Use a ram drive. :popcorn:

Just be sure to save state afterwards.

---

### Post by lovinglinux on 2011-06-06
> **sofasurfer said:**
> I just installed handbrake. The deinterlace option is not to be found in picture settings. I will look further. But for right now I am going to go convert. I will let you know how it goes.

[[IMG]http://www3.picturepush.com/photo/a/5815531/220/5815531.png[/IMG]](http://picturepush.com/public/5815531)

> **sofasurfer said:**
> I just converted a 2 hour show with handbrake. It seems to have done it in about 2 hours. About the same time to convert it as the length of the show. A bit faster than winff. And at least you have a ata (approx time of arrival) for when it will be done.
I like it. Thanks.

The time will depend on the resolution and compression of the original source. It takes about 15 to 20 minutes to transcode a 90 minutes DVD and 45 minutes (estimated) to transcode a 135 minutes video with 1280 x 528 resolution.

I suppose your source has even bigger resolution and the image is a raw dump from the TV card, so it expected to take longer. You could use Handbrake resizing options to reduce the output size. I am not sure if it will help, because the resizing could add an extra overhead, but worth a try.

---

### Post by sofasurfer on 2011-06-06
Man, I swear it wasn't there before:)

---

### Post by lovinglinux on 2011-06-06
> **sofasurfer said:**
> Man, I swear it wasn't there before:)

:-)

You need to check the Deinterlace checkbox before you can see the Deinterlace options.

---

