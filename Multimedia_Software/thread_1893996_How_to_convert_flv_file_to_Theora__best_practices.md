---
title: "How to convert flv file to Theora : best practices"
date: 2011-12-11
forum: Multimedia Software
---

### Post by le_phoceen on 2011-12-11
Hi,

I already posted this message on the General Help forum, but I'm afraid it's more for this one.

I have a video file in the .flv format, which I would like to convert in  the Theora (.ogv) format (I prefer free open source format :grin:).

For that I type this command in the terminal :

```
ffmpeg -i myfile.flv myfile.ogv
```The video and audio streams  are correctly identified, but the conversion takes a very long time and  the resulting file in Theora is very heavy. Moreover, when I play it,  the audio quality is okay (I don't notice any difference with the  original) but the video quality is terrible :-k.

I would like to know if I may get better results by using additonal  options to the in the ffmpeg command and what are the recommended best  pratices in this kind of work.

Many thanks

---

### Post by FakeOutdoorsman on 2011-12-11
> **le_phoceen said:**
> I would like to know if I may get better results by using additonal  options to the in the ffmpeg command and what are the recommended best  pratices in this kind of work.

The default encoding settings for FFmpeg are not always very good, but they can be improved with a few options. Example:
```
ffmpeg -i input -vcodec libtheora -qscale 6 -acodec libvorbis -aq 5 output.ogv
```
The important options here are *qscale* and *aq*:
[list]
[*]**qscale** - adjust video quality. I believe the qscale range for libtheora is 0 to 10. A higher value is a higher quality. Use the lowest value that still has an acceptable quality.
[*]**aq** - adjust audio quality. Should be similar to the *q* option in *oggenc*. A higher value is higher quality. See the [Recommended Vorbis Encoder Settings](http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis#Recommended_Encoder_Settings) for more info on what values to use. Range is -2 to 10, but I'm not sure if FFmpeg can use the negative values.
[/list]

---

### Post by le_phoceen on 2011-12-12
Thank you very much FakeOutdoorsman :). I get much better results now.

---

### Post by andrew.46 on 2011-12-12
> **FakeOutdoorsman said:**
> 
[list]
[*]**qscale** - adjust video quality. I believe the qscale range for libtheora is 0 to 10.
[/list]


Certainly a grep through the FFmpeg source seems to confirm this. This comment in libavcodec/libtheoraenc.c:

```

/* to be constant with the libvorbis implementation, clip global_quality to 0 - 10

```

---

