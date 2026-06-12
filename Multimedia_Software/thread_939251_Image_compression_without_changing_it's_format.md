---
title: "Image compression without changing it's format"
date: 2008-10-05
forum: Multimedia Software
---

### Post by RuleMaker on 2008-10-05
Is there any free application which could compress the images size?
For example i have a picture in jpg format and it has 800 Kb, I want it to stay in jpg format but to compress it to be under 500 Kb (for example).
I used mogrify to change pictures size and format but I dont know how could I compress them.

---

### Post by ghantoos on 2008-10-05
You can try imagemagick:
```

sudo apt-get install imagemagick

```then just use this:
```

convert -quality 80 input.jpg output.jpg

```You can even resize at the same time:
```

convert -resize 50% -quality 80 input.jpg output.jpg

```Hope this helps,

Cheers,

---

### Post by jpkotta on 2008-10-05
I like to use the Gimp for this.  It has a very nice jpeg compression settings dialog.  It tells you how big the file will be.

---

### Post by RuleMaker on 2008-10-05
Ghantoos, thanks a lot, exactly what I needed!
Jpkotta, thanks for your reply too.

---

