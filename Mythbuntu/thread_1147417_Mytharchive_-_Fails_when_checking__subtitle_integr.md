---
title: "Mytharchive - Fails when checking  subtitle integrity"
date: 2009-05-03
forum: Mythbuntu
---

### Post by jb5 on 2009-05-03
Jaunty + Mythtv 0.21 20455 (all available patches installed)

Trying to use mytharchive to create an iso of some TV shows (UK DVB-T) so I can clear my TV show drive.

In the Media -> Archive settings  I have 
add subtitles, use projectX & use fifos checked. Everything else is default.

The archive fails when checking the subtitles:-
Here are the logs
Progress.log```
2009-05-02 17:58:52 mythburn.py (0.1.20080726-1-fixes) starting up...
2009-05-02 17:58:52 Found 2 CPUs
2009-05-02 17:58:52 Obtaining MythTV settings from MySQL database for hostname ERIC
2009-05-02 17:58:52 temppath: /hmv/temp/work
2009-05-02 17:58:52 logpath:  /hmv/temp/logs
2009-05-02 17:58:52 Setting process priority to 10
2009-05-02 17:58:52 Processing Mythburn job number 1.
2009-05-02 17:58:52 Options - mediatype = 3, doburn = 1, createiso = 1, erasedvdrw = 0
2009-05-02 17:58:52           savefilename = '/hmv/dvd/aa.iso'
2009-05-02 17:58:52 Looking for: /usr/share/mythtv/mytharchive/themes/Simple - Autoplay/theme.xml
2009-05-02 17:58:52 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
2009-05-02 17:58:52 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
2009-05-02 17:58:52 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
2009-05-02 17:58:52 wantIntro: 0, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 0
2009-05-02 17:58:52 Final DVD Video format will be pal
2009-05-02 17:58:52 There are 1 files to process
2009-05-02 17:58:52 Pre-processing recording 1: '/tv1/1007_20090430232500.mpg'
2009-05-02 17:58:52           Family Guy
2009-05-02 17:58:52 Video resolution is 720 by 576
2009-05-02 17:58:52 *************************************************************
2009-05-02 17:58:52 Processing recording 1: '/tv1/1007_20090430232500.mpg'
2009-05-02 17:58:52 *************************************************************
2009-05-02 17:58:56 Preferred audio languages eng and eng
2009-05-02 17:58:56 Video id: 0x26c, Audio1: [1] 0x26d (MP2, eng), Audio2: [-1] - 0x-1 (N/A, N/A)
2009-05-02 17:58:56 Using Project-X to demux file
2009-05-02 17:58:56 Preferred audio languages eng and eng
2009-05-02 17:58:56 Video id: 0x26c, Audio1: [1] 0x26d (MP2, eng), Audio2: [-1] - 0x-1 (N/A, N/A)
2009-05-02 17:58:56 Preferred languages eng and eng
2009-05-02 17:58:56 Subtitle id: 0x26f
2009-05-02 17:58:56 projectx -id 0x26c,0x26d,0x26f -out "/hmv/temp/work/1" -name "1007_20090430232500" "/tv1/1007_20090430232500.mpg"
2009-05-02 17:59:59 Preferred audio languages eng and eng
2009-05-02 17:59:59 Video id: 0x26c, Audio1: [1] 0x26d (MP2, eng), Audio2: [-1] - 0x-1 (N/A, N/A)
2009-05-02 17:59:59 Found DVB subtitles converting to DVD subtitles
2009-05-02 18:00:02 Audio track 1 is in mp2 format - NOT re-encoding to ac3
2009-05-02 18:00:02 *************************************************************
2009-05-02 18:00:02 Finished processing file '/tv1/1007_20090430232500.mpg'
2009-05-02 18:00:02 *************************************************************
2009-05-02 18:00:02 Creating DVD XML file for dvd author (No Menus)
2009-05-02 18:00:02 Adding item 1
2009-05-02 18:00:02 aspect ratio is: 1.77778
2009-05-02 18:00:02 Fixed length chapters: 00:00:00,00:05:00,00:10:00,00:15:00,00:20:00
2009-05-02 18:00:02 Total size of video files, before multiplexing, is 572 Mbytes, audio is 45 MBytes, menus are 0 MBytes.
2009-05-02 18:00:02 Video will fit onto DVD. 3819.24 MBytes of space remaining on recordable DVD.
2009-05-02 18:00:02 Multiplexing MPEG stream to /hmv/temp/work/1/final.mpg
2009-05-02 18:00:02 Available streams - video and one audio stream
2009-05-02 18:00:17 Checking integrity of subtitle pngs
2009-05-02 18:00:17 ************************************************************
2009-05-02 18:00:17 ERROR: Failed while running testsubtitlepngs.sh - /usr/share/mythtv/mytharchive/scripts/testsubtitlepngs.sh /hmv/temp/work/1/stream.d/spumux.xml
2009-05-02 18:00:17 ************************************************************
2009-05-02 18:00:17 
2009-05-02 18:00:17 Terminated
```mythburn.log```
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
Using simple_fix_rtl
mythburn.py (0.1.20080726-1-fixes) starting up...
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /hmv/temp/config/mydata.xml
passed progress log file: /hmv/temp/logs/progress.log
mythburn.py (0.1.20080726-1-fixes) starting up...
Found 2 CPUs
Obtaining MythTV settings from MySQL database for hostname ERIC
temppath: /hmv/temp/work
logpath:  /hmv/temp/logs
Setting process priority to 10
Processing Mythburn job number 1.
Options - mediatype = 3, doburn = 1, createiso = 1, erasedvdrw = 0
          savefilename = '/hmv/dvd/aa.iso'
Looking for: /usr/share/mythtv/mytharchive/themes/Simple - Autoplay/theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
wantIntro: 0, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 0
Final DVD Video format will be pal
There are 1 files to process
Pre-processing recording 1: '/tv1/1007_20090430232500.mpg'
2009-05-02 17:58:52.292 Opening /tv1/1007_20090430232500.mpg
Input #0, mpegts, from '/tv1/1007_20090430232500.mpg':
  Duration: 00:24:59.2, start: 1817.033811, bitrate: 4762 kb/s
    Stream #0.0[0x26c]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 25.00 tb(r)
    Stream #0.1[0x26d](eng): Audio: mp2, 48000 Hz, stereo, 256 kb/s
    Stream #0.2[0x26e](eng): Audio: mp2, 48000 Hz, mono, 64 kb/s
    Stream #0.3[0x26f](eng): Subtitle: dvbsub
    Stream #0.4[0x3f3]: Data: 0x0000
    Stream #0.5[0x3f4]: Data: 0x0000
    Stream #0.6[0x28a]: Data: 0x0000
    Stream #0.7[0x28b]: Data: 0x0000
    Stream #0.8[0x28c]: Data: 0x0000
2009-05-02 17:58:52.337 duration = 1499
2009-05-02 17:58:52.337 Extracting details from: 1007_20090430232500.mpg
2009-05-02 17:58:52.338 chanid: 1007 starttime:2009-04-30T23:25:00 
2009-05-02 17:58:52.341 File is a Myth recording.
2009-05-02 17:58:52.341 cutframes = 0
2009-05-02 17:58:52.341 cutduration = 0
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="1499" duration="1499" filename="/tv1/1007_20090430232500.mpg" type="mpegts">    
        <streams count="9">        
                <video aspectratio="1.77778" bitrate="15000000" codec="mpeg2video" ffmpegindex="0" fps="25" height="576" id="620" start_time="163.590455" streamindex="0" width="720"/>        
                <audio bitrate="256000" channels="2" codec="mp2" ffmpegindex="1" id="621" language="eng" samplerate="48000" start_time="163.533043" streamindex="1"/>        
                <audio bitrate="64000" channels="1" codec="mp2" ffmpegindex="2" id="622" language="eng" samplerate="48000" start_time="163.533043" streamindex="2"/>        
                <subtitle codec="dvbsub" ffmpegindex="3" id="623" language="eng" streamindex="3"/>        
                <data codec="Data: 0x0000" streamindex="4"/>        
                <data codec="Data: 0x0000" streamindex="5"/>        
                <data codec="Data: 0x0000" streamindex="6"/>        
                <data codec="Data: 0x0000" streamindex="7"/>        
                <data codec="Data: 0x0000" streamindex="8"/>        
        </streams>    
</file>
          Family Guy
Video resolution is 720 by 576
*************************************************************
Processing recording 1: '/tv1/1007_20090430232500.mpg'
*************************************************************
2009-05-02 17:58:52.502 Opening /tv1/1007_20090430232500.mpg
Input #0, mpegts, from '/tv1/1007_20090430232500.mpg':
  Duration: 00:24:59.2, start: 1817.033811, bitrate: 4762 kb/s
    Stream #0.0[0x26c]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 25.00 tb(r)
    Stream #0.1[0x26d](eng): Audio: mp2, 48000 Hz, stereo, 256 kb/s
    Stream #0.2[0x26e](eng): Audio: mp2, 48000 Hz, mono, 64 kb/s
    Stream #0.3[0x26f](eng): Subtitle: dvbsub
    Stream #0.4[0x3f3]: Data: 0x0000
    Stream #0.5[0x3f4]: Data: 0x0000
    Stream #0.6[0x28a]: Data: 0x0000
    Stream #0.7[0x28b]: Data: 0x0000
    Stream #0.8[0x28c]: Data: 0x0000
2009-05-02 17:58:52.531 Calculating frame count
2009-05-02 17:58:56.334 frames = 37421
2009-05-02 17:58:56.335 duration = 1496
2009-05-02 17:58:56.335 Extracting details from: 1007_20090430232500.mpg
2009-05-02 17:58:56.336 chanid: 1007 starttime:2009-04-30T23:25:00 
2009-05-02 17:58:56.338 File is a Myth recording.
2009-05-02 17:58:56.338 cutframes = 0
2009-05-02 17:58:56.338 cutduration = 0
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file cutduration="1496" duration="1496" filename="/tv1/1007_20090430232500.mpg" type="mpegts">    
        <streams count="9">        
                <video aspectratio="1.77778" bitrate="15000000" codec="mpeg2video" ffmpegindex="0" fps="25" height="576" id="620" start_time="163.590455" streamindex="0" width="720"/>        
                <audio bitrate="256000" channels="2" codec="mp2" ffmpegindex="1" id="621" language="eng" samplerate="48000" start_time="163.533043" streamindex="1"/>        
                <audio bitrate="64000" channels="1" codec="mp2" ffmpegindex="2" id="622" language="eng" samplerate="48000" start_time="163.533043" streamindex="2"/>        
                <subtitle codec="dvbsub" ffmpegindex="3" id="623" language="eng" streamindex="3"/>        
                <data codec="Data: 0x0000" streamindex="4"/>        
                <data codec="Data: 0x0000" streamindex="5"/>        
                <data codec="Data: 0x0000" streamindex="6"/>        
                <data codec="Data: 0x0000" streamindex="7"/>        
                <data codec="Data: 0x0000" streamindex="8"/>        
        </streams>    
</file>
Preferred audio languages eng and eng
Video id: 0x26c, Audio1: [1] 0x26d (MP2, eng), Audio2: [-1] - 0x-1 (N/A, N/A)
Using Project-X to demux file
Preferred audio languages eng and eng
Video id: 0x26c, Audio1: [1] 0x26d (MP2, eng), Audio2: [-1] - 0x-1 (N/A, N/A)
Preferred languages eng and eng
Subtitle id: 0x26f
projectx -id 0x26c,0x26d,0x26f -out "/hmv/temp/work/1" -name "1007_20090430232500" "/tv1/1007_20090430232500.mpg"
Reading GUI-Switch...
Reading Help Switch...
Reading Config File Switch...
Start without GUI...
Loading last Config or Standard File...
ini load error: java.io.FileNotFoundException: /home/jb/X.ini (No such file or directory)
Loading Language -> 'en'

ProjectX 0.90.4.00/30.03.2006 TEST PROJECT ONLY , User: jb


TERMS AND CONDITIONS:
(1) this is a free Java based demux utility.
(2) It is intended for educational purposes only, as a non-commercial test project.
(3) released under the terms of the GNU GPL.
(4) there is NO WARRANTY of any kind attached to this software.
(5) use it at your own risk and for your own education.

Java Environment
02 May 2009    17:58:56 BST
java.version	1.6.0_0
java.vendor	Sun Microsystems Inc.
java.home	/usr/lib/jvm/java-6-openjdk/jre
java.vm.version	14.0-b08
java.vm.vendor	Sun Microsystems Inc.
java.vm.name	OpenJDK 64-Bit Server VM
java.class.vers	50.0
java.class.path	/usr/share/java/ProjectX.jar
os.name	Linux
os.arch	amd64
os.version	2.6.28-11-generic
ini.file	/home/jb/X.ini
ext.disk.access	disabled or library not found
user.language	en
user.name	jb
user.home	/home/jb

quick CL usage: 
Note: CL doesn't load the GUI components, except with switch [-gui]
<without options>  ...starts the GUI
switches and inputfiles can be in any order

options:
[-ini <path + inifile>] ..use that specified iniFile instead of the standard
[-dvx1] ..create a .d2v ProjectFile on demux
[-dvx2] ..create a .d2v ProjectFile + .ac3.wav (RIFF WAVE Header)
[-dvx3] ..create a .d2v ProjectFile + .mpa.wav (RIFF WAVE Header)
[-dvx4] ..create a .d2v ProjectFile + .ac3.wav + mpa.wav (RIFF WAVE Header)
[-out <path>] ..use that specified directory for output
[-name <filename>] ..use that specified filename for output
[-cut <file>] ..use that text based file as cutpoint list
[-chp <file>] ..use that text based file as chapterpoint list
[-id <tokens>] ..use only these (P)IDs, separated by comma ","
[-gui] ..display the GUI using all given CLI options
[-log] ..write the normal logfile
[-saveini] ..save changes made bei CLI in active .ini
[-split <xxx>] ..split output at xxx MB
[-demux, -tom2p, -topva, -tovdr, -tots, -filter] ..action types

Loading Basic Classes...
Reading CLI Switches...
-> loading 3 (P)IDs...
Checking Commons-Net library access...
Loading AC3 frames...
Starting Collection Process...
preparing collection(s)...

1 %<<< session infos >>>

Saturday, 2 May 2009  17:58:57 o'clock BST
ProjectX 0.90.4.00 (30.03.2006)

-> working with collection 0
 
-> save normal log file
-> write all video data
-> write all other data
-> patch c.d.flagged infos of pictures
-> add sequence end code
-> set resolution in SDE 
-> PVA: strictly specs. for audio streams
-> VOB: determine diff. Cell timelines
-> TS: ignore scrambled packets
-> TS: enhanced search for open packets
-> TS: join file segments (of Dreambox®)
-> TS: generate PMT stream dependent
-> get only enclosed PES/TS packets
-> concatenate different recordings
-> ensure 1st PES-packet start with video
-> generate PCR/SCR from PTS
 
-> write output files to: '/hmv/temp/work/1'

-> Input File 0:  '/tv1/1007_20090430232500.mpg' (892,522,104 bytes)
-> Filetype is TS (generic PES Container)
-> demux
-> Service ID 0x1
-> PMT 0x10FF refers to these usable streams:
Video:
PID: 0x26C(#1)
Audio:
PID: 0x26D(#2)(eng)
PID: 0x26E(#6)(eng)
Teletext:
n/a
Subpict.:
PID: 0x26F(#5)(eng_0x10_p1_a1 )

-> special PIDs for searching defined: { 0x26C 0x26D 0x26F }
demuxing DVB MPEG-TS file 1007_20090430232500.mpg
ok> PID 0x26C has PES-ID 0xE0 (MPEG Video) (376 #3) 
ok> PID 0x26D has PES-ID 0xC0 (MPEG Audio) (23876 #128) 
ok> PID 0x26F has PES-ID 0xBD (private stream 1) (SubID 0x20) (221464 #1179) 
-> video basics: 720*576 @ 25fps @ 0.7031 (16:9) @ 15000000bps, vbvBuffer 112
-> starting export of video data @ GOP# 0
!> dropping useless B-Frames @ GOP# 0 / new Timecode 00:00:00.000

2 %
3 %
4 %
5 %
6 %
7 %
8 %
9 %
10 %
11 %
12 %
13 %
14 %
15 %
16 %
17 %
18 %
19 %
20 %
21 %
22 %
23 %
24 %
25 %
26 %
27 %
28 %
29 %
30 %
31 %
32 %
33 %
34 %
35 %
36 %!> PID 0x26C -> packet 1685872 @ pos. 316943748 out of sequence (0/14) (shifting..) (~00:09:58.120)
!> PID 0x26C -> packet 1689297 @ pos. 317587648 out of sequence (4/2) (shifting..) (~00:09:59.080)

37 %
38 %
39 %
40 %
41 %
42 %
43 %
44 %
45 %
46 %
47 %
48 %
49 %
50 %
51 %
52 %
53 %
54 %
55 %
56 %
57 %
58 %
59 %
60 %
61 %
62 %
63 %
64 %
65 %
66 %
67 %
68 %
69 %
70 %
71 %
72 %
73 %
74 %
75 %
76 %
77 %
78 %
79 %
80 %
81 %
82 %
83 %
84 %
85 %
86 %
87 %
88 %
89 %
90 %
91 %
92 %
93 %
94 %
95 %
96 %
97 %
98 %
99 %
100 %
101 %packs: 3547390 100% 892522104

-> Video: fr/ ct/ 1p/ cg/ og/ dg -> 37411/ 1/ 0/ 3068/ 0/ 0
-> Video length: 37411 frames @ 00:24:56.440
-> GOP summary: min. 18, max. 36 fields; contains interlaced frames
-> avg. nom. bitrate 3206545bps (min/max: 754000/6962800)
-> set first sequenceheader bitrate to 6962800bps
---> new File: /hmv/temp/work/1/1007_20090430232500.m2v

--> MPEG Audio (0xC0) on PID 0x26D
check & synchronize audio file  1007_20090430232500.mp

1 %-> check CRC of AC-3 / MPEG-Audio L1,2
-> delete CRC in MPEG-Audio Layer1,2
-> add frames
Audio PTS: first packet 00:30:17.033, last packet 00:55:14.033
Video PTS: start 1.GOP 00:30:17.671, end last GOP 00:55:14.111
-> adjusting audio at video-timeline
-> src_audio: MPEG-1, Layer2, 48000Hz, stereo, 256kbps, CRC @ 00:00:00.000

2 %
3 %
4 %
5 %
6 %
7 %
8 %
9 %
10 %
11 %
12 %
13 %
14 %
15 %
16 %
17 %
18 %
19 %
20 %
21 %
22 %
23 %
24 %
25 %
26 %
27 %
28 %
29 %
30 %
31 %
32 %
33 %
34 %
35 %
36 %
37 %
38 %
39 %
40 %
41 %
42 %
43 %
44 %
45 %
46 %
47 %
48 %
49 %
50 %
51 %
52 %
53 %
54 %
55 %
56 %
57 %
58 %
59 %
60 %
61 %
62 %
63 %
64 %
65 %
66 %
67 %
68 %
69 %
70 %
71 %
72 %
73 %
74 %
75 %
76 %
77 %
78 %
79 %
80 %
81 %
82 %
83 %
84 %
85 %
86 %
87 %
88 %
89 %
90 %
91 %
92 %
93 %
94 %
95 %
96 %
97 %
98 %
99 %
100 %audio frames: wri/pre/skip/ins/add 62351/0/0/0/0 @ 00:24:56.424 done...
---> new File: '/hmv/temp/work/1/1007_20090430232500.mp2'

101 %
--> Subpicture (SubID 0x20)
-> selected DVB subpicture color model: (0) 4 colors ; fixed to page id: 

-> export format: sup
-> temp. file: 1007_20090430232500.sp (2255741 bytes)
check & synchronize 1007_20090430232500.sp

1 %Subpicture PTS: first packet 00:30:19.830, last packet 00:55:13.639
Video PTS: start 1.GOP 00:30:17.671, end last GOP 00:55:14.111
-> adjusting subpicture at video-timeline
-> source is DVB Subtitle...

2 %
3 %
4 %
5 %
6 %
7 %
8 %
9 %
10 %
11 %
12 %
13 %
14 %
15 %
16 %
17 %
18 %
19 %
20 %
21 %
22 %
23 %
24 %
25 %
26 %
27 %
28 %
29 %
30 %
31 %
32 %
33 %
34 %
35 %
36 %
37 %
38 %
39 %
40 %
41 %
42 %
43 %
44 %
45 %
46 %
47 %
48 %
49 %
50 %
51 %
52 %
53 %
54 %
55 %
56 %
57 %
58 %
59 %
60 %
61 %
62 %
63 %
64 %
65 %
66 %
67 %
68 %
69 %
70 %
71 %
72 %
73 %
74 %
75 %
76 %
77 %
78 %
79 %
80 %
81 %
82 %
83 %
84 %
85 %
86 %
87 %
88 %
89 %
90 %
91 %
92 %
93 %
94 %
95 %
96 %
97 %
98 %
99 %
100 %665 subpictures written...
---> new File: /hmv/temp/work/1/1007_20090430232500.sup

101 %
summary of created media files:
.Video (m2v):	37411 Frames	00:24:56.440		'/hmv/temp/work/1/1007_20090430232500.m2v'
Audio 0 (mp2):	62351 Frames	00:24:56.424	0/0/0/0	'/hmv/temp/work/1/1007_20090430232500.mp2'
SubPicture 0:	665 subpictures		'/hmv/temp/work/1/1007_20090430232500.sup'
=> 649,557,986 bytes written...
-> we have 3 warnings/errors.
done...    1 collection(s) processed  @ 00:01:01.882
 
renameProjectXFiles start -----------------------------------------
found stream 0x26C
found stream 0x26D
found stream 0x26F
/hmv/temp/work/1/1007_20090430232500.m2v
/hmv/temp/work/1/1007_20090430232500.mp2
/hmv/temp/work/1/1007_20090430232500.sup
Preferred audio languages eng and eng
Video id: 0x26c, Audio1: [1] 0x26d (MP2, eng), Audio2: [-1] - 0x-1 (N/A, N/A)
got stream: 620
found video streamID
found video stream file
got stream: 621
found audio1 streamID
found audio1 stream file
got stream: 623
renameProjectXFiles end -----------------------------------------
Found DVB subtitles converting to DVD subtitles


00:00:02.16
00:08:36.28
00:16:00.28
00:21:14.90
00:24:48.47
Writing image files and spumux.tmp.
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Dropping overlapping subtitle
Dropping overlapping subtitle
Dropping overlapping subtitle
Dropping overlapping subtitle
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Fixed overlapping subtitle!
Writing palette.ycrcb and palette.rgb.
Renaming spumux.tmp to spumux.xml.
Output files reside in /hmv/temp/work/1/stream.d/
All done.
removing subtitle: 00:01:59.00 to 00:02:01.38 - (10710000 - 10890038 (10710096))
removing subtitle: 00:04:38.00 to 00:04:42.17 - (25020000 - 25380017 (25020097))
removing subtitle: 00:07:02.00 to 00:07:04.29 - (37980000 - 38160029 (37980095))
removing subtitle: 00:09:32.00 to 00:09:34.83 - (51480000 - 51660083 (51480096))
removing subtitle: 00:09:35.00 to 00:09:37.05 - (51750000 - 51930005 (51750098))
removing subtitle: 00:12:44.00 to 00:12:47.10 - (68760000 - 69030010 (68760095))
removing subtitle: 00:15:41.00 to 00:15:43.93 - (84690000 - 84870093 (84690096))
removing subtitle: 00:17:08.00 to 00:17:10.05 - (92520000 - 92700005 (92520097))
removing subtitle: 00:18:59.00 to 00:19:00.39 - (102510000 - 102600039 (102510093))
removing subtitle: 00:19:02.00 to 00:19:04.19 - (102780000 - 102960019 (102780096))
removing subtitle: 00:19:06.00 to 00:19:07.03 - (103140000 - 103230003 (103140093))
removing subtitle: 00:19:20.96 to 00:19:20.00 - (104400096 - 104400000 (104400090))
removing subtitle: 00:19:22.88 to 00:19:22.00 - (104580088 - 104580000 (104580081))
removing subtitle: 00:19:38.00 to 00:19:41.70 - (106020000 - 106290070 (106020093))
Audio track 1 is in mp2 format - NOT re-encoding to ac3
*************************************************************
Finished processing file '/tv1/1007_20090430232500.mpg'
*************************************************************
Creating DVD XML file for dvd author (No Menus)
Adding item 1
aspect ratio is: 1.77778
Fixed length chapters: 00:00:00,00:05:00,00:10:00,00:15:00,00:20:00
Total size of video files, before multiplexing, is 572 Mbytes, audio is 45 MBytes, menus are 0 MBytes.
Video will fit onto DVD. 3819.24 MBytes of space remaining on recordable DVD.
Multiplexing MPEG stream to /hmv/temp/work/1/final.mpg
Available streams - video and one audio stream
Checking integrity of subtitle pngs
sh: /usr/share/mythtv/mytharchive/scripts/testsubtitlepngs.sh: Permission denied
************************************************************
ERROR: Failed while running testsubtitlepngs.sh - /usr/share/mythtv/mytharchive/scripts/testsubtitlepngs.sh /hmv/temp/work/1/stream.d/spumux.xml
************************************************************

Terminated
```
The problem/s appear to involve checking subtitle integrity (testsubtitlepngs.sh)

I looked in the working directory and the subtitle .png files are present as is spumux.xml, so I tried running the command from a terminal and this is what it returned.
```
cd /usr/share/mythtv/mytharchive/scripts
sh testsubtitlepngs.sh /hmv/temp/work/1/stream.d/spumux.xml

read: 26: arg count
cat /hmv/temp/work/1/stream.d/spumux.xml.bad: No such file or directory
```
spumux.xml**.bad** is NOT present in the working directory, should it be, or am I missing the point entirely????

I can uncheck 'add subtitles' (media settings) and the iso will generate, but as myth-archive appears to complete most of the work i.e. the subtitle pngs are generated etc.  that I'm hoping that it is an easy fix! 

Anybody any ideas?

---

### Post by chorltan on 2009-10-26
Hi 

Have you checked the permissions of /usr/share/mythtv/mytharchive/scripts/testsubtitlepngs.sh   ?

I had a similar problem - but it worked after I changed it to be executable by all.

E.g. sudo chmod +x /usr/share/mythtv/mytharchive/scripts/testsubtitlepngs.sh

Let us know if it works for you.

C

---

### Post by jb5 on 2009-10-30
Hi - Thanks for the thought. I tried it again and it seems to hang at the DVD authoring point. 

I'm just starting to recover from a cold, hence the delayed reply, and I need to look at the logs a little more closely when I'm back up to speed again.

But at first glance, it doesn't look like it has solved the problem, unfortunately.

I will try and have another play with it soon. Thanks again.

---

### Post by bigtdp on 2009-11-26
> **chorltan said:**
> Hi 

Have you checked the permissions of /usr/share/mythtv/mytharchive/scripts/testsubtitlepngs.sh   ?

I had a similar problem - but it worked after I changed it to be executable by all.

E.g. sudo chmod +x /usr/share/mythtv/mytharchive/scripts/testsubtitlepngs.sh

Let us know if it works for you.

C

The problem still persists in the latest Mythbuntu, 9.10. the mythtv package is: 0.22.0+fixes22594-0ubuntu1

I resolved by making executable by all, as suggested above...

Now if only I can figure out why subs are not being found when you choose to re-encode to SP in mytharchive, and why recordings that *are* re-encoded have out of sync audio! :)

xTx

---

### Post by jb5 on 2010-04-18
Hi - Thanks for the tip.
 
Actually making the directory _+ Children_ executable did get me a little further. The script runs through without crashing out.

However, although the subtitle .png files are present in the working directory, they still do not display when watching the iso file. :(

---

