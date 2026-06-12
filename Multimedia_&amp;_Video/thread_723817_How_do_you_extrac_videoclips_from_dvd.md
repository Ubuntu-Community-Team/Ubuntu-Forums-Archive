---
title: "How do you extrac videoclips from dvd"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by Foxfire on 2008-03-13
I want to extract scenes  from diff movies  off dvd

---

### Post by xc3RnbFO8P on 2008-03-14
You could use DVD::RIP , be sure that you got all codec and add this for ripping dvds :
> 
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

Use[ Avidemux]("http://www.getdeb.net/release.php?id=2178") to cut the part you want.

---

