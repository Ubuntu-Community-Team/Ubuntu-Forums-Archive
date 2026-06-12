---
title: "Make movie from single frames?"
date: 2007-05-12
forum: Multimedia Production
---

### Post by whitefort on 2007-05-12
Hi - apologies for my ignorance - I don't even know the proper name of the kind of software I'm looking for.

I have an animation program which only produces output in the form of a directory containing still images of every frame in the final scene.

What I need is something that will 'glue' these all together into a final movie - avi, mp3, or whatever.

I presume Linux must HAVE something, but because I don't know the proper name for this sort of program, my searches haven't worked out too well.

I would be grateful if someone could point me in the general direction of what I'm looking for.  If it's in the Ubuntu repositories, that would be even better!  Thanks!

---

### Post by handaxe on 2007-05-12
Avidemux ([http://www.getdeb.net/search.php?keywords=avidemux](http://www.getdeb.net/search.php?keywords=avidemux)) will open a sequence of jpgs and they can then be saved as a video.

img-0001.jpg, img_0002.jpg, img_0003.jpg etc.

Edit: just tested it - it works with jpg and mpg.

HA

---

### Post by whitefort on 2007-05-12
Excellent, that's exactly what I was looking for.  I've just tested it and it works fine with my output files.

MANY  thanks!!!

---

### Post by cylon359 on 2007-05-21
If you want something scriptable, you can use transcode... just make a text file with the filenames of all your input frames, and then do something like:

transcode -i imlist.txt -x imlist,null -y mjpeg,null -z -g 640x480 --use_rgb -o output.avi

(I think that will work - if you read the manpage, it explains all the options)

---

