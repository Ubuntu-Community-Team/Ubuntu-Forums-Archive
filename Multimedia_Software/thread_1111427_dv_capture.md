---
title: "dv capture"
date: 2009-03-30
forum: Multimedia Software
---

### Post by Komir on 2009-03-30
Is there some other way to capture from dv camera except dvgrab.

---

### Post by inobe on 2009-03-30
kino will do that but make sure you have all the requirements even after installing with synaptic.

[http://www.kinodv.org/article/static/3](http://www.kinodv.org/article/static/3)

i don't know what trouble you were having with dvgrab' but if it lacks the requirements nothing will work as expected.

---

### Post by Komir on 2009-03-31
I capture from VHS through Sony DCR-TRV223 PAL.
After some time of capture I had error :
[HTML]komir@komir-laptop:/media/disk/Stari$ sudo dvgrab -noavc -s 0 -showstatus -d 03:10:00 -f dv2 -nostop
Found AV/C device with GUID 0x08004601021fda7e
Turning on OpenDML to support large file size.
Capture Started
                                                                                 03:57:30
"dvgrab-001.avi": buffer underrun near: timecode 45:85:85.45 date 2009.03.29 03:57:30
This error means that the frames could not be written fast enough.
                                                                                 04:06:42
"dvgrab-001.avi": buffer underrun near: timecode 45:85:85.45 date 2009.03.29 04:06:42
This error means that the frames could not be written fast enough.
                                                                                 04:06:42
"dvgrab-001.avi": buffer underrun near: timecode 45:85:85.45 date 2009.03.29 04:06:42
This error means that the frames could not be written fast enough.
"dvgrab-001.avi":  1997.82 MiB 13806 frames timecode 45:85:85.45 date 2009.03.29 04:06:42Segmentation fault (core dumped)
#


I capture from VHS through Sony DCR-TRV223 PAL

komir@komir-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu jaunty (development branch)"

same problem  appears  on ubuntu 8.10


komir@komir-laptop:~$ aptitude show dvgrab
Package: dvgrab
State: installed
Automatically installed: no
Version: 3.2-2
Priority: extra
Section: universe/graphics
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 369k
Depends: libavc1394-0 (>= 0.5.3), libc6 (>= 2.4), libdv4, libgcc1 (>= 1:4.1.1),
         libiec61883-0 (>= 1.1.0), libjpeg62, libquicktime1 (>= 2:1.0.3+debian),
         libraw1394-8, libstdc++6 (>= 4.2.1), zlib1g (>= 1:1.1.4)
Description: grab digital video data via IEEE1394 and USB links
 dvgrab receives audio and video data from a digital camcorder via an IEEE1394
 (widely known as FireWire) or USB link and stores them into one of several file
 formats. It features autosplit of long video sequences, and supports saving the
 data as raw frames, AVI type 1, AVI type 2, Quicktime DV, a series of JPEG
 stills or MPEG2-TS.
Homepage: http://www.kinodv.org/
 [/PHP]komir@komir-laptop:/media/disk/Stari$ sudo dvgrab -noavc -s 0 -showstatus -d 03:10:00 -f dv2 -nostop
Found AV/C device with GUID 0x08004601021fda7e
Turning on OpenDML to support large file size.
Capture Started
                                                                                 03:57:30
"dvgrab-001.avi": buffer underrun near: timecode 45:85:85.45 date 2009.03.29 03:57:30
This error means that the frames could not be written fast enough.
                                                                                 04:06:42
"dvgrab-001.avi": buffer underrun near: timecode 45:85:85.45 date 2009.03.29 04:06:42
This error means that the frames could not be written fast enough.
                                                                                 04:06:42
"dvgrab-001.avi": buffer underrun near: timecode 45:85:85.45 date 2009.03.29 04:06:42
This error means that the frames could not be written fast enough.
"dvgrab-001.avi":  1997.82 MiB 13806 frames timecode 45:85:85.45 date 2009.03.29 04:06:42Segmentation fault (core dumped)
#




komir@komir-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu jaunty (development branch)"

same problem  appears  on ubuntu 8.10


komir@komir-laptop:~$ aptitude show dvgrab
Package: dvgrab
State: installed
Automatically installed: no
Version: 3.2-2
Priority: extra
Section: universe/graphics
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 369k
Depends: libavc1394-0 (>= 0.5.3), libc6 (>= 2.4), libdv4, libgcc1 (>= 1:4.1.1),
         libiec61883-0 (>= 1.1.0), libjpeg62, libquicktime1 (>= 2:1.0.3+debian),
         libraw1394-8, libstdc++6 (>= 4.2.1), zlib1g (>= 1:1.1.4)
Description: grab digital video data via IEEE1394 and USB links
 dvgrab receives audio and video data from a digital camcorder via an IEEE1394
 (widely known as FireWire) or USB link and stores them into one of several file
 formats. It features autosplit of long video sequences, and supports saving the
 data as raw frames, AVI type 1, AVI type 2, Quicktime DV, a series of JPEG
 stills or MPEG2-TS.
Homepage: [http://www.kinodv.org/](http://www.kinodv.org/)[/HTML]

---

