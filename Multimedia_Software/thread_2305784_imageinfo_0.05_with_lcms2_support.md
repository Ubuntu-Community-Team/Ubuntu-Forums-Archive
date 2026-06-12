---
title: "imageinfo 0.05 with lcms2 support"
date: 2015-12-09
forum: Multimedia Software
---

### Post by rmstock2 on 2015-12-09
imageinfo-0.05 from [http://wohlberg.net/public/software/photo/imageinfo/](http://wohlberg.net/public/software/photo/imageinfo/)
has been adjusted to work together with lcms2 
(liblcms2-2  2.5-0ubuntu4  Little CMS 2 color management library ).

With imageinfo you can extract ICC Profiles from your favorate images, to be 
used for other graphics work, and can also be inserted in programs like gimp :

```

stock@acer30u:~/Pictures/icc$ imageinfo --iccname 37.jpg
sRGB IEC61966-2.1
stock@acer30u:~/Pictures/icc$ imageinfo --iccfile=37.icc --iccname 37.jpg
sRGB IEC61966-2.1
stock@acer30u:~/Pictures/icc$ ll
total 1580
drwxrwxr-x 2 stock stock    4096 dec  9 12:05 ./
drwxr-xr-x 4 stock stock    4096 dec  9 05:34 ../
-rw-rw-r-- 1 stock stock    3144 dec  9 12:05 37.icc
-rw-rw-r-- 1 stock stock 1603736 dec  9 12:04 37.jpg
stock@acer30u:~/Pictures/icc$ file *
37.icc: Microsoft ICM Color Profile
37.jpg: JPEG image data, JFIF standard 1.02
stock@acer30u:~/Pictures/icc$ 

```

[IMG]http://crashrecovery.org/imageinfo/RPMS/mdv2011/lcms/RGB-profile1.jpg[/IMG]

[IMG]http://crashrecovery.org/imageinfo/RPMS/mdv2011/lcms/RGB-profile2.jpg[/IMG]

[IMG]http://crashrecovery.org/imageinfo/RPMS/mdv2011/lcms/RGB-profile3.jpg[/IMG]

the version which is installed on ubuntu 14.04 normally does not work :
$ imageinfo --iccname IMG_0657.jpg
imageinfo: installed imagemagick does not support lcms
$ imageinfo --version
imageinfo 0.04
$

Download is at [ftp://ftp.crashrecovery.org/pub/linux/imageinfo/DEB/ubuntu1404/](ftp://ftp.crashrecovery.org/pub/linux/imageinfo/DEB/ubuntu1404/)
[ftp://ftp.crashrecovery.org/pub/linux/imageinfo/DEB/ubuntu1404/imageinfo-lcms2.patch](ftp://ftp.crashrecovery.org/pub/linux/imageinfo/DEB/ubuntu1404/imageinfo-lcms2.patch)
[ftp://ftp.crashrecovery.org/pub/linux/imageinfo/DEB/ubuntu1404/README](ftp://ftp.crashrecovery.org/pub/linux/imageinfo/DEB/ubuntu1404/README)

```

imageinfo (0.05-0ubuntu8) quantal; urgency=low

  * added lcms2 support for extracting ICC Profiles
  * created imageinfo-lcms2.patch

 -- Robert M. Stockmann <stock@stokkie.net>  Wed, 09 Dec 2015 09:21:46 +010

installation :

root@ubu14:~# ll imageinfo_0.05-0ubuntu8_amd64.deb 
-rw-r--r-- 1 root root 21962 dec  9 11:05 imageinfo_0.05-0ubuntu8_amd64.deb
root@ubu14:~# dpkg -i imageinfo_0.05-0ubuntu8_amd64.deb 
Selecting previously unselected package imageinfo.
(Reading database ... 178943 files and directories currently installed.)
Preparing to unpack imageinfo_0.05-0ubuntu8_amd64.deb ...
Unpacking imageinfo (0.05-0ubuntu8) ...
Setting up imageinfo (0.05-0ubuntu8) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
root@ubu14:~#

Usage :

stock@ubu14:~/Pictures$ imageinfo --help
Usage: imageinfo <image file>
      --format           Display image format
      --fmtdscr          Display image format description
      --size             Display image size
      --depth            Display bit depth
      --geom             Display image geometry
      --width            Display image width
      --height           Display image height
      --iccname          Display ICC profile name
      --iccfile=file     Save ICC profile to file
      --iccmd5           Display MD5 hash of ICC profile
      --md5hash          Display MD5 hash of image
      --sha256hash       Display SHA-256 hash of image
      --version          Display imageinfo version

Help options:
  -?, --help             Show this help message
      --usage            Display brief usage message
stock@ubu14:~/Pictures$ 
stock@ubu14:~/Pictures/icc$ cd Adobe\ ICC\ Profiles\ \(end-user\)/CMYK/
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)/CMYK$ ll *
-rw-r--r-- 1 stock stock 557188 aug 25  2008 CoatedFOGRA27.icc
-rw-r--r-- 1 stock stock 654352 aug 25  2008 CoatedFOGRA39.icc
-rw-r--r-- 1 stock stock 654372 aug 25  2008 CoatedGRACoL2006.icc
-rw-r--r-- 1 stock stock 557168 aug 25  2008 JapanColor2001Coated.icc
-rw-r--r-- 1 stock stock 557168 aug 25  2008 JapanColor2001Uncoated.icc
-rw-r--r-- 1 stock stock 557172 aug 25  2008 JapanColor2002Newspaper.icc
-rw-r--r-- 1 stock stock 654432 aug 25  2008 JapanColor2003WebCoated.icc
-rw-r--r-- 1 stock stock 557164 aug 25  2008 JapanWebCoated.icc
-rw-r--r-- 1 stock stock 654140 aug 25  2008 UncoatedFOGRA29.icc
-rw-r--r-- 1 stock stock 557168 aug 25  2008 USWebCoatedSWOP.icc
-rw-r--r-- 1 stock stock 557164 aug 25  2008 USWebUncoated.icc
-rw-r--r-- 1 stock stock 654140 aug 25  2008 WebCoatedFOGRA28.icc
-rw-r--r-- 1 stock stock 654372 aug 25  2008 WebCoatedSWOP2006Grade3.icc
-rw-r--r-- 1 stock stock 654372 aug 25  2008 WebCoatedSWOP2006Grade5.icc
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)/CMYK$
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)/CMYK$ for i in *
> do
> imageinfo --iccname $i
> done
Coated FOGRA27 (ISO 12647-2:2004)
Coated FOGRA39 (ISO 12647-2:2004)
Coated GRACoL 2006 (ISO 12647-2:2004)
Japan Color 2001 Coated
Japan Color 2001 Uncoated
Japan Color 2002 Newspaper
Japan Color 2003 Web Coated
Japan Web Coated (Ad)
Uncoated FOGRA29 (ISO 12647-2:2004)
U.S. Web Coated (SWOP) v2
U.S. Web Uncoated v2
Web Coated FOGRA28 (ISO 12647-2:2004)
Web Coated SWOP 2006 Grade 3 Paper
Web Coated SWOP 2006 Grade 5 Paper
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)/CMYK$
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)/CMYK$ cd ..
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)$ cd RGB/
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)/RGB$ ll
total 48
drwxr-xr-x 2 stock stock 4096 okt 27  2008 ./
drwxr-xr-x 4 stock stock 4096 okt 23  2008 ../
-rw-r--r-- 1 stock stock  560 aug 25  2008 AdobeRGB1998.icc
-rw-r--r-- 1 stock stock  552 aug 25  2008 AppleRGB.icc
-rw-r--r-- 1 stock stock  560 aug 25  2008 ColorMatchRGB.icc
-rw-r--r-- 1 stock stock 6148 okt 27  2008 .DS_Store
-rw-r--r-- 1 stock stock  552 okt 22  2008 PAL_SECAM.icc
-rw-r--r-- 1 stock stock  552 okt 22  2008 SMPTE-C.icc
-rw-r--r-- 1 stock stock 1480 okt 13  2008 VideoHD.icc
-rw-r--r-- 1 stock stock 1468 okt 13  2008 VideoNTSC.icc
-rw-r--r-- 1 stock stock 1464 okt 13  2008 VideoPAL.icc
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)/RGB$
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)/RGB$ for i in *; do imageinfo --iccname $i; done
Adobe RGB (1998)
Apple RGB
ColorMatch RGB
PAL/SECAM
SMPTE-C
HDTV (Rec. 709)
SDTV NTSC
SDTV PAL
stock@ubu14:~/Pictures/icc/Adobe ICC Profiles (end-user)/RGB$ 


```

---

