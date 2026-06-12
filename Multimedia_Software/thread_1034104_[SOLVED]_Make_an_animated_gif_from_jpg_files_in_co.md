---
title: "[SOLVED] Make an animated gif from jpg files in command line"
date: 2009-01-08
forum: Multimedia Software
---

### Post by afbase on 2009-01-08
suppose i have a set of images in a directory (image1.jpg, image2.jpg, image3.jpg,...).  how can i make an animated gif that repeats the order (image1.jpg, image2.jpg, image3.jpg,...) from command line?   thanks

---

### Post by FakeOutdoorsman on 2009-01-08
The package imagemagick can do this:
```
convert -delay 100 -loop 0 image*.jpg animation.gif
```
I believe my delay value will wait 1 second before moving to the next frame.

---

### Post by afbase on 2009-01-11
Thanks:popcorn:

---

### Post by SL666 on 2009-05-12
Anyone know how to make this more compressed? (currently the result is simular to the included files)

---

### Post by el_itur on 2010-12-10
> **SL666 said:**
> Anyone know how to make this more compressed? (currently the result is simular to the included files)

Mogrify the files first:

```
$ mogrify -resample 72x72 -resize 256x256 *.JPG
```

keep in mind that this will overwrite the original files so it would be wise to do that with a copy

---

### Post by pony1912 on 2013-04-20
The quality of gif animation created with ImageMagick is realy good - [http://www.youtube.com/watch?v=OFusYizJ-bA](http://www.youtube.com/watch?v=OFusYizJ-bA)

---

### Post by overdrank on 2013-04-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

