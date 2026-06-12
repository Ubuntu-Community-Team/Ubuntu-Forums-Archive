---
title: "Minimizing Images !!"
date: 2011-05-02
forum: Multimedia Software
---

### Post by &#342;à&#939; &#7887;ƒ &#1186;&#972;&#961;&#281; on 2011-05-02
Hi

I have around 150 images and each one of them has the size of 3.3 MB.

I need to shrank them to small size. What I need is, is there any way to minimize them in few minutes ?

Thank you

---

### Post by nothingspecial on 2011-05-02
Assuming they are all have a .jpg extension, navigate to the folder they are in and do


```
sudo apt-get install imagemagick
```

```
for p in *.jpg; do convert -resize 50% $p new_$p; done
```

That will halve them

This will convert all the .jpgs in that folder, so if you have others you don't want to resize move the ones you do to a new folder first.

---

