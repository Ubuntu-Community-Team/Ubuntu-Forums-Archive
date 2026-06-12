---
title: "FFMPEG Thumbnailer"
date: 2012-01-02
forum: Multimedia Software
---

### Post by inkrypted on 2012-01-02
I have been Googling myself silly looking for a solution. I am using Ubuntu 11.10 with Unity and have installed FFMPEG Thumbnailer and no thumbnails. So after alot of research I found a script for FFMPEG Thumbnailer that goes into /usr/share/thumbnailers directory here it is.

[Thumbnailer Entry]
TryExec=ffmpegthumbnailer
Exec=ffmpegthumbnailer -s %s -i %u -o %o -c png -f -t 10
MimeType=video/flv;video/webm;video/mkv;video/mp4;video/mpeg;video/avi;video/ogg;video/quicktime;video/x-avi;video/x-flv;video/x-mp4;video/x-mpeg;video/x-webm;video/x-mkv;application/x-extension-webm;video/x-matroska;video/x-ms-wmv;video/x-msvideo;video/x-msvideo/avi;video/x-theora/ogg;video/x-theora/ogv;video/x-ms-asf;video/x-m4v;

With this in place and the old thumbnails deleted and Nautilus restarted as recommended in several other tutorials only a few of my videos and pictures have thumbnails?
Any help with this issue would be appreciated.

---

### Post by inkrypted on 2012-01-02
Finally stumbled across the solution here is the link in case anyone else has the same problem.
[http://www.hecticgeek.com/2011/11/how-to-make-ffmpegthumbnailer-work-in-ubuntu-11-10-oneiric-ocelot/](http://www.hecticgeek.com/2011/11/how-to-make-ffmpegthumbnailer-work-in-ubuntu-11-10-oneiric-ocelot/)

---

