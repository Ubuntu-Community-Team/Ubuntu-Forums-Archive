---
title: "Converting WMA to OGG or MP3 (just one song)"
date: 2009-01-10
forum: Multimedia Software
---

### Post by timzak on 2009-01-10
My wife bought some songs online and accidentally purchased a DRM encrypted WMA format for one of the songs.  Is there a way to convert it to MP3 or OGG, either on a Linux or Windows machine?  We can always re-purchase it as it was only 99 cents, but if there's an easy way to do this, I'm open to suggestions.  I've already tried dir2ogg and nautilus-script-audio-convert and had no luck.  I'm not even sure how the nautilus script is supposed to work as I see no right-click context menus related to it.

Thanks for any help.

---

### Post by timzak on 2009-01-11
*bump*

Anyone?  Is it not possible to do this?

I do have access to Windows machines if this is something that must be done in Windows.

---

### Post by FakeOutdoorsman on 2009-01-11
You can try ffmpeg.  This will use the native ogg vorbis encoder built in ffmpeg:
```
ffmpeg -i input.wma -acodec vorbis output.ogg
```
This will use libvorbis to encode:
```
ffmpeg -i input.wma -acodec libvorbis output.ogg
```
I suppose it doesn't make much of a difference which you use, but it is nice to have options.  Since a bitrate wasn't supplied ffmpeg will use the default of 64 kb/s.  You can change the audio bitrate with the *-ab* option, for example *-ab 128k*.

If you want to encode to mp3 with ffmpeg, you will need to install the package **libavcodec-unstripped-51** because Ubuntu's ffmpeg does not initially support this format due to it not being "free".  Then you can simply:
```
ffmpeg -i input.wmv -acodec libmp3lame -ab 128k output.mp3
```

---

### Post by timzak on 2009-01-11
Thanks, it doesn't seem to work.  I think it is the drm that is in this song.  I think there are some drm strippers for Windows, so I'll give that a shot before re-purchasing the song.

---

### Post by timzak on 2009-01-14
Could not figure out how to do it.  I just re-purchased the song in MP3 format.

---

### Post by FakeOutdoorsman on 2009-01-14
Curse you, DRM! The honest customer is the real victim when record labels proactively treat them all as criminals.

---

