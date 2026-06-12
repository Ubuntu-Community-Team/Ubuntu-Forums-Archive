---
title: "pdf converter?"
date: 2009-01-21
forum: Multimedia Software
---

### Post by gardengxc on 2009-01-21
hi I have a pdf file witch I want to crack into jpeg or bitmaps or even pngs. what software could I use to exponentiate the process over cut and paiste (its about 1200 images):popcorn:

---

### Post by pnutzh4x0r on 2009-01-21
> **gardengxc said:**
> hi I have a pdf file witch I want to crack into jpeg or bitmaps or even pngs. what software could I use to exponentiate the process over cut and paiste (its about 1200 images):popcorn:


You can use the convert tool from imagemagick as so:

```
convert "file.pdf" "new_files.png"
```

It will produce a new file for each page.  You can change png to any format you want (bmp/jpg, etc.)

---

### Post by gardengxc on 2009-01-23
> **pnutzh4x0r said:**
> You can use the convert tool from imagemagick as so:

```
convert "file.pdf" "new_files.png"
```

It will produce a new file for each page.  You can change png to any format you want (bmp/jpg, etc.)

about how long should this take? I had it going for about an hour yesterday and the terminal gave no sign of doing anything.
nvmd it must've froze yesterday it took about 10 minutes today.

---

### Post by kelargo on 2009-01-24
Is there a tool that can identify the images in a PDF and just extract those images?

---

