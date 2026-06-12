---
title: "Remove Metadata From Pictures"
date: 2009-01-13
forum: Multimedia Software
---

### Post by Eviltechie on 2009-01-13
I've started a blog, and I want to add pictures. What is the best way to remove all the metadata in the pictures before I upload them?

---

### Post by DieB on 2009-01-14
> sudo apt-get install exif
cd to/folder/
exif --remove *


should do the trick

exiftran -d *

might do it too

---

### Post by Eviltechie on 2009-01-14
I did some searching and found jhead. I just had do cd to the directory and do jhead -purejpg *.

---

