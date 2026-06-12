---
title: "Flac to mp3?"
date: 2010-11-20
forum: Multimedia Software
---

### Post by chrispche on 2010-11-20
Hi this might be an easy question. How do you convert a flac file to mp3? Well I have an entire album to convert actually.

Thanks in advance.

---

### Post by whoop on 2010-11-20
[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+convert+flac+to+mp3&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+convert+flac+to+mp3&ie=utf-8&oe=utf-8)

---

### Post by ron999 on 2010-11-20
> **chrispche said:**
> ... How do you convert a flac file to mp3? Well I have an entire album to convert actually.


Easiest way with Ubuntu is 
Applications > Sound & Video > **Sound Converter**

---

### Post by stefangr1 on 2010-11-20
> **chrispche said:**
> Hi this might be an easy question. How do you convert a flac file to mp3? Well I have an entire album to convert actually.

Thanks in advance.

I always use this little script for that:
```
#!/bin/sh

for file in */*.flac
do
	flac -d "$file"
	lame -V 0 "${file%\.*}.wav" "${file%\.*}.mp3"
	rm "${file%\.*}.wav" "${file%\.*}.flac"
done

exit 0
```

Note that this script also removes the original!

---

### Post by ajgreeny on 2010-11-20
I prefer ffmpeg, as it gives you so many possibilities for control of the quality.  Perhaps lame does as well, but I have never used that on its own, always through ffmpeg.

You also may need the following lib files from medibuntu to enable mp3 encoding in ffmpeg.
libavcodec-extra-52 (4:0.5.1-1ubuntu1+medibuntu1)
libavdevice-extra-52 (4:0.5.1-1ubuntu1+medibuntu1)
libavfilter0 (4:0.5.1-1ubuntu1)
libavformat-extra-52 (4:0.5.1-1ubuntu1+medibuntu1)
libavutil-extra-49 (4:0.5.1-1ubuntu1+medibuntu1)

 To convert audio flac file to mp3.
```
ffmpeg -i file.flac -acodec libmp3lame -ab 128k file.mp3
```       
-acodec is the audio codec libmp3lame
-ab is audio bitrate

Or:
```
ffmpeg -i file.flac -acodec libmp3lame -aq # file.mp3
```
-aq # is vbr quality - 1(high) - 9(low)

---

### Post by chrispche on 2010-11-20
Thank you all.

---

