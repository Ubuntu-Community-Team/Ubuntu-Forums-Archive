---
title: "RAW Images"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by JonE8 on 2007-06-29
Hi I have recently purchased a Panasonic Lumix DMC-FZ8 and thought I would try some shots in RAW mode but when I open them with Gimp and ufraw I can't see them see the screenshot for how they look, I also get his error messgae after closing Gimp "Opening '/home/jon/Photos/RAW Photos/P1000130.RAW' failed: Plug-In could not open image".
Can anyone help.

Cheers 
Jon

---

### Post by JonE8 on 2007-06-30
Have I posted in the wrong place?

---

### Post by Epeli on 2007-07-13
I have also a Panasonic FZ8 and i've similar results with dcraw. It seems that Ubuntu's version of dcraw is broken or something. When I compiled it by my self it worked fine. I've attached a working binary for i386 in tar.gz-package. Put it to **/usr/bin/dcraw**  but use at one's own risk ;) Or you can compile it by your self. Source can be found here: [http://cybercom.net/~dcoffin/dcraw/](http://cybercom.net/~dcoffin/dcraw/)

I've also filled a bug report in launcpad: [https://bugs.launchpad.net/ubuntu/+source/dcraw/+bug/125798](https://bugs.launchpad.net/ubuntu/+source/dcraw/+bug/125798)

---

### Post by vanadium on 2007-07-13
This would lead me to suspect that the RAW format of your camera is still different than raw formats of other vendors. I can read the raw format of a Canon powershot without problems. You might try to use the adobe utility to convert your raw format to the adobe DNF (Digital Negative Format) first, which then can surely be opened with dfraw.

---

### Post by Epeli on 2007-07-13
According to developper version 8.70 or later is required to read DMC-FZ8 RAW-files. 

files:  [http://cybercom.net/~dcoffin/dcraw/archive/](http://cybercom.net/~dcoffin/dcraw/archive/)

---

### Post by Wim De Winter on 2008-04-07
> **Epeli said:**
> I have also a Panasonic FZ8 and i've similar results with dcraw. It seems that Ubuntu's version of dcraw is broken or something. When I compiled it by my self it worked fine. I've attached a working binary for i386 in tar.gz-package. Put it to **/usr/bin/dcraw**  but use at one's own risk ;) Or you can compile it by your self. Source can be found here: [http://cybercom.net/~dcoffin/dcraw/](http://cybercom.net/~dcoffin/dcraw/)

I've also filled a bug report in launcpad: [https://bugs.launchpad.net/ubuntu/+source/dcraw/+bug/125798](https://bugs.launchpad.net/ubuntu/+source/dcraw/+bug/125798)
Hi,
I had the same problem. Epeli's solution however works fine with me! Thanks!!

---

