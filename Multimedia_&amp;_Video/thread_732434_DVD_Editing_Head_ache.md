---
title: "DVD Editing Head ache"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by AdNZL on 2008-03-22
I think I'm going to have to end up using windows to avoid this problem, which really sux, but before I bite that bullet I wanted to see if there was anyone out there that could help me figure this out.

I have a Hard Drive video camera that saves its files in a .MOD format. This just seems to me another name for MP4 or some form of mpeg anyway as they play fine in any player in linux especially if I change the file extension to mpeg or mpg. I am trying to make a DVD video with these files and this is where I'm running into major issues. DeeVeeDee works just fine but is much to primitive. QDVDAuther looks like it could be really good if it didn't crash when I tried to use it, so that is out of the question. The only other option available in ManDVD which work's pretty well untill get towards the end of the process and Click on the generate DVD structure. It starts doing its thing, and then after a little while it says that it ran into an error and tells me to check the console.

This is what I find

```
--> Lancement de l'encodage des fichiers ------------------------------------------------------------
--> Lancement de la génération du menu ------------------------------------------------------------
1920+0 records in
1920+0 records out
7680 bytes (7.7 kB) copied
, 0.00147683 seconds, 5.2 MB/s
Assuming raw pcm input file

LAME: Can't get "TERM" environment string.
LAME 3.97 32bits (http://www.mp3dev.org/)
CPU features: 
MMX (ASM used)
, 3DNow! (ASM used)
, SSE

Using polyphase lowpass filter, transition band: 16452 Hz - 17032 Hz
Encoding /dev/stdin to silent.mpa
Encoding as 48 kHz 128 kbps j-stereo MPEG-1 Layer III (12x) qval=3

    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
     0/       ( 0%)|    0:00/     :  |    0:00/     :  |         x|     :  

     0/2      ( 0%)|    0:00/    0:00|    0:00/    0:00|   0.0000x|    0:00 

     4/4     (100%)|    0:00/    0:00|    0:00/    0:00|   9.6000x|    0:00 

   INFO: [ppmtoy4m] Command-line Parameters:
   INFO: [ppmtoy4m]              framerate:  25:1
   INFO: [ppmtoy4m]     pixel aspect ratio:  59:54
   INFO: [ppmtoy4m]          pixel packing:  RGB
   INFO: [ppmtoy4m]              interlace:  top-field-first (interleaved PPM input)
   INFO: [ppmtoy4m]         starting frame:  0
   INFO: [ppmtoy4m]            # of frames:  1, or until input exhausted
   INFO: [ppmtoy4m]     chroma subsampling:  4:2:0 MPEG-2 (horiz. cositing)
jpegtopnm: 
WRITING PPM FILE

   INFO: [ppmtoy4m] Output Stream parameters:
   INFO: [ppmtoy4m]     frame size:  720x576 pixels (622080 bytes)
   INFO: [ppmtoy4m]         chroma:  4:2:0 MPEG-2 (horiz. cositing)
   INFO: [ppmtoy4m]     frame rate:  25/1 fps (~25.000000)
   INFO: [ppmtoy4m]      interlace:  top-field-first
   INFO: [ppmtoy4m]   sample aspect ratio:  59:54
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
   INFO: [mpeg2enc] Selecting DVD output profile
   INFO: [mpeg2enc] Interlaced input - selecting interlaced encoding.
   INFO: [mpeg2enc] Encoding MPEG-2 video to genmenu.m2v
   INFO: [mpeg2enc] Horizontal size: 720 pel
   INFO: [mpeg2enc] Vertical size: 576 pel
   INFO: [mpeg2enc] Aspect ratio code: 2 = 4:3 display
   INFO: [mpeg2enc] Frame rate code:   3 = 25.0 (PAL/SECAM VIDEO / converted FILM)
   INFO: [mpeg2enc] Bitrate: 7500 KBit/s
   INFO: [mpeg2enc] Quality factor: 8 (Quantisation = 9) (1=best, 31=worst)
   INFO: [mpeg2enc] Field order for input: top-field-first
   INFO: [mpeg2enc] Sequence unlimited length
   INFO: [mpeg2enc] Search radius: 16
   INFO: [mpeg2enc] DualPrime: no
   INFO: [mpeg2enc] Using one-pass rate controller
   INFO: [mpeg2enc] GOP SIZE RANGE 9 TO 15 
   INFO: [mpeg2enc] Setting colour/gamma parameters to "PAL B/G"
   INFO: [mpeg2enc] Progressive format frames = 0
   INFO: [mpeg2enc] Using default unmodified quantization matrices
   INFO: [mpeg2enc] Buffering 33 frames
   INFO: [mpeg2enc] Signaling last frame = 0
   INFO: [mpeg2enc] SETTING MMX and MMX for QUANTIZER!
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame     0     0 I q=11.59 sum act=234.62530    
   INFO: [mpeg2enc] Sequence end inserted
   INFO: [mpeg2enc] Guesstimated final muxed size = 63913

   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
   INFO: [mplex] File genmenu.m2v looks like an MPEG Video stream.
   INFO: [mplex] File silent.mpa looks like an MPEG Audio stream.
   INFO: [mplex] Video stream 0: profile 8 selected - ignoring non-standard options!
   INFO: [mplex] Found 1 audio streams and 1 video streams
   INFO: [mplex] Selecting dvdauthor DVD output profile
   INFO: [mplex] Multiplexing video program stream!
   INFO: [mplex] Scanning for header info: Video stream e0 (genmenu.m2v) 
   INFO: [mplex] VIDEO STREAM: e0
   INFO: [mplex] Frame width     : 720
   INFO: [mplex] Frame height    : 576
   INFO: [mplex] Aspect ratio    : 4:3 display
   INFO: [mplex] Picture rate    : 25.000 frames/sec
   INFO: [mplex] Bit rate        : 7500000 bits/sec
   INFO: [mplex] Vbv buffer size : 229376 bytes
   INFO: [mplex] CSPF            : 0
   INFO: [mplex] Scanning for header info: Audio stream c0 (silent.mpa)
   INFO: [mplex] MPEG AUDIO STREAM: c0
   INFO: [mplex] Audio version  : 1.0
   INFO: [mplex] Layer          :        3
   INFO: [mplex] CRC checksums  :       no
   INFO: [mplex] Bit rate       :    16384 bytes/sec (128 kbit/sec)
   INFO: [mplex] Frequency      :     48000 Hz
   INFO: [mplex] Mode           :        1 joint stereo
   INFO: [mplex] Mode extension :        2
   INFO: [mplex] Copyright bit  :        0 no copyright
   INFO: [mplex] Original/Copy  :        1 original
   INFO: [mplex] Emphasis       :        0 none
   INFO: [mplex] SYSTEMS/PROGRAM stream:
   INFO: [mplex] rough-guess multiplexed stream data rate    : 7788744
   INFO: [mplex] target data-rate specified               : 10080000
   INFO: [mplex] Setting specified specified data rate: 10080000
   INFO: [mplex] Scanned to end AU 0
   INFO: [mplex] Run-in Sectors = 89 Video delay = 13019 Audio delay = 16619
   INFO: [mplex] New sequence commences...
   INFO: [mplex] Video e0: buf=      0 frame=000000 sector=00000000
   INFO: [mplex] Audio c0: buf=      0 frame=000000 sector=00000000
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_NZ.UTF-8
INFO: Converting filenames to UTF-8
STAT: 
0:00:00.000

INFO: Picture survolee.png had 2 colors
INFO: Picture cliquee.png had 2 colors
INFO: Constructing blank img
INFO: Pickbuttongroups, success with 1 groups, useimg=1
   INFO: [mplex] STREAM e0 completed @ frame 0.
   INFO: [mplex] STREAM c0 completed @ frame 4.
   INFO: [mplex] Multiplex completion at SCR=4973.
   INFO: [mplex] Video e0: buf=  63913 frame=000000 sector=00000032
   INFO: [mplex] Audio c0: buf=   1920 frame=000004 sector=00000001
   INFO: [mplex] VIDEO_STATISTICS: e0
   INFO: [mplex] Video Stream length:       63913 bytes
   INFO: [mplex] Sequence headers:        1
   INFO: [mplex] Sequence ends   :        1
   INFO: [mplex] No. Pictures    :        1
   INFO: [mplex] No. Groups      :        1
   INFO: [mplex] No. I Frames    :        1 avg. size 63913 bytes
   INFO: [mplex] No. P Frames    :        0 avg. size     0 bytes
   INFO: [mplex] No. B Frames    :        0 avg. size     0 bytes
   INFO: [mplex] Average bit-rate : 12782400 bits/sec
   INFO: [mplex] Peak bit-rate    :        0  bits/sec
   INFO: [mplex] BUFFERING stream too short for useful statistics
   INFO: [mplex] AUDIO_STATISTICS: c0
   INFO: [mplex] Audio stream length 1920 bytes.
   INFO: [mplex] Syncwords      :        5
   INFO: [mplex] Frames         :        5 padded
   INFO: [mplex] Frames         :        0 unpadded
   INFO: [mplex] BUFFERING stream too short for useful statistics
   INFO: [mplex] MUX STATUS: no under-runs detected.
INFO: After read_bmp(): xd=116 yd=4 x0=60 y0=142
INFO: Found EOF in .sub file.
INFO: Max_sub_size=38
WARN: Button y coordinates are odd for button 0: 61x61-175x152; they may not display properly.
INFO: Subtitle inserted at: 0.184656 sd=0
INFO: 1 subtitles added, 0 subtitles skipped, stream: 32, offset: 0.18

Statistics:
- Processed 0 subtitles.
- The longest display line had -1 characters.
- The maximum number of displayed lines was 0.
- The normal display height of the font arial.ttf was 0.
- The bottom display height of the font arial.ttf was 0.
- The biggest subtitle box had 38 bytes.
--> Lancement de DVD Author ------------------------------------------------------------
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_NZ.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
WARN: First cell is not marked as a chapter in PGC 0, setting chapter flag
STAT: Picking VTS 01

STAT: Processing /home/adam//genmenu.mpg...

INFO: Video pts = 
0.184
 .. 
0.224

INFO: Audio[8] pts = 
0.184
 .. 
0.184

INFO: Audio[32] pts = 
0.184
 .. 
0.184

STAT: VOBU 1 at 0MB, 1 PGCS


INFO: Generating VTSM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: pal
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x576
INFO: Audio ch 0 format: mp2/2ch, 48khz 20bps


STAT: Processing /home/adam//gibvideo0.mpg...
WARN: System header found, but PCI/DSI information is not where expected
	(make sure your system header is 18 bytes!)
WARN: Skipping sector, waiting for first VOBU...
WARN: System header found, but PCI/DSI information is not where expected
	(make sure your system header is 18 bytes!)
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
```

And so on for hundreds and hundreds up lines untill it ends with

```
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
WARN: Skipping sector, waiting for first VOBU...
STAT: VOBU 0 at 0MB, 1 PGCS


```

I've tried converting the files into different formats but ManDVD will only read Mpeg of AVI. I tried Cinellera but it doesn't seem to have the options I need. For some reason it only has microsoft AVI, it dosn't have any sound options when saving as an Mpeg and is just basically a pain in the rear. Kino has also not been very helpful and Avidemux won't save video and the sound track together no matter what I try.

I know I could just load up windoze and use nero, and if I had the spare cash I'd just buy the linux version of nero (which I might do at some point when I have the money), But I'd really like to get this working on linux. At the same time I understand that the whole DVD video editing thing is hard thing for people to program in there spare time and that linux will probably always be struggling to provide decent reliable video editing software, still it'd be nice to have.

Anyone have a clue on how to proceed?

---

### Post by brownknight on 2008-03-22
I dont know if this will be of interest to you but I heard Nero 3.0 is free to try for 30 days. Here's the link...

[http://www.nero.com/enu/downloads-linux3-trial.php](http://www.nero.com/enu/downloads-linux3-trial.php)

---

### Post by AdNZL on 2008-03-22
Thank you Brownknight :) I will give that a go. I wonder how many people have actually bought Nero for Linux. Hopefully enough to keep it going, I think I might buy it if the trial works out ok.

Also a bit of an update on my current situation, I have tried ManDVD with some of the smaller unedited files from my camera and they worked absolutely perfectly. I'm currently trying the large unedited video and seeing how well that works. If it works I know that somewhere along the line the editing process is mucking it up. I will try editing it with the built in editor for ManDVD as well, although that is very limited. I'll let ya know how I go.

---

