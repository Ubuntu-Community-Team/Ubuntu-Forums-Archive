---
title: "having problems installing cinelerra"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by Skeptical on 2007-09-08
When I try to install cinelerra I get this
cinelerra:
  Depends: libasound2 (>1.0.14) but 1.0.13-1ubuntu5 is to be installed
  Depends: libc6 (>=2.6-1) but 2.5-0ubuntu14 is to be installed
  Depends: libfreetype6 (>=2.3.5) but 2.2.1-5ubuntu1.1 is to be installed
  Depends: libgcc1 (>=1:4.2-20070516) but 1:4.1.2-0ubuntu4 is to be installed
 Depends: libmjpegtools0 but it is not going to be installed
 Depends: libopenexr2ldbl (>=1.2.2) but it is not installable
 Depends: libquicktimehv but it is not going to be installed
  Depends: libstdc++6 (>=4.2-20070516) but 4.1.2-0ubuntu4 is to be installed
  Depends: libvorbis0a (>=1.2.0) but 1.1.2.dfsg-1.2ubuntu2 is to be installed
  Depends: libvorbisfile3 (>=1.2.0) but 1.1.2.dfsg-1.2ubuntu2 is to be installed
  Depends: zlib1g (>=1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed

---

### Post by distroman on 2007-09-08
Which source are you installing from and how?

Anyway, this stands out, Depends: libopenexr2ldbl (>=1.2.2) but it is not installable.

---

### Post by rainwalker on 2007-09-08
I installed Cinelerra a whle back, so I checked my sources.list:
> ##Cinelerra
# deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
# deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
# deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main

That's where I HAD installed it from, I've since uninstalled it. Where are you installing from?

---

### Post by distroman on 2007-09-08
[http://cv.cinelerra.org/getting_cinelerra.php#ubuntu](http://cv.cinelerra.org/getting_cinelerra.php#ubuntu)
I got it there. 

Unfortunately the repositories didn't work out to well for me. So I had to compile it, there's debian files available if need and there might be a couple of howtos around that's fairly up-to-date.

---

### Post by rainwalker on 2007-09-08
I think that's the same place I got it...
I'm sorry, I don't know what could be wrong

---

### Post by usacomputertec on 2008-01-03
owner> dpkg: dependency problems prevent configuration of libquicktimehv:
<owner>  libquicktimehv depends on libfaad2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp); however:
<owner>   Package libfaad2-0 is not installed.
<owner>  libquicktimehv depends on libmpeg3hv (>= 1:2.1.0); however:
<owner>   Package libmpeg3hv is not installed.
<owner> dpkg: error processing libquicktimehv (--install):
<owner>  dependency problems - leaving unconfigured
<owner> Errors were encountered while processing:
<owner>  libquicktimehv
<owner> RESULT=1
<owner> looks like we need libfaad2-0 or higher and libmpeg3hv

---

