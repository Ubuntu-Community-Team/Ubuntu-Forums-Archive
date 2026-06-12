---
title: "Analog NTSC with bars gets more bars in mytharchive"
date: 2009-12-31
forum: Mythbuntu
---

### Post by eljeffe on 2009-12-31
This results in a DVD with the shows stretched out in width. Not sure how to have mytharchive not do this.

---

### Post by eljeffe on 2010-01-03
Mythburn changes the aspect ratio from 4:3 to 16:10.

From the beginning of mythburn.log

```
          Doctor Who
Video resolution is 720 by 480
*************************************************************
Processing recording 1: '/spare/mythtv/recordings/Doctor Who - 2009-12-31, 9-00 PM - Christmas Invasion.nuv'
*************************************************************
File type is 'nuv'
Video codec is 'mpeg4'
2010-01-03 10:23:05.265 getFileInfo(): Opening '/spare/mythtv/recordings/Doctor Who - 2009-12-31, 9-00 PM - Christmas Invasion.nuv'
Input #0, nuv, from '/spare/mythtv/recordings/Doctor Who - 2009-12-31, 9-00 PM - Christmas Invasion.nuv':
  Duration: 01:53:24.47, start: 0.028000, bitrate: 1411 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480, PAR 8:9 **[SIZE="4"]DAR 4:3[/SIZE]**, 30 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 1411 kb/s
2010-01-03 10:23:05.270 duration = 6804
2010-01-03 10:23:05.270 Extracting details from: Doctor Who - 2009-12-31, 9-00 PM - Christmas Invasion.nuv
2010-01-03 10:23:05.271 chanid: 6162 starttime:2009-12-31T21:00:00 
2010-01-03 10:23:05.273 File is a Myth recording.
2010-01-03 10:23:05.273 cutframes = 0
2010-01-03 10:23:05.273 cutduration = 0
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="6804" duration="6804" filename="/spare/mythtv/recordings/Doctor Who - 2009-12-31, 9-00 PM - Christmas Invasion.nuv" type="nuv">   
```

After making the intermediate mpeg 

```
Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x80 (AC3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Splitting MPEG stream into audio and video parts
Running: mythreplex --demux --fix_sync -o /var/log/mytharchive/temp/work/1/stream -v 224 -c 128 "/var/log/mytharchive/temp/work/1/newfile2.mpg"
Reading from /var/log/mytharchive/temp/work/1/newfile2.mpg
Input file length: 842.36 MB
Checking for TS: failed
Checking for AVI: failed
Checking for PS: confirmed(maybe)
Video: **[SIZE="4"]aspect ratio: 16:9[/SIZE]**  size = 720x480  frame rate: 29.970 fps  bit rate: 104.86 Mbit/s
  vbvbuffer 1359872
Sequence Extension: chroma 4:2:0   size = 720x480  bit rate: 104.86 Mbit/s  vbvbuffer 1359872  frame rate: 29.970
starting with video PTS:  0:00:00.5000 
AC3 stream:  bit rate: 192 kb/s  freq: 48000 Hz
  frame size 768
starting audio PTS:  0:00:00.5000 
Video output File is: /var/log/mytharchive/temp/work/1/stream.mv2
AC30 output File is: /var/log/mytharchive/temp/work/1/stream0.ac3
```

I'm not sure why this is happening. It is, however, a real problem.

---

### Post by eljeffe on 2010-01-10
Bump with corrected title.

---

