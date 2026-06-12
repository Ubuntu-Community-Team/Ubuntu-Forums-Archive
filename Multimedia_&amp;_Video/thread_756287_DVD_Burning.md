---
title: "DVD Burning"
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by id220mb on 2008-04-15
I have alot of movies that are Mpeg 2 for DVD.  DeVeDe converted one of them from .avi.  When I was running windows I was using Total Video Converter.  It converted and burned for me.  Now I have 20 something gigs of video and I cannot figure out how to burn it.  All the burners in the repo keep giving me error messages.:guitar:

---

### Post by xc3RnbFO8P on 2008-04-15
Install in Synaptic Package Manager:

libmad0
libmad0-dev
python-pymad

k3b
k3b-i18n
libk3b2
libk3b2-extracodecs
libk3b2-mp3
libk3b-dev

dvd95
dvdauthor
liba52
liba52  dev
libdvdnav4
mkisofs

And be sure you got this:
> wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
> sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb
> wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
> sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
> sudo /usr/share/doc/libdvdread3/install-css.sh

---

