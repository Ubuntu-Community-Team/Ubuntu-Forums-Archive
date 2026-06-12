---
title: "batch convert all mp3s to ogg"
date: 2009-10-04
forum: Multimedia Software
---

### Post by kehon on 2009-10-04
I have a music library full of mp3 and I recently looked up ogg again and found that contrary to my beliefs ogg was better than mp3. I would like to convert all mp3s in my music library to ogg because all of the devices I play them on support ogg and lack space enough space. How can I convert all of the mp3 files in my library to ogg but I need them to be converted to a resonable rate because some mp3s are variable or constant bit rates and a lot of them have different kbps values such as 128 and 320. Is there a program that can do this for me and keep the rates at a reasonable amount so if its one rate its converted to a rate in ogg based on that.

---

### Post by ikacer on 2009-10-04
converting mp3 to ogg will only reduce the sound quality because both are lossy codecs. If you really want ogg vorbis files (and in my experience ogg is the best format currently available with AAC a close second), I suggest you convert them from a lossless format, like WAV or FLAC.

If you still want to convert them, oggenc is probably your best choice. For example, if you wanted to change all mp3 files in a directory to 192 ogg you could use:
```
oggenc -q6 *.mp3
```

however, varying the output bitrate by file based on the mp3s bitrate would be rather complicated. I doubt there are any programs to do this as it is generally not a good idea to do, but if you are really hellbent on this you could always write a script to do it.

---

### Post by size_XXM on 2009-12-09
For **batch** conversion I'd suggest mp32ogg (it's in the repository). It's a perl script that takes minimum (or no) parameters (I only set quality and the directory), uses the oggenc you'd use by the previous suggestion anyway and best of all, preserves tags.

---

### Post by kehon on 2009-12-09
sorry but i forgot to post in reply because I decided not to looking at the fact that ogg is lossless and mp3 is lossy so any conversion would probably make the sound worse

---

### Post by imtheguru on 2009-12-09
> **kehon said:**
> sorry but i forgot to post in reply because I decided not to looking at the fact that ogg is lossless and mp3 is lossy so any conversion would probably make the sound worseBoth encoding formats are lossy.

---

### Post by kehon on 2009-12-09
sorry must have been confusing ogg with FLAC and lossy to lossy makes more since now as to why I didn't choose it

---

### Post by MartyBuntu on 2009-12-09
You will not gain any quality converting from mp3 to OGG. The source dictates the standard and the conversion itself will introduce "loss".

It's impossible for the output OGG to be of better quality than the original mp3.

---

### Post by andrew.46 on 2009-12-11
Hi Marty,

> **MartyBuntu said:**
> You will not gain any quality converting from mp3 to OGG. The source dictates the standard and the conversion itself will introduce "loss".

True enough but whenever I have transcoded in a similar fashion neither my crap computer speakers or my cheap ipod clone sound any different :).

Andrew

---

