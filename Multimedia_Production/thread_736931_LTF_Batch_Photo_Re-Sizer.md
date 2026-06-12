---
title: "LTF Batch Photo Re-Sizer"
date: 2008-03-27
forum: Multimedia Production
---

### Post by indytim on 2008-03-27
Title pretty much says it all.  I have 170+ jpeg's in  a folder that I need to resize down.  Ideally, would like to identify a separate destination folder for the re-sized photo's.  Do we have such a critter on Lx?

Thanks,

IndyTim
p.s.  Using GIMP

---

### Post by FrankVdb on 2008-03-29
Phatch

Don't think it's in the repos but you can download a ready-made .deb file from the maker's site:

[http://photobatch.stani.be/](http://photobatch.stani.be/)

Great piece of software!

---

### Post by cotcot on 2008-03-29
Image Magick : see 'mogrify' command

---

### Post by jamesgate on 2008-03-29
+1 for Image Magick.  "convert IMG_3383.JPG -resize 50% tucker.jpg" brought a 1.9MB image to 443K, and very quick.

---

### Post by Creative2 on 2008-03-29
fuoco tools.. can do that ..or 

with bash

for f in *.png; do convert  -resize 800x600 "$f" "${f%.png}.jpeg"; done

---

### Post by munkyeetr on 2008-03-29
+1 for phatch.

---

### Post by stani on 2008-04-01
> **FrankVdb said:**
> Phatch

Don't think it's in the repos but you can download a ready-made .deb file from the maker's site:

[http://photobatch.stani.be/](http://photobatch.stani.be/)

Great piece of software!

Phatch will be in the repos from the next Ubuntu Hardy!

---

