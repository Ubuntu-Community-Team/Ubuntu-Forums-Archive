---
title: "Avidemux crash traceback"
date: 2009-10-24
forum: Multimedia Software
---

### Post by bashphoenux on 2009-10-24
I could really use all the suggestions and help regarding the issue stated below!! Firstly i downloaded AVIdemux, obviously i wanted it for video editing.. i open a video and go to video filters (ctrl+alt+F) and the video filter manager opens in a window!! in that i go to misc option to the left and select eraser(which is used to erase a certain area in the video) i erase the video part i want to and then when close the video filter manager i get a crash traceback window!! Take a look at the screenshot and look at the error displayed, any insight on what went wrong is very much appreciated :) Waiting in anticipation of hearing from someone :) 


[IMG]http://i561.photobucket.com/albums/ss54/bashphoenux/crashbacktrace.png[/IMG]
 I ran the AVIDEMUX from terminal to try and get perspective of what is going wrong ... here the list of events that showed up when i was working with avidemux
```
$ avidemux2_qt4
***************************
Avidemux v2.4.4
***************************
http://www.avidemux.org
Code : Mean, JSC, Gruntster
GFX : Nestor Di , nestordi@augcyl.org
Design : Jakub Misak
FreeBSD : Anish Mistry, amistry@am-productions.biz
Audio : Mihail Zenkov
MacOsX : Kuisathaverat
Win32 : Gruntster

Compiler: GCC 4.3.3
Build Target: Linux (x86)
User Interface: Qt (4.5.0)

Large file available: 1 offset

Initialising prefs
Directory /home/dt/.avidemux exists.Good.
Using /home/dt/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
[cpuCaps]Checking CPU capabilities
MMX detected
3DNOW detected
MMXEXT detected
SSE detected
SSE2 detected
SSE3 detected
[cpuCaps]End of CPU capabilities check (cpuMask :ffffffff)

Registering Encoders
*********************
MJPEG encoder registered
Xvid-4 encoder registered
FFmpeg encoder registered

3 encoder(s) registered

[SDL] Version: 1.2.13
[SDL] Initialisation succeeded
[SDL] Video Driver: x11

Initializing Dithering tables
[xvid] Initializing global Xvid 4
[xvid] Build: xvid-1.1.2
[xvid] SIMD supported: (ff)
MMX
MMXEXT
SSE
SSE2
3DNOW
3DNOWEXT
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3



Registering Filters
*********************

Using real audio device
Spidermonkey initialized.

[Locale] Locale: en_IN
[Locale] Loading language file /usr/bin/i18n/qt_en_IN FAILED
[Locale] Loading language file /usr/bin/i18n/avidemux_en_IN FAILED
[Locale] Test: &Edit -> &Edit

Directory /home/dt/.avidemux/custom exists.Good.
No custom scripts
Custom menu built
The screen seems to be 1152 x 839 px
Found 20 video encoder(s)
Found 9 audio encoder(s)
Found 13 format(s)
46464952 -> 46464952

Riff file detected...
AVI file detected...
** opening OpenDML files **
Main avi header :
Idx1 found at offset 1debd968
Video track is 0
Track 0/2 :
vids (73646976)DX50 (30355844)
Track 1/2 is audio
Not an audio track!
Main header
______________________
dwStreams: :2
dwMicroSecPerFrame: :40000
dwMaxBytesPerSec: :0
dwPaddingGranularity: :0
dwFlags: :2320
dwTotalFrames: :188821
dwInitialFrames: :0
dwWidth: :352
dwHeight: :240

video stream attached:
______________________
Extra Data : 0
fccType :vids (73646976)
fccHandler :DX50 (30355844)
dwFlags: :0
dwInitialFrames: :0
dwRate: :25
dwStart: :0
dwSampleSize: :0
dwScale: :1
dwLength: :188821
dwQuality: :0
dwSampleSize: :0
biSize: :40
biWidth: :352
biHeight: :240
biBitCount: :24
biCompression: :808802372
DX50 (30355844)
biSizeImage: :253440
biXPelsPerMeter: :0
biYPelsPerMeter: :0
biClrUsed: :0

audio stream attached:
______________________

fccType :auds (73647561)
fccHandler :U (00000055)
fccHandler :0x55
dwFlags: :0
dwInitialFrames: :20
dwRate: :12000
dwScale: :1
dwStart: :0
dwLength: :90633091
dwSuggestedBufferSize: :314
dwQuality: :0
dwSampleSize: :1encoding: :85
channels: :2
frequency: :22050
byterate: :12000
blockalign: :1
bitspersample: :0
Extra Data : 24

0000 : ......9.....LIST 01 00 02 00 00 00 39 01 01 00 00 00 4c 49 53 54
0010 : P...INFO 50 00 00 00 49 4e 46 4f
_regularIndex.offset : yes
_Tracks[vidTrack].indx.offset : no
Trying avi type 1 index
Found 188821 videos chunk
Audio track :0, 0 audio chunk
Audio track :1, 289129 audio chunk
Audio track :2, 0 audio chunk
Audio track :3, 0 audio chunk
Audio track :4, 0 audio chunk
Audio track :5, 0 audio chunk
Audio track :6, 0 audio chunk
Audio track :7, 0 audio chunk
Audio track :8, 0 audio chunk
Found 188821 video
we have 24 bytes of extra data in wavheader

Audio streamer initialized
Total audio length : 90633091
OpenDML file successfully read..
Deleting post proc
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3
[Editor] Duration in seconds: 7552, in samples: 166540128

Decoder FCC: DX50 (30355844)
Searching decoder (352 x 240, extradataSize:0)...
[lavc] Build: 3352580
[lavc] Using 0 bytes of extradata for MPEG4 decoder
[lavc] Decoder init: CODEC_ID_MPEG4 video decoder initialized!

checking for B-Frames...
scanning 125 frames








Seems it does not contain B-frames...
End of B-frame check

Editor :Audio streamer initialized
Audio codec: MP2-3
[RDR] Resizing to 352 x 240
[lavc] No accelerated colorspace conversion found


** conf updated **
0 Start at 1 size :10
1 Start at 12 size :22
2 Start at 35 size :11
3 Start at 47 size :9
4 Start at 57 size :8
5 Start at 66 size :4
6 Start at 71 size :13
7 Start at 2000 size :0
Family :0
Family :6
No selection
Tag : 1079
ADMVideoEraser ctor (0xb587080, conf = (nil)), pi = 0xb5b4320, rc now 1
Eraser: no input file selected!
ADMVideoEraser dtor (0xb587080), conf = (nil), pi = 0xb5b4320, rc now 0
No selection
partial
No selection
No selection
Tag : 1079
ADMVideoEraser ctor (0xb587080, conf = (nil)), pi = 0xb59b400, rc now 1
Eraser: no input file selected!
No such file or directory
******** FAILED to write eraser data to (2)
ADMVideoEraser::getCoupledConf(): this = 0xb587080, couples = 0xb5876c0, oldConf = (nil) (was (nil)), pi = 0xb59b400
[lavc] No accelerated colorspace conversion found

in ADMVideoEraser::getFrameNumberNoAlloc(0, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(0, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(527, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(34811, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(52743, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(54326, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(126584, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(176163, ...)
Eraser: no input file selected!
[FlyDialog] Cannot get frame 188821
in ADMVideoEraser::getFrameNumberNoAlloc(188294, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(160340, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(61710, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(11076, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(10549, ...)
Eraser: no input file selected!
in ADMVideoEraser::getFrameNumberNoAlloc(0, ...)
Eraser: no input file selected!
Rank : 1
Eraser: no input file selected!
No such file or directory
******** FAILED to write eraser data to (2)
ADMVideoEraser::getCoupledConf(): this = 0xb587080, couples = 0xb5fec30, oldConf = 0xb5876c0 (was (nil)), pi = 0xb59b400
Saving crash file to /home/dt/.avidemux/crash.js

**Saving script project **
ADMVideoEraser::getCoupledConf(): this = 0xb587080, couples = 0xa791a30, oldConf = 0xb5fec30 (was 0xb5876c0), pi = 0xb59b400
[ADM_escape] Null string ?
Conf size : 0

*********** BACKTRACK **************
Frame 0: avidemux2_qt4(ADM_backTrack+0x4b) [0x8213ccb]
Frame 1: avidemux2_qt4(_Z20sig_segfault_handleri+0x2d) [0x821410d]
()
Frame 2: [0xb8033400]
Frame 3: /lib/tls/i686/cmov/libc.so.6(strlen+0x33) [0xb69c1613]
Frame 4: avidemux2_qt4(_ZN14ADMVideoEraserC1EP22AVDMGenericVideoStreamP10CONFcouple+0x118) [0x81ad4a8]
<>()
Frame 5: avidemux2_qt4(_Z13eraser_createP22AVDMGenericVideoStreamP10CONFcouple+0x30) [0x81ad990]
(AVDMGenericVideoStream,CONFcouple)
Frame 6: avidemux2_qt4 [0x80f7e13]
Frame 7: avidemux2_qt4(_Z19getFirstVideoFilterv+0x31) [0x80f7ee1]
()
Frame 8: avidemux2_qt4(_ZN16filtermainWindow9configureEb+0x11e) [0x86eb02e]
<>()
Frame 9: avidemux2_qt4(_ZN16filtermainWindow11qt_metacallEN11QMetaObject4CallEiPPv+0x17d) [0x86eb6fd]
<>()
Frame 10: /usr/lib/libQtCore.so.4(_ZN11QMetaObject8activateEP7QObjectiiPPv+0x228) [0xb6d31ca8]
<>()
Frame 11: /usr/lib/libQtCore.so.4(_ZN11QMetaObject8activateEP7QObjectPKS_iiPPv+0x60) [0xb6d320e0]
<>()
Frame 12: /usr/lib/libQtGui.so.4(_ZN15QAbstractButton7clickedEb+0x51) [0xb760b2b1]
<>()
Frame 13: /usr/lib/libQtGui.so.4 [0xb73360b9]
Frame 14: /usr/lib/libQtGui.so.4 [0xb7337d14]
Frame 15: /usr/lib/libQtGui.so.4(_ZN15QAbstractButton17mouseReleaseEventEP11QMouseEvent+0x96) [0xb7337fa6]
<>()
Frame 16: /usr/lib/libQtGui.so.4(_ZN11QToolButton17mouseReleaseEventEP11QMouseEvent+0x2c) [0xb741f81c]
<>()
Frame 17: /usr/lib/libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0x753) [0xb6fabb43]
<>()
Frame 18: /usr/lib/libQtGui.so.4(_ZN15QAbstractButton5eventEP6QEvent+0x3e) [0xb7335f5e]
<>()
Frame 19: /usr/lib/libQtGui.so.4(_ZN11QToolButton5eventEP6QEvent+0x4a) [0xb742224a]
<>()
*********** BACKTRACK **************
Memory stat:

Images stat:
___________
Max memory consumed (MB) : 1856
Current memory consumed (MB) : 1856
Max image used : 16
Cur image used : 16
Cleaning up
[lavc] Destroyed
Deleting post proc
Waiting for Spidermonkey to finish...
Cleaning up Spidermonkey.
ADMVideoEraser dtor (0xb587080), conf = 0xa791a30, pi = 0xb59b400, rc now 0
[SDL] Quitting...
End of cleanup

Images stat:
___________
Max memory consumed (MB) : 1856
Current memory consumed (MB) : 371
Max image used : 16
Cur image used : 3
Global mem stat
______________
Memory consumed: 2 (MB)

Goodbye...


here is the contents of crash.js



//AD  <- Needed to identify//
//--automatically built--
//--Project: /home/dt/.avidemux/crash.js

var app = new Avidemux();

//** Video **
// 01 videos source
app.load("/media/sdb7/filename.AVI");
//01 segments
app.clearSegments();
app.addSegment(0,0,188821);
app.markerA=0;
app.markerB=188820;

//** Postproc **
app.video.setPostProc(3,3,0);

app.video.setFps1000(25000);

//** Filters **
app.video.addFilter("eraser","brush_mode=1","brush_size=10","output_color=0","data_file=","debug=12");

//** Video Codec conf **
app.video.codec("Copy","CQ=4","0 ");

//** Audio **
app.audio.reset();
app.audio.codec("copy",128,0,"");
app.audio.normalizeMode=0;
app.audio.normalizeValue=0;
app.audio.delay=0;
app.audio.mixer("NONE");
app.setContainer("AVI");
setSuccess(1);
//app.Exit();

//End of script

```

---

