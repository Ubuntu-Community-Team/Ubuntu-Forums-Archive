---
title: "mytharchive - trouble with non-HD shows"
date: 2009-10-21
forum: Multimedia Software
---

### Post by wooddealer on 2009-10-21
I'm having trouble making a usable DVD of several shows I have recorded.  The only thing I can see which is different between successful DVDs and unsuccessful ones, is that successful ones come from HD recordings and unsuccessful ones come from non-HD recordings.

I'm new to Linux, so I could be missing something obvious.  Below are the mythburn.log and progress.log outputs from an unsuccessful attempt, some repetitive lines were removed to save space.

To clarify, it is not that Mytharchive does not make a DVD, it does, but when played that video is slow and out of sync with the audio, and the total length is about 30 seconds, when the original is an hour long.

More info to try and help troubleshoot this.  When in the "Select Archive Items" page, after selecting a non-HD show, the "size indicator bar" on the lower right hand side, appears empty.  If later on in the wizard at the "Items Selected for Archive" page, I change the "Encoder Profile" to "Don't re-encode", then I get something that makes sense in the "size indicator bar".  This obviously won't work since the original broadcast isn't DVD compatible, and I understand why the "size indicator bar" is empty for any re-encoding, since the size of the file if I blindly try to re-encode and make the DVD will end up being only about 20MB.

I found some code on a different thread which I added to my mythburn.py to rename my .ICEauthority file, so it isn't getting in the way.

My main focus has been to concentrate on the fact that original recording's resolution (in the case below) is 720X576 and the output for DVD needs to be 720X480, but ffmpeg doesn't seem to throw any errors about that when it runs.  At least no errors I'm aware of.

I appreciate any help and suggestions.

mythburn.log
```

Using simple_fix_rtl
mythburn.py (0.1.20090515-1-fixes) starting up...
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /mnt/lombardi/mythtv/temp/config/mydata.xml
passed progress log file: /mnt/lombardi/mythtv/temp/logs/progress.log
mythburn.py (0.1.20090515-1-fixes) starting up...
Found 2 CPUs
Obtaining MythTV settings from MySQL database for hostname hobie-desktop
temppath: /mnt/lombardi/mythtv/temp/work
logpath:  /mnt/lombardi/mythtv/temp/logs
Setting process priority to 17
Processing Mythburn job number 1.
Options - mediatype = 0, doburn = 0, createiso = 1, erasedvdrw = 0
          savefilename = ''
Looking for: /usr/share/mythtv/mytharchive/themes/Compact/theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 19
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 15
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 13
wantIntro: 1, wantMainMenu: 1, wantChapterMenu:0, wantDetailsPage: 0
Final DVD Video format will be ntsc
There are 1 files to process
Pre-processing recording 1: '/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv'
2009-10-21 04:28:46.845 Opening /mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv
Input #0, nuv, from '/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv':
  Duration: 43:37:51.4, start: 53861.391000, bitrate: 127 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 16:9 DAR 20:9], 59.94 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
2009-10-21 04:28:46.913 duration = 157071
2009-10-21 04:28:46.913 Extracting details from: 1111_20090906220000.nuv
2009-10-21 04:28:46.914 chanid: 1111 starttime:2009-09-06T22:00:00 
2009-10-21 04:28:46.917 File is a Myth recording.
2009-10-21 04:28:46.917 cutframes = 45597
2009-10-21 04:28:46.917 cutduration = 760
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="156311" duration="157071" filename="/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv" type="nuv">    
        <streams count="2">        
                <video aspectratio="1.77778" bitrate="0" codec="mpeg4" ffmpegindex="0" fps="59.9401" height="576" id="0" start_time="53.861391" streamindex="0" width="720"/>        
                <audio bitrate="128000" channels="2" codec="mp3" ffmpegindex="1" id="1" language="N/A" samplerate="48000" start_time="53.861449" streamindex="1"/>        
        </streams>    
</file>
          Doctor Who
Video resolution is 720 by 576
*************************************************************
Processing recording 1: '/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv'
*************************************************************
File type is 'nuv'
Video codec is 'mpeg4'
2009-10-21 04:28:47.124 Opening /mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv
Input #0, nuv, from '/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv':
  Duration: 43:37:51.4, start: 53861.391000, bitrate: 127 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 16:9 DAR 20:9], 59.94 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
2009-10-21 04:28:47.128 duration = 157071
2009-10-21 04:28:47.128 Extracting details from: 1111_20090906220000.nuv
2009-10-21 04:28:47.145 chanid: 1111 starttime:2009-09-06T22:00:00 
2009-10-21 04:28:47.147 File is a Myth recording.
2009-10-21 04:28:47.147 cutframes = 45597
2009-10-21 04:28:47.148 cutduration = 760
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="156311" duration="157071" filename="/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv" type="nuv">    
        <streams count="2">        
                <video aspectratio="1.77778" bitrate="0" codec="mpeg4" ffmpegindex="0" fps="59.9401" height="576" id="0" start_time="53.861391" streamindex="0" width="720"/>        
                <audio bitrate="128000" channels="2" codec="mp3" ffmpegindex="1" id="1" language="N/A" samplerate="48000" start_time="53.861449" streamindex="1"/>        
        </streams>    
</file>
Preferred audio languages eng and eng
Video id: 0x0, Audio1: [1] 0x1 (MP3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Aspect ratio is 16:9
Re-encoding audio and video from nuv file
Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_ntsc.xml
Encoding profile (SP) found
mythtranscode started PID = 25493
WARNING: frames rates do not match
The frame rate for ntsc should be 29.97 but the stream info file report a fps of 59.9401
Waiting for mythtranscode to create the fifos
Running: /usr/bin/mythtranscode.real -p 27 -c 1111 -s 2009-09-06T22:00:00 -f /mnt/lombardi/mythtv/temp/work/1
2009-10-21 04:28:47.343 Using runtime prefix = /usr
2009-10-21 04:28:47.343 Empty LocalHostName.
2009-10-21 04:28:47.347 New DB connection, total: 1
2009-10-21 04:28:47.350 Closing DB connection named 'DBManager0'
2009-10-21 04:28:47.351 Enabled verbose msgs: important
2009-10-21 04:28:47.352 New DB connection, total: 2
2009-10-21 04:28:47.516 Using protocol version 40
2009-10-21 04:28:47.792 mythtranscode: 0% Completed @ -37.037 fps.
Running ffmpeg
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
Input #0, s16le, from '/mnt/lombardi/mythtv/temp/work/1/audout':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Input #1, rawvideo, from '/mnt/lombardi/mythtv/temp/work/1/vidout':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #1.0: Video: rawvideo, yuv420p, 720x576 [PAR 0:1 DAR 0:1], 29.97 tb(r)
Output #0, dvd, to '/mnt/lombardi/mythtv/temp/work/1/newfile2.mpg':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=5-31, 4771 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=   61 fps=  0 q=1.6 size=     338kB time=2.0 bitrate=1383.1kbits/s    
frame=  112 fps=109 q=2.0 size=     608kB time=3.7 bitrate=1344.8kbits/s    
frame=  164 fps=107 q=2.0 size=     884kB time=5.4 bitrate=1331.5kbits/s    

****-----removed lines---------****

frame= 1921 fps=  3 q=2.0 size=   13838kB time=64.1 bitrate=1769.5kbits/s    
/usr/bin/mythtranscode: line 8: 25497 Killed                  /usr/bin/mythtranscode.real $@
frame= 1921 fps=  3 q=2.0 Lsize=   13860kB time=64.1 bitrate=1772.3kbits/s    
video:11686kB audio:1508kB global headers:0kB muxing overhead 5.055610%
2009-10-21 04:41:19.548 Opening /mnt/lombardi/mythtv/temp/work/1/newfile2.mpg
Input #0, mpeg, from '/mnt/lombardi/mythtv/temp/work/1/newfile2.mpg':
  Duration: 00:01:04.2, start: 0.500000, bitrate: 1767 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 104857 kb/s, 29.97 tb(r)
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
2009-10-21 04:41:19.769 Calculating frame count
2009-10-21 04:41:19.931 frames = 1921
2009-10-21 04:41:19.932 duration = 64
2009-10-21 04:41:19.932 Extracting details from: newfile2.mpg
2009-10-21 04:41:20.021 Cannot find details for newfile2.mpg
2009-10-21 04:41:20.021 File is not a Myth recording.
2009-10-21 04:41:20.021 cutframes = 0
2009-10-21 04:41:20.021 cutduration = 0
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="64" duration="64" filename="/mnt/lombardi/mythtv/temp/work/1/newfile2.mpg" type="mpeg">    
        <streams count="2">        
                <video aspectratio="1.77778" bitrate="104857200" codec="mpeg2video" ffmpegindex="0" fps="29.97" height="480" id="480" start_time="0.45000" streamindex="0" width="720"/>        
                <audio bitrate="192000" channels="2" codec="ac3" ffmpegindex="1" id="128" language="N/A" samplerate="48000" start_time="0.45000" streamindex="1"/>        
        </streams>    
</file>
Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x80 (AC3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Splitting MPEG stream into audio and video parts
Running: mythreplex --demux --fix_sync -o /mnt/lombardi/mythtv/temp/work/1/stream -v 224 -c 128 "/mnt/lombardi/mythtv/temp/work/1/newfile2.mpg"
Reading from /mnt/lombardi/mythtv/temp/work/1/newfile2.mpg
Input file length: 13.54 MB
Checking for TS: failed
Checking for AVI: failed
Checking for PS: confirmed(maybe)
read   1%
Video: aspect ratio: 16:9  size = 720x480  frame rate: 29.970 fps  bit rate: 104.86 Mbit/s
  vbvbuffer 1359872
Sequence Extension: chroma 4:2:0   size = 720x480  bit rate: 104.86 Mbit/s  vbvbuffer 1359872  frame rate: 29.970
starting with video PTS:  0:00:00.5000 
AC3 stream:  bit rate: 192 kb/s  freq: 48000 Hz
  frame size 768
starting audio PTS:  0:00:00.5000 
Video output File is: /mnt/lombardi/mythtv/temp/work/1/stream.mv2
AC30 output File is: /mnt/lombardi/mythtv/temp/work/1/stream0.ac3
STARTING DEMUX
read   2%
read   3%
read   5%
read   6%
video PTS inconsistent:  0:00:06.0722  0:00:06.0722  0:00:06.1389  0:00:05.6389  diff:  0:00:00.0667 

****-----removed lines---------****

read  96%
read  98%
read  99%
read 100%
Audio is already in ac3 format
*************************************************************
Finished processing '/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv'
*************************************************************
Menu items per page 6
Background image file is /usr/share/mythtv/mytharchive/themes/Compact/Compact-Background.png
Music is menumusic.ac3, length is 15 seconds
Creating DVD menus
Menu page 1
Creating Preview Video
Wrapped text  = Page 1
Wrapped text  = 1. Doctor Who
Wrapped text  = Sun Sep 06 10:00 PM
Encoding Menu Page 1 using aspect ratio '16:9'
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
   INFO: [mpeg2enc] Selecting DVD output profile
   INFO: [mpeg2enc] Assuming norm NTSC
   INFO: [mpeg2enc] Progressive input - selecting progressive encoding.
   INFO: [mpeg2enc] Encoding MPEG-2 video to /mnt/lombardi/mythtv/temp/work/temp.m2v
   INFO: [mpeg2enc] Horizontal size: 720 pel
   INFO: [mpeg2enc] Vertical size: 480 pel
   INFO: [mpeg2enc] Aspect ratio code: 3 = 16:9 display
   INFO: [mpeg2enc] Frame rate code:   4 = 30000.0/1001.0 (NTSC VIDEO)
   INFO: [mpeg2enc] Bitrate: 5000 KBit/s
   INFO: [mpeg2enc] Quality factor: 8 (Quantisation = 9) (1=best, 31=worst)
   INFO: [mpeg2enc] Field order for input: none/progressive
   INFO: [mpeg2enc] Sequence unlimited length
   INFO: [mpeg2enc] Search radius: 16
   INFO: [mpeg2enc] DualPrime: no
   INFO: [mpeg2enc] Using one-pass rate controller
   INFO: [mpeg2enc] GOP SIZE RANGE 9 TO 15 
   INFO: [mpeg2enc] Setting colour/gamma parameters to "NTSC"
   INFO: [mpeg2enc] Progressive format frames = 1
   INFO: [mpeg2enc] Using default unmodified quantization matrices
   INFO: [mpeg2enc] Buffering 33 frames
   INFO: [mpeg2enc] SETTING MMX and MMX for QUANTIZER!
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame     0     0 I q=8.00 sum act=278.49375    
   INFO: [mpeg2enc] Frame     1     1 P q=8.00 sum act=291.71902    

****-----removed lines---------****
  
   INFO: [mpeg2enc] Frame   447   447 P q=8.00 sum act=13760.14986    
   INFO: [mpeg2enc] Frame   448   448 P q=8.00 sum act=13773.05750    
   INFO: [mpeg2enc] Sequence end inserted
   INFO: [mpeg2enc] Guesstimated final muxed size = 616756

DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
STAT: 0:00:00.000
INFO: Picture /mnt/lombardi/mythtv/temp/work/backgroundmask-1.png had 2 colors
INFO: Picture /mnt/lombardi/mythtv/temp/work/backgroundmask-1.png had 2 colors
INFO: Constructing blank img
INFO: Pickbuttongroups, success with 1 groups, useimg=1
INFO: Found EOF in .sub file.
INFO: Max_sub_size=296
WARN: Button y coordinates are odd for button 1: 133x77-588x123; they may not display properly.
INFO: 1 subtitles added, 0 subtitles skipped, stream: 32, offset: 0.18

Statistics:
- Processed 0 subtitles.
- The longest display line had -1 characters.
- The maximum number of displayed lines was 0.
- The normal display height of the font arial.ttf was 0.
- The bottom display height of the font arial.ttf was 0.
- The biggest subtitle box had 296 bytes.
Menu items per page 6
Creating DVD XML file for dvd author
Menu page 1
aspect ratio is: 1.77778
aspect ratio is: 1.77778
Total size of video files, before multiplexing, is 11 Mbytes, audio is 1 MBytes, menus are 1 MBytes.
Video will fit onto DVD. 4468.12 MBytes of space remaining on recordable DVD.
Multiplexing MPEG stream to /mnt/lombardi/mythtv/temp/work/1/final.mpg
Adding sync offset of 0ms
Available streams - video and one audio stream
Multiplex started PID=25654
Starting dvdauthor
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing /mnt/lombardi/mythtv/temp/work/1/final.mpg...
STAT: VOBU 16 at 0MB, 1 PGCS
STAT: VOBU 32 at 2MB, 1 PGCS
STAT: VOBU 48 at 4MB, 1 PGCS
STAT: VOBU 64 at 5MB, 1 PGCS
STAT: VOBU 80 at 6MB, 1 PGCS
STAT: VOBU 96 at 8MB, 1 PGCS
STAT: VOBU 112 at 9MB, 1 PGCS
STAT: VOBU 128 at 10MB, 1 PGCS
STAT: VOBU 144 at 11MB, 1 PGCS
STAT: VOBU 160 at 13MB, 1 PGCS
INFO: Video pts = 0.178 .. 63.975
INFO: Audio[0] pts = 0.178 .. 63.474
STAT: VOBU 160 at 13MB, 1 PGCS
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 16:9
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: fixing VOBU at 0MB (17/160, 10%)
STAT: fixing VOBU at 2MB (33/160, 20%)
STAT: fixing VOBU at 4MB (49/160, 30%)
STAT: fixing VOBU at 5MB (65/160, 40%)
STAT: fixing VOBU at 6MB (81/160, 50%)
STAT: fixing VOBU at 8MB (97/160, 60%)
STAT: fixing VOBU at 9MB (113/160, 70%)
STAT: fixing VOBU at 10MB (129/160, 80%)
STAT: fixing VOBU at 11MB (145/160, 90%)
STAT: fixing VOBU at 13MB (161/160, 100%)
STAT: fixed 160 VOBUS                         
INFO: dvdauthor creating table of contents
INFO: Scanning /mnt/lombardi/mythtv/temp/work/dvd/VIDEO_TS/VTS_01_0.IFO
INFO: Creating menu for TOC

STAT: Processing /usr/share/mythtv/mytharchive/intro/ntsc_mythlogo_intro.mpg...
WARN: attempt to update aspect ratio from 16:9 to 4:3; skipping

INFO: Video pts = 0.500 .. 7.473
INFO: Audio[0] pts = 0.500 .. 8.212

STAT: Processing /mnt/lombardi/mythtv/temp/work/menu-1.mpg...
STAT: VOBU 28 at 2MB, 3 PGCS
INFO: Video pts = 0.178 .. 15.159
INFO: Audio[0] pts = 0.178 .. 30.226
INFO: Audio[32] pts = 0.178 .. 0.178
STAT: VOBU 42 at 3MB, 3 PGCS
INFO: Generating VMGM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 16:9
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: fixing VOBU at 1MB (17/42, 38%)
STAT: fixing VOBU at 2MB (33/42, 76%)
STAT: fixed 42 VOBUS                         
Finished  dvdauthor
Creating ISO image
I: -input-charset not specified, using utf-8 (detected in locale settings)
 56.02% done, estimate finish Wed Oct 21 04:41:34 2009
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4248
Path table size(bytes): 42
Max brk space used 0
8952 extents written (17 MB)
Finished creating ISO image
Removing all archive items from the archiveitems DB table
Finished processing jobs!!!

```

progress.log
```

2009-10-21 04:28:46 mythburn.py (0.1.20090515-1-fixes) starting up...
2009-10-21 04:28:46 Found 2 CPUs
2009-10-21 04:28:46 Obtaining MythTV settings from MySQL database for hostname hobie-desktop
2009-10-21 04:28:46 temppath: /mnt/lombardi/mythtv/temp/work
2009-10-21 04:28:46 logpath:  /mnt/lombardi/mythtv/temp/logs
2009-10-21 04:28:46 Setting process priority to 17
2009-10-21 04:28:46 Processing Mythburn job number 1.
2009-10-21 04:28:46 Options - mediatype = 0, doburn = 0, createiso = 1, erasedvdrw = 0
2009-10-21 04:28:46           savefilename = ''
2009-10-21 04:28:46 Looking for: /usr/share/mythtv/mytharchive/themes/Compact/theme.xml
2009-10-21 04:28:46 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 19
2009-10-21 04:28:46 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 15
2009-10-21 04:28:46 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 13
2009-10-21 04:28:46 wantIntro: 1, wantMainMenu: 1, wantChapterMenu:0, wantDetailsPage: 0
2009-10-21 04:28:46 Final DVD Video format will be ntsc
2009-10-21 04:28:46 There are 1 files to process
2009-10-21 04:28:46 Pre-processing recording 1: '/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv'
2009-10-21 04:28:46           Doctor Who
2009-10-21 04:28:47 Video resolution is 720 by 576
2009-10-21 04:28:47 *************************************************************
2009-10-21 04:28:47 Processing recording 1: '/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv'
2009-10-21 04:28:47 *************************************************************
2009-10-21 04:28:47 File type is 'nuv'
2009-10-21 04:28:47 Video codec is 'mpeg4'
2009-10-21 04:28:47 Preferred audio languages eng and eng
2009-10-21 04:28:47 Video id: 0x0, Audio1: [1] 0x1 (MP3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
2009-10-21 04:28:47 Aspect ratio is 16:9
2009-10-21 04:28:47 Re-encoding audio and video from nuv file
2009-10-21 04:28:47 Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_ntsc.xml
2009-10-21 04:28:47 Encoding profile (SP) found
2009-10-21 04:28:47 mythtranscode started PID = 25493
2009-10-21 04:28:47 WARNING: frames rates do not match
2009-10-21 04:28:47 The frame rate for ntsc should be 29.97 but the stream info file report a fps of 59.9401
2009-10-21 04:28:47 Waiting for mythtranscode to create the fifos
2009-10-21 04:28:48 Running ffmpeg
2009-10-21 04:41:21 Preferred audio languages eng and eng
2009-10-21 04:41:21 Video id: 0x1e0, Audio1: [1] 0x80 (AC3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
2009-10-21 04:41:21 Splitting MPEG stream into audio and video parts
2009-10-21 04:41:21 Running: mythreplex --demux --fix_sync -o /mnt/lombardi/mythtv/temp/work/1/stream -v 224 -c 128 "/mnt/lombardi/mythtv/temp/work/1/newfile2.mpg"
2009-10-21 04:41:21 Audio is already in ac3 format
2009-10-21 04:41:21 *************************************************************
2009-10-21 04:41:21 Finished processing '/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv'
2009-10-21 04:41:21 *************************************************************
2009-10-21 04:41:21 Menu items per page 6
2009-10-21 04:41:22 Background image file is /usr/share/mythtv/mytharchive/themes/Compact/Compact-Background.png
2009-10-21 04:41:22 Music is menumusic.ac3, length is 15 seconds
2009-10-21 04:41:22 Creating DVD menus
2009-10-21 04:41:22 Menu page 1
2009-10-21 04:41:22 Creating Preview Video
2009-10-21 04:41:23 Encoding Menu Page 1 using aspect ratio '16:9'
2009-10-21 04:41:33 Menu items per page 6
2009-10-21 04:41:33 Creating DVD XML file for dvd author
2009-10-21 04:41:33 Menu page 1
2009-10-21 04:41:33 aspect ratio is: 1.77778
2009-10-21 04:41:33 aspect ratio is: 1.77778
2009-10-21 04:41:33 Total size of video files, before multiplexing, is 11 Mbytes, audio is 1 MBytes, menus are 1 MBytes.
2009-10-21 04:41:33 Video will fit onto DVD. 4468.12 MBytes of space remaining on recordable DVD.
2009-10-21 04:41:33 Multiplexing MPEG stream to /mnt/lombardi/mythtv/temp/work/1/final.mpg
2009-10-21 04:41:33 Adding sync offset of 0ms
2009-10-21 04:41:33 Available streams - video and one audio stream
2009-10-21 04:41:33 Multiplex started PID=25654
2009-10-21 04:41:33 Starting dvdauthor
2009-10-21 04:41:34 Finished  dvdauthor
2009-10-21 04:41:34 Creating ISO image
2009-10-21 04:41:34 Finished creating ISO image
2009-10-21 04:41:34 Removing all archive items from the archiveitems DB table
2009-10-21 04:41:35 Finished processing jobs!!!

```

---

### Post by wooddealer on 2009-10-21
Upon further investigation I notice that the duration of the of the show is changed significantly by ffmpeg and I'm not sure why.  Maybe the 60fps isn't handled properly?


mythburn.log
```

File type is 'nuv'
Video codec is 'mpeg4'
2009-10-21 04:28:47.124 Opening /mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv
Input #0, nuv, from '/mnt/lombardi/mythtv/recorded/1111_20090906220000.nuv':
  **Duration: 43:37:51.4**, start: 53861.391000, bitrate: 127 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 16:9 DAR 20:9], 59.94 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s


...

running ffmpeg

...

2009-10-21 04:41:19.548 Opening /mnt/lombardi/mythtv/temp/work/1/newfile2.mpg
Input #0, mpeg, from '/mnt/lombardi/mythtv/temp/work/1/newfile2.mpg':
  **Duration: 00:01:04.2**, start: 0.500000, bitrate: 1767 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 104857 kb/s, 29.97 tb(r)
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 192 kb/s


```

---

