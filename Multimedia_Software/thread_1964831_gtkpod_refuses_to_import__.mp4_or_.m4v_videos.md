---
title: "gtkpod refuses to import  .mp4 or .m4v videos"
date: 2012-04-24
forum: Multimedia Software
---

### Post by ticket on 2012-04-24
I'm using a ipod nano 4th gen, gtkpod v2.1.0, Ubuntu 11.10.

gtkpod recognises the ipod, and I can import .mp3 audio files to it easily with no problems.

However, I am unable to import .mp4 or .m4v video files.

Even if I copy an existing (and unencrypted) .m4v file off the ipod and re-import the same file (which therefore must have the correct format) the file is still refused.

Error message: 
 
  "File type of / .../12345678.m4v is not recognised"

Is import of video files broken in this version of gtkpod?

---

### Post by ticket on 2012-04-25
I see the latest version of gtkpod (v2.1.1) still require the library libmp4v2, which is not in the Ubuntu 11.10 repositories.  Could that be the problem?

No libmp4v2 in 11.10:
[http://www.ubuntuupdates.org/package/core/oneiric/multiverse/base/libmp4v2-0](http://www.ubuntuupdates.org/package/core/oneiric/multiverse/base/libmp4v2-0)

But it appears a version will be avialable in Ubuntu 12.04:
[http://www.ubuntuupdates.org/package/core/precise/universe/base/libmp4v2-2](http://www.ubuntuupdates.org/package/core/precise/universe/base/libmp4v2-2)

---

### Post by ticket on 2012-04-26
An unroasted bean bump ...

---

### Post by ticket on 2012-04-28
Is anyone using gtkpod on Ubuntu 11.10?

---

### Post by philman1008 on 2012-04-28
You are better off than me. I have Ipod touch 4th gen, I cant even transfer music. Tried Banshee, gtkpod and rythymbox.... none work!!

---

### Post by ticket on 2012-04-28
> You are better off than me. I have Ipod touch 4th gen, I cant even transfer music. Tried Banshee, gtkpod and rythymbox.... none work!!
Works for me on 11.10.  What version of Ubuntu are you using?
Ooops, I see you have the 'Touch' version - I know they are more of a problem,

---

