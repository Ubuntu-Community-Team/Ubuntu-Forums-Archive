---
title: "Creating VOB Files with ffmpeg"
date: 2009-05-16
forum: Multimedia Software
---

### Post by Geffers on 2009-05-16
Using ffmpeg I know how to create DVD quality image files and have even altered the sound flags to get a file to play on a certain device.

The output file though is an mpg.

If I want a VOB type DVD setup is ffmpeg able to do this or do I need DVD authoring software.

Geffers

---

### Post by FakeOutdoorsman on 2009-05-16
VOB is based on based on MPEG-2 PS, so your mpg files may already work.  The easiest way to create a vob with FFmpeg is:
```
ffmpeg -i input.avi -target pal-dvd output.vob
```
or
```
ffmpeg -i input.avi -target pal-dvd output.mpg
```
Either one should work.  You could also use *-target ntsc-dvd*.  You may have to enable some encoders to get it to convert correctly:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Geffers on 2009-05-16
> **FakeOutdoorsman said:**
> VOB is based on based on MPEG-2 PS, so your mpg files may already work.  The easiest way to create a vob with FFmpeg is:
```
ffmpeg -i input.avi -target pal-dvd output.vob
```

You may have to enable some encoders to get it to convert correctly:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Thanks for quick reply.

My MPGs work fine when burnt to a DVD except on my Philips PVR, for some obscure reason it reports 'unknown data', as it does with JPGs. The file types are fine as is the media so I just want to try VOBs.

Geffers

---

