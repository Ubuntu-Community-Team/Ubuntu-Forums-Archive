---
title: "Zoneminder with Ubuntu 9.04 and Mysql 5.1"
date: 2009-07-26
forum: Multimedia Software
---

### Post by mjy78 on 2009-07-26
When trying to install zoneminder on Ubuntu 9.04 server from the command line I get the following dependency problems...

```

user@SERVER:~$ sudo aptitude install zoneminder
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
  mysql-client-5.1 mysql-server-5.1
The following NEW packages will be installed:
  ffmpeg{a} libarchive-zip-perl{a} libasound2{a} libavcodec52{a} libavdevice52{a} libavfilter0{a} libavformat52{a} libavutil49{a}
  libconvert-binhex-perl{a} libdate-manip-perl{a} libdc1394-22{a} libdevice-serialport-perl{a} libdirectfb-1.0-0{a}
  libemail-date-format-perl{a} libgsm1{a} libio-stringy-perl{a} libjpeg62{a} libmime-lite-perl{a} libmime-perl{a} libmime-tools-perl{a}
  libmime-types-perl{a} libogg0{a} liboil0.3{a} libphp-serialization-perl{a} libpostproc51{a} libraw1394-8{a} libschroedinger-1.0-0{a}
  libsdl1.2debian{a} libsdl1.2debian-alsa{a} libspeex1{a} libswscale0{a} libsysfs2{a} libtheora0{a} libts-0.0-0{a} libvorbis0a{a}
  libvorbisenc2{a} mysql-client-5.0{a} mysql-server{a} mysql-server-5.0{a} mysql-server-core-5.0{a} zoneminder
0 packages upgraded, 41 newly installed, 0 to remove and 0 not upgraded.
Need to get 44.4MB of archives. After unpacking 136MB will be used.
The following packages have unmet dependencies:
  mysql-server-5.1: Conflicts: mysql-server (< 5.1.31-1ubuntu2) but 5.1.30really5.0.75-0ubuntu10.2 is to be installed.
                    Conflicts: mysql-server-5.0 but 5.1.30really5.0.75-0ubuntu10.2 is to be installed.
                    Conflicts: mysql-server-core-5.0 but 5.1.30really5.0.75-0ubuntu10.2 is to be installed.
  mysql-client-5.1: Conflicts: mysql-client-5.0 but 5.1.30really5.0.75-0ubuntu10.2 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
mysql-client-5.1
mysql-server-5.1

Score is -172

Accept this solution? [Y/n/q/?]

```

I get dependency conflicts because I have mysql 5.1 installed (and need). Is there a way to force zoneminder to install without it trying to remove mysql 5.1 and revert to mysql 5.0?

---

