---
title: "Mytharchive Fails with Mythtv 0.21"
date: 2008-03-19
forum: Mythbuntu
---

### Post by ahood on 2008-03-19
Last week I updated Mythbuntu based on Gutsy to Mythtv version 0.21 via the update manager. I am trying to burn two recordings to a single DVD-R disc. 

Every time, Mytharchive ends in a failure. The original recordings are non-HD (i.e., standard definition NTSC TV), 480x480, mpeg files recorded with Mythtv 0.21.

**[COLOR="Blue"]ATTEMPTED SOLUTIONS SO FAR BUT FAILED[/COLOR]**
I have deleted the /home/user/.ICEauthority file, so that isn't causing the termination.

The temp files are stored in /home/user/temp, the owner of which is the user, the group is the username, and the permissions is read and write for owner, group, and others. I changed the group to mythtv for this directory and all subdirectories and files it contains but mytharchive still terminates.

A google search for mythtv demux "standard IDs (0xc0 or 0xe0)" turned up this post [[vdr] Basic shell problems / stdin / requant]("http://linvdr.org/mailinglists/vdr/2005/03/msg00716.html"), but it is old...


**[COLOR="Blue"]MORE INFORMATION[/COLOR]**
The mythburn.log and progress.log files are below...

I would be very grateful if someone could point me to a possible solution.

**[COLOR="Blue"]MYTHBURN.LOG[/COLOR]**
> Using simple_fix_rtl
mythburn.py (0.1.20080127-1) starting up...
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /home/alan/temp/config/mydata.xml
passed progress log file: /home/alan/temp/logs/progress.log
mythburn.py (0.1.20080127-1) starting up...
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Found 1 CPUs
Obtaining MythTV settings from MySQL database for hostname mythbuntu
temppath: /home/alan/temp/work
logpath:  /home/alan/temp/logs
Setting process priority to 17
Processing Mythburn job number 1.
Options - mediatype = 0, doburn = 1, createiso = 0, erasedvdrw = 0
          savefilename = ''
Looking for: /usr/share/mythtv/mytharchive/themes/MythCenter - Animated/theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 19
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 15
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 13
wantIntro: 1, wantMainMenu: 1, wantChapterMenu:1, wantDetailsPage: 0
Final DVD Video format will be ntsc
There are 2 files to process
Pre-processing file '/mnt/mythcontent/recordings/1060_20080302210000.mpg' of type 'recording'
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2008-03-19 05:10:54.344 Opening /mnt/mythcontent/recordings/1060_20080302210000.mpg
Input #0, mpeg, from '/mnt/mythcontent/recordings/1060_20080302210000.mpg':
  Duration: 00:59:56.7, start: 0.289389, bitrate: 5188 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480 [PAR 4:3 DAR 4:3], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
2008-03-19 05:10:54.376 duration = 3596
2008-03-19 05:10:54.376 Extracting details from: 1060_20080302210000.mpg
2008-03-19 05:10:54.377 chanid: 1060 starttime:2008-03-02T21:00:00 
2008-03-19 05:10:54.383 File is a Myth recording.
2008-03-19 05:10:54.384 cutframes = 29737
2008-03-19 05:10:54.384 cutduration = 992
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="2604" duration="3596" filename="/mnt/mythcontent/recordings/1060_20080302210000.mpg" type="mpeg">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffmpegindex="0" fps="29.97" height="480" id="480" start_time="0.36038" streamindex="0" width="480"/>        
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="448" language="N/A" samplerate="48000" start_time="0.26045" streamindex="1"/>        
        </streams>    
</file>
          The Human Body: Pushing the Limits
Video resolution is 480 by 480
Pre-processing file '/mnt/mythcontent/recordings/1060_20080309210000.mpg' of type 'recording'
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2008-03-19 05:10:54.669 Opening /mnt/mythcontent/recordings/1060_20080309210000.mpg
Input #0, mpeg, from '/mnt/mythcontent/recordings/1060_20080309210000.mpg':
  Duration: 01:04:56.8, start: 0.289444, bitrate: 5190 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480 [PAR 4:3 DAR 4:3], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
2008-03-19 05:10:54.701 duration = 3896
2008-03-19 05:10:54.701 Extracting details from: 1060_20080309210000.mpg
2008-03-19 05:10:54.702 chanid: 1060 starttime:2008-03-09T21:00:00 
2008-03-19 05:10:54.708 File is a Myth recording.
2008-03-19 05:10:54.709 cutframes = 38498
2008-03-19 05:10:54.709 cutduration = 1284
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="2612" duration="3896" filename="/mnt/mythcontent/recordings/1060_20080309210000.mpg" type="mpeg">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffmpegindex="0" fps="29.97" height="480" id="480" start_time="0.36039" streamindex="0" width="480"/>        
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="448" language="N/A" samplerate="48000" start_time="0.26050" streamindex="1"/>        
        </streams>    
</file>
          The Human Body: Pushing the Limits
Video resolution is 480 by 480
*************************************************************
Processing file /mnt/mythcontent/recordings/1060_20080302210000.mpg of type recording
*************************************************************
File type is 'mpeg'
Video codec is 'mpeg2video'
File has a cut list - running mythtrancode to remove unwanted segments
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2008-03-19 05:10:54.922 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-19 05:10:54.923 DBHostName is not set in mysql.txt
2008-03-19 05:10:54.923 Assuming localhost
2008-03-19 05:10:54.923 Empty LocalHostName.
2008-03-19 05:10:54.937 New DB connection, total: 1
2008-03-19 05:10:54.943 Closing DB connection named 'DBManager0'
2008-03-19 05:10:54.943 Enabled verbose msgs: important
2008-03-19 05:10:54.946 New DB connection, total: 2
Mux rate: 6.49 Mbit/s
File will be re-encoded using profile SP
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2008-03-19 05:12:46.935 Opening /home/alan/temp/work/1/newfile.mpg
Input #0, mpeg, from '/home/alan/temp/work/1/newfile.mpg':
  Duration: 00:43:24.6, start: 0.308300, bitrate: 4959 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480 [PAR 4:3 DAR 4:3], 6000 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
2008-03-19 05:12:47.004 duration = 2604
2008-03-19 05:12:47.004 Extracting details from: newfile.mpg
2008-03-19 05:12:47.006 Cannot find details for newfile.mpg
2008-03-19 05:12:47.006 File is not a Myth recording.
2008-03-19 05:12:47.006 cutframes = 0
2008-03-19 05:12:47.006 cutduration = 0
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="2604" duration="2604" filename="/home/alan/temp/work/1/newfile.mpg" type="mpeg">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffmpegindex="0" fps="29.97" height="480" id="480" start_time="0.27747" streamindex="0" width="480"/>        
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="448" language="N/A" samplerate="48000" start_time="0.27885" streamindex="1"/>        
        </streams>    
</file>
Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x1c0 (MP2, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Aspect ratio is 4:3
Re-encoding audio and video
Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_ntsc.xml
Encoding profile (SP) found
ffmpeg -v 1 -i "/home/alan/temp/work/1/newfile.mpg" -r ntsc -target dvd -b 4771k -s 720x480 -acodec ac3 -ab 192k -ac 2 -copyts -aspect 4:3 "/home/alan/temp/work/1/newfile2.mpg" -map 0:0 -map 0:1 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from '/home/alan/temp/work/1/newfile.mpg':
  Duration: 00:43:24.2, start: 0.308300, bitrate: 4960 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Assuming NTSC for target.
Output #0, dvd, to '/home/alan/temp/work/1/newfile2.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=2-31, 4771 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[mpeg2video @ 0xb7e49a68]ac-tex damaged at 2 24itrate=5087.2kbits/s     
[mpeg2video @ 0xb7e49a68]Warning MVs not available
[mpeg2video @ 0xb7e49a68]concealing 180 DC, 180 AC, 180 MV errors
[mpeg2video @ 0xb7e49a68]ac-tex damaged at 29 24
[mpeg2video @ 0xb7e49a68]Warning MVs not available
[mpeg2video @ 0xb7e49a68]concealing 180 DC, 180 AC, 180 MV errors
frame=78060 q=5.2 Lsize= 1617424kB time=2604.1 bitrate=5088.2kbits/s    
video:1516994kB audio:61033kB global headers:0kB muxing overhead 2.496633%
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2008-03-19 05:50:04.184 Opening /home/alan/temp/work/1/newfile2.mpg
Input #0, mpeg, from '/home/alan/temp/work/1/newfile2.mpg':
  Duration: 00:43:24.5, start: 0.500000, bitrate: 5087 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 9000 kb/s, 29.97 tb(r)
    Stream #0.1[0x80]: Audio: liba52, 48000 Hz, stereo, 192 kb/s
2008-03-19 05:50:04.269 Calculating frame count
2008-03-19 05:50:30.707 frames = 78060
2008-03-19 05:50:30.734 duration = 2604
2008-03-19 05:50:30.743 Extracting details from: newfile2.mpg
2008-03-19 05:50:30.767 Cannot find details for newfile2.mpg
2008-03-19 05:50:30.767 File is not a Myth recording.
2008-03-19 05:50:30.768 cutframes = 0
2008-03-19 05:50:30.768 cutduration = 0
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="2604" duration="2604" filename="/home/alan/temp/work/1/newfile2.mpg" type="mpeg">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="9000000" codec="mpeg2video" ffmpegindex="0" fps="29.97" height="480" id="480" start_time="0.45000" streamindex="0" width="720"/>        
                <audio bitrate="192000" channels="2" codec="liba52" ffmpegindex="1" id="128" language="N/A" samplerate="48000" start_time="0.45000" streamindex="1"/>        
        </streams>    
</file>
Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x80 (LIBA52, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Splitting MPEG stream into audio and video parts
Running: mythreplex --demux --fix_sync -o /home/alan/temp/work/1/stream -v 224 "/home/alan/temp/work/1/newfile2.mpg"
Reading from /home/alan/temp/work/1/newfile2.mpg
Input file length: 1579.52 MB
Checking for TS: failed
Checking for AVI: failed
Checking for PS: confirmed(maybe)
Video: aspect ratio: 4:3  size = 720x480  frame rate: 29.970 fps  bit rate: 9.00 Mbit/s
  vbvbuffer 1835008
Sequence Extension: chroma 4:2:0   size = 720x480  bit rate: 9.00 Mbit/s  vbvbuffer 1835008  frame rate: 29.970
starting with video PTS:  0:00:00.5000 
Video output File is: /home/alan/temp/work/1/stream.mv2
Audio0 output File is: /home/alan/temp/work/1/stream0.mp2
STARTING DEMUX
read 100%
Can't find all required streams
Please check if audio and video have standard IDs (0xc0 or 0xe0)
************************************************************
ERROR: Failed while running mythreplex. Command was mythreplex --demux --fix_sync -o /home/alan/temp/work/1/stream -v 224 "/home/alan/temp/work/1/newfile2.mpg"
************************************************************

Terminated

[B][COLOR="Blue"]
PROGRESS.LOG[/COLOR][/B]
> 2008-03-19 05:10:49 mythburn.py (0.1.20080127-1) starting up...
2008-03-19 05:10:49 Found 1 CPUs
2008-03-19 05:10:49 Obtaining MythTV settings from MySQL database for hostname mythbuntu
2008-03-19 05:10:49 temppath: /home/alan/temp/work
2008-03-19 05:10:49 logpath:  /home/alan/temp/logs
2008-03-19 05:10:49 Setting process priority to 17
2008-03-19 05:10:49 Processing Mythburn job number 1.
2008-03-19 05:10:49 Options - mediatype = 0, doburn = 1, createiso = 0, erasedvdrw = 0
2008-03-19 05:10:49           savefilename = ''
2008-03-19 05:10:49 Looking for: /usr/share/mythtv/mytharchive/themes/MythCenter - Animated/theme.xml
2008-03-19 05:10:49 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 19
2008-03-19 05:10:49 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 15
2008-03-19 05:10:49 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 13
2008-03-19 05:10:49 wantIntro: 1, wantMainMenu: 1, wantChapterMenu:1, wantDetailsPage: 0
2008-03-19 05:10:49 Final DVD Video format will be ntsc
2008-03-19 05:10:49 There are 2 files to process
2008-03-19 05:10:54 Pre-processing file '/mnt/mythcontent/recordings/1060_20080302210000.mpg' of type 'recording'
2008-03-19 05:10:54           The Human Body: Pushing the Limits
2008-03-19 05:10:54 Video resolution is 480 by 480
2008-03-19 05:10:54 Pre-processing file '/mnt/mythcontent/recordings/1060_20080309210000.mpg' of type 'recording'
2008-03-19 05:10:54           The Human Body: Pushing the Limits
2008-03-19 05:10:54 Video resolution is 480 by 480
2008-03-19 05:10:54 *************************************************************
2008-03-19 05:10:54 Processing file /mnt/mythcontent/recordings/1060_20080302210000.mpg of type recording
2008-03-19 05:10:54 *************************************************************
2008-03-19 05:10:54 File type is 'mpeg'
2008-03-19 05:10:54 Video codec is 'mpeg2video'
2008-03-19 05:10:54 File has a cut list - running mythtrancode to remove unwanted segments
2008-03-19 05:12:45 File will be re-encoded using profile SP
2008-03-19 05:12:47 Preferred audio languages eng and eng
2008-03-19 05:12:47 Video id: 0x1e0, Audio1: [1] 0x1c0 (MP2, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
2008-03-19 05:12:47 Aspect ratio is 4:3
2008-03-19 05:12:47 Re-encoding audio and video
2008-03-19 05:12:47 Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_ntsc.xml
2008-03-19 05:12:47 Encoding profile (SP) found
2008-03-19 05:12:47 ffmpeg -v 1 -i "/home/alan/temp/work/1/newfile.mpg" -r ntsc -target dvd -b 4771k -s 720x480 -acodec ac3 -ab 192k -ac 2 -copyts -aspect 4:3 "/home/alan/temp/work/1/newfile2.mpg" -map 0:0 -map 0:1 
2008-03-19 05:50:30 Preferred audio languages eng and eng
2008-03-19 05:50:30 Video id: 0x1e0, Audio1: [1] 0x80 (LIBA52, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
2008-03-19 05:50:30 Splitting MPEG stream into audio and video parts
2008-03-19 05:50:30 Running: mythreplex --demux --fix_sync -o /home/alan/temp/work/1/stream -v 224 "/home/alan/temp/work/1/newfile2.mpg"
2008-03-19 05:53:12 ************************************************************
2008-03-19 05:53:12 ERROR: Failed while running mythreplex. Command was mythreplex --demux --fix_sync -o /home/alan/temp/work/1/stream -v 224 "/home/alan/temp/work/1/newfile2.mpg"
2008-03-19 05:53:12 ************************************************************
2008-03-19 05:53:12 
2008-03-19 05:53:12 Terminated


**SOLVED**
*Mytharchive will burn to DVD TV recordings that are 720x480 resolution but not the default 480x480 resolution (see post below for more info).*

---

### Post by muken on 2008-03-21
I also get the same result after upgrading from 0.20 to 0.21 last week.

When running mythplex after transcoding to the LP profile I get the following result in the mythburn.log:

> 
Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x80 (LIBA52, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Splitting MPEG stream into audio and video parts
Running: mythreplex --demux --fix_sync -o /opt/mythtv/mytharchive/work/1/stream -v 224 "/opt/mythtv/mytharchive/work/1/newfile2.mpg"
Reading from /opt/mythtv/mytharchive/work/1/newfile2.mpg
Input file length: 526.68 MB
Checking for TS: failed
Checking for AVI: failed
Checking for PS: confirmed(maybe)
Video: aspect ratio: 16:9  size = 352x576  frame rate: 25.000 fps  bit rate: 9.00 Mbit/s
  vbvbuffer 1835008
Sequence Extension: chroma 4:2:0   size = 352x576  bit rate: 9.00 Mbit/s  vbvbuffer 1835008  frame rate: 25.000
starting with video PTS:  0:00:00.5000
Video output File is: /opt/mythtv/mytharchive/work/1/stream.mv2
Audio0 output File is: /opt/mythtv/mytharchive/work/1/stream0.mp2
STARTING DEMUX
video DTS inconsistent:  0:28:05.0200  0:28:05.0200  0:28:05.1000  0:28:04.6000 diff:  0:00:00.0800
video PTS inconsistent:  0:28:05.0600  0:28:05.0600  0:28:05.1800  0:28:04.6800  diff:  0:00:00.1200
video DTS inconsistent:  0:28:05.0200  0:28:05.0200  0:28:05.1400  0:28:04.6400 diff:  0:00:00.1200
video PTS inconsistent:  0:28:05.2200  0:28:05.2200  0:28:05.3000  0:28:04.8000  diff:  0:00:00.0800
video DTS inconsistent:  0:28:05.1800  0:28:05.1800  0:28:05.2600  0:28:04.7600 diff:  0:00:00.0800
video PTS inconsistent:  0:28:05.5000  0:28:05.5000  0:28:05.5800  0:28:05.0800  diff:  0:00:00.0800
video DTS inconsistent:  0:28:05.4600  0:28:05.4600  0:28:05.5400  0:28:05.0400 diff:  0:00:00.0800
video PTS inconsistent:  0:28:05.5000  0:28:05.5000  0:28:05.6200  0:28:05.1200  diff:  0:00:00.1200
video DTS inconsistent:  0:28:05.4600  0:28:05.4600  0:28:05.5800  0:28:05.0800 diff:  0:00:00.1200
video PTS inconsistent:  0:28:05.6600  0:28:05.6600  0:28:05.7400  0:28:05.2400  diff:  0:00:00.0800
video DTS inconsistent:  0:28:05.6200  0:28:05.6200  0:28:05.7000  0:28:05.2000 diff:  0:00:00.0800
video PTS inconsistent:  0:28:05.6600  0:28:05.6600  0:28:05.7800  0:28:05.2800  diff:  0:00:00.1200
video DTS inconsistent:  0:28:05.6200  0:28:05.6200  0:28:05.7400  0:28:05.2400 diff:  0:00:00.1200
video PTS inconsistent:  0:28:05.6600  0:28:05.6600  0:28:05.8200  0:28:05.3200  diff:  0:00:00.1600
video DTS inconsistent:  0:28:05.6200  0:28:05.6200  0:28:05.7800  0:28:05.2800 diff:  0:00:00.1600
video PTS inconsistent:  0:28:05.9800  0:28:05.9800  0:28:06.0600  0:28:05.5600  diff:  0:00:00.0800
video DTS inconsistent:  0:28:05.9400  0:28:05.9400  0:28:06.0200  0:28:05.5200 diff:  0:00:00.0800
video PTS inconsistent:  0:28:06.1000  0:28:06.1000  0:28:06.1800  0:28:05.6800  diff:  0:00:00.0800
video DTS inconsistent:  0:28:06.0600  0:28:06.0600  0:28:06.1400  0:28:05.6400 diff:  0:00:00.0800
video PTS inconsistent:  0:28:06.1000  0:28:06.1000  0:28:06.2200  0:28:05.7200  diff:  0:00:00.1200
video DTS inconsistent:  0:28:06.0600  0:28:06.0600  0:28:06.1800  0:28:05.6800 diff:  0:00:00.1200
video PTS inconsistent:  0:28:06.1000  0:28:06.1000  0:28:06.2600  0:28:05.7600  diff:  0:00:00.1600
video DTS inconsistent:  0:28:06.0600  0:28:06.0600  0:28:06.2200  0:28:05.7200 diff:  0:00:00.1600
video PTS inconsistent:  0:28:06.5000  0:28:06.5000  0:28:06.5800  0:28:06.0800  diff:  0:00:00.0800
video DTS inconsistent:  0:28:06.4600  0:28:06.4600  0:28:06.5400  0:28:06.0400 diff:  0:00:00.0800
video PTS inconsistent:  0:28:06.6200  0:28:06.6200  0:28:06.7000  0:28:06.2000  diff:  0:00:00.0800
video DTS inconsistent:  0:28:06.5800  0:28:06.5800  0:28:06.6600  0:28:06.1600 diff:  0:00:00.0800
video PTS inconsistent:  0:28:06.6200  0:28:06.6200  0:28:06.7400  0:28:06.2400  diff:  0:00:00.1200
video DTS inconsistent:  0:28:06.5800  0:28:06.5800  0:28:06.7000  0:28:06.2000 diff:  0:00:00.1200
video PTS inconsistent:  0:28:06.9400  0:28:06.9400  0:28:07.0200  0:28:06.5200  diff:  0:00:00.0800
video DTS inconsistent:  0:28:06.9000  0:28:06.9000  0:28:06.9800  0:28:06.4800 diff:  0:00:00.0800
video PTS inconsistent:  0:28:06.9400  0:28:06.9400  0:28:07.0600  0:28:06.5600  diff:  0:00:00.1200
video DTS inconsistent:  0:28:06.9000  0:28:06.9000  0:28:07.0200  0:28:06.5200 diff:  0:00:00.1200
video PTS inconsistent:  0:28:06.9400  0:28:06.9400  0:28:07.1000  0:28:06.6000  diff:  0:00:00.1600
video DTS inconsistent:  0:28:06.9000  0:28:06.9000  0:28:07.0600  0:28:06.5600 diff:  0:00:00.1600
read 100%
Can't find all required streams
Please check if audio and video have standard IDs (0xc0 or 0xe0)
************************************************************
ERROR: Failed while running mythreplex. Command was mythreplex --demux --fix_sync -o /opt/mythtv/mytharchive/work/1/stream -v 224 "/opt/mythtv/mytharchive/work/1/newfile2.mpg"
************************************************************

Terminated


Any ideas?

---

### Post by muken on 2008-03-21
> **muken said:**
> I also get the same result after upgrading from 0.20 to 0.21 last week.

When running mythplex after transcoding to the LP profile I get the following result in the mythburn.log:


When trying to use mytharchive on another DVB-T recording which has NOT been transcoded I get this result in the mythburn.log:

> Preferred audio languages eng and eng
Didn't find any audio elements in stream info file.!!!

---

### Post by ahood on 2008-03-22
Thanks for the replies Muken!

I have made several attempts at getting mytharchive to burn a DVD. After a lot of google searching, I tried the following possible fixes....

**1. Unchecked cutlist to disable the removing of commercials.**

Result - Same error as I mentioned above. Mytharchive could not burn DVD.

**2. Enable Projectx and Disabled Mythtranscode**

Result - Projectx failed to start. Mytharchive could not burn DVD.

**3. Recorded a show using 720x480 resolution and retained commercials**

Result - SUCCESS! Mytharchive burned DVD, although there were still error messages after the media was ejected. "Don't Re-encode" was selected in Mytharchive by default instead of SP. 


Things to do...

1. Enable cutlist checkbox in Mytharchive to remove commercials of the 720x480 recording.

2. Use Mytharchive to burn a 480x480 recording to DVD disk making sure that I select "Don't Re-encode" instead of SP/LP.

I will post again what I find out after doing the two additional steps above.

I am highly interested in other work-arounds/solutions that Mythbuntu users find/discover for the Mytharchive error described above (post here! :) ).

---

### Post by ahood on 2008-03-22
I have tested the following and this is what happened.

**1. Checked the cutlist checkbox in Mytharchive to remove commercials of a 720x480 recording and "Don't Re-encode" was used instead of SP/LP.**

Mytharchive successfully saved the recording to a DVD disk.

**2. Checked the cutlist checkbox in Mytharchive to remove commercials of a 480x480 recording and "Don't Re-encode" was used instead of SP/LP, etc.**

Mytharchive failed to burn the recording to a DVD disk. The error message is the same as the one I posted above in the original message.


**SUMMARY**

[LIST]
[*]Mytharchive does not burn to DVD TV recording save in 480x480 resolution.
[*]Mytharchive will burn to DVD TV recordings saved in 720x480 resolution.
[/LIST]

---

### Post by tpeerd on 2008-03-24
I also had success when I didn't re-encode the file to be burned on DVD. But the menu's and chapters don't appear in that way.

---

### Post by Cryophallion on 2008-03-24
Having same problem here. I could burn dvd's of just about anything before, but not now.

Tried the following earlier today:

1920x1080, no cut list, 2 hours in SP - failed
720x480, cut list, SP also - Failed

I had no problems with this before the upgrade.

I never saw mythreplex before though either, it would just show removing the cutlist, then re-encoding, but I never saw anything for replex.

Has anyone filed a bug yet?

---

### Post by Slitz76 on 2008-03-25
hi,

I've got the same problem with Mythtv 0.21, mythreplex fails if using any re-encoding profiles and succeeds only if burning the DVD with option "Don't Re-encode".

How could I install the old (0.20.2) version of mythreplex, with what package?

---

### Post by muken on 2008-03-26
> **ahood said:**
> **SOLVED**
*Mytharchive will burn to DVD TV recordings that are 720x480 resolution but not the default 480x480 resolution (see post below for more info).*

Well, the DVB broadcasts over here are broadcasted in 720x576 which doesn't work with mytharchive.

---

### Post by Slitz76 on 2008-03-26
i think the problem is not in the video resolution but in the audio stream(s).

My mythburn.log is:

```
Can't find all required streams
Please check if audio and video have standard IDs (0xc0 or 0xe0)
************************************************************
ERROR: Failed while running mythreplex. Command was mythreplex --demux --fix_sync -o /usr/share/mythtv/mytharchive/temp/work/1/stream -v 224 "/usr/share/mythtv/mytharchive/temp/work/1/newfile2.mpg"
************************************************************
```


and the files in the work/1 directory are:

```
New"]root@telefunken:/usr/share/mythtv/mytharchive/temp/work/1# ll
total 685224
drwxrwxrwx  2 mythtv mythtv        64 2008-03-26 02:38 .
drwxrwxrwx 15 mythtv mythtv      8192 2008-03-26 02:21 ..
-rw-rw-rw-  1 mythtv mythtv       644 2008-03-26 02:21 info.xml
-rw-rw-rw-  1 mythtv mythtv 373313536 2008-03-26 02:38 newfile2.mpg
-rw-rw-rw-  1 mythtv mythtv     58443 2008-03-26 02:23 newfile.mpg.map
**-rw-rw-rw-  1 mythtv mythtv         0 2008-03-26 02:38 stream0.mp2**
-rw-rw-rw-  1 mythtv mythtv       578 2008-03-26 02:21 streaminfo_orig.xml
-rw-rw-rw-  1 mythtv mythtv       521 2008-03-26 02:38 streaminfo.xml
-rw-rw-rw-  1 mythtv mythtv 328250592 2008-03-26 02:39 stream.mv2

```
so looks like the stream0.mp2 (audio data) is empty.

Earlier in the log was:

```
Input #0, mpegts, from '/var/lib/mythtv/recordings/4352_20080221093000.mpg':
  Duration: 18:55:48.2, start: 6224.338267, bitrate: 101 kb/s
    **Stream #0.0[0x200]: Video: mpeg2video**, yuv420p, 704x576 [PAR 16:11 DAR 16:9], 5000 kb/s, 25.00 tb(r)
    **Stream #0.1[COLOR="Red"][0x28a](fin)[/COLOR]: Audio: mp2**, 48000 Hz, stereo, 224 kb/s
    Stream #0.2[0x240](fin): Data: 0x0000
2008-03-26 02:21:51.019 duration = 68148
2008-03-26 02:21:51.019 Extracting details from: 4352_20080221093000.mpg
2008-03-26 02:21:51.022 chanid: 4352 starttime:2008-02-21T09:30:00 
2008-03-26 02:21:51.032 File is a Myth recording.

```

And when it was encoded with ffmpeg the log said:

```
Encoding profile (EP) found
ffmpeg -v 1 -i "/usr/share/mythtv/mytharchive/temp/work/1/newfile.mpg" -r pal -target dvd -b 1526k -s 352x288 -acodec ac3 -ab 12
8k -ac 2 -copyts -aspect 16:9 "/usr/share/mythtv/mytharchive/temp/work/1/newfile2.mpg" -map 0:0 -map 0:1 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-lib
ogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, mpeg, from '/usr/share/mythtv/mytharchive/temp/work/1/newfile.mpg':
  Duration: 00:29:54.8, start: 0.360000, bitrate: 3519 kb/s
  **Stream #0.0[0x1e0]: Video: mpeg2video**, yuv420p, 704x576, 5000 kb/s, 25.00 fps(r)
  **Stream #0.1[COLOR="Red"][0x1c0][/COLOR]: Audio: mp2**, 48000 Hz, stereo, 224 kb/s
Assuming PAL for target.
Output #0, dvd, to '/usr/share/mythtv/mytharchive/temp/work/1/newfile2.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 352x288, q=2-31, 1526 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 128 kb/s
```

So looks like ffmpeg doesnt identify the audio stream correctly?

---

### Post by Slitz76 on 2008-03-26
ok, I played with the encoding profiles and ffmpeg and found a solution:

I changed duplicated "EP" profile in ffmpeg_dvd_pal.xml (copy+paste the lines between <profile>.....</profile> and gave another name for it.)

Also changed the ffmpeg parameter "-acodec" from "ac3" --> "copy" and added parameter "-alang" with value "fin" (for Finnish language) so my profile is:

```
    <profile>
        <name>MYPROFILE</name>
        <description>Same as EP - approx. 6 hour of video on a single layer DVD but trying to fix ffmpeg audio lang problems</description>
        <bitrate>671.48</bitrate>
        <passes>1</passes>
        <parameter name="-v"      value="1"/>
        <parameter name="-i"      value="%inputfile"/>
        <parameter name="-r"      value="pal"/>
        <parameter name="-target" value="dvd"/>
        <parameter name="-b"      value="1526k"/>
        <parameter name="-s"      value="352x288"/>
        <parameter name="-acodec" value="copy"/>
        <parameter name="-alang"  value="fin"/>
        <parameter name="-ab"     value="128k"/>
        <parameter name="-ac"     value="2"/>
        <parameter name="-copyts" value=""/>
        <parameter name="-aspect" value="%aspect"/>
        <parameter name=""        value="%outputfile"/>
    </profile>


```

and now its re-encoding with no problems:
```

Audio track 1 is in mp2 format - NOT re-encoding to ac3
*************************************************************
Finished processing file /var/lib/mythtv/recordings/4352_20080225130000.mpg
*************************************************************

```

Mytharchive hasn't yet finished the whole project so I'll post the full results later, so does the final DVD has sound at all or does my DVD player identify the lang as Finnish or something else.

---

### Post by Slitz76 on 2008-03-26
ok, mytharchive created the project ok but it is too big.

It told size would be 4.4Gb but ended 4.8Gb and doesn't fit on SL-DVD. Overhead approx 9-10%, my guess is due to the different audio format mp2 that consumes more space than ac3?

Need to rebuild the project with fewer files and see what happens.

---

### Post by muken on 2008-03-28
Interesting...

I just checked the setting "Always Encode to AC3" in the settings for mytharchive.

Now I get an invalid floating point 0.-3600, but mythreplex came through this time. The mythtranscode also fails...

Anyone else getting this?

> 
Mux rate: 8.13 Mbit/s
ICE default IO error handler doing an exit(), pid = 13927, errno = 32
[COLOR="Red"]Failed while running mythtranscode to cut commercials and/or clean up an mpeg2 file.
Result: 1, Command was mythtranscode --mpeg2 -c 1008 -s 2008-02-24T16:00:00 -o /opt/mythtv/mytharchive/work/1/newfile.mpg
Failed to run mythtrancode to fix any errors[/COLOR]
2008-03-28 07:00:26.033 Opening /opt/mythtv/recordings/1008_20080224160000.mpg
Input #0, mpegts, from '/opt/mythtv/recordings/1008_20080224160000.mpg':
  Duration: 11:39:05.0, start: 0.-40000, bitrate: 248 kb/s
    Stream #0.0[0x3ab]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 8000 kb/s, 25.00 tb(r)
    Stream #0.1[0x3aa]: Audio: mp3
    Stream #0.2[0x3a8](swe): Data: 0x0000
2008-03-28 07:00:26.122 Calculating frame count
2008-03-28 07:00:53.619 frames = 89853
2008-03-28 07:00:53.648 duration = 3594
2008-03-28 07:00:53.670 Extracting details from: 1008_20080224160000.mpg
2008-03-28 07:00:53.709 chanid: 1008 starttime:2008-02-24T16:00:00
2008-03-28 07:00:53.861 File is a Myth recording.
2008-03-28 07:00:53.898 cutframes = 23369
2008-03-28 07:00:53.898 cutduration = 934
streaminfo.xml :-
<?xml version="1.0" ?>
<!DOCTYPE FILEINFO>
<file cutduration="2660" duration="3594" filename="/opt/mythtv/recordings/1008_20080224160000.mpg" type="mpegts">
        <streams count="3">
                <video aspectratio="1.77778" bitrate="8000000" codec="mpeg2video" ffmpegindex="0" fps="25" height="576" id="939" start_time="0.-3600" streamindex="0" width="720"/>
                <audio bitrate="96000" channels="1" codec="mp2" ffmpegindex="1" id="938" language="N/A" samplerate="48000" start_time="3451.982102" streamindex="1"/>     
                <data codec="Data: 0x0000" streamindex="2"/>
        </streams>
</file>
Preferred audio languages eng and eng
Video id: 0x3ab, Audio1: [1] 0x3aa (MP2, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Splitting MPEG stream into audio and video parts
Running: mythreplex --demux --fix_sync -t TS -o /opt/mythtv/mytharchive/work/1/stream -v 939 -a 938 "/opt/mythtv/recordings/1008_20080224160000.mpg"
Reading from /opt/mythtv/recordings/1008_20080224160000.mpg
Input file length: 1241.07 MB
Checking for TS: confirmed
Video: aspect ratio: 16:9  size = 720x576  frame rate: 25.000 fps  bit rate: 8.00 Mbit/s
  vbvbuffer 1835008
Sequence Extension: chroma 4:2:0   size = 720x576  bit rate: 8.00 Mbit/s  vbvbuffer 1835008  frame rate: 25.000
starting with video PTS:  0:00:00.0000
Video output File is: /opt/mythtv/mytharchive/work/1/stream.mv2
Audio0 output File is: /opt/mythtv/mytharchive/work/1/stream0.mp2

....
then there are a lot of these lines:
video PTS inconsistent: 10:39:40.5989 10:39:40.5989  0:00:29.6400  0:00:29.6400  diff:  0:00:14.3989
video DTS inconsistent: 10:39:40.5189 10:39:40.5189  0:00:29.5600  0:00:29.5600 diff:  0:00:14.3989
....

Audio track 1 is in mp2 format - re-encoding to ac3
Encoding audio to ac3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   42058kB time=1794.5 bitrate= 192.0kbits/s    ^M
video:0kB audio:42058kB global headers:0kB muxing overhead 0.000000%
*************************************************************
Finished processing file /opt/mythtv/recordings/1008_20080224160000.mpg
*************************************************************
Creating details pages
Background image file is /usr/share/mythtv/mytharchive/themes/MythCenter - Autoplay/MythCenter-Background.png
Music is silence.ac3, length is 5 seconds
Creating details page for 1
Image (320, 240) into space of (275, 205) at (55, 55)
Image resized to (275, 205) at (55, 55)
Added image /opt/mythtv/mytharchive/work/1/title.jpg
Wrapped text  = Extrem ingenj?rskonst
Wrapped text  = Flytande stad
Wrapped text  = Sun Feb 24 2008 16:00
Wrapped text  = Duration 00:44:20
Wrapped text  = I Karibien g?mmer sig Danny Forster bland bes?ttningen p? det gigantiska
Wrapped text  = kryssningsfartyget Freedom of the Seas f?r att se hur den utfodrar, inhyser och roar
Wrapped text  = de 4 000 passagerarna.
aspect ratio is: 1.77778
Encoding Details Page 1
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
   INFO: [mpeg2enc] Selecting DVD output profile
   INFO: [mpeg2enc] Assuming norm PAL
   INFO: [mpeg2enc] Progressive input - selecting progressive encoding.
   INFO: [mpeg2enc] Encoding MPEG-2 video to /opt/mythtv/mytharchive/work/temp.m2v
   INFO: [mpeg2enc] Horizontal size: 720 pel
   INFO: [mpeg2enc] Vertical size: 576 pel
   INFO: [mpeg2enc] Aspect ratio code: 3 = 16:9 display
   INFO: [mpeg2enc] Frame rate code:   3 = 25.0 (PAL/SECAM VIDEO / converted FILM)
   INFO: [mpeg2enc] Bitrate: 5000 KBit/s
   INFO: [mpeg2enc] Quality factor: 8 (Quantisation = 9) (1=best, 31=worst)
   INFO: [mpeg2enc] Field order for input: none/progressive
   INFO: [mpeg2enc] Sequence unlimited length
   INFO: [mpeg2enc] Search radius: 16
   INFO: [mpeg2enc] DualPrime: no
   INFO: [mpeg2enc] Using one-pass rate controller
   INFO: [mpeg2enc] GOP SIZE RANGE 9 TO 15
   INFO: [mpeg2enc] Setting colour/gamma parameters to "PAL B/G"
   INFO: [mpeg2enc] Progressive format frames = 1
   INFO: [mpeg2enc] Using default unmodified quantization matrices
   INFO: [mpeg2enc] Buffering 33 frames
   INFO: [mpeg2enc] SETTING MMX and MMX for QUANTIZER!
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame     0     0 I q=10.66 sum act=249.32681
 ...
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame   120   120 I q=8.00 sum act=4791.16752
   INFO: [mpeg2enc] Signaling last frame = 124
   INFO: [mpeg2enc] Frame   121   121 P q=8.00 sum act=4816.20741
   INFO: [mpeg2enc] Frame   122   122 P q=8.00 sum act=4838.76575
   INFO: [mpeg2enc] Frame   123   123 P q=8.00 sum act=4861.26497
   INFO: [mpeg2enc] Frame   124   124 P q=8.00 sum act=4883.75274
   INFO: [mpeg2enc] Sequence end inserted
   INFO: [mpeg2enc] Guesstimated final muxed size = 567777

Creating DVD XML file for dvd author (No Menus)
Adding item 1
aspect ratio is: 1.77778
Fixed length chapters: 00:00:00,00:05:00,00:10:00,00:15:00,00:20:00,00:25:00,00:30:00,00:35:00,00:40:00
Total size of video files, before multiplexing, is 1103 Mbytes, audio is 41 MBytes, menus are 0 MBytes.
Video will fit onto DVD. 3249.76 MBytes of space remaining on recordable DVD.
------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 5400, in main
    processJob(job)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 5159, in processJob
    calcSyncOffset(filecount))
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 666, in calcSyncOffset
    video_start = float(video.attributes["start_time"].value)
**ValueError: invalid literal for float():[COLOR="Red"] 0.-3600[/COLOR]**
------------------------------------------------------------


---

### Post by ahood on 2008-03-28
Sounds like you guys are onto something. I too have Always Encode AC3 checked. I read that mencoder will successfully transcode recordings if done manually. 

Anyone know if simply replacing ffmpeg with mencoder in the frontend will be compatible with MythArchive?

---

### Post by Cryophallion on 2008-03-28
> **muken said:**
> Interesting...

I just checked the setting "Always Encode to AC3" in the settings for mytharchive.

Now I get an invalid floating point 0.-3600, but mythreplex came through this time. The mythtranscode also fails...

Anyone else getting this?

First error seems to be that you need to delete .ICEAuthority in your home directory

---

### Post by JPurdy on 2008-03-29
I'm having problems with mytharchive, too, though I am a new user, so I can't say for certain that the upgrade broke it.

I've tried deleting the .ICEauthority file, creating an encoder profile, tried the different options (Don't recode, EP, SP, <CUSTOM_P>) and it always chokes on the mythreplex part. I also set the 'Always encode to ac3' option, too:

```
video:669953kB audio:84275kB global headers:0kB muxing overhead 4.959202%
Session management error: Authentication Rejected, reason : None of the authenti
cation protocols specified are supported and host-based authentication failed
2008-03-29 00:28:48.141 Opening /video/mytharchive/temp/work/1/newfile2.mpg
Input #0, mpeg, from '/video/mytharchive/temp/work/1/newfile2.mpg':
  Duration: 00:59:56.2, start: 0.500000, bitrate: 1803 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 352x288 [PAR 12:11 DAR 4:3],
 9000 kb/s, 29.97 tb(r)
    Stream #0.1[0x80]: Audio: liba52, 48000 Hz, stereo, 192 kb/s
2008-03-29 00:28:48.176 Calculating frame count
2008-03-29 00:28:59.013 frames = 107782
2008-03-29 00:28:59.013 duration = 3596
2008-03-29 00:28:59.013 Extracting details from: newfile2.mpg
2008-03-29 00:28:59.032 Cannot find details for newfile2.mpg
2008-03-29 00:28:59.032 File is not a Myth recording.
2008-03-29 00:28:59.032 cutframes = 0
2008-03-29 00:28:59.032 cutduration = 0
streaminfo.xml :-
...
Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x80 (LIBA52, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Splitting MPEG stream into audio and video parts
Running: mythreplex --demux --fix_sync -o /video/mytharchive/temp/work/1/stream
-v 224 "/video/mytharchive/temp/work/1/newfile2.mpg"
Reading from /video/mytharchive/temp/work/1/newfile2.mpg
Input file length: 773.08 MB
Checking for TS: failed
Checking for AVI: failed
Checking for PS: confirmed(maybe)
Video: aspect ratio: 4:3  size = 352x288  frame rate: 29.970 fps  bit rate: 9.00
 Mbit/s
  vbvbuffer 1835008
Sequence Extension: chroma 4:2:0   size = 352x288  bit rate: 9.00 Mbit/s  vbvbuffer 1835008  frame rate: 29.970
starting with video PTS:  0:00:00.5000
Video output File is: /video/mytharchive/temp/work/1/stream.mv2
Audio0 output File is: /video/mytharchive/temp/work/1/stream0.mp2
STARTING DEMUX
...
video PTS inconsistent:  0:58:55.2979  0:58:55.2979  0:58:55.3646  0:58:54.8646  diff:  0:00:00.0667
video DTS inconsistent:  0:58:55.2645  0:58:55.2645  0:58:55.3313  0:58:54.8313 diff:  0:00:00.0667
read  99%^Mvideo PTS inconsistent:  0:59:41.7777  0:59:41.7777  0:59:41.8444  0:59:41.3444  diff:  0:00:00.0667
video DTS inconsistent:  0:59:41.7443  0:59:41.7443  0:59:41.8110  0:59:41.3110 diff:  0:00:00.0667
read 100%
Can't find all required streams
Please check if audio and video have standard IDs (0xc0 or 0xe0)
************************************************************
ERROR: Failed while running mythreplex. Command was mythreplex --demux --fix_sync -o /video/mytharchive/temp/work/1/stream -v 224 "/video/mytharchive/temp/work/1/newfile2.mpg"
************************************************************

```

It seems it's generating a 0-byte .mp2 audio file:

```
$ ls -l
total 1461720
-rw-rw-rw- 1 jason jason       520 2008-03-29 00:18 info.xml
-rw-rw-rw- 1 jason jason 810631168 2008-03-29 00:28 newfile2.mpg
-rw-rw-rw- 1 jason jason    128451 2008-03-29 00:20 newfile.mpg.map
-rw-rw-rw- 1 jason jason         0 2008-03-29 00:28 stream0.mp2
-rw-rw-rw- 1 jason jason       671 2008-03-29 00:18 streaminfo_orig.xml
-rw-rw-rw- 1 jason jason       513 2008-03-29 00:28 streaminfo.xml
-rw-rw-rw- 1 jason jason 686022914 2008-03-29 00:29 stream.mv2

```

Setup: amd64, no overclocking

---

### Post by muken on 2008-03-29
> **Cryophallion said:**
> First error seems to be that you need to delete .ICEAuthority in your home directory

You're right, it was there again after a reboot or what ever...

It still doesn't work with the recording I tried to burn earlier, but I discovered that if I try to burn a recording which already has an AC3 track and if I don't cut it or reencode it, it works!

I will try different settings for this recording and get back with the results.

---

### Post by jon newbie on 2008-04-01
Hi,

Also pretty new to Linux and MythTV and would appreciate any help.  

I appear to be having the same mythreplex error as many of you so wanted ot post in case this is a widespread issue.  Here is my final error message from the Mythburn.log file when it terminates... 

[COLOR="Red"]
Can't find all required streams
Please check if audio and video have standard IDs (0xc0 or 0xe0)
************************************************************
ERROR: Failed while running mythreplex. Command was mythreplex --demux --fix_sync -o $
************************************************************[/COLOR]

After a few different tries I ended up selecting default SP encoding profile to turn the 480 x 480 recording into a DVD compatible system (the 480x480 resolution seems to be an issue based on some of the posts). Also used the "simple" DVD theme since there was only 1 recording on it.

**Here are the contents of my Work folder - notice the 0 byte "stream0.mp2 file**
```

jon-myth@jon-myth-desktop:/var/lib/mytharchive/tmp/work/1$ ls -l
total 4332428
-rw-rw-rw- 1 jon-myth jon-myth        495 2008-03-31 22:56 info.xml
-rw-rw-rw- 1 jon-myth jon-myth 2286743552 2008-03-31 23:51 newfile2.mpg
-rw-rw-rw- 1 jon-myth jon-myth     118432 2008-03-31 22:59 newfile.mpg.map
[COLOR="Red"]-rw-rw-rw- 1 jon-myth jon-myth          0 2008-03-31 23:52 stream0.mp2[/COLOR]
-rw-rw-rw- 1 jon-myth jon-myth        517 2008-03-31 22:56 streaminfo_orig.xml
-rw-rw-rw- 1 jon-myth jon-myth        514 2008-03-31 23:52 streaminfo.xml
-rw-rw-rw- 1 jon-myth jon-myth 2145185245 2008-03-31 23:57 stream.mv2
```

**Here is the starting snippet from my Mythburn.log**

```
Using simple_fix_rtl
mythburn.py (0.1.20080127-1) starting up...
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /var/lib/mytharchive/tmp/config/mydata.xml
passed progress log file: /var/lib/mytharchive/tmp/logs/progress.log
mythburn.py (0.1.20080127-1) starting up...
Found 1 CPUs
Obtaining MythTV settings from MySQL database for hostname jon-myth-desktop
temppath: /var/lib/mytharchive/tmp/work
logpath:  /var/lib/mytharchive/tmp/logs
Setting process priority to 17
Processing Mythburn job number 1.
Options - mediatype = 0, doburn = 1, createiso = 0, erasedvdrw = 0
          savefilename = ''
Looking for: /usr/share/mythtv/mytharchive/themes/Simple - Autoplay/theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 19
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 15
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 13
wantIntro: 0, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 0
Final DVD Video format will be ntsc
There are 1 files to process
Pre-processing file '/var/lib/mythtv/recordings/1047_20080229210000.mpg' of type 'rec$
2008-03-31 22:56:28.038 Opening /var/lib/mythtv/recordings/1047_20080229210000.mpg
Input #0, mpeg, from '/var/lib/mythtv/recordings/1047_20080229210000.mpg':
  Duration: 00:59:57.3, start: 0.289356, bitrate: 5189 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480 [PAR 4:3 DAR 4:3], 6000 k$
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
2008-03-31 22:56:28.081 duration = 3597
2008-03-31 22:56:28.081 Extracting details from: 1047_20080229210000.mpg
2008-03-31 22:56:28.083 chanid: 1047 starttime:2008-02-29T21:00:00
2008-03-31 22:56:28.090 File is a Myth recording.
2008-03-31 22:56:28.091 cutframes = 0
2008-03-31 22:56:28.092 cutduration = 0
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="3597" duration="3597" fil$
        <streams count="2">
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffm$
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="$
        </streams>
</file>
          Robot CHicken - Star Wars (Manual Record)
Video resolution is 480 by 480
*************************************************************
Processing file /var/lib/mythtv/recordings/1047_20080229210000.mpg of type recording
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="3597" duration="3597" fil$
        <streams count="2">
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffm$
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="$
        </streams>
</file>
          Robot CHicken - Star Wars (Manual Record)
Video resolution is 480 by 480
*************************************************************
Processing file /var/lib/mythtv/recordings/1047_20080229210000.mpg of type recording
*************************************************************
File type is 'mpeg'
Video codec is 'mpeg2video'
Running mythtranscode --mpeg2 to fix any errors
2008-03-31 22:56:28.429 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-31 22:56:28.430 Empty LocalHostName.
2008-03-31 22:56:28.447 New DB connection, total: 1
2008-03-31 22:56:28.454 Closing DB connection named 'DBManager0'
2008-03-31 22:59:03.431 cutframes = 0
2008-03-31 22:59:03.431 cutduration = 0
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="3597" duration="3597" fil$
        <streams count="2">
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffm$
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="$
        </streams>
</file>
Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x1c0 (MP2, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Aspect ratio is 4:3
Re-encoding audio and video
Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd$
Encoding profile (SP) found
ffmpeg -v 1 -i "/var/lib/mythtv/recordings/1047_20080229210000.mpg" -r ntsc -target d$
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.

*************************************************************
File type is 'mpeg'
Video codec is 'mpeg2video'
Running mythtranscode --mpeg2 to fix any errors
2008-03-31 22:56:28.429 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-31 22:56:28.430 Empty LocalHostName.
2008-03-31 22:56:28.447 New DB connection, total: 1
2008-03-31 22:56:28.454 Closing DB connection named 'DBManager0'
2008-03-31 22:56:28.454 Enabled verbose msgs: important
2008-03-31 22:56:28.458 New DB connection, total: 2
Mux rate: 6.49 Mbit/s
ICE default IO error handler doing an exit(), pid = 7007, errno = 32
Failed while running mythtranscode to cut commercials and/or clean up an mpeg2 file.
Result: 1, Command was mythtranscode --mpeg2 -c 1047 -s 2008-02-29T21:00:00 -o /var/l$
Failed to run mythtrancode to fix any errors
File will be re-encoded using profile SP
2008-03-31 22:59:03.202 Opening /var/lib/mythtv/recordings/1047_20080229210000.mpg
Input #0, mpeg, from '/var/lib/mythtv/recordings/1047_20080229210000.mpg':
  Duration: 00:59:57.3, start: 0.289356, bitrate: 5189 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480 [PAR 4:3 DAR 4:3], 6000 k$
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
2008-03-31 22:59:03.414 duration = 3597
2008-03-31 22:59:03.414 Extracting details from: 1047_20080229210000.mpg
2008-03-31 22:59:03.416 chanid: 1047 starttime:2008-02-29T21:00:00
2008-03-31 22:59:03.422 File is a Myth recording.
2008-03-31 22:59:03.431 cutframes = 0
2008-03-31 22:59:03.431 cutduration = 0
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="3597" duration="3597" fil$
        <streams count="2">
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffm$
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="$
        </streams>
</file>
Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x1c0 (MP2, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Aspect ratio is 4:3
Re-encoding audio and video
Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd$
Encoding profile (SP) found
ffmpeg -v 1 -i "/var/lib/mythtv/recordings/1047_20080229210000.mpg" -r ntsc -target d$
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enabl$
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubu$
Input #0, mpeg, from '/var/lib/mythtv/recordings/1047_20080229210000.mpg':
  Duration: 00:59:57.0, start: 0.289356, bitrate: 5189 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Assuming NTSC for target.
Output #0, dvd, to '/var/lib/mytharchive/tmp/work/1/newfile2.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=2-31, 4771 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=   17 q=2.3 size=     122kB time=0.2 bitrate=5205.3kbits/s
frame=   35 q=2.0 size=     610kB time=0.9 bitrate=5783.7kbits/s
ETC....

```




Here is the end snippet from my Mythburn.log

```
Can't find all required streams
Please check if audio and video have standard IDs (0xc0 or 0xe0)
************************************************************
ERROR: Failed while running mythreplex. Command was mythreplex --demux --fix_sync -o $
************************************************************

chmod: changing permissions of `/var/lib/mytharchive/tmp/': Operation not permitted
Terminated
```


Thanks in advance!

---

### Post by ahood on 2008-04-01
> **JPurdy said:**
> '/video/mytharchive/temp/work/1/newfile2.mpg':
  Duration: 00:59:56.2, start: 0.500000, bitrate: 1803 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 352x288 [PAR 12:11 DAR 4:3],

Hey JPurdy,

Is the original recording 720x480 resolution? The above seems to indicate that is isn't, but rather much smaller 352x288.

I have been successful in getting Mytharchive to a DVD, but only if the original recording is 720x480, which is DVD quality. If the original recording is 720x480. then transcoding isn't necessary and selecting "Don't Re-encode" has worked for me.

Actually, my experience has been that if the original recording is at 720x480, then Mytharchive will automatically select "Don't Re-encode".

I hope this helps.

Al

---

### Post by ahood on 2008-04-01
> **jon newbie said:**
> Hi,
chmod: changing permissions of `/var/lib/mytharchive/tmp/': Operation not permitted
Terminated

What are the permissions of /var/lib/mytharchive/tmp/? 
If it is -rw-rw-rw- then it might be worth while to change it to -rwxrwx-r , which is done by executing the command 

> sudo chmod 774 /var/lib/mytharchive/tmp

Also, it might be good to change the group of /var/lib/mytharchive/tmp to 'mythtv' with the following command...

> sudo chgrp mythtv /var/lib/mytharchive/tmp

Only change the group if you are certain that the user account also belongs to the 'mythtv' group. Usually, this is the case though.

I have been successful at using Mytharchive to burn a recording to DVD, but only if the original recording is at 720x480, which is a resolution equivalent to DVD. For me, changing the recording resolution from 480x480 to 720x480 has not increased the file size of the recordings (i.e., they are the same on my system).

I hope this helps.

Al

---

### Post by JPurdy on 2008-04-01
> **ahood said:**
> Hey JPurdy,

Is the original recording 720x480 resolution? The above seems to indicate that is isn't, but rather much smaller 352x288.

I have been successful in getting Mytharchive to a DVD, but only if the original recording is 720x480, which is DVD quality. If the original recording is 720x480. then transcoding isn't necessary and selecting "Don't Re-encode" has worked for me.

Actually, my experience has been that if the original recording is at 720x480, then Mytharchive will automatically select "Don't Re-encode".


Yeah, I don't think it is 720x480.  I'm not sure what it is, exactly (how would I find that out?).

Regardless, shouldn't it "just work" ? :)

---

### Post by muken on 2008-04-02
My tests shows the following:

**A recording with[COLOR="Blue"] 720x576[/COLOR] in resolution,[COLOR="Blue"] AC3 audio[/COLOR], not using any cutlist or reencoding -> works**

[B]Same recording using a cutlist -> works
[/B]
**Same recording using cutlist and reencoding (with AC3 sound) -> [COLOR="Red"]fails with mythreplex[/COLOR].**

---

### Post by jon newbie on 2008-04-02
Thanks ahood!

I checked your suggestions and I think for the most part I am already set up as you suggested.  I still have the problem with mythreplex though.  Here are the results...

> **ahood said:**
> What are the permissions of /var/lib/mytharchive/tmp/? 
If it is -rw-rw-rw- then it might be worth while to change it to -rwxrwx-r

Also, it might be good to change the group of /var/lib/mytharchive/tmp to 'mythtv'



I think I am already good with the permissions and group of the /var/lib/mytharchive/tmp folder as you can see below...

```
jon-myth@jon-myth-desktop:/var/lib/mytharchive$ ls -l
total 4
drwxrwxrwx 5 mythtv mythtv 4096 2008-03-31 22:51 tmp
jon-myth@jon-myth-desktop:/var/lib/mytharchive$ 
```

Not exactly what you suggested, but this should be fine shouldn't it?  "mythtv' is the owner and group on my recordings folders as well and they seem to work fine so I assume that is the proper group to use. 

> **ahood said:**
> 
Only change the group if you are certain that the user account also belongs to the 'mythtv' group. Usually, this is the case though.



I just checked and my user (jon-myth) does belong to the 'mythtv' group so that should be OK.


> **ahood said:**
> 
I have been successful at using Mytharchive to burn a recording to DVD, but only if the original recording is at 720x480, which is a resolution equivalent to DVD. For me, changing the recording resolution from 480x480 to 720x480 has not increased the file size of the recordings (i.e., they are the same on my system).



I tried mytharchive with it set so that it wouldn't re-encode but my res is at 480x480 and it failed at the Mythhelper level (different issue).  Ideally though I would like to re-encode to cut out commercials etc.  For now though I will try to figure out how to set my recording settings to 720 x 480.  

Thanks for the help!!

Jon

---

### Post by ahood on 2008-04-02
FYI - The resolution setting for TV recording in Mythtv is located in...

Home --> Utilities/Setup --> Setup --> TV Settings --> Recording Profiles

Once Recording Profiles is clicked, the first screen will have two options. The first option will be for MPEG recordings and the second option will be for transcoders. 

select the first option and proceed to the next screen that will list several MPEG recording profiles (Default, TV, Low, Normal, and High). 

Highlight and click on one of the options (for example Default) to go through the various configuration screens for the selected profile.

The second configuration screen will have the resolution that will be used for recordings.

I hope this helps.

Al

---

### Post by ahood on 2008-04-02
> **muken said:**
> My tests shows the following:

**A recording with[COLOR="Blue"] 720x576[/COLOR] in resolution,[COLOR="Blue"] AC3 audio[/COLOR], not using any cutlist or reencoding -> works**

[B]Same recording using a cutlist -> works
[/B]
**Same recording using cutlist and reencoding (with AC3 sound) -> [COLOR="Red"]fails with mythreplex[/COLOR].**

Hi Mulken,

Sounds like you are making progress with getting some settings to work with Mytharchive. I suspect that the 720x576 is selected because you are located in an place that uses this resolution for DVDs. Here in the US where I am located, 720x480 is default for DVDs I believe, but elsewhere in the world, the resolution is different (720x576 maybe?).

Based on the last response above, it appears that even re-encoding the audio will mess up Mytharchive.

Were you able to delete the .ICEauthority file that can sometimes appear on some systems?

Al

---

### Post by muken on 2008-04-04
> **ahood said:**
> Hi Mulken,

Sounds like you are making progress with getting some settings to work with Mytharchive. I suspect that the 720x576 is selected because you are located in an place that uses this resolution for DVDs. Here in the US where I am located, 720x480 is default for DVDs I believe, but elsewhere in the world, the resolution is different (720x576 maybe?).

Based on the last response above, it appears that even re-encoding the audio will mess up Mytharchive.

Were you able to delete the .ICEauthority file that can sometimes appear on some systems?

Al

Yes, I have deleted the .ICEauthority file and all the results described are with the file deleted.

720x576 is PAL size and that is the resolution that they use to broadcast standrad TV here in europe.

Has anyone reported these problems in launchpad for mythbuntu?
[https://launchpad.net]("https://launchpad.net/mythbuntu")

I can't find anything when searching the bug list...

---

### Post by tpeerd on 2008-04-04
I posted a request for help to the mailing list of Mythtv.org.

---

### Post by Psikotik on 2008-04-05
I have been having similar problems to the rest of you it seems. 
And may have come up with the solution:

When using ac3 encoding, mytharchivehelper detects the audio as LIBA52, but mythburn.py is only accepting AC3 audio streams, and so tries to split a mp3 audio track from the video - which fails as it doesn't exist.

To fix this problem i editted my mythburn.py (/usr/share/mythtv/mytharchive/scripts/) script to look like the following:

LINE 2639
```

#############################################################
# Splits a file into the separate audio and video streams
# using mythreplex

def deMultiplexMPEG2File(folder, mediafile, video, audio1, audio2):

    if getFileType(folder) == "mpegts":
        command = "mythreplex --demux --fix_sync -t TS -o %s " % (folder + "/stream")
        command += "-v %d " % (video[VIDEO_ID])

        if audio1[AUDIO_ID] != -1: 
            if audio1[AUDIO_CODEC] == 'MP2':
                command += "-a %d " % (audio1[AUDIO_ID])
            elif audio1[AUDIO_CODEC] == 'AC3':
                command += "-c %d " % (audio1[AUDIO_ID])
            elif audio1[AUDIO_CODEC] == 'LIBA52':
                command += "-c %d " % (audio1[AUDIO_ID])

        if audio2[AUDIO_ID] != -1: 
            if audio2[AUDIO_CODEC] == 'MP2':
                command += "-a %d " % (audio2[AUDIO_ID])
            elif audio2[AUDIO_CODEC] == 'AC3':
                command += "-c %d " % (audio2[AUDIO_ID])
            elif audio2[AUDIO_CODEC] == 'LIBA52':
                command += "-c %d " % (audio2[AUDIO_ID])

    else:
        command = "mythreplex --demux --fix_sync -o %s " % (folder + "/stream")
        command += "-v %d " % (video[VIDEO_ID] & 255)

        if audio1[AUDIO_ID] != -1: 
            if audio1[AUDIO_CODEC] == 'MP2':
                command += "-a %d " % (audio1[AUDIO_ID] & 255)
            elif audio1[AUDIO_CODEC] == 'AC3':
                command += "-c %d " % (audio1[AUDIO_ID] & 255)
            elif audio1[AUDIO_CODEC] == 'LIBA52':
                command += "-c %d " % (audio1[AUDIO_ID] & 255)

        if audio2[AUDIO_ID] != -1: 
            if audio2[AUDIO_CODEC] == 'MP2':
                command += "-a %d " % (audio2[AUDIO_ID] & 255)
            elif audio2[AUDIO_CODEC] == 'AC3':
                command += "-c %d " % (audio2[AUDIO_ID] & 255)
            elif audio2[AUDIO_CODEC] == 'LIBA52':
                command += "-c %d " % (audio2[AUDIO_ID] & 255)

    mediafile = quoteFilename(mediafile)
    command += mediafile
    write("Running: " + command)

    result = runCommand(command)

    if result<>0:
        fatalError("Failed while running mythreplex. Command was %s" % command)
```

basically I have just added the ability to recognize LIBA52 as AC3 encoding by adding the following if statements
```
  elif audio2[AUDIO_CODEC] == 'LIBA52':
                command += "-c %d " % (audio2[AUDIO_ID] & 255)
```
to each option. (be careful about using the right audio2 audio1 etc if you make this change)

I am not 100% sure what all the options actually do, but this seems to work for me. After I did this, i re-encoded some files (having 'alway use ac3' check box checked, and the codecs in your .xml files set to ac3 not copy) then attempted to burn an iso.
This unfortunately failed at the mkiso step, but got past mythreplex, and after copying these files to my windows machine i was able to make and test the iso image, and it worked!

[UPDATE]
Just successfully archived 3 videos with the above fix

---

### Post by tpeerd on 2008-04-06
Thanks. It works for me too.

---

### Post by jjohns63 on 2008-04-08
Thanks a ton, this fix worked for me as well. I was disappointed after I finally got a DVD burner and then it wasn't working, now I am able to archive any show, HD or otherwise.

---

### Post by muken on 2008-04-08
This works for me if the recording has an AC3 stream, but for recordings which does not have one, it fails.

I will try some other recordings to see if it is something special with this recording...

Anyway, have you submitted a patch to mythtv so they can include this fix if it is approved?

---

### Post by Psikotik on 2008-04-08
> This works for me if the recording has an AC3 stream, but for recordings which does not have one, it fails.

I will try some other recordings to see if it is something special with this recording...

I did this on straight mp2 recordings intially, which were then transcoded into ac3 by ffmpeg, then converted from that by mythreplex.
I'd double check the ac3 settings in mytharchive aswell as in your ffmpeg conversion schemes, to check they're actually outputting ac3 from ffmpeg. I don't think dvd conversion works too well otherwise.


> Anyway, have you submitted a patch to mythtv so they can include this fix if it is approved?

Wouldn't know where to start :). Plus theres definately a chance my fix has some unintended side affects, but if you can point me in the right direction I'll try see what I need to do.

---

### Post by JPurdy on 2008-04-08
This also worked for me, though I just changed the elsif to an else.

---

### Post by muken on 2008-04-08
Well my problem seem to be that the original streaminfo_orig.xml file contains an audio tag, but it is removed.

streaminfo_orig.xml
> 
<!DOCTYPE FILEINFO>
<file cutduration="41011" type="mpegts" duration="41945" filename="/opt/mythtv/recordings/1008_20080224160000.mpg" >
    <streams count="3" >
        <video start_time="0.-3600" width="720" aspectratio="1.77778" codec="mpeg2video" fps="25" height="576" ffmpegindex="0" id="939" bitrate="8000000" streamindex="0" />
        <audio start_time="3451.982102" codec="mp3" **[COLOR="Red"]samplerate="0"[/COLOR]** ffmpegindex="1" id="938" [COLOR="Red"]**bitrate="0"**[/COLOR] language="N/A" channels="0" streamindex="1" />
        <data codec="Data: 0x0000" streamindex="2" />
    </streams>
</file>


after running through the cutlist the streaminfo.xml file looks like this:
> 
<!DOCTYPE FILEINFO>
<file cutduration="2659" type="mpeg" duration="2659" filename="/opt/mythtv/mytharchive/work/1/newfile.mpg" >
    <streams count="1" >
        <video start_time="0.32400" width="720" aspectratio="1.33333" codec="mpeg2video" fps="25" height="576" ffmpegindex="0" id="480" bitrate="15000000" streamindex="0" />
    </streams>
</file>


The audio tag is missing...

Can it be that the samplerate and bitrate are 0?

The recording plays as a charm in mythtv...

---

### Post by Psikotik on 2008-04-09
I'd suggest posting the full mythburn / progress logs again to get a better idea of whats happening in this case

---

### Post by muken on 2008-04-09
> **Psikotik said:**
> I'd suggest posting the full mythburn / progress logs again to get a better idea of whats happening in this case


mythburn.log
> 
Using simple_fix_rtl
mythburn.py (0.1.20080127-1) starting up...
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /opt/mythtv/mytharchive/config/mydata.xml
passed progress log file: /opt/mythtv/mytharchive/logs/progress.log
mythburn.py (0.1.20080127-1) starting up...
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Found 2 CPUs
Obtaining MythTV settings from MySQL database for hostname mythbuntu-backend
temppath: /opt/mythtv/mytharchive/work
logpath:  /opt/mythtv/mytharchive/logs
Setting process priority to 17
Processing Mythburn job number 1.
Options - mediatype = 0, doburn = 0, createiso = 1, erasedvdrw = 0
          savefilename = ''
Looking for: /usr/share/mythtv/mytharchive/themes/MythCenter - Autoplay/theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
wantIntro: 1, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 1
Final DVD Video format will be pal
There are 1 files to process
Pre-processing file '/opt/mythtv/recordings/1008_20080224160000.mpg' of type 'recording'
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2008-04-08 22:50:01.485 Opening /opt/mythtv/recordings/1008_20080224160000.mpg
Input #0, mpegts, from '/opt/mythtv/recordings/1008_20080224160000.mpg':
  Duration: 11:39:05.0, start: 0.-40000, bitrate: 248 kb/s
    Stream #0.0[0x3ab]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 8000 kb/s, 25.00 tb(r)
    Stream #0.1[0x3aa]: Audio: mp3
    Stream #0.2[0x3a8](swe): Data: 0x0000
2008-04-08 22:50:01.497 duration = 41945
2008-04-08 22:50:01.497 Extracting details from: 1008_20080224160000.mpg
2008-04-08 22:50:01.498 chanid: 1008 starttime:2008-02-24T16:00:00
2008-04-08 22:50:01.502 File is a Myth recording.
2008-04-08 22:50:01.502 cutframes = 23369
2008-04-08 22:50:01.502 cutduration = 934
streaminfo.xml :-
<?xml version="1.0" ?>
<!DOCTYPE FILEINFO>
<file cutduration="41011" duration="41945" filename="/opt/mythtv/recordings/1008_20080224160000.mpg" type="mpegts">
        <streams count="3">
                <video aspectratio="1.77778" bitrate="8000000" codec="mpeg2video" ffmpegindex="0" fps="25" height="576" id="939" start_time="0.-3600" streamindex="0" width="720"/>
                <audio bitrate="0" channels="0" codec="mp3" ffmpegindex="1" id="938" language="N/A" samplerate="0" start_time="3451.982102" streamindex="1"/>
                <data codec="Data: 0x0000" streamindex="2"/>
        </streams>
</file>
          Extrem ingenjörskonst
Video resolution is 720 by 576
*************************************************************
Processing file /opt/mythtv/recordings/1008_20080224160000.mpg of type recording
*************************************************************
File type is 'mpegts'
Video codec is 'mpeg2video'
File has a cut list - running mythtrancode to remove unwanted segments
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2008-04-08 22:50:01.760 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-08 22:50:01.769 New DB connection, total: 1
2008-04-08 22:50:01.774 Closing DB connection named 'DBManager0'
2008-04-08 22:50:01.774 Enabled verbose msgs: important
2008-04-08 22:50:01.776 New DB connection, total: 2
Mux rate: 8.13 Mbit/s
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2008-04-08 22:51:07.235 Opening /opt/mythtv/mytharchive/work/1/newfile.mpg
Input #0, mpeg, from '/opt/mythtv/mytharchive/work/1/newfile.mpg':
  Duration: 00:44:19.4, start: 0.360000, bitrate: 2713 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 16:15 DAR 4:3], 15000 kb/s, 25.00 tb(r)
2008-04-08 22:51:07.246 Calculating frame count
2008-04-08 22:51:09.659 frames = 66488
2008-04-08 22:51:09.659 duration = 2659
2008-04-08 22:51:09.659 Extracting details from: newfile.mpg
2008-04-08 22:51:09.661 Cannot find details for newfile.mpg
2008-04-08 22:51:09.661 File is not a Myth recording.
2008-04-08 22:51:09.661 cutframes = 0
2008-04-08 22:51:09.661 cutduration = 0
streaminfo.xml :-
<?xml version="1.0" ?>
<!DOCTYPE FILEINFO>
<file cutduration="2659" duration="2659" filename="/opt/mythtv/mytharchive/work/1/newfile.mpg" type="mpeg">
        <streams count="1">
                <video aspectratio="1.33333" bitrate="15000000" codec="mpeg2video" ffmpegindex="0" fps="25" height="576" id="480" start_time="0.32400" streamindex="0" width="720"/>
        </streams>
</file>
Preferred audio languages eng and eng
Didn't find any audio elements in stream info file.!!!

Terminated


progress.log
> 
2008-04-08 22:49:59 mythburn.py (0.1.20080127-1) starting up...
2008-04-08 22:49:59 Found 2 CPUs
2008-04-08 22:49:59 Obtaining MythTV settings from MySQL database for hostname mythbuntu-backend
2008-04-08 22:49:59 temppath: /opt/mythtv/mytharchive/work
2008-04-08 22:49:59 logpath:  /opt/mythtv/mytharchive/logs
2008-04-08 22:49:59 Setting process priority to 17
2008-04-08 22:49:59 Processing Mythburn job number 1.
2008-04-08 22:49:59 Options - mediatype = 0, doburn = 0, createiso = 1, erasedvdrw = 0
2008-04-08 22:49:59           savefilename = ''
2008-04-08 22:49:59 Looking for: /usr/share/mythtv/mytharchive/themes/MythCenter - Autoplay/theme.xml
2008-04-08 22:49:59 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
2008-04-08 22:49:59 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
2008-04-08 22:49:59 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
2008-04-08 22:49:59 wantIntro: 1, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 1
2008-04-08 22:49:59 Final DVD Video format will be pal
2008-04-08 22:49:59 There are 1 files to process
2008-04-08 22:50:01 Pre-processing file '/opt/mythtv/recordings/1008_20080224160000.mpg' of type 'recording'
2008-04-08 22:50:01           Extrem ingenjörskonst
2008-04-08 22:50:01 Video resolution is 720 by 576
2008-04-08 22:50:01 *************************************************************
2008-04-08 22:50:01 Processing file /opt/mythtv/recordings/1008_20080224160000.mpg of type recording
2008-04-08 22:50:01 *************************************************************
2008-04-08 22:50:01 File type is 'mpegts'
2008-04-08 22:50:01 Video codec is 'mpeg2video'
2008-04-08 22:50:01 File has a cut list - running mythtrancode to remove unwanted segments
2008-04-08 22:51:09 Preferred audio languages eng and eng
2008-04-08 22:51:09 Didn't find any audio elements in stream info file.!!!
2008-04-08 22:51:09
2008-04-08 22:51:10 Terminated


---

### Post by e00 on 2008-04-26
Made the same changes as you described, now it all works. Brilliant! Thank you very much.

---

