---
title: "How to convert all thumbnails to black and white?"
date: 2009-02-03
forum: Multimedia Software
---

### Post by simo on 2009-02-03
Hi, I need some tool that will convert all thumbnails to black and white.
Now i'm trying with convert, but with -monochrome option it's not what i really wanted.
Tnx for your help!

---

### Post by icheyne on 2009-02-03
[http://www.imagemagick.org/Usage/color/#grayscale](http://www.imagemagick.org/Usage/color/#grayscale)

convert  test.png  -colorspace Gray   gray_colorspace.png

---

### Post by simo on 2009-02-03
Tnx!

Now I need to figure out how to convert 17k+ images to grayscale with keeping filenames.(without creating new one)

---

### Post by kaibob on 2009-02-03
> **simo said:**
> Tnx!

Now I need to figure out how to convert 17k+ images to grayscale with keeping filenames.(without creating new one)
You need to explain a bit more what you want to do. For example, do you want to:

* Overwrite the existing files.

* Put the new files in a different directory than the existing files.

* Keep both the existing and new files in the same directory and retain the existing file names. In this case, the new file names will have to be changed in some way.

---

### Post by simo on 2009-02-04
I need to overwrite existing files(thumbnails) so thumbnails will show in greyscale instead of colored ones...

---

### Post by icheyne on 2009-02-04
I haven't tested this, but it should work:

```
mogrify -type Grayscale *.jpg
```

---

### Post by simo on 2009-02-04
Cool!

Thank you! It works!

---

