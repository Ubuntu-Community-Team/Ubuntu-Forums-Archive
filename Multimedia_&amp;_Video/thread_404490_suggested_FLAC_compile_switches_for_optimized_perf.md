---
title: "suggested FLAC compile switches for optimized performance?"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by zeus77 on 2007-04-08
Hi,

I'm about to do a big lossless audio conversion job using the FLAC command line encoder.  I'd like to compile the latest FLAC (1.1.4) from source, as it claims to offer to significant performance improvements over the older version in the repositories.  Furthermore, I'd like to compile it so that it takes advantage of modern processors (in my case, a Core Duo).  Any suggested compile options?  

Here is what I've been using so far [which I found on the Hydrogen Audio forums, under a discussion about compiling for Windows, I believe], but I'm not sure if all these switches are necessary or relevant for Linux:
```

./configure --enable-sse --disable-shared CFLAGS="-O3 -march=pentium3 -mfpmath=sse -ffast-math -fomit-frame-pointer -s"

```
... which is followed, of course, by 'make' and 'make install'.  

I believe the above should work for a Pentium III or later, and should take advantage of SSE instructions.  

Would be happy to hear what compile options anyone else is using, or if anyone knows if these switches are unnecessary/redundant/wrong/etc.  

Thanks.
zeus77

---

### Post by zeus77 on 2007-04-08
Just did a quick test with v1.1.4 (compiled with above switches) and v.1.1.2 (from the repository).  I detected no noticeable difference in encoding time... the newer version did compress ever-so-slightly smaller (about 1% smaller).  

Perhaps there are better compile switches which would lead to reduced encoding time?

---

