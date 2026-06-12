---
title: "encoding video at low bitrates, any suggestions?"
date: 2012-03-22
forum: Multimedia Software
---

### Post by hurtstotalktoyou on 2012-03-22
Hey all.

I want to perform a (hopefully) simple task.  I have a bunch of high-quality (and hence LARGE) video files which I would like to convert to smaller, lower-quality videos for viewing on my Android device (using Moboplayer).  I've tried Avidemux, but I must be doing something wrong because it gives me larger-size files with lower-quality output.  I hear ffmpeg is good in command line.  But I don't currently speak ffmpeg.

So does anyone know a solution?  Preferably something I can do in a single command in Terminal?

Thanks!

---

### Post by shantiq on 2012-03-23
> **hurtstotalktoyou said:**
> Hey all.

I want to perform a (hopefully) simple task.  I have a bunch of high-quality (and hence LARGE) video files which I would like to convert to smaller, lower-quality videos for viewing on my Android device (using Moboplayer).  I've tried Avidemux, but I must be doing something wrong because it gives me larger-size files with lower-quality output.  I hear ffmpeg is good in command line.  But I don't currently speak ffmpeg.

So does anyone know a solution?  Preferably something I can do in a single command in Terminal?

Thanks!



ok there hurt


so yes ffmpeg perfect tool for this task


**try this for bulk**

> for f in *.wmv; do ffmpeg -i "$f" -b 400k -s cif  -ab 96k "${f%.wmv}.mp4"; done


**to try on single file**

> ffmpeg -i yourfile.wmv  -b 400k -s cif  -ab 96k yourandroidfile.mp4






i chose wmv but change to match your original extension

-b   is for video bitrate
-ab         audio bitrate
-s   is frame size   choose from


> -s size
           Set frame size. The format is wxh (ffserver default = 160x128, ffmpeg default = same as
           source).  The following abbreviations are recognized:

           sqcif
               128x96

           qcif
               176x144

           cif 352x288

           4cif
               704x576

           16cif
               1408x1152

           qqvga
               160x120

           qvga
               320x240

           vga 640x480

           svga
               800x600

           xga 1024x768

           uxga
               1600x1200

           cga 320x200

           ega 640x350

           hd480
               852x480

           hd720
               1280x720

           hd1080
               1920x1080




Personally would pick mkv as final extension but i [**see this**]("http://developer.android.com/guide/appendix/media-formats.html") only works on Android 4.0 or higher so i picked mp4 as i did not know what you have [CENTER][img]http://img824.imageshack.us/img824/2670/smilie201small.png[/img][/CENTER]

---

### Post by hurtstotalktoyou on 2012-03-24
Awesome!  Thanks so much!

For some reason the m4p extension didn't work, so I used mpeg instead.  Any further suggestions there?

Otherwise it worked great!  Thanks again!

---

### Post by shantiq on 2012-03-25
mp4 not m4p  :KS   [if that is the problem]

---

