---
title: "Sox resample gives truncated wav chunks"
date: 2012-02-22
forum: Multimedia Software
---

### Post by Sith Lord Kyle on 2012-02-22
Hopefully this is the right place for this issue...

I am trying to resample wav files with Sox from 96k to 48k.  The files play fine, the resampling works, from what I can tell there is nothing wrong with the file whatsoever.

But, I am trying to embed BWF headers into the wav after this.  In the program I am using it tells me the file size is less than is stated in the file's chunk size declarations.

If I resample in Audacity, they work fine... problem is I have thousands of these files and can only resample in Audacity one at a time.  But with Sox I can write a bash command to do them all automatically.

Any ideas why this is providing the chuck size declarations with Sox?

---

