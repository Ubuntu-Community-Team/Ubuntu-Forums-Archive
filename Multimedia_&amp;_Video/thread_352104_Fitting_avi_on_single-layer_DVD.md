---
title: "Fitting avi on single-layer DVD"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by Dubbayoo on 2007-02-02
I have a 700MB AVI file that I'm trying to convert to DVD format using tovid. However it converts into two files - one 4.2GB and one 933MB file. Is there anyway to force tovid, or any other app, to make the video fit onto a single 4.7GB DVD?

---

### Post by kebes on 2007-02-02
Tovid has lots of commandline options ([see tovid manual page]("http://tovid.sourceforge.net/manpages/tovid.html")). For instance you can add the option "-quality N" (where N is a number from 1 to 10) to change quality (hence filesize). Use a lower number to decrease quality (and size).

You can play with the number to achieve the best quality for the size you want. You can also use "-vbitrate" for better control.

---

### Post by wxnker on 2007-02-18
I use DeVeDe for this if you'd like a GUI solution with the possibility to see the file size, set the DVD disk size and see a preview, before conversion.

---

### Post by amgeex on 2007-02-24
Try this:

```
tovid -kdvd -quality 10 -in your_video.avi -out your_video
```

This will create a dvd compliant mpeg2 video file, but encoded with a different technique, resulting in lower file sizes. Check the tovid wiki and kvcd.net for more info.

---

