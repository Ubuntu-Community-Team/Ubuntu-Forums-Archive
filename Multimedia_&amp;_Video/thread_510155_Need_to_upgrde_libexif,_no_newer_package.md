---
title: "Need to upgrde libexif, no newer package"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by gearjunkie on 2007-07-26
Hey all,
I have been trying to work through some problems with my digital camera and the GIMP.  The issue turns out to be a bug in libexif that doesn't allow the gimp (and some other programs which use libexif) to open pictures taken on my Olympus Stylus 770sw.

The problem is that I need to upgrade libexif to a version newer than 0.6.14, and the package I am finding in the repository is 0.6.13.  I can get the source code for versions all the way up to 0.6.16, and would like to install a newer version of it. 

I would like to manage everything through apt if possible, but I can't find any other newer packages of libexif.  

I thought about just installing it from source, but then I thought I may need to remove the old package first.  So, I went to synaptic to uninstall the old package, and there are a ton of other things that depend on it that I don't want to uninstall.  So, my questions are this:

1) Does anyone know where I can get a newer package of libexif?
2) If not, is it safe to install the source while the package is still installed, and will it just write over the necessary files?
3) If not, does anyone have any easy tutorials to try and build my own package from the source?  (possibly allowing me to upgrade the package without uninstalling and re-installing all the dependant programs)

Thanks in advance,
Nathan

---

