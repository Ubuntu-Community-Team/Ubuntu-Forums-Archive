---
title: "Adding blank tape to video files"
date: 2008-01-28
forum: Multimedia Production
---

### Post by ExquisiteDeadGuy on 2008-01-28
Hey everyone, I have about 30 short video files I need to add about 2 second of black space to the beginning and end of to prevent them from getting chopped when copying to DVD. Can anybody recommend a way to do this on Gutsy either manually or automatically?

Thank you.

---

### Post by FakeOutdoorsman on 2008-01-28
Do you already have the black video?  What format are you encoding from?  You can probably do this with ffmpeg:

```
cat blackvideo originalvideo blackvideo | ffmpeg -f vob -i - -vcodec copy -acodec copy outputvideo.vob
```

For this to work all of the footage needs to have the same parameters (bitrate, frame rate, size, etc).  If you have the black video already, you can prepare it with ffmpeg if the above command doesn't work:

```
ffmpeg -i blackvideo -target ntsc-dvd output.vob
```

You can also use "-target pal-dvd".

---

### Post by ExquisiteDeadGuy on 2008-01-28
Any idea how I can generate this blank video? It seems like something that would be simple, but it's always the simple stuff that trips me up :)

---

### Post by FakeOutdoorsman on 2008-01-28
First make a plain black jpg image that is the same size as your video then try this:
```
ffmpeg -loop_input -i black.jpg -vframes 60 -an blackvideo.vob
```

or maybe this:
```
ffmpeg -loop_input -r ntsc -f image2 -i black.jpg -vframes 60 -an -target ntsc-dvd black.vob
```

Modified from: [[Ffmpeg-user] Adding blank frames]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-December/005813.html").

---

### Post by ExquisiteDeadGuy on 2008-01-29
I was able to get that black video generated, but got all kinds of codec errors with ffmpeg when trying to merge it. I googled a whole lot and fixed those, but the generated video was without sound.

While working with the black video file you showed me how to make, I figured out the app Kino in the Add/Remove programs list has an FX function that will let you generate video of a solid color and append it to video files. This worked like a charm.

Thanks!

---

