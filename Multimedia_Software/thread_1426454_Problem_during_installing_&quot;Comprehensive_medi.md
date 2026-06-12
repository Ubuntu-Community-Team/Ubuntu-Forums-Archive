---
title: "Problem during installing &quot;Comprehensive media howto&quot;"
date: 2010-03-10
forum: Multimedia Software
---

### Post by Laxman_prodigy on 2010-03-10
[B]It stopped giving the following output when I tried to run it again after it interrupted one time before. What is the problem here actually? Here it is:
[/B]
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar
[sudo] password for laxman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-oss is already the newest version.
faac is already the newest version.
faad is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
libmp3lame0 is already the newest version.
libmp3lame0 set to manually installed.
The following extra packages will be installed:
  ca-certificates-java cabextract flashplugin-installer gsfonts-x11
  icedtea-6-jre-cacao java-common lib32asound2 lib32bz2-1.0 lib32gcc1
  lib32ncurses5 lib32nss-mdns lib32stdc++6 lib32v4l-0 lib32z1
  libaccess-bridge-java libaccess-bridge-java-jni libamrnb3 libamrwb3
  libc6-i386 libjline-java nspluginwrapper openjdk-6-jre-headless
  openjdk-6-jre-lib rhino sun-java6-jre ttf-liberation
  ttf-mscorefonts-installer tzdata-java ubuntu-restricted-extras w64codecs
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs equivs lib32asound2-plugins
  libjline-java-doc sun-java6-fonts ttf-kochi-gothic ttf-sazanami-gothic
  ttf-kochi-mincho ttf-sazanami-mincho ttf-telugu-fonts ttf-oriya-fonts
  ttf-kannada-fonts ttf-bengali-fonts rhino-doc sun-java6-plugin
  ia32-sun-java6-plugin ttf-arphic-uming mplayer
The following NEW packages will be installed:
  ca-certificates-java cabextract flashplugin-installer flashplugin-nonfree
  gsfonts-x11 ia32-libs ia32-sun-java6-bin icedtea-6-jre-cacao icedtea6-plugin
  java-common lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32nss-mdns
  lib32stdc++6 lib32v4l-0 lib32z1 libaccess-bridge-java
  libaccess-bridge-java-jni libamrnb3 libamrwb3 libc6-i386 libjline-java
  non-free-codecs nspluginwrapper openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib rhino sun-java6-jre ttf-liberation
  ttf-mscorefonts-installer tzdata-java ubuntu-restricted-extras unrar
  w64codecs
0 upgraded, 37 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB/103MB of archives.
After this operation, 341MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main libc6-i386 2.10.1-0ubuntu16
  Connection failed
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse sun-java6-jre 6-15-1
  500  Internal Server Error
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i386_2.10.1-0ubuntu16_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i386_2.10.1-0ubuntu16_amd64.deb)  Connection failed
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb)  500  Internal Server Error
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

**It seems like a connection problem to me what say?**

---

### Post by MelDJ on 2010-03-10
change your software server in system-admin-software sources

---

### Post by Laxman_prodigy on 2010-03-11
Thanks Meldj.:D

---

