---
title: "Mplayer doesn't play from DVD"
date: 2009-01-09
forum: Multimedia Software
---

### Post by JCrue on 2009-01-09
Tried to get mplayer to play a DVD today, and after setting it to look at the right device, now have another problem. It gets to detect the format ("MPEG-PS"), then, after a long delay (five minutes or something) poured out,

```
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
a52: CRC check failed!  2.215 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
a52: error at resampling
a52: CRC check failed!  8.151 ct: -0.016   5/  5 ??% ??% ??,?% 1 0 
a52: error at resampling
a52: CRC check failed!  7.955 ct: -0.040  11/ 11 ??% ??% ??,?% 1 0 
a52: error at resampling
a52: CRC check failed!  7.717 ct: -0.072  19/ 19 39%  0%  0.6% 1 0 
a52: error at resampling
a52: CRC check failed!  6.981 ct: -0.076  20/ 20 37%  0%  0.6% 2 0 
a52: error at resampling
a52: CRC check failed!  7.006 ct: -0.100  26/ 26 28%  0%  0.6% 7 0 
a52: error at resampling
a52: CRC check failed!  6.329 ct: -0.112  29/ 29 26%  0%  0.6% 9 0 
a52: error at resampling

```

Etc etc. I updated my copy of mplayer and tried again, and after another wait of about five minutes, a blank mplayer popped up for a few seconds, before closing, and the following was printed to the command line, 

```
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
a52: CRC check failed!  2.199 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
a52: error at resampling
a52: CRC check failed!  8.195 ct: -0.020   6/  6 ??% ??% ??,?% 1 0 
a52: error at resampling
a52: CRC check failed!  7.955 ct: -0.040  11/ 11 ??% ??% ??,?% 1 0 
a52: error at resampling
No bind found for key 'MOUSE_BTN3'.-MOUSE_BTN3_DBL                         
No bind found for key 'MOUSE_BTN3_DBL'.                          0 
No bind found for key 'MOUSE_BTN0'.                         ?% 0 0 
No bind found for key 'MOUSE_BTN0_DBL'.                          0 
A:   0.1 V:   1.9 A-V: -1.775 ct: -0.173  59/ 59  2%  0% 629.8% 0 0 
GNOME screensaver enabled

Exiting... (End of file)

```

If anyone has an ideas...? ^^;

---

### Post by wolfen69 on 2009-01-09
have you been able to play dvd's in the past?

---

### Post by JCrue on 2009-01-10
On this machine, yes, but not on ubuntu on this machine.

---

### Post by mgol on 2009-01-10
Maybe try to change video device in:
System -> Preferences -> Multimedia Systems Selection
If You don't have it there, just execute gstreamer-properties program.

---

### Post by JCrue on 2009-01-10
I can get video playback from files on my hard disk, just not from a DVD.

---

### Post by mgol on 2009-01-10
If You copy (some protected DVDs might not allow this, but I'm pretty sure there is a specialised software for copying them) VIDEO_TS folder to hdd, isn't it still possible to play DVD from those files? You can try SMPlayer which is able to play DVDs from folders located on HDD to check it.

---

