---
title: "Sound-Juicer Questions"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by Major_Kong on 2007-06-03
I'm trying to use Sound-juicer to rip a CD to mp3, but i'm having a little trouble... the default settings work right but i wish to use a little different ones...

So, sound-juicer uses gstreamer to do the encoding, but does the gstreamer ugly plugin uses the external liblame library or not ?


PS: Soundjuicer uses cdparanoia to extract the tracks from the cd, right ?

---

### Post by steeleyuk on 2007-06-03
Yes, Ugly uses the liblame0 library (well the Multiverse variant depends on it anyway)

Also, Sound Juicer depends on libcdparanoia0.

---

### Post by Major_Kong on 2007-06-03
Yes, but does it use liblame0 to do the encoding? I installed v.3.97 of liblame0, so i want to make sure it's being used.

But assuming liblame0 is being used, how do i encode to a V5 (~130 kbps) mp3 ? What's the syntax ?

From the CLI i know how to this (lame -V 5 --vbr-new  "infile") but from sound-juicer i have no idea.

---

### Post by diebels on 2007-06-03
```
gst-inspect-0.10 lame
``` shows you syntax

gstreamer lame is in plugins-ugly-multiverse

Use gconf-editor since sound-juicer profile editor is broken. Edit /system/gstreamer/0.10/audio/profiles/mp3

---

### Post by Major_Kong on 2007-06-04
Thx.

I used the following pipeline.
```

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc quality=0 vbr=4 vbr-quality=5 ! id3v2mux
```

But something weird happens. Even if i change the vbr-quality to 2, the displayed bitrate of the mp3 is always 32 kbps. It's not the real bitrate but it's very strange. By using the command line (cdparanoia and lame) i get different results...

A gstreamer bug ?


EDIT: Does anyone know if the developer of sound-juicer is considering adding external encoder (other than gstreamer) support ?

EDIT2: How can i tell if liblame0 is being used to encode ?

---

### Post by Major_Kong on 2007-06-04
> **Major_Kong said:**
> 

EDIT2: How can i tell if liblame0 is being used to encode ?

Found out on my own. Rolled back to v.3.96.1 of liblame0 and encoded again. There is no difference between the mp3 i had encoded earlier...

---

### Post by Major_Kong on 2007-06-08
> **Major_Kong said:**
> Thx.

I used the following pipeline.
```

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc quality=0 vbr=4 vbr-quality=5 ! id3v2mux
```

But something weird happens. Even if i change the vbr-quality to 2, the displayed bitrate of the mp3 is always 32 kbps. It's not the real bitrate but it's very strange. By using the command line (cdparanoia and lame) i get different results...

A gstreamer bug ?


No thoughts on this ?

---

### Post by vanadium on 2007-08-29
This might be a late "thought" but it might be usefull. Perhaps the current command line does produce mp3's with no valid vbr mp3 header. I have seen gstreamer pipelines that include  ! xingmux. This might be needed to have a correct vbr mp3 header. After adding this, your command line would look like:
```

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc quality=0 vbr=4 vbr-quality=5 ! xingmux ! id3v2mux

```

---

### Post by pedja_portugalac on 2008-05-13
> **vanadium said:**
> This might be a late "thought" but it might be usefull. Perhaps the current command line does produce mp3's with no valid vbr mp3 header. I have seen gstreamer pipelines that include  ! xingmux. This might be needed to have a correct vbr mp3 header. 
It's not late for me. Thank You very much for this (xingmux). Now I think I have reached the best VBR quality, for the smallest file I have ever seen, and the sound is greatissimo. 

This is my gstreamer-lame-pipeline: 

```

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc quality=0 mode=0 vbr=4 vbr-quality=0 preset=extreme ! xingmux ! id3v2mux

```

It sounds really great and tags are correct now. Thanks ones again. :lol:

---

