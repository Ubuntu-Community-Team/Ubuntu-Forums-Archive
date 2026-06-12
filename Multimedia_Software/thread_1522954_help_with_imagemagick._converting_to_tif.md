---
title: "help with imagemagick. converting to tif"
date: 2010-07-02
forum: Multimedia Software
---

### Post by youbantwo on 2010-07-02
Hi. I'm trying to convert a from a book I have as a .jpg into a .tif file so I can run tesseract-ocr on it. Here's what I'm trying
```
convert page.jpg -depth 2 page.tif
tesseract page.tif output -l fra
```

This should print out meaningful text but all it prints out is a comma. Am I converting the file incorrectly? I have the depth set to 2 because that's the highest I could set it for tesseract to accept it. (since ubuntu won't allow .tif files so go here for the .tif file it generated: *[http://filevo.com/zyi9bhlq71mq.html](http://filevo.com/zyi9bhlq71mq.html)*).

Thanks in advance

---

### Post by youbantwo on 2010-07-03
aaaaand shameless self-bump

---

