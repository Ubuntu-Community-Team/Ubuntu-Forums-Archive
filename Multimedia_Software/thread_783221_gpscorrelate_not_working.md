---
title: "gpscorrelate not working"
date: 2008-05-05
forum: Multimedia Software
---

### Post by davidfg4 on 2008-05-05
I am trying to use gpscorrelate to add latitude/longitude data to images, but it does not seem to write the exif data to the image.
I am using ubuntu 8.04, gpscorrelate 1.5.5-1build1, and exiv2 0.16-3ubuntu1.

Output(notice the GPS data is not in the exif data of the image):

david@david-desktop:~$ gpscorrelate -g Desktop/08,04,26.gpx -z -6 -v Desktop/CIMG13562.JPG 
EXIF-GPS Photo matching program.
Daniel Foote, 2005.

Reading GPS Data...

Correlate: 
Desktop/CIMG13562.JPG: Interpolated: Lat 38.696365, Long -110.179771, Elev 1300.582189.

Completed correlation process.
Matched:     1 (0 Exact, 1 Interpolated, 0 Rounded).
Failed:      0 (0 Not matched, 0 Write failure, 0 Too Far,
                0 No Date, 0 GPS Already Present.)
david@david-desktop:~$ exiv2 Desktop/CIMG13562.JPG 
File name       : Desktop/CIMG13562.JPG
File size       : 121422 Bytes
Camera make     : CASIO COMPUTER CO.,LTD 
Camera model    : EX-Z750
Image timestamp : 2008:04:22 10:37:12
Image number    : 
Exposure time   : 1/100 s
Aperture        : F5.1
Exposure bias   : 0
Flash           : No, compulsory
Flash bias      : 
Focal length    : 23.7 mm (35 mm equivalent: 114.0 mm)
Subject distance: 
ISO speed       : 
Exposure mode   : Auto
Metering mode   : Multi-segment
Macro mode      : 
Image quality   : 
Exif Resolution : 667 x 500
White balance   : 
Thumbnail       : JPEG, 7093 Bytes
Copyright       : 
Exif comment    : 

david@david-desktop:~$ 


If anyone has any experience with this program your help would be greatly appreciated.

---

