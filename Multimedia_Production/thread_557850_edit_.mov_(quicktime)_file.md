---
title: "edit .mov (quicktime?) file"
date: 2007-09-23
forum: Multimedia Production
---

### Post by kornelix on 2007-09-23
I have some short video clips made with a Panasonic digital camera and I would like to edit them (cut out the junk).

The files have a .mov extension, which I think is quicktime (?). I can play them OK with totem. I tried loading one with kino (as suggested in another thread) but kino claims it is not a DV file.

Is there a way or do I have to do it on Windows?

thanks

---

### Post by UbuWu on 2007-09-23
Try [Kdenlive]("http://www.kdenlive.org/")

---

### Post by kornelix on 2007-09-27
I tried kdenlive. It seems to want the entire KDE environment to work well (help browser, web browser, DVD writer, and I don't know what all). It also crashes. I managed to produce a DV file which no app could play without crashing or complaining about unsupported format. 

Is there no hope with Gnome, anyone?

---

### Post by kornelix on 2007-09-28
I finally found a solution of sorts. 

A .mov file can be edited and converted to .avi using Avidemux. The resulting .avi can be played with VLC. Totem can also play the .avi but the audio is silent.

I found nothing that can cut out part of a .mov file and leave it in .mov format. 

I tried several video editors which all failed miserably until I found avidemux. Most of these projects cannot be taken seriously.

---

### Post by eye208 on 2007-09-28
For simply cutting out scenes, Avidemux will do the job.

If you need a fully featured video editor (with transition effects etc.), try Blender. I do all my video editing with it.

Both programs should be able to read Quicktime .mov files. You can use

mplayer -identify -frames 0 yourfile.mov

to find out details about the video and audio format. (.mov files can contain anything from MJPEG to H.264 and more.)

---

### Post by eye208 on 2007-09-28
> **kornelix said:**
> I found nothing that can cut out part of a .mov file and leave it in .mov format.
Avidemux can export to MP4 which is preferable over MOV. Quicktime can handle both, but the MP4 container format has become an international standard.

You can convert MPEG-4 content from MOV to MP4 containers using simple stream copy mode (i.e. without re-encoding).

---

### Post by kornelix on 2007-09-28
When I used the format MP4, avidemux crashed after spewing the following:

*******************
  Avidemux 2, v  2.3.0
*******************
 [http://fixounet.free.fr/avidemux](http://fixounet.free.fr/avidemux)
 Code      : Mean & JSC 
 GFX       : Nestor Di , [email]nestordi@augcyl.org[/email]
 Testing   : Jakub Misak
 FreeBSD   : Anish Mistry, [email]amistry@am-productions.biz[/email]
Compiled for X86 Arch.

 LARGE FILE AVAILABLE : 1 offset
[Locale] setlocale en_US.UTF-8 
[Locale] Textdomain was messages 
[Locale] Textdomain is now  avidemux 
[Locale] Files  for avidemux appear to be in /usr/share/locale
[Locale] Test : _File 
Initializing prefs

 Registering Encoders
*********************
Mjpeg encoder registred
Xvid-4  encoder registred
FFMPEG  encoder registred

 3 encoder registered
SDL support on Version 1211
Global SDL init...
Initializing Dithering tables
Initializing global xvid 4
        xvid build:xvid-1.1.2
        xvid thread:0
        xvid SIMD supported:(cf)
                MMX
                MMXEXT
                SSE
                SSE2
Checking cpu capabilities
        Cpu has MMX
        Cpu has MMXEXT
        Cpu has SSE
        Cpu has SSE2
End of cpu capabilities check
Directory /home/mico/.avidemux exists.Good.
Using /home/mico/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
Found 17 video encoder
Found 9 audio encoder
Directory /home/mico/.avidemux/custom exists.Good.
No custom script
Found 0 custom scripts, adding them
Menu built
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Registering Filters
*********************

Using dummy audio device
Spidermonkey initialized.
c0b200 -> c0b200
 
 3GPP /MP4/Quicktime file detected..
** opening 3gpp files **
Data first, header later...
Header starts at b2c000
Warning : scale is not in ms 10 !
Duration : 0 ms
**************************************************
Track found
Track Id: 1
Duration: 24500 (ms)
tkhd : 640 480
Decoding mdhd
Myscale in mdhd:10
duration in mdhd:245.000000 (unscaled)
duration in mdhd:24500.000000 (scaled ms)
hdlr video found 
                                        skipping atom vmhd (766D6864) (size 12) at 0xb2c12a
hdlr found but ignored 
sila (616C6973)
                                        skipping atom dinf (64696E66) (size 28) at 0xb2c160
Jpeg Header size 78 
stts:0
Time stts atom found (1)
Using myscale 10
0 frames /245 nbsz..
                nbCo:49
#of chunk 49 max per chunk 0 Max # of sample 245
Time code of last img  : 24500000.000000 
3GP:Tk 1 Nb sz:245 nbFrame:245 duration:10000.000000 us
3gp:All frame keyframes ??
**************************************************
**************************************************
Track found
Track Id: 2
Duration: 24500 (ms)
tkhd : 0 0
Decoding mdhd
Myscale in mdhd:8000
duration in mdhd:196000.000000 (unscaled)
duration in mdhd:24500.000000 (scaled ms)
hdlr audio found (duration 24500.000000 ms)
  (00000000)hdlr found but ignored 
sila (616C6973)
                                        skipping atom dinf (64696E66) (size 28) at 0xb2c7ca
Raw audio detected
Version : 0
Revision :0
Vendor :1885433441
Channels :1
S size :8
Compression :0
Packet Size :0
Bitrate :524288000 (1f400000)
Byterate :8000
Frequency :8000
stts:0
Time stts atom found (1)
Using myscale 8000
1 frames /196000 nbsz..
                196000 frames of the same size 0 , n=1
                nbCo:49
All the same size : 1 (total size 196000 bytes)
Total size in byte : 196000
We have 49 chunks that are too big, adjusting..
**************************************************
Found video codec type :MJPG (47504A4D)

 3gp audio : 196000 bytes (98 chunks)
Byterate     :8000
Frequency :8000
Encoding   :55
Channels   :1
Extra data :0
3gp Go to time succeeded chunk :0 time ask:0 time get:0
3gp/mov file successfully read..
Deleting post proc
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Decoder FCC: MJPG (47504A4D)
 using FF mjpeg codec
FFMpeg build : 3345152
 Decoder init: lavcodec CODEC_ID_MJPEG video decoder initialized!

 no  B- frame with that codec 

 Editor :Audio streamer initialized
 8 BIts pseudo codec unsigned

** conf updated **
**saving:**
Output format:7
 AVI family
We have extradata for video in copy mode (78)
[Raw shift] : Start:0 ms, shift  0
3gp Go to time succeeded chunk :0 time ask:0 time get:0
[Raw shift] : Start:0 ms, offset in sample  0
Ooops, cant mux that...
Ooops, cant mux that...
Ooops, cant mux that...
[LavFormat] Bitrate 64
Cant mux that ! audio
Cant mux that ! audio

Images stat:
___________
Max memory consumed (MB)     : 5400
Current memory consumed (MB) : 5400
Max image used               : 12
Cur image used               : 13
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb72070db in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb77b8755 in g_on_error_stack_trace () from /usr/lib/libglib-2.0.so.0
#3  0x0805b607 in ?? ()
#4  <signal handler called>
#5  0x0843e60a in ?? ()
#6  0x0843e652 in ?? ()
#7  0x08092224 in ?? ()
#8  0x08055fdc in ?? ()
#9  0x08056d63 in ?? ()
#10 0x0843b98f in ?? ()
#11 0x0843bcad in ?? ()
#12 0x0805a429 in ?? ()
#13 0x0814c6e0 in ?? ()
#14 0xb78659d9 in g_cclosure_marshal_VOID__VOID ()
#15 0xb785862b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#16 0xb7869103 in ?? () from /usr/lib/libgobject-2.0.so.0
#17 0x097693c0 in ?? ()
#18 0x00000000 in ?? ()
Memory stat:
Cleaning up
FF base destroyed
Deleting post proc
Waiting for Spidermonkey to finish...
Cleaning up Spidermonkey.
End of cleanup

Images stat:
___________
Max memory consumed (MB)     : 5400
Current memory consumed (MB) : 450
Max image used               : 12
Cur image used               : 1
Global mem stat
______________
        Memory consumed :3 (MB)

 Goodbye...

mico@mico1:~$

---

### Post by kornelix on 2007-09-28
Blender could not open the .mov file. It said "error". UI is horrible.

---

### Post by Perfect Storm on 2007-10-01
Try with cinelerra.

---

### Post by eye208 on 2007-10-01
> **kornelix said:**
> Blender could not open the .mov file. It said "error". UI is horrible.
[LIST=1]
[*]Start Blender.
[*]Switch to the sequence editor screen.
[*]Use the "Add" menu to load the video clip.
[/LIST]

I guess you tried to load the clip using File-->Open. That would have worked if Blender was just a video editor. But it's much more than that. The File menu entries are used to load/save Blender project files.

The Blender wiki ([http://wiki.blender.org/](http://wiki.blender.org/)) contains a manual and some tutorials. Blender has a learning curve, but once you know what it can do, you won't want (or need) anything else.

---

### Post by dangermouse28 on 2008-03-19
Why not use Kino? The trick is to have ffmpeg installed (from Medibuntu repos). Then Kino will happily import from any format and convert to .dv to work on. When you're finished, you can then export to dv, mov, avi as you wish!

---

