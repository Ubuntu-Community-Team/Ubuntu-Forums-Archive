---
title: "R300 - open source 3D ATI driver progress?"
date: 2006-03-12
forum: Multimedia &amp; Video
---

### Post by rgr on 2006-03-12
Hello,

some time ago, r300.sf.net was started and people were even able to play games like Enemy territory on X800 like cards.
Now, recently I found a blog entry[1] which was already posted half a year ago and the author mentioned he got the driver to run fine on PCI-Express based cards. (The last time I checked, it did only work with AGP).

Unfortunatly, the website is outdated and I can't find any more recent info about this. I currently own a nVidia card but would get a PCI-Express X800 if it worked with 3D acceleration. Does anyone know the progress on this?


[1] [http://airlied.livejournal.com/13757.html](http://airlied.livejournal.com/13757.html)

---

### Post by dicecca112 on 2006-03-12
I thought 3d acceleration worked with x800 cards, it would be news to me, seeing I'm using a x800gto, anyway I can test this?  Other than a game, seeing I don't game, and if I do, its on windows

---

### Post by rgr on 2006-03-13
AFAIK that driver is included with Xorg 7.0 - but since the 7.0 release, there were some changes done to driver, so you probably would have to compile it for yourself if you want to try a recent version.

I am just curious, there were reports of even modern games working half a year ago, but I never saw a big buzz about this driver...If those things are true, it should be much more in the spotlight, as the X800 series are then the only modern PCI-Express GPUs with working free 3D drivers and decent performance.

-----
Edit:
I just searched the dri-devel mailing list and found some information from 2006. It seems to work with PCI-Express and 3D basically seems to be working although a bunch of glx corruptions and system lockups are reported. I think I'll get that card and check for myself :)

---

