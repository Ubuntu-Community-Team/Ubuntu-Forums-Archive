---
title: "AVI to DVD.  I don't want a menu.  Just click, and burn if possible."
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by diablo75 on 2007-06-29
Any suggestions?

---

### Post by finite9 on 2007-06-29
```
ffmpeg -i your_avi_file -mbd rd -flags +trell -cmp 2 -subcmp 2 -g 100 -pass 1/2 -target pal-dvd output_file.mpeg
```

will create a high quality mpeg file from most any file you put in.

Following will create the DVD structure then create an ISO file which you can burn with Nero, Nautilus, K3B, Graveman etc etc etc:

```
dvdauthor -o /tmp/DVD/ --video=720x576+pal+16:9 --audio=ac3+en --file=output_file.mpeg
dvdauthor -o /tmp/DVD/ -T

mkisofs -dvd-video -o output_file.iso /tmp/DVD/
```

this applies to Fiesty version of Ubuntu and PAL.

---

