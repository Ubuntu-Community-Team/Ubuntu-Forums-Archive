---
title: "How do i make a you tube vid from an mp3 and ogv?"
date: 2009-07-18
forum: Multimedia Software
---

### Post by Naiki Muliaina on 2009-07-18
As the title asks, ive read some video editing documentation but cant seem to get it either in my head or to work. 

I have a video that i want to put a soundtrack to then upload it to Youtube. How do i go about doing this?

---

### Post by FakeOutdoorsman on 2009-07-18
With FFmpeg you can combine them without losing any quality since you're just copy and pasting the streams into an *OGV container*:
```
ffmpeg -i input.ogv -i audio.mp3 -acodec copy -vcodec copy output.ogv
```
You may also be able do it with Avidemux if you want a graphical interface, but I have no experience with that.

---

### Post by sfantus1 on 2009-07-29
you could try openshot it is just great .... still in development but usable :) and verry easy to use

---

