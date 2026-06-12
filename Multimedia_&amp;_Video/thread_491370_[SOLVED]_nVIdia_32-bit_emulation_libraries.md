---
title: "[SOLVED] nVIdia 32-bit emulation libraries"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by themainliner on 2007-07-03
OK, so I may have made a small (or major) mistake.

have an AMD64 X2 CPU I decided to install Ubuntu 7.04 for AMD64.  Now I am struggling with Cedega, which I had much success with on a 32 bit, earlier release of Ubuntu.

So trawling the Cedega Forums informs me that I need and do not have the 32-bit emulation libraries I need to do anything with Cedega.  It does not tell me how I go about doing this.  I installed the Automatix nVidia drivers and they work really well, glx seems to be configured correctly.

So can anyone advise on how to install 32-bit emulation libraries for my nVidia card before I take the easy way out and install a 32 bit Feisty. :D

---

### Post by david_2001 on 2007-07-03
I don't use Cedega myself but the libraries you need are the 32-bit compatibility libraries and will be one or more of ia32-libs, lib32asound2, lib32ncurses5, ia32-libs-sdl, and ia32-libs-gtk.  If Cedega is anything like wine - I use Crossover Linux myself - and you live outside the USA then you may need to create a symbolic link from /usr/lib/locale to /usr/lib32/locale:
```
sudo ln -s /usr/lib/locale /usr/lib32/locale
```
and add the following to /etc/environment
```
XLOCALELIBDIR=/usr/lib32/locale
```
and  then reboot to get non-US locales to work.

---

### Post by themainliner on 2007-07-04
Fantastic!  Thank you very much, sir! :KS

I followed your advice as far as the locale symbolic link.  I attempted to install a game at that point with some success so I can confirm that final step is not required.

Many thanks.:popcorn:

---

