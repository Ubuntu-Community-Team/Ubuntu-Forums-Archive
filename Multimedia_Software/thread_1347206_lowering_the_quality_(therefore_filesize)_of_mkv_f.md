---
title: "lowering the quality (therefore filesize) of mkv files"
date: 2009-12-05
forum: Multimedia Software
---

### Post by pythonscript on 2009-12-05
I have a 5 GB mkv file that I'd like to compress (as a video, not simply using a 7z archive or something to that effect) and I'm wondering if there's a straightforward way to do this. I have mkvtoolnix and mkvtoolnix-gui installed; would these be of assistance? Thanks for the help!

---

### Post by semitone36 on 2009-12-06
You could try [**handbrake**]("http://handbrake.fr/")

---

### Post by pythonscript on 2009-12-18
Can handbrake work with mkv files? I know it can work with avi files, but I wasn't sure if it supported mkv files or not.

---

### Post by SuperSonic4 on 2009-12-18
Should do, I've wrote to it before

perhaps ffmpeg would work

---

### Post by michael37 on 2009-12-18
I'd use ffmpeg.  
ffmpeg -i input.mkv -vcodec libx284 -acodec libfaac -b NEWVIDEORATE -ab NEWAUDIORATE output.mkv

Add [spice]("http://ffmpeg.org/ffmpeg-doc.html") for desired taste.

---

### Post by FakeOutdoorsman on 2009-12-18
> **michael37 said:**
> I'd use ffmpeg.  
ffmpeg -i input.mkv -vcodec libx284 -acodec libfaac -b NEWVIDEORATE -ab NEWAUDIORATE output.mkv

Add [spice]("http://ffmpeg.org/ffmpeg-doc.html") for desired taste.

This command won't work.  There is no *libx284* and it should be *libx264*, and if you are using a recent FFmpeg, you need to use a libx264 encoding preset.  Compile FFmpeg and x264 from source to get the best encoding quality.  Step-by-step instructions and some encoding examples:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

...or if you don't want to compile you can use FFmpeg from the repository but you need to enable some encoders:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

However, the link above is just slightly out of date.  If you are using Karmic I recommend installing the **libavcodec-extra-52** package from Medibuntu instead of the version from the Ubuntu repository.  The repository **libavcodec-extra-52** does not have AAC encoding and AMR encoding/decoding support.

---

