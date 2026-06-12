---
title: "Problem with ladspa plugins"
date: 2011-06-04
forum: Multimedia Software
---

### Post by justdavesj on 2011-06-04
I recently upgraded to 11.04 from 10.04.  After the upgrade my ladspa plugins are not working.  Here is my asound.conf file:
> dave@devel:~/Desktop$ cat /etc/asound.conf
pcm.ladcomp {
      type plug
      slave.pcm "ladcomp_compressor";
  }

pcm.ladcomp_compressor {
      type ladspa
      slave.pcm "ladcomp_limiter";
      path "/usr/lib/ladspa";
      plugins [
          {
              label dysonCompress
              input {
                  #peak limit, release time, fast ratio, ratio
                  controls [0 1 0.5 0.99]
              }
          }
      ]
  }

pcm.ladcomp_limiter {
      type ladspa
      slave.pcm "ALSA:default";
      path "/usr/lib/ladspa";
      plugins [
          {
              label fastLookaheadLimiter
              input {
               #InputGain(Db) -20 -> +20 ; Limit (db) -20 -> 0 ; Release time (s) 0.01 -> 2
               controls [ 20 -10 0.8  ]
              }
          }
     ]
  }
dave@devel:~/Desktop$ 

Here is the error that I receive:
> dave@devel:~/Desktop$ mplayer 1051_20110525200000.mpg -ao alsa:device=ladcomp
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team

Playing 1051_20110525200000.mpg.
TS file format detected.
VIDEO MPEG2(pid=49) AUDIO A52(pid=52) NO SUBS (yet)!  PROGRAM N. 1
VIDEO:  MPEG2  1920x1080  (aspect 3)  29.970 fps  17066.4 kbps (2133.3 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
[AO_ALSA] alsa-lib: pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM ladcomp_compressor
[AO_ALSA] Playback open error: File exists
Failed to initialize audio driver 'alsa:device=ladcomp'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
V:3424.0  20/ 20 85%  6%  0.0% 0 0 
Exiting... (Quit)
dave@devel:~/Desktop$ 
I have been searching and trying different things for days and cannot get this to work.

Any help would be appreciated.

thanks

dave

---

