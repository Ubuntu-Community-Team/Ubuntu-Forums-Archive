---
title: "Exiftool"
date: 2016-08-10
forum: Multimedia Software
---

### Post by shantiq on 2016-08-10
Like most of you here I use mediainfo to see what is inside images audio and video recordings and i never realized there was an even more detailed tool called exiftool

It is installed by default on 16.04

if not on your version
```
sudo apt-get install libimage-exiftool-perl
```

```
man exiftool
```   gives you all the options     all you  need   is     ```
exiftool  nameofyourfile
```

Below examples on Photo/Audio/Video






```
PHOTO
=====
ExifTool Version Number         : 10.10
File Name                       : 1.JPG
Directory                       : .
File Size                       : 7.2 MB
File Modification Date/Time     : 2016:07:18 14:20:20+01:00
File Access Date/Time           : 2016:08:10 08:51:00+01:00
File Inode Change Date/Time     : 2016:07:18 17:12:07+01:00
File Permissions                : rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
Exif Byte Order                 : Big-endian (Motorola, MM)
Make                            : Apple
Camera Model Name               : iPhone 4S
Orientation                     : Horizontal (normal)
X Resolution                    : 72
Y Resolution                    : 72
Resolution Unit                 : inches
Software                        : 9.3.2
Modify Date                     : 2016:07:18 14:20:20
Y Cb Cr Positioning             : Centered
Exposure Time                   : 1/2762
F Number                        : 2.4
ISO                             : 50
Exif Version                    : 0221
Date/Time Original              : 2016:07:18 14:20:20
Create Date                     : 2016:07:18 14:20:20
Components Configuration        : Y, Cb, Cr, -
Shutter Speed Value             : 1/2762
Aperture Value                  : 2.4
Brightness Value                : 10.78121665
Exposure Compensation           : 0
Metering Mode                   : Multi-segment
Flash                           : No Flash
Focal Length                    : 4.3 mm
Sub Sec Time Original           : 111
Sub Sec Time Digitized          : 111
Flashpix Version                : 0100
Color Space                     : sRGB
Exif Image Width                : 10800
Exif Image Height               : 2332
Sensing Method                  : One-chip color area
Scene Type                      : Directly photographed
Custom Rendered                 : Unknown (6)
White Balance                   : Auto
Focal Length In 35mm Format     : 35 mm
Scene Capture Type              : Standard
Lens Info                       : 4.28mm f/2.4
Lens Make                       : Apple
Lens Model                      : iPhone 4S back camera 4.28mm f/2.4
Compression                     : JPEG (old-style)
Thumbnail Offset                : 822
Thumbnail Length                : 3319
Image Width                     : 10800
Image Height                    : 2332
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Aperture                        : 2.4
Image Size                      : 10800x2332
Megapixels                      : 25.2
Scale Factor To 35 mm Equivalent: 8.2
Shutter Speed                   : 1/2762
Create Date                     : 2016:07:18 14:20:20.111
Date/Time Original              : 2016:07:18 14:20:20.111
Thumbnail Image                 : (Binary data 3319 bytes, use -b option to extract)
Circle Of Confusion             : 0.004 mm
Field Of View                   : 54.4 deg
Focal Length                    : 4.3 mm (35 mm equivalent: 35.0 mm)
Hyperfocal Distance             : 2.08 m
Light Value                     : 15.0






AUDIO
=====

ExifTool Version Number         : 10.10
File Name                       : 06 - Vivent les hommes.flac
Directory                       : .
File Size                       : 161 MB
File Modification Date/Time     : 2016:06:21 10:34:32+01:00
File Access Date/Time           : 2016:08:04 17:21:58+01:00
File Inode Change Date/Time     : 2016:06:21 10:34:32+01:00
File Permissions                : rw-r--r--
File Type                       : FLAC
File Type Extension             : flac
MIME Type                       : audio/flac
Block Size Min                  : 4096
Block Size Max                  : 4096
Frame Size Min                  : 13171
Frame Size Max                  : 19474
Sample Rate                     : 96000
Channels                        : 2
Bits Per Sample                 : 24
Total Samples                   : 43753292
Vendor                          : reference libFLAC 1.2.1 20070917
Tool Name                       : Media Center
Tool Version                    : 15.0.58
Title                           : Vivent les hommes
Artist                          : Gérard Manset
Album                           : la mort d'orion (vinyl rip)
Genre                           : Psychedelic French
Track Number                    : 6
Date                            : 1970
Picture Type                    : Front Cover
Picture MIME Type               : image/jpeg
Picture Description             : 
Picture Width                   : 1227
Picture Height                  : 1198
Picture Bits Per Pixel          : 24
Picture Indexed Colors          : 0
Picture Length                  : 214535
Picture                         : (Binary data 214535 bytes, use -b option to extract)
Duration                        : 0:07:35



VIDEO
=====

ExifTool Version Number         : 10.10
File Name                       : Le fond de l'air est rouge  - 1 - Les Mains Fragiles - 1-2-x11eekv.mp4
Directory                       : .
File Size                       : 255 MB
File Modification Date/Time     : 2013:06:30 12:15:00+01:00
File Access Date/Time           : 2016:07:25 07:59:32+01:00
File Inode Change Date/Time     : 2016:07:25 07:59:32+01:00
File Permissions                : rw-rw-r--
File Type                       : MP4
File Type Extension             : mp4
MIME Type                       : video/mp4
Major Brand                     : MP4  Base Media v1 [IS0 14496-12:2003]
Minor Version                   : 0.2.0
Compatible Brands               : isom, iso2, avc1, mp41
Movie Header Version            : 0
Create Date                     : 0000:00:00 00:00:00
Modify Date                     : 2013:06:30 10:14:41
Time Scale                      : 1000
Duration                        : 0:44:49
Preferred Rate                  : 1
Preferred Volume                : 100.00%
Preview Time                    : 0 s
Preview Duration                : 0 s
Poster Time                     : 0 s
Selection Time                  : 0 s
Selection Duration              : 0 s
Current Time                    : 0 s
Next Track ID                   : 3
Track Header Version            : 0
Track Create Date               : 0000:00:00 00:00:00
Track Modify Date               : 0000:00:00 00:00:00
Track ID                        : 1
Track Duration                  : 0:44:49
Track Layer                     : 0
Track Volume                    : 0.00%
Image Width                     : 600
Image Height                    : 448
Graphics Mode                   : srcCopy
Op Color                        : 0 0 0
Compressor ID                   : avc1
Source Image Width              : 600
Source Image Height             : 448
X Resolution                    : 72
Y Resolution                    : 72
Bit Depth                       : 24
Video Frame Rate                : 25
Matrix Structure                : 1 0 0 0 1 0 0 0 1
Media Header Version            : 0
Media Create Date               : 0000:00:00 00:00:00
Media Modify Date               : 0000:00:00 00:00:00
Media Time Scale                : 44100
Media Duration                  : 0:44:49
Media Language Code             : und
Handler Description             : SoundHandler
Balance                         : 0
Audio Format                    : mp4a
Audio Channels                  : 2
Audio Bits Per Sample           : 16
Audio Sample Rate               : 44100
Handler Type                    : Metadata
Handler Vendor ID               : Apple
Encoder                         : Lavf54.59.106
Movie Data Size                 : 265536175
Movie Data Offset               : 2104448
Avg Bitrate                     : 790 kbps
Image Size                      : 600x448
Megapixels                      : 0.269
Rotation                        : 0
```

---

### Post by coldraven on 2016-08-10
That's a handy thing to know, cheers!

---

### Post by wildmanne39 on 2016-08-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

