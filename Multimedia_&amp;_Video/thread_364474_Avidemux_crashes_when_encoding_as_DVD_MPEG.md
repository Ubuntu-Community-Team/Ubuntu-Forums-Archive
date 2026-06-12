---
title: "Avidemux crashes when encoding as DVD MPEG"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by jamespi on 2007-02-18
My Avidemux crashes when trying to convert a 350mb XViD AVI to DVD format using the Auto -> DVD parameters. It also crashes when using 2 pass mode and some other different paramters. I havent had time to check yet if it crashes when doing other files.

This problem occurs on Edgy. Here is the puke from the terminal:
```
LARGE FILE AVAILABLE : 1 offset
Locales for avidemux appear to be in 

I18N : _File 

*******************
  Avidemux 2, v  2.1.2
*******************
 http://fixounet.free.fr/avidemux
 Code      : Mean & JSC 
 GFX       : Nestor Di , nestordi@augcyl.org
 Testing   : Jakub Misak
 FreeBSD   : Anish Mistry, amistry@am-productions.biz
Arcc X86 X86_64 activated.

 Registering Encoders
*********************
Mjpeg encoder registred
Xvid-4  encoder registred
FFMPEG  encoder registred

 3 encoder registered
Initializing global xvid 4
        xvid build:xvid-1.1.0
        xvid thread:0
        xvid SIMD supported:(f3)
                MMX
                MMXEXT
                3DNOW
                3DNOWEXT
Checking cpu capabilities
        Cpu has MMX
        Cpu has 3DNOW
        Cpu has MMXEXT
End of cpu capabilities check
Using /home/jamespi/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
Found 15 video encoder
Found 9 audio encoder
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Registering Filters
*********************

Using dummy audio device
Global SDL init...
Spidermonkey initialized.
46464952 -> 46464952
 
 Riff file detected... 
 AVI file detected...
** opening OpenDML files **
 Main avi header :
Idx1 found at offset 159b4000
Video track is 0
Track 0/2 :
vids (73646976)xvid (64697678)
Track 1/2 is audio
Not an audio track!
dwStreams:              :2
dwMicroSecPerFrame:             :41708
dwMaxBytesPerSec:               :0
dwPaddingGranularity:           :0
dwFlags:                :272
dwTotalFrames:          :60539
dwInitialFrames:                :0
dwWidth:                :624
dwHeight:               :352

video stream attached:
______________________
 Extra Data  : 0
 fccType     :vids (73646976)
 fccHandler :xvid (64697678)
 dwFlags:               :0
 dwInitialFrames:               :0
 dwRate:                :24000
 dwStart:               :0
 dwSampleSize:          :0
 dwScale:               :1001
 dwLength:              :60539
 dwQuality:             :10000
 dwSampleSize:          :0
biSize:         :40
biWidth:                :624
biHeight:               :352
biBitCount:             :12
biCompression:          :1145656920
XVID (44495658)
biSizeImage:            :1317888
biXPelsPerMeter:                :0
biYPelsPerMeter:                :0
biClrUsed:              :0

audio stream attached:
______________________

 fccType     :auds (73647561)
 fccHandler : (00000000)
 fccHandler :0x0
 dwFlags:               :0
 dwInitialFrames:               :1
 dwRate:                :44100
 dwScale:               :1152
 dwStart:               :0
 dwLength:              :96658
 dwSuggestedBufferSize:         :835
 dwQuality:             :-1
 dwSampleSize:          :0
 encoding:              :85
 channels:              :2
 frequency:             :44100
 byterate:              :14826
 blockalign:            :1152
 bitspersample:         :0 Extra Data  : 24

 0000 : ......&#65533;.....JUNK  01 00 02 00 00 00 83 01 01 00 00 00 4a 55 4e 4b
 0010 : ........  1c 10 00 00 00 00 00 00
_regularIndex.offset : yes
_Tracks[vidTrack].indx.offset : no
Trying avi type 1 index
Found 60539 videos chunk
Audio track :0, 0 audio chunk
Audio track :1, 96658 audio chunk
Audio track :2, 0 audio chunk
Audio track :3, 0 audio chunk
Audio track :4, 0 audio chunk
Audio track :5, 0 audio chunk
Audio track :6, 0 audio chunk
Audio track :7, 0 audio chunk
Audio track :8, 0 audio chunk
Found 60539 video 
 we have 24 bytes of extra data in wavheader

 Audio codec:  MP2-3

 Audio streamer initialized
 Total audio length : 37435951
OpenDML file successfully read..
Deleting post proc
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Decoder FCC: XVID (44495658)FFMpeg build : 3342336
Using 0 bytes of extradata for MPEG4 decoder
 Decoder init: lavcodec CODEC_ID_MPEG4 video decoder initialized!

 scanning timeline
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
**PKTZ:READ ERROR
MP3 packetizer: not enough data (start 0 size 365, needs 248)
MapVBR:Get packet failed

 Nb entries in timeline : 96655

 checking for B-Frames...
[mpeg4 @ 0x851702c]frame skip 8
Probably pseudo black frame...
[mpeg4 @ 0x851702c]frame skip 8
Probably pseudo black frame...
Probably pseudo black frame...
 * Frame 5 is A B frame, flag not ok
 * Frame 12 is A B frame, flag not ok
 * Frame 13 is A B frame, flag not ok
 * Frame 15 is A B frame, flag not ok

 * Frame 16 is A B frame, flag not ok
 * Frame 18 is A B frame, flag not ok
 * Frame 19 is A B frame, flag not ok
 * Frame 23 is A B frame, flag not ok
 * Frame 29 is A B frame, flag not ok
 * Frame 31 is A B frame, flag not ok

 * Frame 33 is A B frame, flag not ok
 * Frame 35 is A B frame, flag not ok
 * Frame 37 is A B frame, flag not ok
 * Frame 39 is A B frame, flag not ok
 * Frame 41 is A B frame, flag not ok
 * Frame 43 is A B frame, flag not ok
 * Frame 44 is A B frame, flag not ok
 * Frame 46 is A B frame, flag not ok
 * Frame 47 is A B frame, flag not ok

 * Frame 49 is A B frame, flag not ok


 Mmm this appear to have b-frame...

 But the  index is not up to date 
Trying to unpack the stream
Sucessfully unpacked the bitstream
Initial # of images : 60539, now we have 60540 
FF base destroyed
Creating fresh decoder
FFMpeg build : 3342336
Using 0 bytes of extradata for MPEG4 decoder
 Decoder init: lavcodec CODEC_ID_MPEG4 video decoder initialized!

 checking for B-Frames...
[mpeg4 @ 0x851702c]frame skip 8
Probably pseudo black frame...
[mpeg4 @ 0x851702c]frame skip 8
Probably pseudo black frame...
 * #  * #  * #  * # 
 * #  * #  * #  * #  * #  * # 
 * #  * #  * #  * #  * #  * #  * #  * #  * # 
 * # 

 Mmm this appear to have b-frame...

 And the index is ok

 Frames re-ordered, B-frame friendly now :)
 End of B-frame check

 Editor :Audio streamer initialized
 Audio codec:  MP2-3

** conf updated **
Looks like FRAME_FILM 
 resize by x

 New X x Y = 720 x 406

 Resized to : 720 x 404, add black border 0 x 76
 Codec XDVD found
Updating
**saving:**
Output format:5

 Audio codec : 4
 resampling to 48000
resampling to 48000, 489939163 -> 533267116 bytes.
Resampling from 44100 to 48000
resample: rate ratio 147:160, coeff interpolation not needed
Resampling from 44100 to 48000
resample: rate ratio 147:160, coeff interpolation not needed
Resample : Going back to beginning
Resampling from 44100 to 48000
resample: rate ratio 147:160, coeff interpolation not needed
Resampling from 44100 to 48000
resample: rate ratio 147:160, coeff interpolation not needed

 Init of toolame with bitrate 160 , mode 0 Incoming : 533267116 bytes, fq : 48000, channel : 2 bitrate: 160 outgoing : 55548658

 **** unknown mode ***
Libtoolame successfully initialized
X*VCD: Using DVD PS
Opening mplex muxer (/home/jamespi/small.mpg)
mplex type is :8
creating slave thread
Slave thread : creating job & muxer
output file created
Init ok

 Using ffmpeg mpeg2 encoder (DVD)
ffmpeg mpeg1 cq mode: 4

 Build : 3342336 
me_method : 5
qmin : 2
qmax : 31
max_b_frames : 2
mpeg_quant : 1
max_qdiff : 3
luma_elim_threshold : -2
chroma_elim_threshold : -5
lumi_masking : 0.050000
dark_masking : 0.010000
qcompress : 0.500000
qblur : 0.500000
temporal_cplx_masking No activated
spatial_cplx_masking No activated
Looks like FRAME_FILM 

Pulldown activated...

 Using 2 b frames 
Mpeg12 settings:
____________
FF Max rate   (header) : 8000 kbps
FF Buffer Size(header) : 1966080 bits / 240 kB
FF Max rate   (rc) : 8000 kbps
FF Buffer Size(rc) : 1966080 bits / 240 kB
FF GOP Size    : 12
[mpeg2video @ 0x851702c]removing common factors from framerate

[mpeg4 @ 0x851702c]frame skip 8
 ffmpeg Encoder , w: 720 h:480 mode:1Probably pseudo black frame...
[mpeg4 @ 0x851702c]frame skip 8
Probably pseudo black frame...
[mpeg2video @ 0x851702c]rc buffer underflow
audio done, creating video bitstream
Both stream ready
[MPLEX]File unnamed looks like an MPEG Video stream.
[MPLEX]File unnamed looks like an MPEG Audio stream.
[MPLEX]Video stream 0: profile 8 selected - ignoring non-standard options!
[MPLEX]Found 1 audio streams and 1 video streams
[MPLEX]Scanning for header info: Video stream e0 (unnamed) 
[MPLEX]VIDEO STREAM: e0
[MPLEX]Frame width     : 720
[MPLEX]Frame height    : 480
[MPLEX]Aspect ratio    : 4:3 display
[MPLEX]Picture rate    : 29.970 frames/sec
[MPLEX]Bit rate        : 8000000 bits/sec
[MPLEX]Vbv buffer size : 245760 bytes
[MPLEX]CSPF            : 0
[MPLEX]Scanning for header info: Audio stream c0 (unnamed)
[MPLEX]MPEG AUDIO STREAM: c0
[MPLEX]Audio version  : 1.0
[MPLEX]Layer          :        2
[MPLEX]CRC checksums  :      yes
[MPLEX]Bit rate       :    20480 bytes/sec (160 kbit/sec)
[MPLEX]Frequency      :     48000 Hz
[MPLEX]Mode           :        0 stereo
[MPLEX]Mode extension :        0
[MPLEX]Copyright bit  :        0 no copyright
[MPLEX]Original/Copy  :        0 copy
[MPLEX]Emphasis       :        0 none
Slave :Muxing
Probably pseudo black frame...
Images stat:___________Max memory consumed (MB)     : 5115
Current memory consumed (MB) : 5115
Max image used               : 15
Cur image used               : 15
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb712c34b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb77315a5 in g_on_error_stack_trace () from /usr/lib/libglib-2.0.so.0
#3  0x08059eb7 in ?? ()
#4  <signal handler called>
#5  0x082a6b35 in operator new ()
#6  0x082a7cb7 in operator new ()
#7  0x082a0441 in operator new ()
#8  0x082a0700 in operator new ()
#9  0x0829dd3e in operator new ()
#10 0x0829abde in operator new ()
#11 0x081e58d4 in operator new ()
#12 0x081efbda in operator new ()
#13 0x08054f89 in ?? ()
#14 0x08055c92 in ?? ()
#15 0x0839f51f in operator new ()
#16 0x0839f84d in operator new ()
#17 0x08058d3c in ?? ()
#18 0x082aa9a0 in operator new ()
#19 0xb7844b29 in g_cclosure_marshal_VOID__VOID ()
#20 0xb783779b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#21 0xb7847b93 in g_signal_chain_from_overridden ()
#22 0xb78490b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#23 0xb7849279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#24 0xb7cb8994 in gtk_widget_activate () from /usr/lib/libgtk-x11-2.0.so.0
#25 0xb7bad7d8 in gtk_menu_shell_activate_item ()
#26 0xb7baeda2 in gtk_menu_shell_append () from /usr/lib/libgtk-x11-2.0.so.0
#27 0xb7ba6995 in gtk_menu_reorder_child () from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb7ba0b00 in _gtk_marshal_BOOLEAN__BOXED ()
#29 0xb7835fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#30 0xb783779b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#31 0xb78481e3 in g_signal_chain_from_overridden ()
#32 0xb7848e7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#33 0xb7849279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#34 0xb7cb45f8 in gtk_widget_get_default_style ()
#35 0xb7b99ef3 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#36 0xb7b9b0f7 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#37 0xb7a247ea in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#38 0xb774d802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#39 0xb77507df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#40 0xb7750b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#41 0xb7b9b574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#42 0x0805a143 in ?? ()
#43 0xb6db08cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#44 0x08054311 in ?? ()
Memory stat:
Images stat:___________Max memory consumed (MB)     : 5115
Current memory consumed (MB) : 4367
Max image used               : 15
Cur image used               : 13
Global mem stat
        Memory consumed :59 (MB)

 Goodbye...

```

any ideas?

---

### Post by SadaraX on 2007-02-19
James, you should probably get an updated version of Avidemux. I see that you are using version 2.1.2, which is very old. The latest stable version of Avidemux is 2.3.0. 

You can download it from [www.getdeb.net](www.getdeb.net) or you can try my custom Edgy version:
[http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb](http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb)

If the problem persists, I suggest you talk to the people at the Avidemux forums ([http://www.avidemux.org/admForum/)](http://www.avidemux.org/admForum/)). They are very nice (and I hang out there most of the time).

---

