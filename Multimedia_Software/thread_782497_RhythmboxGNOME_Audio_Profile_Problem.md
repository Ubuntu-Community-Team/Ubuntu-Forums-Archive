---
title: "Rhythmbox/GNOME Audio Profile Problem"
date: 2008-05-05
forum: Multimedia Software
---

### Post by rondmc170 on 2008-05-05
I seem to be having some sort of problem with my Rhythmbox... I attempted to switch my ripping codec to AAC (for the iPod) and it wont switch from OGG. The window in question is located in Edit > Preferences > Music > Preferred Format. It is as if the window closes without applying any of the changes, as when I reopen the window, it still continues to not list AAC as an option, even if I select it in the "edit" menu located next to it. This is very irritating, it does the same thing in the Audio CD Extractor.

I'm using Hardy, with Rhythmbox 0.11.5. I'm not sure if the problem is Rhythmbox or GNOME Audio Profile (like I said, it's doing the same thing in Audio CD Extractor.

Thanks for the help!

---

### Post by rookworm on 2009-01-26
same problem here.... any ideas?

---

### Post by Linuxdork on 2009-01-26
I hope this isn't a stupid question, but do you have faac installed?  I'm pretty sure you need that to rip in aac.

---

### Post by broken tibula on 2009-04-07
Having the same problem, except I edited the mp3 profile so that I could rip at 256 bitrate, and now the option to encode in mp3 format at all is gone.  Help?  Anyone?

---

### Post by logos34 on 2009-04-07
do you have the gstreamer codecs metapackage installed?

> sudo apt-get install ubuntu-restricted-extras

---

### Post by broken tibula on 2009-04-08
I reinstalled the package and now it works fine!  Thanks so much!

---

### Post by hardyfan on 2009-05-16
Thank you , solved my problems as well.  I really appreciate the experienced users that take the time to help others (I hope to repay in kind as I learn more).

Cheers

---

