---
title: "encode subtitles onto video"
date: 2009-07-26
forum: Multimedia Software
---

### Post by oiad on 2009-07-26
I have multiple files that are x264 or xvid, in avi's and mkv's, that have subtitles either within the container or as a separate file.  I would like to know if there is a good program to actually encode the subtitles into the video making them permanent in all players/devices.  Hopefully without sacrificing quality.  So any good recommendations??

Thanks

---

### Post by MepisReign on 2009-07-26
Avidemux will do that for you

sudo apt-get install avidemux

Also here is a video showing how to do it, please note that you can experiment with different settings

[http://www.youtube.com/watch?v=mNt6mEQ658s](http://www.youtube.com/watch?v=mNt6mEQ658s)

Hope this helps,


MepisReign

---

### Post by oiad on 2009-07-26
Thanks for the reply.  I already use avidemux so no problem there.  Is it actually hardcoding the subtitles into the film or just embedding them into the container?\

EDIT:  I tried one and it does hardcode it.  The answer was right under my nose the whole time.  Thanks a lot!

---

### Post by oiad on 2009-11-30
I found a CLI way of doing this using mencoder as well that is much quicker for .avi's.

```
mencoder file.avi \
-ovc lavc -oac mp3lame \
-sub file.srt \
-font “/usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf” -subfont-autoscale 2 \
-fps 'whatever'
-o file-sub.avi

```

---

### Post by VertexPusher on 2009-11-30
> **oiad said:**
> I found a CLI way of doing this using mencoder as well that is much quicker for .avi's.
1. It's not quicker.
2. It doesn't support SSA subtitles.

---

### Post by verweym on 2009-12-01
I have been trying to use avidemux to install subtitles for a while, no subtitles show up in the preview or the video afterwards.  I think I may have isolated the problem to the fonts.  When I click on the font window I get an error msg saying unable to locate folder or file.  Do I have to install fonts separately?  I really don't care what the font is I would be happy with a default.  Any help is appreciated.

---

