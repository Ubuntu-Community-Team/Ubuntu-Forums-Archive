---
title: "Hmmm... Huge PNG File!"
date: 2010-10-22
forum: Multimedia Software
---

### Post by ks07 on 2010-10-22
Hey guys,

So I've recently downloaded a png file, and it's filesize is over 100MB! (It's a very high res map from a minecraft server, if you're interested). Anyway, because it's so large, Eye of Gnome refuses to open it, and GIMP freezes while loading. Is there any way to view this file? Maybe a command line program that can slice it up into smaller chunks?

I'm currently running pngcrush on the file to try and reduce it's size - but I don't expect it will make a huge difference. So, any suggestions? :popcorn:

---

### Post by Old *ix Geek on 2010-10-22
Its size shouldn't be a problem with the GIMP. In the GIMP, under Preferences | Environment, try adjusting the "maximum new image size" and the "maximum filesize for thumbnailing" and see if that helps.

---

### Post by ks07 on 2010-10-23
Thanks

The good news is - the image opened after some time. The bad news - too much swapping to the hard disk meant actually scrolling through the image was nigh on impossible! Oh well...

---

### Post by MooPi on 2010-10-23
You could try feh.  ```
feh -F **.png
``` Will try to render or scale to full screen.
Worth a try.

---

### Post by glennrp on 2010-10-23
> **ks07 said:**
> 
I'm currently running pngcrush on the file to try and reduce it's size - but I don't expect it will make a huge difference. So, any suggestions? 

pngcrush might reduce the filesize but it won't affect the dimensions or resolution of the image, so probably won't help you.

You could try using ImageMagick or GraphicsMagick to scale the image down or to cut it into tiles.

---

