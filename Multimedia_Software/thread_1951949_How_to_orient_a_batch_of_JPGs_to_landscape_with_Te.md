---
title: "How to orient a batch of JPGs to landscape with Terminal tool?"
date: 2012-04-03
forum: Multimedia Software
---

### Post by jarednielsen on 2012-04-03
I have 8000+ images I need to orient in landscape to compile into a stop motion video (with ffmpeg, naturally). The problem is some are already in landscape and some are in portrait (horizontal vs. vertical). When I strip or dump and/or apply an automatic orientation the exif data the images retain their orientation. If I use a rotate command, all of the images rotate. There are too many to do this one by one so I need a batch solution. I've spent too many hours now mucking about with Exiftran and Mogrify without luck so I am appealing to the community. Is this possible? If so, how? Thoughts? Thanks!

---

### Post by SeijiSensei on 2012-04-03
One approach is to use a bash script that iterates over the files, uses Imagemagick identify to determine the orientation, then uses Imagemagick convert to rotate the ones in portrait.  Here's a start:

```

#!/bin/sh

mkdir -p new

for f in *.JPG
do
   # extract the size of the image
   SIZE=$(identify $f | awk '{print $3}')

   case $SIZE in 
     
       480x640|1200x1600|1920x2560)
           # portrait --do nothing
           cp $f new
           ;;

       *)
           # landscape -- rotate file
           convert -rotate 90 $f new/$f   
   
   esac

done

```

This places a copy of all the images in the "new" subdirectory.  You'd run this script while in the directory containing your images.  If all the files in that directory are images, you can replace "*.JPG" with just "*".  You'll need to include all the portrait dimensions you're going to find in your images in the first entry.

---

### Post by FakeOutdoorsman on 2012-04-03
Instead of Imagemagick's *convert* another good tool to rotate is jpegtran. This will perform a lossless "perfect" rotation, or a lossy rotation if perfect is not possible.
```
jpegtran -rotate 90 -perfect $f > new/$f || djpeg $f | pnmflip -r90 | cjpeg -quality 85 > new/$f
```
jpegtran alone usually works for me. I don't recall ever having to use the *djpeg | pnmflip | cjpeg* chain. These tools are all part of the **libjpeg-progs** package.

---

### Post by jarednielsen on 2012-04-04
The bash script worked like a charm. Jpegtran looks very useful, too. I'll spend some time playing around with it.  

Thanks!

---

### Post by SeijiSensei on 2012-04-04
> **jarednielsen said:**
> The bash script worked like a charm. Jpegtran looks very useful, too. I'll spend some time playing around with it.  

Thanks!

You're welcome.  I'm glad I could cobble something together for you.

---

