---
title: "Can't install ffmpeg with restricted codecs on Hardy"
date: 2008-05-20
forum: Multimedia Software
---

### Post by Funzo22 on 2008-05-20
I have tried several times, following tutorials that have worked for me back when I used feisty and precompiled packages, I don't get any errors or anything, but when I try encoding aac videos it complains that the codec doesn't work.

I think i had the same problem with gutsy, but I just made do... now I really need to be able to encode videos for my ipod


Any help is apprciated!



Thanks~!!!!

Also: I should note that when I compile ffmpeg it says that aac and other restricted codecs will be present, but then they are not

---

### Post by monraaf on 2008-05-20
ffmpeg from the standard repository is crippled.  Just add the Medibuntu repository then update ffmpeg and you'll be fine.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Funzo22 on 2008-05-22
> **monraaf said:**
> ffmpeg from the standard repository is crippled.  Just add the Medibuntu repository then update ffmpeg and you'll be fine.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

thanks, but it still doesn't work I get unknown codec 'aac' when I try to encode anything

---

### Post by cor2y on 2008-05-22
you need to have the aac codec library for encoding which means libfaac try having that installed.

---

### Post by Funzo22 on 2008-06-02
> **cor2y said:**
> you need to have the aac codec library for encoding which means libfaac try having that installed.

still no luck

---

### Post by Pjotr123 on 2008-06-02
Try applying this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

Hope this helps.

Greetz, Pjotr.

---

