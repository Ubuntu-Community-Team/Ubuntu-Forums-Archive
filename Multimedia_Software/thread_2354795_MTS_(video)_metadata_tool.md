---
title: "MTS (video) metadata tool"
date: 2017-03-06
forum: Multimedia Software
---

### Post by alain.roger on 2017-03-06
Hi,

i have several MTS video files that i got from video cameras and i would like to get the REAL date when those videos have been recorded.
What is the best tool or command to do that ?

thx

---

### Post by deadflowr on 2017-03-06
*Thread moved to **Multimedia Software**.*

---

### Post by ajgreeny on 2017-03-06
Install the packages that allow you to use exiftool
```
sudo apt install exif libexif12 libimage-exiftool-perl
```
then simply run ```
exiftool /path/to/file.mts
```
Here's what I see when using it with the various times shown in red.  Creation date/time is the top of the three.
```
~/Videocamera/1/PRIVATE/AVCHD/BDMV/STREAM$ exiftool 00003.MTS 
ExifTool Version Number         : 10.10
File Name                       : 00003.MTS
Directory                       : .
File Size                       : 298 MB
File Modification Date/Time     : [COLOR="#FF0000"]2010:12:25 12:56:54+00:00[/COLOR]
File Access Date/Time           : [COLOR="#FF0000"]2017:03:06 22:42:41+00:00[/COLOR]
File Inode Change Date/Time     : [COLOR="#FF0000"]2013:04:05 17:44:07+01:00[/COLOR]
File Permissions                : rw-r--r--
File Type                       : M2TS
File Type Extension             : mts
MIME Type                       : video/m2ts
Video Stream Type               : H.264 Video
Audio Stream Type               : A52/AC-3 Audio
Audio Bitrate                   : 256 kbps
Surround Mode                   : Not indicated
Audio Channels                  : 2
Image Width                     : 1920
Image Height                    : 1080
Date/Time Original              : 2010:12:25 13:53:38+00:00
Aperture Setting                : 1.8
Gain                            : 0 dB
Exposure Program                : Program AE
White Balance                   : Auto
Image Stabilization             : On (0x7f)
Exposure Time                   : 1/50
Exposure Compensation           : 0
Focal Length In 35mm Format     : inf mm
Make                            : Panasonic
Audio Sample Rate               : 48000
Duration                        : 0:03:14
Image Size                      : 1920x1080
Megapixels                      : 2.1
Shutter Speed                   : 1/50

```

---

