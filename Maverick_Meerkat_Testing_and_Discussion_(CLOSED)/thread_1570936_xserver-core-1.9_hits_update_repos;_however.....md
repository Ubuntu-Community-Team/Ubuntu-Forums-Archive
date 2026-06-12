---
title: "xserver-core-1.9 hits update repos; however...."
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by PGHammer on 2010-09-08
The official (non-beta) Xorg-xserver 1.9 core hit the repos today; however, due to there being no FOSS driver support (and the only closed-source driver is from nVidia), I'd advise holding off for now (I'll be waiting for radeon 1.9-compatible server to arrive at either xorg-edgers or X-swat).

Additional Info: A 1.9-compatible version of the FOSS AMD server(s) is now available at xorg-edgers (6.13.99+ for Maverick Meerkat) in AMD64 and i386 *flavors*; however, it must be installed *before* updating to Xorg 1.9.  While there is still no 3D or DRI/DRI2 support for R800/HD5xxx, 2D is faster (much faster) than original Maverick Meerkat beta; even more surprising, standard compositing in KWin 4.5.x now works. (Completely unexpected, especially with DRI/DRI2 still using software rendering.)

However, I have noticed that Mesa in Maverick is still 7.8.2; should I also update Mesa to the xorg-edgers version?

---

### Post by andrewthomas on 2010-09-17
> **PGHammer said:**
> 
A 1.9-compatible version of the FOSS AMD server(s) is now available at  xorg-edgers (6.13.99+ for Maverick Meerkat) in AMD64 and i386 *flavors*;  however, it must be installed *before* updating to Xorg 1.9.  While  there is still no 3D or DRI/DRI2 support for R800/HD5xxx, 2D is faster  (much faster) than original Maverick Meerkat beta..........
However, I have noticed that Mesa in Maverick is still 7.8.2; **should I also update Mesa to the xorg-edgers version?**
I would say yes.  
[QUOTE=https://launchpad.net/~xorg-edgers/+archive/ppa]
This PPA is currently meant to be used as a whole. Please do _not_  individually install packages from it, add it to your sources and let  your package manager pull in every update. The packages here build  against each other and compile different features based on whats  available at build time. Do not assume that because it lets you install a  DDX with just the driver and libdrm update that it will work.  These  packages are made with scripts that use the the current packages as the  base, so some dependencies can be wrong and your package manager will  not resolve that for you.  If you want to individually install something  from here, grab the source and rebuild it in your current environment  instead.[/QUOTE]

---

