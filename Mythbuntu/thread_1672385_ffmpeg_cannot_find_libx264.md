---
title: "ffmpeg cannot find libx264"
date: 2011-01-20
forum: Mythbuntu
---

### Post by linuxhippy on 2011-01-20
In mythbuntu 10.04 I built ffmpeg with divx capability and removed the ffmpeg that came with the system.  I see that 10.10 has the x264 library and ffmpeg but ffmpeg gives this error:

Unknown encoder 'libx264'

This is the command I use to convert nuv files to mkv divx files:

ffmpeg -i /recordings/LiveTV/1065_20110107070257.nuv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 22 -threads 0 -g 100 -aspect 16:9 -async 1 /recordings/goldenvoice.mkv

How can I make ffmpeg recognise libx264 without rebuilding it in 10.10?

---

### Post by FakeOutdoorsman on 2011-01-20
> **linuxhippy said:**
> In mythbuntu 10.04 I built ffmpeg with divx capability and removed the ffmpeg that came with the system.  I see that 10.10 has the x264 library and ffmpeg but ffmpeg gives this error:

Unknown encoder 'libx264'
If you're using FFmpeg from the repository you'll need to enable some additional encoders. See **Option C** in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)


> **linuxhippy said:**
> This is the command I use to convert nuv files to mkv divx files:
```
ffmpeg -i /recordings/LiveTV/1065_20110107070257.nuv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 22 -threads 0 -g 100 -aspect 16:9 -async 1 /recordings/goldenvoice.mkv

```
"DivX" generally refers to the MPEG-4 Part 2 encoder. Your example command is making H.264 video and AAC audio in a MKV container.

---

### Post by linuxhippy on 2011-01-21
I used synaptic and installed x264.  I'm not sure what you mean by ./configure...I did updatedb and then looked for any conf files for ffmpeg and x264 and didn't find any.  Where would this file be?

---

### Post by FakeOutdoorsman on 2011-01-21
I assumed that you were compiling. Your original post wasn't clear that you are using FFmpeg from the repository.  Also, I confused 10.10 with 11.04, so I guess you can disregard my post.  I'll rewrite it.

**Edit:** I've updated the previous post.

---

### Post by linuxhippy on 2011-01-21
nice-that worked well (option C) and was a whole lot easier than trying to build ffmpeg from source like I did in 10.04.  Thanks!

---

