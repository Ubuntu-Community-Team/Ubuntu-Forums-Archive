---
title: "feisty, hauppage pvr 150 and ivtv?"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by Ghosty.be on 2007-05-26
Hello,

i have a hauppage pvr 150 in my pc, now since i am using it already for a long time in previous ubuntu releases i was pleased to hear that it should work out of the box on feisty.
So i did modprobe ivtv, copied my old settings and a script over to the new box, but it seems not to work very nice ...
if i restart my pc and then open mplayer /dev/video0 and switch with ivtv-tune to some frequency i get some other channel than i am expecting and net very clear ... 
this stays like that until i do an rmmod ivtv and modprobe ivtv again. If i tune then to the same frequency i get the right channel completely clear.

Also i have still problems with mplayer itself, i had this in previous releases too, but this was on my older pc which wasnt that fast. 
When playing tv, sometimes the image slows down a bit and then i see in the terminal of the script where i started mplayer: your system is too slow and try the following options ...
but my new machine is an E6600 corre2duo, how can this be too slow? which settings could i use for mplayer to do some more caching perhaps or some other settings that are wrong?
already tried to add nice -5 option in front of my mplayer startup but this does not seem to help ...

script i use to start up my teve window: 
#!/bin/bash
mplayer /dev/video0 
sleep 1
ivtv-tune -f 273.250
exit 0

script to switch channels:
#!/bin/bash
# use: switch [channelnumber]
ARRAY=(203.250 175.250 224.250 273.250 231.250 259.250 266.250 196.250 238.250 168.250 189.250 140.250 210.250 399.250 147.250 442.250 217.250 182.250 161.250 133.250 449.250 245.250 252.250 280.250 154.250 )
channum=$1-1
ivtv-tune -f ${ARRAY[$channum]}

(do not look at the frequencies themselves, they are for belgian television and are perfectly fine)

.ivtv-tune contains:
device=/dev/video0
freqtable=europe-west

.mplayer/gui.conf 
enable_audio_equ = "no"
vo_driver = "xmga"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "-1"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
osd_level = "1"
sub_auto_load = "yes"
sub_unicode = "no"
sub_pos = "100"
sub_overlap = "no"
font_factor = "0.750000"
font_text_scale = "5.000000"
font_osd_scale = "6.000000"
font_blur = "2.000000"
font_outline = "2.000000"
font_autoscale = "3"
cache = "no"
cache_size = "2048"
playbar = "yes"
load_fullscreen = "no"
show_videowin = "yes"
stopxscreensaver = "no"
autosync = "no"
autosync_size = "0"
gui_skin = "default"
gui_save_pos = "yes"
gui_main_pos_x = "454"
gui_main_pos_y = "679"
gui_video_out_pos_x = "454"
gui_video_out_pos_y = "369"
equ_band_00 = "0.000000"
...
equ_band_59 = "0.000000"

output from mplayer:
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================

---

