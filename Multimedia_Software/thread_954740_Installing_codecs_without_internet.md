---
title: "Installing codecs without internet"
date: 2008-10-21
forum: Multimedia Software
---

### Post by ahmerin on 2008-10-21
Hi all,

I have recently installed ubuntu 8.04 from a cd received from a friend. Now the problem is that I want to watch movies from DVDs and from avi, DivX files but totem says that I need to install codecs to watch them. It gives me option to go online and download codecs. 

The issue with me is that I do not have internet connection... There is no broadband where I live. I just have wll phone and  I am having problems configuring it too. Even if I manage to configure it, the connection will be too slow and will take hours to download a small file. The internet at work is fast but I can not take my machine there. I can, however download files from there.

Now, the question is: is there a site from where I can download codecs without using my machine? Or is there any good player that I can install which has all the codecs? All the help on internet seems to assume that one has a working internet connection.

Any help will be appreciated.

Kind Regards
Ahmerin

---

### Post by cor2y on 2008-10-21
You can get the standalone deb files from here for gstreamer and xine
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and the w32codec pack, libdvdcss2, libdvdnav libdvdread etc from here
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

They are deb files or the source files if you wish to compile yourself but in the case of the gstreamer/xine plugins make sure you download the dependancies as well since you don't have net access to download and install in synaptic.

---

