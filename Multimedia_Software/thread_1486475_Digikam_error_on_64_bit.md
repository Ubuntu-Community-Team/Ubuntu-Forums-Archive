---
title: "Digikam error on 64 bit"
date: 2010-05-17
forum: Multimedia Software
---

### Post by randyklein99 on 2010-05-17
I have digikam installed from the repos on both a 64 bit and 32 bit.  It works just fine on the 32 bit, but on the 64 bit, I get this error:

```
digikam: error while loading shared libraries: libkipi.so.6: cannot open shared object file: No such file or directory

```

That library doesn't exist on either system, so I'm not sure why it's only erring out on the 64 bit.  I've tried re-installing and completely removing and reinstalling, but same error. 

Any clues?

---

### Post by randyklein99 on 2010-05-18
Well, I compiled digikam from source and it works now on the 64 bit.  Still don't know why the repo version doesn't.

---

### Post by RedRat on 2010-05-18
I run digikam on Hardy and find that the program is not quite complete. There are many things that it does poorly, e.g., finding and showing duplicate files larger than 1Mb. I think it has a lot of potential but it feels to me as if it is about 90% complete. I suspect that part of the problem is that the program was written originally for 32 bit architecture. I don't know if development of the program is still going on.

---

