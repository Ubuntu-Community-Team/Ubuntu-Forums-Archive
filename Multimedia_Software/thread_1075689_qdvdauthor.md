---
title: "qdvdauthor"
date: 2009-02-20
forum: Multimedia Software
---

### Post by Komir on 2009-02-20
To create a dvd with menus I started to use qdvdauthor. Everything is great but the problem is when qdvdauthor should make a dvd on the execution dialog displays the following text and dont make dvd.
At the end make "Error opening /home/komir/Desktop//Unnamed/test/test.mpeg2: No such file or directory". 	
I am a little confused :-k
Sorry for my english, 	
I hope that you understand me:oops:


[PHP]cmd> /usr/bin/jpegtopnm "/home/komir/Desktop//Unnamed/Main Menu VMGM/background.jpg" |/usr/bin/ppmtoy4m -n 25 -r -S 420mpeg2 -F25:1 -A59:54 -I t -L |/usr/bin/mpeg2enc -f 8 -n p -a 3 -o "/home/komir/Desktop//Unnamed/Main Menu VMGM/menu.m2v"
cmd> cp /usr/share/qdvdauthor/silence.ac3 "/home/komir/Desktop//Unnamed/Main Menu VMGM/menu.mp2"
cmd> /usr/bin/mplex -f 8 -S 0 -M -o "/home/komir/Desktop//Unnamed/Main Menu VMGM/menu.mpg" "/home/komir/Desktop//Unnamed/Main Menu VMGM/menu.m2v" "/home/komir/Desktop//Unnamed/Main Menu VMGM/menu.mp2"
cmd> /usr/bin/spumux -m dvd "/home/komir/Desktop//Unnamed/Main Menu VMGM/menu.xml" < "/home/komir/Desktop//Unnamed/Main Menu VMGM/menu.mpg" > "/home/komir/Desktop//Unnamed/Main Menu VMGM_menu.mpg"
cmd> /usr/bin/dvdauthor -x "/home/komir/Desktop//Unnamed/dvdauthor.xml"[/PHP]

[PHP]   INFO: [ppmtoy4m] Command-line Parameters:
   INFO: [ppmtoy4m]              framerate:  25:1
   INFO: [ppmtoy4m]     pixel aspect ratio:  59:54
   INFO: [ppmtoy4m]          pixel packing:  RGB
   INFO: [ppmtoy4m]              interlace:  top-field-first (interleaved PPM input)
   INFO: [ppmtoy4m]         starting frame:  0
   INFO: [ppmtoy4m]            # of frames:  25, repeat last frame until done
   INFO: [ppmtoy4m]     chroma subsampling:  4:2:0 MPEG-2 (horiz. cositing)
jpegtopnm: WRITING PPM FILE
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
   INFO: [mpeg2enc] SETTING EXTENDED MMX for PREDICTION!
   INFO: [ppmtoy4m] Output Stream parameters:
   INFO: [ppmtoy4m]     frame size:  720x576 pixels (622080 bytes)
   INFO: [ppmtoy4m]         chroma:  4:2:0 MPEG-2 (horiz. cositing)
   INFO: [ppmtoy4m]     frame rate:  25/1 fps (~25.000000)
   INFO: [ppmtoy4m]      interlace:  top-field-first
   INFO: [ppmtoy4m]   sample aspect ratio:  59:54
   INFO: [mpeg2enc] Selecting DVD output profile
   INFO: [mpeg2enc] Interlaced input - selecting interlaced encoding.
   INFO: [mpeg2enc] Encoding MPEG-2 video to /home/komir/Desktop//Unnamed/Main Menu VMGM/menu.m2v
   INFO: [mpeg2enc] Horizontal size: 720 pel
   INFO: [mpeg2enc] Vertical size: 576 pel
   INFO: [mpeg2enc] Aspect ratio code: 3 = 16:9 display
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
   INFO: [mpeg2enc] SETTING MMX and MMX for QUANTIZER!
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame     0     0 I q=8.00 sum act=246.25749    
   INFO: [mpeg2enc] Frame     1     1 P q=8.00 sum act=266.71818    
   INFO: [mpeg2enc] Frame     2     2 P q=8.00 sum act=286.48531    
   INFO: [mpeg2enc] Frame     3     3 P q=8.00 sum act=306.23716    
   INFO: [mpeg2enc] Frame     4     4 P q=8.00 sum act=325.98431    
   INFO: [mpeg2enc] Frame     5     5 P q=8.00 sum act=345.73014    
   INFO: [mpeg2enc] Frame     6     6 P q=8.00 sum act=365.47563    
   INFO: [mpeg2enc] Frame     7     7 P q=8.00 sum act=385.22103    
   INFO: [mpeg2enc] Frame     8     8 P q=8.00 sum act=404.96644    
   INFO: [mpeg2enc] Frame     9     9 P q=8.00 sum act=424.71185    
   INFO: [mpeg2enc] Frame    10    10 P q=8.00 sum act=444.45726    
   INFO: [mpeg2enc] Frame    11    11 P q=8.00 sum act=464.20267    
   INFO: [mpeg2enc] Frame    12    12 P q=8.00 sum act=483.94808    
   INFO: [mpeg2enc] Frame    13    13 P q=8.00 sum act=503.69349    
   INFO: [mpeg2enc] Frame    14    14 P q=8.00 sum act=523.43890    
   INFO: [mpeg2enc] NEW GOP INIT length 15
   INFO: [mpeg2enc] Frame    15    15 I q=8.00 sum act=769.69639    
   INFO: [mpeg2enc] Frame    16    16 P q=8.00 sum act=790.15708    
   INFO: [mpeg2enc] Frame    17    17 P q=8.00 sum act=809.92421    
   INFO: [mpeg2enc] Frame    18    18 P q=8.00 sum act=829.67606    
   INFO: [mpeg2enc] Frame    19    19 P q=8.00 sum act=849.42320    
   INFO: [mpeg2enc] Frame    20    20 P q=8.00 sum act=869.16904    
   INFO: [mpeg2enc] Frame    21    21 P q=8.00 sum act=888.91452    
   INFO: [mpeg2enc] Signaling last frame = 24
   INFO: [mpeg2enc] Frame    22    22 P q=8.00 sum act=908.65993    
   INFO: [mpeg2enc] Frame    23    23 P q=8.00 sum act=928.40534    
   INFO: [mpeg2enc] Frame    24    24 P q=8.00 sum act=948.15075    
   INFO: [mpeg2enc] Sequence end inserted
   INFO: [mpeg2enc] Guesstimated final muxed size = 79803

   INFO: [mplex] mplex version 1.8.0 (2.2.4 $Date: 2005/08/28 17:50:54 $)
   INFO: [mplex] File /home/komir/Desktop//Unnamed/Main Menu VMGM/menu.m2v looks like an MPEG Video stream.
   INFO: [mplex] File /home/komir/Desktop//Unnamed/Main Menu VMGM/menu.mp2 looks like an AC3 Audio stream.
   INFO: [mplex] Video stream 0: profile 8 selected - ignoring non-standard options!
   INFO: [mplex] Found 1 audio streams and 1 video streams
   INFO: [mplex] Selecting dvdauthor DVD output profile
   INFO: [mplex] Multiplexing video program stream!
   INFO: [mplex] Scanning for header info: Video stream e0 (/home/komir/Desktop//Unnamed/Main Menu VMGM/menu.m2v) 
   INFO: [mplex] VIDEO STREAM: e0
   INFO: [mplex] Frame width     : 720
   INFO: [mplex] Frame height    : 576
   INFO: [mplex] Aspect ratio    : 16:9 display
   INFO: [mplex] Picture rate    : 25.000 frames/sec
   INFO: [mplex] Bit rate        : 7500000 bits/sec
   INFO: [mplex] Vbv buffer size : 229376 bytes
   INFO: [mplex] CSPF            : 0
   INFO: [mplex] Scanning for header info: AC3 Audio stream 00 (/home/komir/Desktop//Unnamed/Main Menu VMGM/menu.mp2)
   INFO: [mplex] AC3 frame size = 256
   INFO: [mplex] AC3 AUDIO STREAM:
   INFO: [mplex] Bit rate       :     8192 bytes/sec ( 64 kbit/sec)
   INFO: [mplex] Frequency      :     48000 Hz
   INFO: [mplex] SYSTEMS/PROGRAM stream:
   INFO: [mplex] rough-guess multiplexed stream data rate    : 7721848
   INFO: [mplex] target data-rate specified               : 10080000
   INFO: [mplex] Setting specified specified data rate: 10080000
   INFO: [mplex] Run-in Sectors = 89 Video delay = 13019 Audio delay = 16619
   INFO: [mplex] New sequence commences...
   INFO: [mplex] Video e0: buf=      0 frame=000000 sector=00000000
   INFO: [mplex] Audio bd: buf=      0 frame=000000 sector=00000000
   INFO: [mplex] Scanned to end AU 24
   INFO: [mplex] STREAM bd completed @ frame 29.
   INFO: [mplex] STREAM e0 completed @ frame 24.
   INFO: [mplex] Multiplex completion at SCR=12141.
   INFO: [mplex] Video e0: buf=  79803 frame=000024 sector=00000041
   INFO: [mplex] Audio bd: buf=   7680 frame=000029 sector=00000004
   INFO: [mplex] VIDEO_STATISTICS: e0
   INFO: [mplex] Video Stream length:       79803 bytes
   INFO: [mplex] Sequence headers:        2
   INFO: [mplex] Sequence ends   :        1
   INFO: [mplex] No. Pictures    :       25
   INFO: [mplex] No. Groups      :        2
   INFO: [mplex] No. I Frames    :        2 avg. size 28433 bytes
   INFO: [mplex] No. P Frames    :       23 avg. size   997 bytes
   INFO: [mplex] No. B Frames    :        0 avg. size     0 bytes
   INFO: [mplex] Average bit-rate :   638400 bits/sec
   INFO: [mplex] Peak bit-rate    :   544000  bits/sec
   INFO: [mplex] BUFFERING stream too short for useful statistics
   INFO: [mplex] AUDIO_STATISTICS: bd
   INFO: [mplex] Audio stream length 7680 bytes.
   INFO: [mplex] Frames         :       30
   INFO: [mplex] BUFFERING stream too short for useful statistics
   INFO: [mplex] MUX STATUS: no under-runs detected.
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_AU.UTF-8
INFO: Converting filenames to UTF-8
STAT: 0:00:00.000

INFO: Picture /home/komir/Desktop//Unnamed/Main Menu VMGM/highlighted.png had 2 colors
INFO: Picture /home/komir/Desktop//Unnamed/Main Menu VMGM/selected.png had 2 colors
INFO: Constructing blank img
INFO: Pickbuttongroups, success with 1 groups, useimg=1
INFO: Found EOF in .sub file.
INFO: Max_sub_size=194
INFO: 1 subtitles added, 0 subtitles skipped, stream: 32, offset: 0.18

Statistics:
- Processed 0 subtitles.
- The longest display line had -1 characters.
- The maximum number of displayed lines was 0.
- The normal display height of the font arial.ttf was 0.
- The bottom display height of the font arial.ttf was 0.
- The biggest subtitle box had 194 bytes.
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_AU.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing /home/komir/Desktop//Unnamed/test/test.mpeg2...
ERR:  Error opening /home/komir/Desktop//Unnamed/test/test.mpeg2: No such file or directory
[/PHP]

---

### Post by Komir on 2009-02-20
Think I know, what could be a problem. Temp path must be /tmp/ folder:redface:

---

