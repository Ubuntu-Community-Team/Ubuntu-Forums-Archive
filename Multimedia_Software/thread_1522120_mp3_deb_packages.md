---
title: "mp3 deb packages"
date: 2010-07-01
forum: Multimedia Software
---

### Post by gizmoo200 on 2010-07-01
hi, can anyone tell me what deb packages are needed to install mp3 support? the ubuntu-restricted-extras is a meta package and requires an internet connection. i don't have an internet connection at home with my workstation, i have to take my laptop to a wi-fi hot spot and download the needed deb files, take them home and install them manually 

   thank you
        mike

---

### Post by nmaster on 2010-07-01
> **gizmoo200 said:**
> hi, can anyone tell me what deb packages are needed to install mp3 support? the ubuntu-restricted-extras is a meta package and requires an internet connection. i don't have an internet connection at home with my workstation, i have to take my laptop to a wi-fi hot spot and download the needed deb files, take them home and install them manually 

   thank you
        mike

why not apt-get in the restricted extras while at the hot spot?  once the packages are downloaded you can leave and they will continue to install.

you should check the apt-get man page for how to download the deb files so that you can install them at a later time.  i'd check now, but i'm at work using osx.

---

### Post by mc4man on 2010-07-01
> needed to install mp3 support?
A bit to open ended, but

If just meaning decoding support for gstreamer apps then 2 ways, 1 quite simple
This will provide decoding in gstreamer - no add. deps needed
> gstreamer0.10-fluendo-mp3 
or you could go the gstreamer plugin route - will provide mp3 decoding and a bit more
 > gstreamer0.10-ffmpeg
 gstreamer0.10-plugins-ugly
liba52-0.7.4 
libavcodec52
libavformat52 
libavutil49 
libdvdnav4 
libdvdread4 
libgsm1 
libid3tag0 
libmad0
libmpeg2-4 
libopencore-amrnb0 
libopencore-amrwb0 
libpostproc51
libschroedinger-1.0-0 
libsidplay1 
libswscale0 
libtwolame0


If you also want encoding support then more packages are needed

Third party player have other deps

---

### Post by gizmoo200 on 2010-07-09
thank you, that was just what i needed

       mike

---

