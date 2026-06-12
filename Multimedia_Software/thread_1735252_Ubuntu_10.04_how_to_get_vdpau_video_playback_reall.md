---
title: "Ubuntu 10.04 how to get vdpau video playback really working"
date: 2011-04-21
forum: Multimedia Software
---

### Post by azenz on 2011-04-21
I have ready around a fair bit, but I find nothing that really helps me to get video acceleration properly working. I got a 64 bit 10.04 system with an Intel 2.8 Ghz quad core, Nvidia 8400GS and Nvidia driver 195.36.24 installed (through Ubuntu's automated system). When I play 1080p video through mplayer or smplayer, I get about 60-90% cpu utilisation (on one core, measured by TOP). Video playback can be choppy with lots of panning or detailed video. Smplayer video playback device is set at standard setting xv in the preferences. When I choose 'vdpau', then playback gets very, very slow! 

Running mplayer -vo vdpau works, but CPU utilisation is even higher than when just running mplayer ..., and with that option I also get choppy video and continual error messages:

Too many video packets in the buffer: (73 in 33789530 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?

The video being played is an mp4v 1080p video. With a 1080i mpeg2 video, I get cpu rates of 30% with mplayer command line, 40% with mplayer -vo vdpau, and about 80% with smplayer using mplayer! But the key issue is mp4 / h264 video, since that is now most of my video. 

Your help is greatly appreciated!

---

### Post by aeiah on 2011-04-21
you may need vpdau enabled versions of mplayer etc. you may find it easier to see if xbmc works as expected rather than replace mplayer with a ppa version or custom compile but the choice is yours.

---

### Post by azenz on 2011-04-21
OK, I managed to upgrade to the latest svn build via adding the PPA repository.

Now - mplayer no longer plays the video fluently, even without vdpau!!! Amazingly, it is worse than before. CPU use is about 100% and the frame rate is terrible. Below some output:

xxx@ubuntu:/$ mplayer 2011-Apr-18_00028.mp4 

MPlayer SVN-r33269-4.4.3 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 2011-Apr-18_00028.mp4.
libavformat file format detected.
[lavf] stream 0: video (mpeg4), -vid 0
[lavf] stream 1: audio (ac3), -aid 0, -alang und
VIDEO:  [MP4V]  1920x1080  24bpp  50.000 fps  153311.7 kbps (18714.8 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 512
 compatible_brands: isomiso2mp41
 creation_time: 1970-01-01 00:00:00
 encoder: Lavf52.93.0
Load subtitles in ./
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
===========================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
=============================================================
===============================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
============================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 1920x1080 => 1920x1080 Planar YV12 
A:   1.7 V:   1.3 A-V:  0.426 ct:  0.020   0/  0 61% 53%  2.4% 48 0 
Capturing not enabled (forgot -capture parameter?)
A:   2.6 V:   2.1 A-V:  0.499 ct:  0.020   0/  0 60% 54%  1.9% 87 0 


           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

--------------
NOTE: I tried the suggestions, such as -nosound, -nocache, -ni etc., but made no difference.

---

### Post by SeijiSensei on 2011-04-21
The video codec is DivX:

VIDEO: [MP4V] 1920x1080 24bpp 50.000 fps 153311.7 kbps (18714.8 kbyte/s)
Selected video codec: [ffo**divx**] vfm: ffmpeg (FFmpeg MPEG-4)

with a ridiculous bitrate.  VDPAU only works with H.264 encodes. 

Do you have a dual- or quad-core machine?  Since you're running the SVN version, you can try adding "-lavdopts threads=2" or "threads=4" as appropriate and see if that helps.

Frankly, I've never seen a video with bitrates like that.  Perhaps it's a Blu-ray rip?  Whoever encoded it made a poor choice of codec by using DivX.

You might want to try these suggestions from the mplayer output:

> - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.

---

### Post by mc4man on 2011-04-21
For mplayer itself you have to specify a -vc, not just a -vo 
Generally on vdpau capable systems mplayer will default to a -vo vdpau anyway ( and for non vdpau supported files it's better to then use a -vo xv, here that is all .avi files

There is a ffodivxvdpau though I believe it only works on some newer nvidia cards (feature-set-C ?)

So here on a barely capable card (feature-set-A I believe), I use something like this in ~/mplayer/config (clipped all non relevant lines, 
```

# Write your default config options here!
vc=ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,

[extension.avi]
profile-desc="profile for .avi files"
vo=xv

```
You could try adding ffodivxvdpau, to end of line if your card supports, if not then don't
```
vc=ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffodivxvdpau,
```

---

### Post by azenz on 2011-04-21
The video is transcoded AVCHD 1080 50p video from my HD camcorder, transcoding with ffmpeg -sameq can result in incredibly high bitrates depending on the video contents! I did mpeg2 before, but divx/mp4 has smaller bitrates for -sameq and plays back better. 

Basically, vdpau playback is terrible! I now encoded using x264, and playback even at 9Mbit with 1080 50p is choppy. I do have a quad core 2.8 Ghz system after all and cpus are not maxed out. It must be something else...Divx/mp4 video does play back fine as long as the bitrate is not much over 75Mbit, I tested that (the -sameq resulting in 100+ Mbit was a bit too much ;) ). But that of course does utilise the cpu a fair bit. 

So basically the problem is h264 / vdpau playback. I did make the mplayer config changes that were suggested, but they made no difference. Using  mplayer vo=vdpau vc=ffh264vdpau gives very very slow playback and the "too slow" warning. But why is my system too slow? Surely, this must be a software config issue!

Also: mplayer vo=vdpau vc=ffodivxvdpau produces very slow divx/mp4 video playback, which is much better using totem or vlc. That has gotten worse since the update to the most recent version.

---

### Post by azenz on 2011-05-30
I ended up getting a better video card, the Nvidia GT 520, but AVCHD (h264) video playback was still extremely choppy. The solution was to use smplayer with vdpau enabled, and skipping the loop filter for HD videos setting - together with the latest Nvidia Linux driver (270.xxx). Now, cpu utilisation during playback is under 10 percent, and playback is almost smooth. Using VLC turned out to be hopeless.

---

### Post by Yellow Pasque on 2011-05-30
VLC doesn't have a direct vdpau output. You have to use va-api and a custom libva to get acceleration in VLC. I have a PPA with that stuff in it, but it only goes back to 10.10 :\

---

