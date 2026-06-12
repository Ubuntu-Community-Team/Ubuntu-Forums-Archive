---
title: "Digikam Broken"
date: 2008-08-21
forum: Multimedia Software
---

### Post by cj100570 on 2008-08-21
I've noticed that under Hardy digikam no longer converts photos into an mpeg slideshow. Whenever I try it immediately says that the process completed when nothing actually happens. Anyone else noticed this or have a fix? here's the output I get when I try to make a video slideshow;

THE COMMAND LINE IS :

images2mpg --with-gui  -f SVCD -n NTSC -S 420mpeg2 -d 10 -t 2 -c 000000 -T /tmp/kde-cj/kipi-mpegencoderplugin-14500/ -M /usr/bin -I /usr/bin -o "/home/cj/output.mpg" -i  "/home/cj/Pictures/Personal/Kenya/img_0008.jpg"  "/home/cj/Pictures/Personal/Kenya/img_0009.jpg"  "/home/cj/Pictures/Personal/Kenya/img_0010.jpg"  "/home/cj/Pictures/Personal/Kenya/img_0011.jpg" 
-----------------------------------------------
Initialising...

-----------------------------------------------

EXIT STATUS : encoding process finished successfully.

---

### Post by ajhunt on 2008-09-30
> **cj100570 said:**
> I've noticed that under Hardy digikam no longer converts photos into an mpeg slideshow. Whenever I try it immediately says that the process completed when nothing actually happens. Anyone else noticed this or have a fix? here's the output I get when I try to make a video slideshow;

THE COMMAND LINE IS :

images2mpg --with-gui  -f SVCD -n NTSC -S 420mpeg2 -d 10 -t 2 -c 000000 -T /tmp/kde-cj/kipi-mpegencoderplugin-14500/ -M /usr/bin -I /usr/bin -o "/home/cj/output.mpg" -i  "/home/cj/Pictures/Personal/Kenya/img_0008.jpg"  "/home/cj/Pictures/Personal/Kenya/img_0009.jpg"  "/home/cj/Pictures/Personal/Kenya/img_0010.jpg"  "/home/cj/Pictures/Personal/Kenya/img_0011.jpg" 
-----------------------------------------------
Initialising...

-----------------------------------------------

EXIT STATUS : encoding process finished successfully.
Hi!

Had the same problem and found that mgp123 was missing which is available in the repositries or by 
> sudo apt-get install mpg123

Hope this helps!

---

### Post by nudge on 2008-11-18
I had the same problem, no mpeg slideshow from Digikam. I tried installing mpg123, but Digikam still will not work.  Also tried mgp123, I do not think this is a valid call. I have Digikam on another computer and it will make slideshows, ah the wonders of Linux! Thanks

---

