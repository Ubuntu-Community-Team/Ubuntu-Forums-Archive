---
title: "Any experiences with the PGF-format (instead of JPG)?"
date: 2010-05-06
forum: Multimedia Software
---

### Post by Jenske on 2010-05-06
I've stumbled upon the so-called pgf-format in a Digikam-related website. According to the makers of this format, it ought to be better than jpg.

Your experiences?

---

### Post by Judo on 2010-05-06
Judging by its compression methods, it could be much better.

Wavelet transformations never do well on images.  Although they have better compression, they lack detail in comparison to discrete cosine transformations.

Its entropy coding seems to be rice/golomb coding.  I'm not really sure how well it does on images, but JPEG 2000's arithmetic coding is almost certainly more efficient in that area.

Long story short, it's probably just below JPEG 2000 in compression but better than JPEG by far, especially when you consider it can be lossless.

However, it's not very likely that it will become popular so don't expect to see it on the web.

---

