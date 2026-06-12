---
title: "Program to convert .jp2 to tiff"
date: 2016-05-02
forum: Multimedia Software
---

### Post by luckystar3 on 2016-05-02
Hello all,
does anyone know of a program that could convert a .jp2 file to tiff or jpeg? Converseen, which was my first guess didnt see the .jp2 file on my flashdrive.

---

### Post by FakeOutdoorsman on 2016-05-03
There are at least a few cli tools that can decode JPEG 2000:

convert from imagemagick:
```
convert input.jp2 output.tiff
```

or ffmpeg:
```
ffmpeg -i input.jp2 output.tiff
```

---

### Post by luckystar3 on 2016-05-16
Thanks for the heads up. I think ive made a break through with GRASS GIS. Ill let you know if it works.

---

