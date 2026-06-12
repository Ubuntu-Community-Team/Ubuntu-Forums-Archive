---
title: "How to do this moving effect?"
date: 2014-02-26
forum: Multimedia Software
---

### Post by lonekingc4 on 2014-02-26
Hi,

I am using Ubuntu 12.04 (32 bit). This question is not entirely about Ubuntu, but maybe it is somehow.

I am trying to do a small video slideshow, and there is an effect that I want to do, but I cannot find a good way of doing it. It is simply this: there is a still image and the screen will just "read" the image. I mean, the picture will just slide through the capture frame. It's hard to explain. Here is a demo of the simple effect: [http://youtu.be/5uegOl8G6Uw](http://youtu.be/5uegOl8G6Uw)

As you can see, the effort was bad, the image was not still and was shaking.

I have tried the following:

1. Selected an area of the screen using RecordMyDesktop, started the record and dragged the image. (This was how the demo was made)
2. Used LibreOffice Impress to make a Fly-in animation, but I cannot get the right position to select on the screen using RecordMyDesktop (selecting from the small preview is really annoying)
3. Tried altering some settings in the Layout menu of a clip in OpenShot, but could not figure out how to achieve the exact effect.

So, is there a way of doing this smoothly (without having too much video editing skills)?

Thanks.

---

### Post by lonekingc4 on 2014-02-28
Never mind. Managed to do it with JavaScript (making the picture slide on a web page and then capturing with RecordMyDesktop). Kind of worked for me :)

---

### Post by Pinoy Tux on 2014-03-01
I use Inkscape to create titles and import them in an OpenShot project.  Then it's just a matter of setting the titles to animate from right to left (or whatever direction it needs to go).

---

### Post by FakeOutdoorsman on 2014-03-02
You can also try the [overlay video filter](http://ffmpeg.org/ffmpeg-filters.html#overlay) with some [arithmetic expressions](http://ffmpeg.org/ffmpeg-utils.html#Expression-Evaluation) in ffmpeg if you want a command line solution.

---

### Post by vanadium on 2014-03-03
If all you want is a slide show with the camera moving over the slides ("Ken Burns" effects), then PhotofilmStrip can be recommended. Specifically dedicated to that job, and very easy to use.

---

### Post by lonekingc4 on 2014-03-05
> **Pinoy Tux said:**
> I use Inkscape to create titles and import them in an OpenShot project.  Then it's just a matter of setting the titles to animate from right to left (or whatever direction it needs to go).
Thanks. I used InkScape before, but didn't know it could do that.

---

### Post by lonekingc4 on 2014-03-05
> **FakeOutdoorsman said:**
> You can also try the [overlay video filter]("http://ffmpeg.org/ffmpeg-filters.html#overlay") with some [arithmetic expressions]("http://ffmpeg.org/ffmpeg-utils.html#Expression-Evaluation") in ffmpeg if you want a command line solution.
Thanks. Sounds a bit complex to do the entire thing with only command line. But worth a try I guess.

---

### Post by lonekingc4 on 2014-03-05
> **vanadium said:**
> If all you want is a slide show with the camera moving over the slides ("Ken Burns" effects), then PhotofilmStrip can be recommended. Specifically dedicated to that job, and very easy to use.
Wow, thanks for the official name. It's great :D

---

