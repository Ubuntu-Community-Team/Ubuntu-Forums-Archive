---
title: "Mux 2 .ogg files. One is video (theora) the other is audio (vorbis)"
date: 2007-12-13
forum: Multimedia Production
---

### Post by MetalMusicAddict on 2007-12-13
Like the title says I have 2 oggs I need to combine into one that contains both the audio and video. (vorbis/theora)

For the life of me I can figure this out. :(

---

### Post by MetalMusicAddict on 2007-12-13
I'll answer my own thread here:
```
 gst-launch filesrc location=VIDEO.ogg ! oggdemux ! theoraparse ! oggmux name=mux ! filesink location=OUTPUT.ogg filesrc location=AUDIO.ogg ! oggdemux ! vorbisparse !  mux.
```

Everything in that is needed. Replace things in CAPS with your source and output files.

So as long as you don't have to worry about sync. that will mux a OGG/Theora and a OGG/Vorbis file together into one. Make sure you're CD'ed into the dir of your source files.

---

### Post by eggdeng on 2008-02-16
Many thanks to MMA for posting this. I would just add that to run gst-launch, I had to supply  the version number 
```
gst-launch-0.10 
```
which I found using the locate command.

---

