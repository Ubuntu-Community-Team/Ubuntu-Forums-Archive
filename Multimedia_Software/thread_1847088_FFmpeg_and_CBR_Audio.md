---
title: "FFmpeg and CBR Audio"
date: 2011-09-20
forum: Multimedia Software
---

### Post by dodle on 2011-09-20
Is there a way to get ffmpeg to output constant bitrate audio when encoding with libvorbis? libmp3lame defaults to cbr but libvorbis is vbr.

```
ffmpeg -f alsa -i hw:0,0 -acodec libvorbis -ab 128k -vn audio.ogg
```

---

### Post by ron999 on 2011-09-20
> **dodle said:**
> Is there a way to get ffmpeg to output constant bitrate audio when encoding with libvorbis? 

Hi
Vorbis is a **VBR** codec.
Use a command like this:-
```
ffmpeg -f alsa -i hw:0,0 -acodec libvorbis -aq 4 -vn audio.ogg
```

The **-aq** "quality" values and "nominal" bitrates are shown in the chart here:- [http://en.wikipedia.org/wiki/Vorbis#Technical_details]("http://en.wikipedia.org/wiki/Vorbis#Technical_details")

---

### Post by dodle on 2011-09-20
> **ron999 said:**
> Vorbis is a **VBR** codec.

Thanks, I didn't know this.

---

