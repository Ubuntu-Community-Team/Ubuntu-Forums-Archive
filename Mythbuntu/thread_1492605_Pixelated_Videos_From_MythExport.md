---
title: "Pixelated Videos From MythExport"
date: 2010-05-24
forum: Mythbuntu
---

### Post by tom purl on 2010-05-24
I'm using the default version of ffmpeg, mythexport, and Ubuntu 10.4.  When I try to export my videos into a format that I can watch with my laptop, they are very, very pixelated.  Here are my settings:

```
[Foobar_De_Roobarb]
removeCommercials=1
codec=xvid
extension=
sizeX=640
sizeY=480
aspect="4:3"
videoBR=1000
device=laptop
threads=
podcastName="Foobar De Roobarb"
deletePeriod=
audioBR=192
audioChannels=
ffmpegArgs="-y -acodec libmp3lame -ab 192 -vcodec libxvid -b 1000 -mbd 2 -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -s 640x480 -deinterlace -aspect 4:3"
deinterlace=1
```

Those are similar to the settings that I used to use with nuvexport.

Is there anything I can do to improve the picture?  I'm thinking about compiling a newer version of ffmpeg, but I worry about how that will affect tovid and Pitivi.

Thanks!

Tom Purl

---

### Post by picbits on 2010-05-25
Have you tried increasing your VideoBR from 1000 to something higher ?

1000 seems a little on the low side to me.

---

### Post by sydneysuder on 2010-08-31
The resolution (648*480) will also give you pixelation if you go full screen on a laptop. At that resolution you have to watch it in a window if you don't want pixelation

---

