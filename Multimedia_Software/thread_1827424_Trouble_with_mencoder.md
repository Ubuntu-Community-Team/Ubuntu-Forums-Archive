---
title: "Trouble with mencoder"
date: 2011-08-17
forum: Multimedia Software
---

### Post by /Dev on 2011-08-17
> 
[root@Tira dev]# mencoder tv:// -tv device=/dev/video0 input=1 norm=1 width=640 height=480 -vf pp=md -o Recording -ovc lavc -lavcopts vcodec=avi vbitrate=8000 forceaudio adevice=/dev/snd
MEncoder SVN-r33805-4.6.1 (C) 2000-2011 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: EasyCAP DC60
 Capabilities:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Current format: UYVY
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
Unable to open '/dev/dsp': No such file or directory
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...


Seems like no matter what I try it always prints Selected input hasn't got a tuner! and Unable to open '/dev/dsp' even with forceaudio adevice=/dev/snd

I'm using an EasyCap DC60 Syntek capture card apparently its compatible with the v4l drivers


> 
[root@Tira dev]# lsmod | grep easycap
easycap              1216841  0 
videodev               70734  1 easycap
snd_pcm                60311  6 snd_usb_audio,easycap,snd_cs4236,snd_intel8x0,snd_wss_lib,snd_ac97_codec
usbcore               119004  7 snd_usb_audio,snd_usbmidi_lib,easycap,usbhid,uhci_hcd,ehci_hcd
snd                    43527  16 snd_usb_audio,snd_usbmidi_lib,easycap,snd_mpu401,snd_cs4236,snd_wavefront,snd_intel8x0,snd_wss_lib,snd_ac97_codec,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_pcm,snd_rawmidi,snd_seq_device,snd_timer


What am I doing wrong?

---

