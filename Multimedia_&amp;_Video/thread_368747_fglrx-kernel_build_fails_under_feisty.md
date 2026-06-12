---
title: "fglrx-kernel build fails under feisty"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by Rippy on 2007-02-23
Not a month ago, I followed this guide

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

and got the fglrx driver installed without problems on Edgy. Now I've upgraded to Feisty Herd 4, and it's not so easy. I've gotten to the step were you have to build fglrx-kernel, but it fails partway through the operation (I can post the log, it's pretty huge though).

Does anyone know why this is? I thought this'd be something I could find an easy answer for, but several searches have come up with nothing. Any help appreciated

-Rippy

---

### Post by skug on 2007-02-23
The problem is that Feisty uses kernel version 2.6.20 where Edgy used 2.6.17. The newest fglrx driver (8.34.6) should work with a patch (don't have the url but google for fglrx 8.34 2.6.20 patch), It has worked for some but not for my X700 Mobility Radeon. 
Happy hacking :P

---

### Post by Rippy on 2007-02-23
Unfortunately, I have a Radeon 9250, which isn't supported by any version higher than 8.28.8 (which is what I'm trying to install).

Any way of getting it working with 8.28.8, or getting a 9250 working with the latest drivers? Otherwise I'll be stuck with the radeon driver, which doesn't give me nearly the same performance.

---

### Post by skug on 2007-02-23
The way I see it you have three options:
A: By a newer ati gpu... (the fammiliar)

B: By a newer Nvidia gpu... (not so familliar)

C: Beg ATI to continue development on the old gpu *grin*

out of these i think the first would be the wiser choise...

or then you could just use the open source driver that still supports your card :(

---

### Post by Rippy on 2007-02-24
I'll try the open-source driver, see if things are still playable with it, and if so use it.

---

