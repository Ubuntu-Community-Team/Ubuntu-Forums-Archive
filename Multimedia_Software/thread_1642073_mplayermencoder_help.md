---
title: "mplayer/mencoder help"
date: 2010-12-09
forum: Multimedia Software
---

### Post by mithereal on 2010-12-09
im trying to recrd frm my video device /dev/video0 with mencoder
it works to view using mplayer with these options

mplayer tv:// -tv driver=v4l2:input=1:channel=1:width=768:height=768:device=/dev/video0:norm=NTSC
however when i try to use mencoder using these options i get the following error:

mencoder tv:// -tv driver=v4l2:input=1:channel=1:width=768:height=768:device=/dev/video0:norm=1 -o a.avi -ovc xvid
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: BT878 video ( *** UNKNOWN/GENER
 Capabilites:  video capture  video overlay  VBI capture device  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = PAL; 5 = PAL-BG; 6 = PAL-H; 7 = PAL-I; 8 = PAL-DK; 9 = PAL-M; 10 = PAL-N; 11 = PAL-Nc; 12 = PAL-60; 13 = SECAM; 14 = SECAM-B; 15 = SECAM-G; 16 = SECAM-H; 17 = SECAM-DK; 18 = SECAM-L; 19 = SECAM-Lc;
 inputs: 0 = Composite0; 1 = Composite1; 2 = S-Video; 3 = Composite3;
 Current input: 1
 Current format: YVU420
tv.c: norm_from_string(1): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
Video buffer shorter than 3 times audio frame duration.
You will probably experience heavy framedrops.
[V] filefmt:9  fourcc:0x32315659  size:768x480  fps:29.970  ftime:=0.0334
xvid: using library version 1.2.2 (build xvid-1.2.2)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 768 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: XviD (768x480 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=768x480, sampled=768x480
xvid: you must specify one or a valid combination of 'bitrate', 'pass', 'fixed_quant' settings
FATAL: Cannot initialize video driver.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x32315659.
Read DOCS/HTML/en/codecs.html!
==========================================================================

Exiting...

any ideas on how to fix??

---

