---
title: "Mytharchive error"
date: 2010-12-27
forum: Mythbuntu
---

### Post by williammanda on 2010-12-27
I was trying out mytharchive today and tried to create a iso file of a video. The process seems to get to a point where it is shrinking the video and then has the error. The error is at the very bottom This is the process log:

```
2010-12-27 13:26:35 mythburn.py (0.1.20101206-1) starting up...
2010-12-27 13:26:35 Found 4 CPUs
2010-12-27 13:26:35 Obtaining MythTV settings from MySQL database for hostname C2Q
2010-12-27 13:26:35 temppath: /var/lib/mythtv/archivevideos/work
2010-12-27 13:26:35 logpath:  /var/lib/mythtv/archivevideos/logs
2010-12-27 13:26:35 Setting process priority to 17
2010-12-27 13:26:35 Processing Mythburn job number 1.
2010-12-27 13:26:35 Options - mediatype = 3, doburn = 0, createiso = 1, erasedvdrw = 0
2010-12-27 13:26:35           savefilename = ''
2010-12-27 13:26:35 Looking for: /usr/share/mythtv/mytharchive/themes/MythCenter/theme.xml
2010-12-27 13:26:35 Loading font 0, /usr/share/mythtv/fonts/FreeSans.ttf size 18
2010-12-27 13:26:35 Loading font 1, /usr/share/mythtv/fonts/FreeSans.ttf size 15
2010-12-27 13:26:35 Loading font 2, /usr/share/mythtv/fonts/FreeSans.ttf size 13
2010-12-27 13:26:35 wantIntro: 1, wantMainMenu: 1, wantChapterMenu:1, wantDetailsPage: 0
2010-12-27 13:26:35 Final DVD Video format will be ntsc
2010-12-27 13:26:35 There are 1 files to process
2010-12-27 13:26:36 Pre-processing video 1: 'Avatar.mkv'
2010-12-27 13:26:36           Avatar
2010-12-27 13:26:36 Video resolution is 720 by 480
2010-12-27 13:26:36 *************************************************************
2010-12-27 13:26:36 Processing video 1: 'Avatar.mkv'
2010-12-27 13:26:36 *************************************************************
2010-12-27 13:26:36 File type is 'matroska,webm'
2010-12-27 13:26:36 Video codec is 'mpeg2video'
2010-12-27 13:26:36 File will be re-encoded using profile HQ
2010-12-27 13:26:36 File will be re-encoded using profile HQ
2010-12-27 13:26:36 Preferred audio languages eng and eng
2010-12-27 13:26:36 Video id: 0x0, Audio1: [1] 0x0 (AC3, eng), Audio2: [-1] - 0x-1 (N/A, N/A)
2010-12-27 13:26:36 Aspect ratio is 16:9
2010-12-27 13:26:36 Re-encoding audio and video
2010-12-27 13:26:36 Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_ntsc.xml
2010-12-27 13:26:36 Encoding profile (HQ) found
2010-12-27 13:26:36 Pass 1 - ffmpeg -threads 4 -v 1 -i "/var/lib/mythtv/videos/Avatar.mkv" -r ntsc -target dvd -b 9000k -s 720x480 -acodec copy -copyts -aspect 16:9 -pass 1 -passlogfile /var/lib/mythtv/archivevideos/work/pass "/var/lib/mythtv/archivevideos/work/1/newfile2.mpg" -map 0:0 -map 0:1 
2010-12-27 13:44:03 Pass 2 - ffmpeg -threads 4 -v 1 -i "/var/lib/mythtv/videos/Avatar.mkv" -r ntsc -target dvd -b 9000k -s 720x480 -acodec copy -copyts -aspect 16:9 -pass 2 -passlogfile /var/lib/mythtv/archivevideos/work/pass "/var/lib/mythtv/archivevideos/work/1/newfile2.mpg" -map 0:0 -map 0:1 
2010-12-27 14:04:58 Preferred audio languages eng and eng
2010-12-27 14:04:58 Video id: 0x1e0, Audio1: [1] 0x80 (AC3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
2010-12-27 14:04:58 Splitting MPEG stream into audio and video parts
2010-12-27 14:04:58 Running: mythreplex --demux --fix_sync -o /var/lib/mythtv/archivevideos/work/1/stream -v 224 -c 128 "/var/lib/mythtv/archivevideos/work/1/newfile2.mpg"
2010-12-27 14:10:30 Audio is already in ac3 format
2010-12-27 14:10:30 Extracting thumbnail image from /var/lib/mythtv/archivevideos/work/1/stream.mv2 at position 10
2010-12-27 14:10:30 Destination file /var/lib/mythtv/archivevideos/work/1/title.jpg
2010-12-27 14:10:32 *************************************************************
2010-12-27 14:10:32 Finished processing 'Avatar.mkv'
2010-12-27 14:10:32 *************************************************************
2010-12-27 14:10:32 Menu items per page 3
2010-12-27 14:10:32 Background image file is /usr/share/mythtv/mytharchive/themes/MythCenter/MythCenter-Background.png
2010-12-27 14:10:32 Music is menumusic.ac3, length is 15 seconds
2010-12-27 14:10:32 Creating DVD menus
2010-12-27 14:10:32 Menu page 1
2010-12-27 14:10:32 Creating Preview Video
2010-12-27 14:10:33 Added image /var/lib/mythtv/archivevideos/work/1/title.jpg
2010-12-27 14:10:33 Encoding Menu Page 1 using aspect ratio '16:9'
2010-12-27 14:10:43 Chapter items per page 8 
2010-12-27 14:10:43 Background image file is /usr/share/mythtv/mytharchive/themes/MythCenter/MythCenter-Background.png
2010-12-27 14:10:43 Music is menumusic.ac3, length is 15 seconds
2010-12-27 14:10:43 Creating DVD sub-menus
2010-12-27 14:10:43 Sub-menu 1 
2010-12-27 14:10:43 Video length is 9701 seconds. Each chapter will be 1212 seconds
2010-12-27 14:10:43 Extracting thumbnail images from: /var/lib/mythtv/archivevideos/work/1/stream.mv2 - at 10,1212,2424,3636,4848,6060,7272,8484
2010-12-27 14:10:43 Destination file /var/lib/mythtv/archivevideos/work/1/chapter-%1.jpg
2010-12-27 14:12:04 Added image /var/lib/mythtv/archivevideos/work/1/chapter-1.jpg
2010-12-27 14:12:04 Added image /var/lib/mythtv/archivevideos/work/1/chapter-2.jpg
2010-12-27 14:12:04 Added image /var/lib/mythtv/archivevideos/work/1/chapter-3.jpg
2010-12-27 14:12:04 Added image /var/lib/mythtv/archivevideos/work/1/chapter-4.jpg
2010-12-27 14:12:04 Added image /var/lib/mythtv/archivevideos/work/1/chapter-5.jpg
2010-12-27 14:12:04 Added image /var/lib/mythtv/archivevideos/work/1/chapter-6.jpg
2010-12-27 14:12:04 Added image /var/lib/mythtv/archivevideos/work/1/chapter-7.jpg
2010-12-27 14:12:04 Added image /var/lib/mythtv/archivevideos/work/1/chapter-8.jpg
2010-12-27 14:12:04 Added button image /usr/share/mythtv/mytharchive/images/previous.png
2010-12-27 14:12:04 Added titlemenu button
2010-12-27 14:12:04 aspect ratio is: 1.77778
2010-12-27 14:12:04 Encoding Chapter Menu Page 1 using aspect ratio 'Video'
2010-12-27 14:12:12 Menu items per page 3
2010-12-27 14:12:12 Chapters per recording 8
2010-12-27 14:12:12 Creating DVD XML file for dvd author
2010-12-27 14:12:12 Menu page 1
2010-12-27 14:12:12 aspect ratio is: 1.77778
2010-12-27 14:12:12 aspect ratio is: 1.77778
2010-12-27 14:12:12 Video length is 9701 seconds. Each chapter will be 1212 seconds
2010-12-27 14:12:12 Total video  7074.02 Mb, audio 518.10 Mb, menus 5.22 Mb.
2010-12-27 14:12:12 Video files are 3287.5 Mb too big. Need to shrink.
2010-12-27 14:12:13 vrate 409.281 kb/s, testsize 3786.4979 , mv2space 3786.4979 Mb 
2010-12-27 14:12:13 File 1, size 7074.02 Mb, rate 764.63, limit 409.28 kb/s 
2010-12-27 14:12:13 Initial M2Vsize is 7074.02 Mb , target is 3700.51 Mb
2010-12-27 14:12:13 Running: M2VRequantiser 1.91163  7417649700  <  /var/lib/mythtv/archivevideos/work/1/stream.mv2  >  /var/lib/mythtv/archivevideos/work/1/stream.small.mv2 
2010-12-27 14:12:13 M2Vsize after requant is  0.00 Mb 
2010-12-27 14:12:13 ------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 5510, in main
    processJob(job)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 5253, in processJob
    performMPEG2Shrink(files, dvdrsize[0])
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 2892, in performMPEG2Shrink
    runM2VRequantiser(os.path.join(getItemTempPath(filecount),"stream.mv2"),os.path.join(getItemTempPath(filecount),"stream.small.mv2"),scalefactor)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 2741, in runM2VRequantiser
    fac1=float(M2Vsize0) / float(M2Vsize1)
ZeroDivisionError: float division
2010-12-27 14:12:13 ------------------------------------------------------------
```

---

### Post by williammanda on 2010-12-28
ZeroDivisionError: float division

What does this mean?

---

### Post by calimarno on 2011-02-18
I have the same problem and would also be interested if somebody could help to find what is going wrong there...

[EDIT]
Ok, I had a look at mythburn.py and apparently I was missing M2VRequantiser ([https://launchpad.net/m2vrequantiser/+download](https://launchpad.net/m2vrequantiser/+download)) ... I installed it and trying again (crossing fingers! ;-))

---

### Post by jim.hitch on 2011-11-07
> **calimarno said:**
> I have the same problem and would also be interested if somebody could help to find what is going wrong there...

[EDIT]
Ok, I had a look at mythburn.py and apparently I was missing M2VRequantiser ([https://launchpad.net/m2vrequantiser/+download](https://launchpad.net/m2vrequantiser/+download)) ... I installed it and trying again (crossing fingers! ;-))

This is a while ago now, I know. But I've got this issue too, did your solution work?

---

