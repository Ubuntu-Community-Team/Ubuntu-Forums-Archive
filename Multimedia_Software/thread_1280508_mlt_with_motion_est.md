---
title: "mlt with motion_est"
date: 2009-10-02
forum: Multimedia Software
---

### Post by barna on 2009-10-02
Hi,

I am experiencing with kdenlive in ubuntu-9.10. In the list of effects the automask and motion_est filters are missing. This is probably because MLT was compiled without the motion_est module ([http://www.kdenlive.org/forum/automask-kdenlive-0721-and-ubuntu-intrepid](http://www.kdenlive.org/forum/automask-kdenlive-0721-and-ubuntu-intrepid)). 

So my question is a bit more general: if the official ubuntu packages have a limited functionality (they have been compiled with certain features disabled), is there a way to obtain them in a fully functional form, from some other repos? Why are the official packages limited in functionality?
Or how can I easily recompile and install them? If I do so, and there will be an update of this package later, which I install, I guess I will again loose this feature, and I need to recompile it again. 
Thanks

---

### Post by barna on 2009-10-02
According to [http://www.kdenlive.org/forum/blurring-faces](http://www.kdenlive.org/forum/blurring-faces), one should look for libmltmotion_est.so to figure out wether mlt was compiled with motion_est module. 

According to
[http://packages.ubuntu.com/search?searchon=contents&keywords=libmltmotion_est.so&mode=exactfilename&suite=karmic&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libmltmotion_est.so&mode=exactfilename&suite=karmic&arch=any)
the file /usr/lib/mlt/libmltmotion_est.so is in the libmlt1 package, which I have installed. Still, this file is not present on my system. How can this be?
Thanks

Oops, that must be an ubuntu-package bug: even though the above site lists libmltmotion_est.so as part of the libmlt1 package, navigating to the filelist of this package I can not find this file:
[http://packages.ubuntu.com/karmic/i386/libmlt1/filelist](http://packages.ubuntu.com/karmic/i386/libmlt1/filelist)

---

