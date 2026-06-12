---
title: "ffmpeg , capture audio + video."
date: 2009-01-16
forum: Multimedia Software
---

### Post by StOoZ on 2009-01-16
Hi,
is it possible to capture the mic audio with ffmpeg?
I tried using 
ffmpeg -f oss -i /dev/dsp  ...  but to no avail.

any idea?

---

### Post by huzia on 2010-05-04
> **StOoZ said:**
> Hi,
is it possible to capture the mic audio with ffmpeg?
I tried using 
ffmpeg -f oss -i /dev/dsp  ...  but to no avail.

any idea?
you can try the argument :

ffmpeg -f oss /dev/dsp out.mpg

---

