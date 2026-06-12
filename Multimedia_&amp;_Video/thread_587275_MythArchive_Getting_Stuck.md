---
title: "MythArchive Getting Stuck"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by clayton on 2007-10-22
Since my upgrade to Gutsy, and when creating dvd iso's in MythArchive, the mytharchive log page stops at "starting dvdauthor". The wiki page for MythArchive says that a majority of this type of error is problems with missing python modules. I tried "apt-get --reinstall install mytharchive" with no success.  Below is my mythburn.log. Anyone have a suggestion on troubleshooting this?
```

mythburn.py (0.1.20070428-1.fixes) starting up...
Process priority 8
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /media/store/config/mydata.xml
passed progress log file: /media/store/logs/progress.log
mythburn.py (0.1.20070428-1.fixes) starting up...
Found 1 CPUs
Obtaining MythTV settings from MySQL database for hostname turnip.obhouse.org
temppath: /media/store//work
logpath:  /media/store//logs
Processing Mythburn job number 1.
Options - mediatype = 0, doburn = 0, createiso = 1, erasedvdrw = 0
          savefilename = ''
Looking for: /usr/share/mythtv/mytharchive/themes/MythCenter - Autoplay/theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 19
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 15
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 13
wantIntro: 1, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 1
Final DVD Video format will be ntsc
There are 1 files to process
Pre-processing file '1057_20071018121500.mpg' of type 'recording'
2007-10-19 18:02:50.709 Opening /media/store/1057_20071018121500.mpg
Input #0, mpeg, from '/media/store/1057_20071018121500.mpg':
  Duration: 02:14:56.9, start: 0.189256, bitrate: 5188 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
0: start_time: 0.036 duration: 728.711
1: start_time: 0.017 duration: 728.687
stream: start_time: 0.189 duration: 8097.000 bitrate=5188 kb/s
2007-10-19 18:02:50.719 duration = 8096
streaminfo.xml :-
<?xml version="1.0" ?>
<!DOCTYPE FILEINFO>
<file duration="3802" filename="/media/store/1057_20071018121500.mpg" type="mpeg">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffmpegindex="0" fps="29.97" height="480" id="480" start_time="0.36036" streamindex="0" width="720"/>        
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="448" language="N/A" samplerate="48000" start_time="0.17033" streamindex="1"/>        
        </streams>    
</file>
          Mad Max Beyond Thunderdome
Video resolution is 720 by 480
*************************************************************
Processing file 1057_20071018121500.mpg of type recording
*************************************************************
File type is 'mpeg'
Video codec is 'mpeg2video'
File has a cut list - running mythtrancode to remove unwanted segments
2007-10-19 18:02:50.978 Using runtime prefix = /usr
2007-10-19 18:02:51.018 New DB connection, total: 1
2007-10-19 18:02:51.025 Enabled verbose msgs: important
2007-10-19 18:02:51.028 New DB connection, total: 2
Mux rate: 6.49 Mbit/s
2007-10-19 18:08:44.764 Opening /media/store//work/1/tmp
Input #0, mpeg, from '/media/store//work/1/tmp':
  Duration: 01:40:19.0, start: 0.312411, bitrate: 4959 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
0: start_time: 0.028 duration: 541.717
1: start_time: 0.034 duration: 541.667
stream: start_time: 0.312 duration: 6019.080 bitrate=4959 kb/s
2007-10-19 18:08:44.828 Calculating frame count
2007-10-19 18:10:13.549 frames = 180402
2007-10-19 18:10:13.567 duration = 6019
streaminfo.xml :-
<?xml version="1.0" ?>
<!DOCTYPE FILEINFO>
<file duration="6019" filename="/media/store//work/1/tmp" type="mpeg">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffmpegindex="0" fps="29.97" height="480" id="480" start_time="0.28117" streamindex="0" width="720"/>        
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="448" language="N/A" samplerate="48000" start_time="0.34251" streamindex="1"/>        
        </streams>    
</file>
Preferred audio languages eng and eng
Video id: 0x1e0, Audio1: [1] 0x1c0 (MP2, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Splitting MPEG stream into audio and video parts
Running: mythreplex --demux --fix_sync -o /media/store//work/1/stream -v 224 -a 192 "/media/store//work/1/tmp"
Reading from /media/store//work/1/tmp
Input file length: 3558.64 MB
Checking for TS: failed
Checking for AVI: failed
Checking for PS: confirmed(maybe)
Video: aspect ratio: 4:3  size = 720x480  frame rate: 29.970 fps  bit rate: 6.00 Mbit/s
  vbvbuffer 1835008
Sequence Extension: chroma 4:2:0   size = 720x480  bit rate: 6.00 Mbit/s  vbvbuffer 1835008  frame rate: 29.970
starting with video PTS:  0:00:00.379 
Video output File is: /media/store//work/1/stream.mv2
Audio0 output File is: /media/store//work/1/stream0.mp2
STARTING DEMUX
Audiostream: layer: 2  BRate: 384 kb/s  Freq: 48.0 kHz frame size: 1152 ( 0:00:00.024 ) starting audio PTS:  0:00:00.380 
fixing audio PTS inconsistency - diff:  0:00:00.024  - need to remove 1 frame(s)
fixing audio PTS inconsistency - diff:  0:00:00.024  - need to remove 1 frame(s)
fixing audio PTS inconsistency - diff:  0:00:00.024  - need to add 1 frame(s)
encoding an MP2 audio frame
fixing audio PTS inconsistency - diff:  0:00:00.024  - need to add 1 frame(s)
encoding an MP2 audio frame
read   1%
read   2%
read   3%
read   4%
read   5%
read   6%
read   7%
read   8%
read   9%
read  10%
read  11%
read  12%
read  13%
read  14%
read  15%
read  16%
read  17%
read  18%
read  19%
read  20%
read  21%
read  22%
read  23%
read  24%
read  25%
read  26%
read  27%
read  28%
read  29%
fixing audio PTS inconsistency - diff:  0:00:00.060  - need to add 2 frame(s)
encoding an MP2 audio frame
read  30%
read  31%
read  32%
read  33%
read  34%
read  35%
read  36%
read  37%
read  38%
read  39%
read  40%
read  41%
fixing audio PTS inconsistency - diff:  0:00:00.031  - need to add 1 frame(s)
encoding an MP2 audio frame
read  42%
video PTS inconsistent:  0:42:32.395  0:42:32.395  0:42:32.528  0:42:32.149  diff:  0:00:00.133 
read  43%
video PTS inconsistent:  0:43:55.978  0:43:55.978  0:43:56.112  0:43:55.733  diff:  0:00:00.133 
read  44%
read  45%
read  46%
read  47%
read  48%
read  49%
read  50%
read  51%
video PTS inconsistent:  0:52:09.972  0:52:09.972  0:52:10.039  0:52:09.659  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.072  0:52:10.072  0:52:10.139  0:52:09.759  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.005  0:52:10.005  0:52:10.072  0:52:09.693  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.039  0:52:10.039  0:52:10.105  0:52:09.726  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.172  0:52:10.172  0:52:10.239  0:52:09.860  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.105  0:52:10.105  0:52:10.172  0:52:09.793  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.139  0:52:10.139  0:52:10.205  0:52:09.826  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.272  0:52:10.272  0:52:10.339  0:52:09.960  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.205  0:52:10.205  0:52:10.272  0:52:09.893  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.239  0:52:10.239  0:52:10.305  0:52:09.926  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.372  0:52:10.372  0:52:10.439  0:52:10.060  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.305  0:52:10.305  0:52:10.372  0:52:09.993  diff:  0:00:00.066 
video PTS inconsistent:  0:52:10.339  0:52:10.339  0:52:10.406  0:52:10.026  diff:  0:00:00.066 
fixing audio PTS inconsistency - diff:  0:00:00.030  - need to add 1 frame(s)
encoding an MP2 audio frame
read  52%
read  53%
read  54%
read  55%
read  56%
read  57%
read  58%
read  59%
read  60%
read  61%
read  62%
read  63%
read  64%
read  65%
read  66%
read  67%
read  68%
read  69%
read  70%
read  71%
fixing audio PTS inconsistency - diff:  0:00:00.050  - need to add 2 frame(s)
encoding an MP2 audio frame
read  72%
read  73%
read  74%
read  75%
read  76%
read  77%
read  78%
read  79%
read  80%
read  81%
read  82%
fixing audio PTS inconsistency - diff:  0:00:00.039  - need to add 1 frame(s)
encoding an MP2 audio frame
read  83%
read  84%
read  85%
read  86%
read  87%
read  88%
read  89%
read  90%
read  91%
read  92%
read  93%
fixing audio PTS inconsistency - diff:  0:00:00.047  - need to add 1 frame(s)
encoding an MP2 audio frame
read  94%
read  95%
read  96%
read  97%
read  98%
read  99%
read 100%
video PTS inconsistent:  1:40:19.625  1:40:19.625  1:40:19.692  1:40:19.313  diff:  0:00:00.066 
video PTS inconsistent:  1:40:19.659  1:40:19.659  1:40:19.725  1:40:19.346  diff:  0:00:00.066 
video PTS inconsistent:  1:40:19.692  1:40:19.692  1:40:19.759  1:40:19.380  diff:  0:00:00.066 

Audio track 1 is in mp2 format - re-encoding to ac3
Encoding audio to ac3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=  141064kB time=6018.8 bitrate= 192.0kbits/s    

video:0kB audio:141064kB global headers:0kB muxing overhead 0.000000%
*************************************************************
Finished processing file 1057_20071018121500.mpg
*************************************************************
Creating details pages
Background image file is /usr/share/mythtv/mytharchive/themes/MythCenter - Autoplay/MythCenter-Background.png
Music is silence.ac3, length is 5 seconds
Creating details page for 1
Added image /media/store//work/1/thumbnail.jpg
Wrapped text  = Mad Max Beyond Thunderdome
Wrapped text  = Thu Oct 18 12:15 PM
Wrapped text  = Duration 01:40:19
Wrapped text  = Aunty Entity (Tina Turner) will return Mad Max's (Mel Gibson) camels if he will fight the giant Blaster
Wrapped text  = in a barbaric caged arena.
aspect ratio is: 1.33333
Encoding Details Page 1
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
   INFO: [mpeg2enc] Selecting DVD output profile
   INFO: [mpeg2enc] Assuming norm NTSC
   INFO: [mpeg2enc] Progressive input - selecting progressive encoding.
   INFO: [mpeg2enc] Encoding MPEG-2 video to /media/store//work/temp.m2v
   INFO: [mpeg2enc] Horizontal size: 720 pel
   INFO: [mpeg2enc] Vertical size: 480 pel
   INFO: [mpeg2enc] Aspect ratio code: 2 = 4:3 display
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
   INFO: [mpeg2enc] Frame     0     0 I q=8.14 sum act=225.45576    
   INFO: [mpeg2enc] Frame     1     1 P q=8.00 sum act=243.74303    
   INFO: [mpeg2enc] Frame     2     2 P q=8.00 sum act=260.66030    
   INFO: [mpeg2enc] Frame     3     3 P q=8.00 sum act=277.54432    
   INFO: [mpeg2enc] Frame     4     4 P q=8.00 sum act=294.42354    
   INFO: [mpeg2enc] Frame     5     5 P q=8.00 sum act=311.30168    
   INFO: [mpeg2enc] Frame     6     6 P q=8.00 sum act=328.17923    
   INFO: [mpeg2enc] Frame     7     7 P q=8.00 sum act=345.05678    
   INFO: [mpeg2enc] Frame     8     8 P q=8.00 sum act=361.93432    
   INFO: [mpeg2enc] Frame     9     9 P q=8.00 sum act=378.81187    
   INFO: [mpeg2enc] Frame    10    10 P q=8.00 sum act=395.68942    
   INFO: [mpeg2enc] Frame    11    11 P q=8.00 sum act=412.56696    
   INFO: [mpeg2enc] Frame    12    12 P q=8.00 sum act=429.44451    
   INFO: [mpeg2enc] Frame    13    13 P q=8.00 sum act=446.32206    
   INFO: [mpeg2enc] Frame    14    14 P q=8.00 sum act=463.19960    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame    15    15 I q=8.00 sum act=688.65536    
   INFO: [mpeg2enc] Frame    16    16 P q=8.00 sum act=706.87851    
   INFO: [mpeg2enc] Frame    17    17 P q=8.00 sum act=723.77217    
   INFO: [mpeg2enc] Frame    18    18 P q=8.00 sum act=740.63365    
   INFO: [mpeg2enc] Frame    19    19 P q=8.00 sum act=757.49004    
   INFO: [mpeg2enc] Frame    20    20 P q=8.00 sum act=774.34536    
   INFO: [mpeg2enc] Frame    21    21 P q=8.00 sum act=791.20008    
   INFO: [mpeg2enc] Frame    22    22 P q=8.00 sum act=808.05480    
   INFO: [mpeg2enc] Frame    23    23 P q=8.00 sum act=824.90953    
   INFO: [mpeg2enc] Frame    24    24 P q=8.00 sum act=841.76425    
   INFO: [mpeg2enc] Frame    25    25 P q=8.00 sum act=858.61897    
   INFO: [mpeg2enc] Frame    26    26 P q=8.00 sum act=875.47369    
   INFO: [mpeg2enc] Frame    27    27 P q=8.00 sum act=892.32842    
   INFO: [mpeg2enc] Frame    28    28 P q=8.00 sum act=909.18314    
   INFO: [mpeg2enc] Frame    29    29 P q=8.00 sum act=926.03786    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame    30    30 I q=8.00 sum act=1151.49362    
   INFO: [mpeg2enc] Frame    31    31 P q=8.00 sum act=1169.71677    
   INFO: [mpeg2enc] Frame    32    32 P q=8.00 sum act=1186.61042    
   INFO: [mpeg2enc] Frame    33    33 P q=8.00 sum act=1203.47191    
   INFO: [mpeg2enc] Frame    34    34 P q=8.00 sum act=1220.32830    
   INFO: [mpeg2enc] Frame    35    35 P q=8.00 sum act=1237.18362    
   INFO: [mpeg2enc] Frame    36    36 P q=8.00 sum act=1254.03834    
   INFO: [mpeg2enc] Frame    37    37 P q=8.00 sum act=1270.89306    
   INFO: [mpeg2enc] Frame    38    38 P q=8.00 sum act=1287.74779    
   INFO: [mpeg2enc] Frame    39    39 P q=8.00 sum act=1304.60251    
   INFO: [mpeg2enc] Frame    40    40 P q=8.00 sum act=1321.45723    
   INFO: [mpeg2enc] Frame    41    41 P q=8.00 sum act=1338.31195    
   INFO: [mpeg2enc] Frame    42    42 P q=8.00 sum act=1355.16667    
   INFO: [mpeg2enc] Frame    43    43 P q=8.00 sum act=1372.02140    
   INFO: [mpeg2enc] Frame    44    44 P q=8.00 sum act=1388.87612    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame    45    45 I q=8.00 sum act=1614.33188    
   INFO: [mpeg2enc] Frame    46    46 P q=8.00 sum act=1632.55503    
   INFO: [mpeg2enc] Frame    47    47 P q=8.00 sum act=1649.44868    
   INFO: [mpeg2enc] Frame    48    48 P q=8.00 sum act=1666.31017    
   INFO: [mpeg2enc] Frame    49    49 P q=8.00 sum act=1683.16655    
   INFO: [mpeg2enc] Frame    50    50 P q=8.00 sum act=1700.02188    
   INFO: [mpeg2enc] Frame    51    51 P q=8.00 sum act=1716.87660    
   INFO: [mpeg2enc] Frame    52    52 P q=8.00 sum act=1733.73132    
   INFO: [mpeg2enc] Frame    53    53 P q=8.00 sum act=1750.58605    
   INFO: [mpeg2enc] Frame    54    54 P q=8.00 sum act=1767.44077    
   INFO: [mpeg2enc] Frame    55    55 P q=8.00 sum act=1784.29549    
   INFO: [mpeg2enc] Frame    56    56 P q=8.00 sum act=1801.15021    
   INFO: [mpeg2enc] Frame    57    57 P q=8.00 sum act=1818.00493    
   INFO: [mpeg2enc] Frame    58    58 P q=8.00 sum act=1834.85966    
   INFO: [mpeg2enc] Frame    59    59 P q=8.00 sum act=1851.71438    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame    60    60 I q=8.00 sum act=2077.17014    
   INFO: [mpeg2enc] Frame    61    61 P q=8.00 sum act=2095.39329    
   INFO: [mpeg2enc] Frame    62    62 P q=8.00 sum act=2112.28694    
   INFO: [mpeg2enc] Frame    63    63 P q=8.00 sum act=2129.14842    
   INFO: [mpeg2enc] Frame    64    64 P q=8.00 sum act=2146.00481    
   INFO: [mpeg2enc] Frame    65    65 P q=8.00 sum act=2162.86014    
   INFO: [mpeg2enc] Frame    66    66 P q=8.00 sum act=2179.71486    
   INFO: [mpeg2enc] Frame    67    67 P q=8.00 sum act=2196.56958    
   INFO: [mpeg2enc] Frame    68    68 P q=8.00 sum act=2213.42430    
   INFO: [mpeg2enc] Frame    69    69 P q=8.00 sum act=2230.27903    
   INFO: [mpeg2enc] Frame    70    70 P q=8.00 sum act=2247.13375    
   INFO: [mpeg2enc] Frame    71    71 P q=8.00 sum act=2263.98847    
   INFO: [mpeg2enc] Frame    72    72 P q=8.00 sum act=2280.84319    
   INFO: [mpeg2enc] Frame    73    73 P q=8.00 sum act=2297.69792    
   INFO: [mpeg2enc] Frame    74    74 P q=8.00 sum act=2314.55264    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame    75    75 I q=8.00 sum act=2540.00840    
   INFO: [mpeg2enc] Frame    76    76 P q=8.00 sum act=2558.23154    
   INFO: [mpeg2enc] Frame    77    77 P q=8.00 sum act=2575.12520    
   INFO: [mpeg2enc] Frame    78    78 P q=8.00 sum act=2591.98668    
   INFO: [mpeg2enc] Frame    79    79 P q=8.00 sum act=2608.84307    
   INFO: [mpeg2enc] Frame    80    80 P q=8.00 sum act=2625.69840    
   INFO: [mpeg2enc] Frame    81    81 P q=8.00 sum act=2642.55312    
   INFO: [mpeg2enc] Frame    82    82 P q=8.00 sum act=2659.40784    
   INFO: [mpeg2enc] Frame    83    83 P q=8.00 sum act=2676.26256    
   INFO: [mpeg2enc] Frame    84    84 P q=8.00 sum act=2693.11729    
   INFO: [mpeg2enc] Frame    85    85 P q=8.00 sum act=2709.97201    
   INFO: [mpeg2enc] Frame    86    86 P q=8.00 sum act=2726.82673    
   INFO: [mpeg2enc] Frame    87    87 P q=8.00 sum act=2743.68145    
   INFO: [mpeg2enc] Frame    88    88 P q=8.00 sum act=2760.53617    
   INFO: [mpeg2enc] Frame    89    89 P q=8.00 sum act=2777.39090    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame    90    90 I q=8.00 sum act=3002.84666    
   INFO: [mpeg2enc] Frame    91    91 P q=8.00 sum act=3021.06980    
   INFO: [mpeg2enc] Frame    92    92 P q=8.00 sum act=3037.96346    
   INFO: [mpeg2enc] Frame    93    93 P q=8.00 sum act=3054.82494    
   INFO: [mpeg2enc] Frame    94    94 P q=8.00 sum act=3071.68133    
   INFO: [mpeg2enc] Frame    95    95 P q=8.00 sum act=3088.53666    
   INFO: [mpeg2enc] Frame    96    96 P q=8.00 sum act=3105.39138    
   INFO: [mpeg2enc] Frame    97    97 P q=8.00 sum act=3122.24610    
   INFO: [mpeg2enc] Frame    98    98 P q=8.00 sum act=3139.10082    
   INFO: [mpeg2enc] Frame    99    99 P q=8.00 sum act=3155.95554    
   INFO: [mpeg2enc] Frame   100   100 P q=8.00 sum act=3172.81027    
   INFO: [mpeg2enc] Frame   101   101 P q=8.00 sum act=3189.66499    
   INFO: [mpeg2enc] Frame   102   102 P q=8.00 sum act=3206.51971    
   INFO: [mpeg2enc] Frame   103   103 P q=8.00 sum act=3223.37443    
   INFO: [mpeg2enc] Frame   104   104 P q=8.00 sum act=3240.22916    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame   105   105 I q=8.00 sum act=3465.68491    
   INFO: [mpeg2enc] Frame   106   106 P q=8.00 sum act=3483.90806    
   INFO: [mpeg2enc] Frame   107   107 P q=8.00 sum act=3500.80172    
   INFO: [mpeg2enc] Frame   108   108 P q=8.00 sum act=3517.66320    
   INFO: [mpeg2enc] Frame   109   109 P q=8.00 sum act=3534.51959    
   INFO: [mpeg2enc] Frame   110   110 P q=8.00 sum act=3551.37491    
   INFO: [mpeg2enc] Frame   111   111 P q=8.00 sum act=3568.22964    
   INFO: [mpeg2enc] Frame   112   112 P q=8.00 sum act=3585.08436    
   INFO: [mpeg2enc] Frame   113   113 P q=8.00 sum act=3601.93908    
   INFO: [mpeg2enc] Frame   114   114 P q=8.00 sum act=3618.79380    
   INFO: [mpeg2enc] Frame   115   115 P q=8.00 sum act=3635.64853    
   INFO: [mpeg2enc] Frame   116   116 P q=8.00 sum act=3652.50325    
   INFO: [mpeg2enc] Frame   117   117 P q=8.00 sum act=3669.35797    
   INFO: [mpeg2enc] Frame   118   118 P q=8.00 sum act=3686.21269    
   INFO: [mpeg2enc] Frame   119   119 P q=8.00 sum act=3703.06741    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame   120   120 I q=8.00 sum act=3928.52317    
   INFO: [mpeg2enc] Frame   121   121 P q=8.00 sum act=3946.74632    
   INFO: [mpeg2enc] Frame   122   122 P q=8.00 sum act=3963.63998    
   INFO: [mpeg2enc] Frame   123   123 P q=8.00 sum act=3980.50146    
   INFO: [mpeg2enc] Frame   124   124 P q=8.00 sum act=3997.35785    
   INFO: [mpeg2enc] Frame   125   125 P q=8.00 sum act=4014.21317    
   INFO: [mpeg2enc] Frame   126   126 P q=8.00 sum act=4031.06790    
   INFO: [mpeg2enc] Frame   127   127 P q=8.00 sum act=4047.92262    
   INFO: [mpeg2enc] Frame   128   128 P q=8.00 sum act=4064.77734    
   INFO: [mpeg2enc] Frame   129   129 P q=8.00 sum act=4081.63206    
   INFO: [mpeg2enc] Frame   130   130 P q=8.00 sum act=4098.48678    
   INFO: [mpeg2enc] Frame   131   131 P q=8.00 sum act=4115.34151    
   INFO: [mpeg2enc] Frame   132   132 P q=8.00 sum act=4132.19623    
   INFO: [mpeg2enc] Frame   133   133 P q=8.00 sum act=4149.05095    
   INFO: [mpeg2enc] Frame   134   134 P q=8.00 sum act=4165.90567    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame   135   135 I q=8.00 sum act=4391.36143    
   INFO: [mpeg2enc] Frame   136   136 P q=8.00 sum act=4409.58458    
   INFO: [mpeg2enc] Frame   137   137 P q=8.00 sum act=4426.47824    
   INFO: [mpeg2enc] Frame   138   138 P q=8.00 sum act=4443.33972    
   INFO: [mpeg2enc] Frame   139   139 P q=8.00 sum act=4460.19611    
   INFO: [mpeg2enc] Frame   140   140 P q=8.00 sum act=4477.05143    
   INFO: [mpeg2enc] Frame   141   141 P q=8.00 sum act=4493.90615    
   INFO: [mpeg2enc] Frame   142   142 P q=8.00 sum act=4510.76088    
   INFO: [mpeg2enc] Frame   143   143 P q=8.00 sum act=4527.61560    
   INFO: [mpeg2enc] Frame   144   144 P q=8.00 sum act=4544.47032    
   INFO: [mpeg2enc] Signaling last frame = 148
   INFO: [mpeg2enc] Frame   145   145 P q=8.00 sum act=4561.32504    
   INFO: [mpeg2enc] Frame   146   146 P q=8.00 sum act=4578.17977    
   INFO: [mpeg2enc] Frame   147   147 P q=8.00 sum act=4595.03449    
   INFO: [mpeg2enc] Frame   148   148 P q=8.00 sum act=4611.88921    
   INFO: [mpeg2enc] Sequence end inserted
   INFO: [mpeg2enc] Guesstimated final muxed size = 352256

Creating DVD XML file for dvd author (No Menus)
Adding item 1
aspect ratio is: 1.33333
Total size of video files, before multiplexing, is 3229 Mbytes, audio is 137 MBytes, menus are 0 MBytes.
Video will fit onto DVD. 954.55 MBytes of space remaining on recordable DVD.
Multiplexing MPEG stream to /media/store//work/1/final.mpg
Adding sync offset of -61ms
Available streams - video and one audio stream
Multiplex started PID=6484
Starting dvdauthor
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
**ERROR: [mplex] File /media/store//work/1/stream.mv2 unrecogniseable!
**ERROR: [mplex] Unrecogniseable file(s)... exiting.
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing /media/store//work/details-1.mpg...

INFO: Video pts = 0.178 .. 5.149
INFO: Audio[0] pts = 0.178 .. 7.826
STAT: VOBU 10 at 0MB, 1 PGCS

INFO: Generating VTSM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: Processing /media/store//work/1/final.mpg...
```

Clayton

---

### Post by dmfrey on 2007-10-24
Clayton,

I can't say that I have been having the same issue where MythArchive never completes, but it has been giving me problems as well since I moved to Mythbuntu final release.  My audio is well out of sync.  I clearly see in the logs that an audio offset is being applied, but I am not sure how it is deriving the values it is getting.  I am currently trying a test where I set -O 0ms on the mplex command to see if that resolves it, but not sure if that will solve it.

I hope you get MythArchive to work again.  Sorry I couldn't be more helpful.

Dan

---

### Post by bigtdp on 2007-11-02
> **clayton said:**
> Since my upgrade to Gutsy, and when creating dvd iso's in MythArchive, the mytharchive log page stops at "starting dvdauthor". The wiki page for MythArchive says that a majority of this type of error is problems with missing python modules. I tried "apt-get --reinstall install mytharchive" with no success.  Below is my mythburn.log. Anyone have a suggestion on troubleshooting this?

<snip>
Clayton

Hi Clayton,

I'm having the same problem as you... Mytharchive is stuck at "Starting dvdauthor" - have you managed to find a workaround? 

xTx

---

