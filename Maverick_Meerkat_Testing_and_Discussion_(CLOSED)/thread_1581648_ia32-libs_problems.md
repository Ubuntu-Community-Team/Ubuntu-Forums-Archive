---
title: "ia32-libs problems"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by peacewithall on 2010-09-25
I ran my usual updates, and noticed this morning that flash, on my 64-bit 10.10 has no sound, at first I thought it was a problem with nspluginwrapper. I checked my packages and nspluginwrapper was last modified on the 9th, and I know it was working back then. I decided to take a break and start Secondlife application, it didn't start, I tried it in terminal and had complaints about installing ia32-libs (which of course are installed), I rechecked the date of the ia32-libs, and the last date is the 24th, the day before all the problems, anyone else noticing problems?, specifically 32-bit applications running in 64-bit.

---

### Post by peacewithall on 2010-09-25
Seems several 32-bit applications are effected by the new ia32-libs_20090808ubuntu5, only workaround until things are fixed is to downgrade to ia32-libs_20090808ubuntu4, using the deb in the link below from the skype forums,

[http://forum.skype.com/index.php?showtopic=716653](http://forum.skype.com/index.php?showtopic=716653)


All my problems are solved downgrading, flash works again and so doe's secondlife.

---

### Post by Casey R on 2010-09-25
Got this in terminal when trying to downgrade :( 

dpkg: error processing ia32-libs*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ia32-libs*.deb

---

### Post by peacewithall on 2010-09-25
> **Casey R said:**
> Got this in terminal when trying to downgrade :( 

dpkg: error processing ia32-libs*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ia32-libs*.deb

Thats strange all I did was remove the current ia32 libs (it will remove various applications also, but can be reinstalled after) using synaptic, then installed the older ia32 libs deb.

---

### Post by Casey R on 2010-09-25
> **peacewithall said:**
> Thats strange all I did was remove the current ia32 libs (it will remove various applications also, but can be reinstalled after) using synaptic, then installed the older ia32 libs deb.

Thanks.

Removed from Synaptic (it also removed my Skype, Picasa and Wine... grr).

My Skype voice chat and my Google calling now work with the old libs.....but my webcam still doesn't. 

Skype isn't showing that there's a webcam installed and neither is Cheese. Tried installing Camorama and it says "could not connect to /dev/video0"

Any ideas?

---

### Post by cdEWoozy on 2010-09-25
> **Casey R said:**
> Got this in terminal when trying to downgrade :( 

dpkg: error processing ia32-libs*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ia32-libs*.deb

You have to be in the directory you downloaded the debs into.

The bug report for this issue is here:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/647484](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/647484)

---

### Post by Casey R on 2010-09-25
OK, I fixed my webcam.... just had to activate it with FN + F10. lol.

---

