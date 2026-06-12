---
title: "Vid editing software that will flip the image"
date: 2010-12-04
forum: Multimedia Software
---

### Post by 98cwitr on 2010-12-04
My camera was mounted upside down on a drive today and I need to flip all frames in 3 clips...what software can I use to do this quickly and efficiently?

---

### Post by ajgreeny on 2010-12-04
Try the terminal command ```
convert -rotate 180 /path/to/files
```

EDIT:  Sorry ignore this, I didn't notice it was videos!  I think convert only works with pictures (stills).

---

### Post by ron999 on 2010-12-04
Hi
Check to see whether your version of ffmpeg has the **vflip** filter fitted.
Use this command to find out:- 
```
ffmpeg -filters
```

If the filter is listed then use a command something like this:-
```
ffmpeg -i in.avi -vf vflip out.avi
```

Information is here:- [http://www.ffmpeg.org/ffmpeg-doc.html#SEC91]("http://www.ffmpeg.org/ffmpeg-doc.html#SEC91")

---

### Post by 98cwitr on 2010-12-05
filter isn't listed. How can I install it? Btw, it's in .mov format, so quicktime bs.

---

### Post by ron999 on 2010-12-05
> **98cwitr said:**
> filter isn't listed. How can I install it?

Hi
It's not straightforward, I think that it's necessary to compile ffmpeg from source.

Probably less hassle if you use different software. Maybe Avidemux will do the job.
There's information here:- [http://voyager8.blogspot.com/2009/11/using-avidemux-to-rotate-video-movie-in.html]("http://voyager8.blogspot.com/2009/11/using-avidemux-to-rotate-video-movie-in.html")

If you decide to compile ffmpeg the guide is here:- [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264")

---

### Post by 98cwitr on 2010-12-06
thank you...Ill try that when I get home :)

---

### Post by 98cwitr on 2010-12-06
worked great. Thank you.

---

