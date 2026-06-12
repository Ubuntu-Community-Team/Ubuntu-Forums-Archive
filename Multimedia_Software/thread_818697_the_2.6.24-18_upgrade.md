---
title: "the 2.6.24-18 upgrade"
date: 2008-06-04
forum: Multimedia Software
---

### Post by Ob1 on 2008-06-04
I'm satisfied with the better performance with this kernel, but the update messed up my screen resolution and video driver settings. This happened to anyone else?

---

### Post by Technoviking on 2008-06-04
> **Ob1 said:**
> I'm satisfied with the better performance with this kernel, but the update messed up my screen resolution and video driver settings. This happened to anyone else?

I have not had this problem. 
What video card do you have? 
Did you file a bug report at [https://bugs.launchpad.net/bugs/+filebug](https://bugs.launchpad.net/bugs/+filebug)?

Mike

---

### Post by K.Mandla on 2008-06-04
Moved to Multimedia and Video.

---

### Post by mabovo on 2008-06-04
> **Ob1 said:**
> I'm satisfied with the better performance with this kernel, but the update messed up my screen resolution and video driver settings. This happened to anyone else?

Yes, MacBook2,1 with Intel 945GM.

I can hear sound but no video output from video player Totem, VLC, etc.
It doesn't happen with kernel 2.6.24.17.

---

### Post by Sirchristopher on 2008-06-05
I had a problem where I was only able to boot into low graphics mode.  It was caused by changing the screen and graphics settings.  I used 

'gksudo displayconfig-gtk' and it fixed it.

---

