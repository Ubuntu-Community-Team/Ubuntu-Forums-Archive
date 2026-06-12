---
title: "ffmpeg won't compile all images in directory into video for stopmotionme drop"
date: 2012-04-23
forum: Multimedia Software
---

### Post by jarednielsen on 2012-04-23
I'm trying to compile a stop motion video using ffmpeg. I have 8000+ images. I run a command like this:
```

ffmpeg -i %04d.jpg -r 30 output.mp4

```
Everything is smooth up until about frame 6000 where it cuts off. The other 2000 are left out of the video.

Could there be something wrong with an image at that point that I'm not seeing?

Is this a limitation of ffmpeg?

Thanks!

---

### Post by Jose Catre-Vandis on 2012-04-23
I've used this command successfully in the past:

```
ffmpeg -r 25  -qscale 2 -i image%d.jpeg output1.mp4
```

where all files were like image01.jpeg

Check all your image filenames exactly fit the wildcard expression, this is usually the problem

You could also try making it in two halves if there is a file number limitation, then join them together with mkvmerge.

---

### Post by FakeOutdoorsman on 2012-04-23
> **jarednielsen said:**
> I'm trying to compile a stop motion video using ffmpeg. I have 8000+ images. I run a command like this:
```

ffmpeg -i %04d.jpg -r 30 output.mp4

```
Everything is smooth up until about frame 6000 where it cuts off. The other 2000 are left out of the video.

Could there be something wrong with an image at that point that I'm not seeing?

Is this a limitation of ffmpeg?

Thanks!
Can you show the console output too? It may have some useful information on the issue. Note that ffmpeg by default reads the input files at *-r 25*, so you may want to move your *-r 30* as an input option (before *-i input*). The output will then inherit the frame rate of the input. Otherwise ffmpeg may drop or duplicate frames when the input(s) and output(s) do not match frame rates.

> **Jose Catre-Vandis said:**
> I've used this command successfully in the past:
```
ffmpeg -r 25  -qscale 2 -i image%d.jpeg output1.mp4
```
I also often suggest using *-qscale* for MPEG-1/2/4 outputs, but be mindful that more recent ffmpeg (I'm not sure about the status of repository ffmpeg/avconv) now uses the encoder *libx264* by default for .mp4 output, and *-crf* should be used instead of *-qscale* if that is the case (the default value of *-crf 23* will be applied if you omit *-crf*). However, I can understand that syntax changes and such are hard/annoying to keep up with.

Also, you're applying *-qscale* as in input option (before *-i input*) although FFmpeg will probably understand that you're intending on using it as an output option (usually placed after *-i input.*), but option placement is important.

> **Jose Catre-Vandis said:**
> Check all your image filenames exactly fit the wildcard expression, this is usually the problem
Good suggestion.
> **Jose Catre-Vandis said:**
> You could also try making it in two halves if there is a file number limitation, then join them together with mkvmerge.
Alternatively you could use *cat* to pipe non-properly numbered (but still properly sequential) images to ffmpeg:
```
cat *.jpg | ffmpeg -f image2pipe -vcodec mjpeg -i - output
```

---

