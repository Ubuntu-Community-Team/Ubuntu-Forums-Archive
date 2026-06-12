---
title: "resize with mogrify"
date: 2010-02-03
forum: Multimedia Software
---

### Post by sombrancelha on 2010-02-03
I want to batch resize some pictures, and they are all either 3264x2448 or 2448x3264.

I want to resize them to 1600x1200 or 1200x1600 - how to make mogrify recognize which pictures it should do what?

EDIT: Discovered!

```

mogrify -resize 49.0196% *

```

---

### Post by kaibob on 2010-02-03
> **sombrancelha said:**
> I want to batch resize some pictures, and they are all either 3264x2448 or 2448x3264.

I want to resize them to 1600x1200 or 1200x1600 - how to make mogrify recognize which pictures it should do what?
I assume you want to resize the 3264x2448 pictures to 1600x1200 and the 2448x3264 pictures to 1200x1600. Although not precisely what you want, the easiest solution is to use the resize command with a percent, as in the following:

```
mogrify -resize 50% *.png
```

Otherwise, you will have to write a shell script to first identify the current image size and then to resize to the desired image size.

---

### Post by bryanlarsen on 2011-03-21
There's an easier way: `mogrify -resize 1600x1600` does exactly what you want.   That specifies that you want the maximum size for both dimensions to be 1600, and maintain the aspect ratio, so the other dimension will always be the correct 1200.

---

### Post by tomek_wap on 2011-11-08
or simply use the first pixel size, i.e. mogrify -resize 1024 -format jpg *
the other side of photo will do automatically/proportionally.

but I guess if you have portrait and landscape photos in same folder you would need to separate them from each other before batch resizing.

mogrify works good and fast, but I'm still looking for a GUI based app for batch resizing.

Phatch is unusable ...

---

