---
title: "Image magick producing large eps files"
date: 2012-12-10
forum: Multimedia Software
---

### Post by Xeovke on 2012-12-10
Hello all,
  I recently needed to convert a bunch of png files into eps format (ultimately to put into a LaTeX dvi). I thought the best way was to use a simple mogrify command from image magick, such as
  mogrify -format eps *.png
  The problem is the files obtained are way too large (easily over a 10Mb for an original 100kb png file). Even after fooling around more with options (-trim, -colors, ...) I could not get it much below 4Mb (without seriously damaging the quality of the picture).
  On the other hand, GIMP gives a perfectly satisfactory eps file (quality and size about 600kb).
  Any idea how to make mogrify use more sensible parameters?

---

