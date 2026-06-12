---
title: "Encoding CDs to MP3 using Soundjuicer (Bad Bitrate info)"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by Major_Kong on 2007-06-14
I'm using soundjuicer to encode to mp3, but whatever quality settings i use, the displayed bitrate is always 32 kBps. It's not the real bitrate but it's weird. 
If i use the lame CLI to do the encoding the displayed bitrate is more accurate.

The pipeline i use:
```
audio/x-raw-int,rate=44100,channels=2 ! lame quality=0 vbr=4 vbr-quality=3 ! id3v2mux

```

Any thoughts ?

---

### Post by fredj on 2007-06-16
Install Grip and use it in the GUI. It is fully configurable and will let you see exactly what you are doing.

---

### Post by Major_Kong on 2007-06-18
I guess i'll have to... but it's too bad, soundjuicer has a better overall interface...

EDIT: Yup, it's a gstreamer bug: [http://bugzilla.gnome.org/show_bug.cgi?id=322461](http://bugzilla.gnome.org/show_bug.cgi?id=322461)

Soundjuicer should allow external encoders...

---

### Post by Major_Kong on 2007-06-19
Ok, after some reading i found out that it's a good idea to include xingmux in the pipeline. (i have no clue why it's not the default...)

So i get something like this:

```
audio/x-raw-int,rate=44100,channels=2 ! lame quality=0 vbr=4 vbr-quality=3 ! xingmux ! id3v2mux
```

Now the displayed bitrate is the avg. (except on Audacious that now displays 32 kbps...oh, well you gain some, you loose some...)

The displayed track length is still variable. No ideas on this too ?

---

