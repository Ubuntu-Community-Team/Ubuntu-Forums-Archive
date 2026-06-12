---
title: "Resize images in place with extension"
date: 2017-07-14
forum: Multimedia Software
---

### Post by david-oldcolo on 2017-07-14
I have several thousands of images across a slew of folders in Linux.  I need to be able to create thumbnails recursively, in their respective folders, so I can copy only the thumbs (tar or zip recursively)  and maintain the folder structure so I can find them again.
 
 
 Reason for this is I need to transfer the thumbs and folder structure to another laptop so my missus can view them, searching for images going back 15 years.   
 
 
 Any ideas on how I can do this?  If I can convert to thumbs with a say, Filename001-sized.jpg, where the "-sized" is added to each thumb, I can go tearing through and create a tarball recursively using a wildcard of course.  Anyone have a better way of doing this?  I need to recreate this on a separate computer or android device, hence why.  tx

---

### Post by CatKiller on 2017-07-15
ImageMagick is a command-line utitility to manipulate images. I've never used it personally, but I'd imagine that there are plenty of tutorials in how to use it. It is often used by webservers for exactly the task you are doing: automatically generating thumbnails from a disparate collection of different images.

---

### Post by SeijiSensei on 2017-07-15
If you have any bash shell skills, it's pretty easy to write a short script to iterate over the images in a directory and create thumbnails with ImageMagick convert.  Something like this:
```

#!/bin/bash
# height and width of images in pixels
HEIGHT=1080
WIDTH=1920
# height and width of thumbnails
THEIGHT=108
TWIDTH=192

mkdir -p thumbnails

for f in *.jpg
do
   convert -format png -define jpeg:size=${HEIGHT}x${WIDTH} $f  -auto-orient  -thumbnail ${THEIGHT}x${$TWIDTH}  thumbnails/$f.png
done

exit 0

```

See the examples here for details: [http://www.imagemagick.org/Usage/thumbnails/#creation](http://www.imagemagick.org/Usage/thumbnails/#creation)

This creates PNG thumbnails for all the JPEGs in the current directory and stores them in a "thumbnails/" subdirectory.

---

### Post by david-oldcolo on 2017-07-16
Thank you SeijiSensei,  My bash scripting skills are rusty at best... hence why I come here and ask.  Very much appreciated that you replied.  I will give your script a run and see if it works.  Am sure it will.  Mainly, I really appreciate you taking the time to reply.  Most don't..

---

### Post by david-oldcolo on 2017-07-16
> **CatKiller said:**
> ImageMagick is a command-line utitility to manipulate images. I've never used it personally, but I'd imagine that there are plenty of tutorials in how to use it. It is often used by webservers for exactly the task you are doing: automatically generating thumbnails from a disparate collection of different images.

Tx for your reply.  Yes, I have imagemagick and all the associated tools installed.  Was hoping that someone might have or know of a script that fits the bill.   Will give the one script that was posted a try.  I have over 150,000 images (pro camera, I don't just take snaps for the heck of it), but now have run into the need to have someone else work thru the images on a separate system.  The time it takes to do this online is impossible.  So will see if the above script will work.  tx for replying.  Much much appreciated.

---

### Post by SeijiSensei on 2017-07-16
Try the convert command on a specific file to see if it works as expected.  You'll need to replace $f with a file name like myphoto0001.jpg and ${HEIGHT}, etc. with actual values.

---

### Post by ymbride on 2017-07-19
modifier - resize 50% * .png this using for resize converting for ubuntu.,

---

