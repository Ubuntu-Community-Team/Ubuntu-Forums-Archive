---
title: "replacement for Sound Juicer?"
date: 2012-09-30
forum: Multimedia Software
---

### Post by karrank% on 2012-09-30
running 10.04.2 and generally happy, but using Sound Juicer is becoming more and more difficult.--Mainly since MusicBrainz appears to be not working... 

 I've tried Asunder, RipperX, and a few others (forget which now) with unsatisfactory results. 

Any recommendations?

Thanks for looking.

---

### Post by shantiq on 2012-10-01
a lot of those early gui linux rippers are now mostly obsolete or they have something missing




may i suggest Command Line pacpl 



```
sudo apt-get install pacpl
```


SYNTAX FOR RIPPING
===============


```
pacpl  --outdir ~/Desktop --rip all  -t  flac --fcomp 8
```

or for single trax


```
pacpl  --outdir ~/Desktop --rip 1,2,3  -t  flac --fcomp 8
```


if mp3   is your weapon of choice      replace flac --fcomp 8    with  > mp3 -bitrate 256  or whichever bitrate you wish for


**PS**   of course you can create a folder anywhere you want and send files there

ie:   --outdir ~/Desktop/MyNewTracks  having first created MyNewTracks



or you can make this easier this way


> cd Music && mkdir 'My New Album' \
pacpl  --outdir ~/Music/'My New Album' --rip 5,6  -t mp3 -bitrate 320


include ''   or   ""  around folder name if you want to leave gaps in your folder name   ie   "The Drunken Rolling Stones of Ulan Baator - Live in Bamako"







> man pacpl



Perl Audio Converter is a tool for converting multiple audio types from one
format to another using various external encoders/decoders.

It supports the following audio formats: AAC, AC3, AIFF, APE, AU, AVR, BONK,
CAF, CDR, FAP, FLA, FLAC, IRCAM, LA, LPAC, M4A, MAT, MAT4, MAT5, MMF, MP2, MP3,
MP4, MPC, MPP, NIST, OFR, OFS, OGG, PAC, PAF, PVF, RA, RAM, RAW, SD2, SF, SHN,
SMP, SND, SPX, TTA, VOC, W64, WAV, WMA, and WV.

It can also convert audio from the following video extensions: RM, RV, ASF,
DivX, MPG, MKV, MPEG, AVI, MOV, OGM, QT, VCD, SVCD, M4V, NSV, NUV, PSP, SMK,
VOB, FLV, and WMV.

Pacpl also includes a CD ripping function with CDDB support, batch conversion,
tag preservation for most supported formats, independent tag reading/writing,
a simple kommander gui and extensions for Dolphin and Konqueror. You can
write your own modules in order to add support for new file formats.



**Would then advise puddletag  to give in-depth tagging and add image**

---

