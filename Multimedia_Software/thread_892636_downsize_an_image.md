---
title: "downsize an image"
date: 2008-08-17
forum: Multimedia Software
---

### Post by ZeldaFan on 2008-08-17
How do you downsize a .gif animation in Ubuntu (presumably in GIMP)? I've tried just scaling down by oddly enough file size increases.

---

### Post by QkEterror on 2008-08-17
If you are not "afraid" of KDE you could use Kolourpaint. I find it to be really easy and useful software for these kinds of things. If you are afraid gThumb might be an option for you.

For the GIMP I can't help you unfortunately.

---

### Post by ZeldaFan on 2008-08-18
Kolourpaint seems pretty easy to use, but unfortunately it cannot save in the .gif format so it doesn't help me in this scenario. Thanks for the reply though.

---

### Post by finer recliner on 2008-08-18
install imagemagick from the repos,

then check out here for an example of how to resize with it:

[http://www.imagemagick.org/Usage/resize/#resize](http://www.imagemagick.org/Usage/resize/#resize)

(there is A LOT of other functionality available as well)

---

### Post by cor2y on 2008-08-18
Imagemagick is great for resizing image files but i have never tried to resize an animated gif with it.

For GIMP.
After your gif is open, go to Image->Scale Image and resize from there.
But you are not done yet if you wish to keep your gif animated then select File->Save As and below all the dialogue of where the file is to be saved select the gif extension from the file type drop down box.
Once gif is selected , pick save as animation and leave everything as is in the next window that pops up and you should now have a smaller size gif both in resolution and file size.

---

