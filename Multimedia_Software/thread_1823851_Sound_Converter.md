---
title: "Sound Converter"
date: 2011-08-12
forum: Multimedia Software
---

### Post by motermouth15 on 2011-08-12
I am running ubuntu server on a headless machine. I was wondering what sound converters are out there that i could run through ssh being that i don't have a keyboard or mouse hooked up to my machine. My goal is to get everything converted to MP3 because my MPD crashes whenever it runs mp4. Thanks for all of the help!!

---

### Post by papibe on 2011-08-12
[ffmpeg]("http://fosswire.com/post/2007/11/using-ffmpeg-to-convert-to-mp3/") works in the command line, perfect for non gui interfaces.

Regards.

EDIT: it is in the repositories. To install it:
```
$ sudo apt-get update
$ sudo apt-get install ffmpeg
```

---

### Post by motermouth15 on 2011-08-12
Thank you soo much!!

---

### Post by FakeOutdoorsman on 2011-08-12
You'll need to enable the mp3 encoder, libmp3lame, in the repository FFmpeg (Ubuntu switched to libav as of Natty):
```
sudo apt-get install libavcodec-extra-52
```
More info: [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by motermouth15 on 2011-08-12
So now i have 10,000 some music files in a folder thats organized in subfolders. How can i make it convert them all no matter what types they are to mp3 and delete the old versions?

---

