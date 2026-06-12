---
title: "cannot get display to start"
date: 2009-08-11
forum: Mythbuntu
---

### Post by bcg30506 on 2009-08-11
I just did an apt-get install dist-upgrade to get my system "up to date" even though it required downgrading my video driver from a working nvidia 185 version back to 180 with vdpau.  The upgrade ran successfully with no errors reported.  I then rebooted, and voila, it now starts in failsafe mode with this in the Xorg.0.log file:

(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

When I run lsmod|grep nvidia, I get:
nvidia               9550436  0 
agpgart                42696  1 nvidia

I did an apt-get --reinstall install nvidia-180-libvdpau

and again, it completed with no errors.  Rebooted and again it starts in failsafe mode instead of my previously working HD mode claiming it cannot find the nvidia module.

uname shows:

2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

How do I get my video back?  Are these upgrades ever tested?  Seems like anytime I do an update to either the kernel package or the video driver, this happens and it is always tricky to make it work.  (Sorry if you sense my frustration.)

---

### Post by bcg30506 on 2009-08-11
I got the display starting back in HD now.  Turns out version 180 of the driver needs the glx package to be installed with:

sudo apt-get install nvidia-glx-180

Then when I rebooted, mythfrontend came back up and I was back in 1920x1080 res and think I'm still using VDPAU for low CPU usage.

However, everything was blue/magenta with the interval player.  I had to drop the Hue setting from 50% back to 0% to make the colors look right.  I recall this same issue in reverse going from the 180 version to 185 before; colors were wrong until I changed Hue from 0 to 50 in the internal player, so this is worth noting to remember.

The only thing wrong now that wasn't before is my mts files from our Canon HD camcorder that I've imported into the recordings database now play stuttered.  They will play for a second this pause then play, etc.  In 185 of nvidia, they played perfectly.  I will try them with mplayer later to see if it's the driver or the version of mythtv.  The dist-upgrade updated mythtv and ffmpeg so I guess they could be the culprit.

By the way, my mythtv version is:

2:0.21.0+fixes-20918-openglvdpau2-0ubuntu0

---

### Post by bcg30506 on 2009-08-11
mplayer plays the files fine, and ffmpeg properly detects the codecs, so it appears the playback problem is due to the mythfrontend internal player.


MPlayer SVN-r29352-4.3.3 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick

Playing /monolith/Canon/AmicalolaWithForemans-2008Jun21/private/avchd/bdmv/stream/00000.mts.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
FPS forced to be 60.000  (ftime: 0.017).
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 1920x1080 => 1920x1080 Planar YV12  [fs]
A:  39.8 V:  39.8 A-V:  0.018 ct: -0.018 2339/2339 64% 10%  0.9% 0 0 

Exiting... (End of file)


From the mythfrontend log when playing it:

2009-08-11 11:35:45.161 TV: Attempting to change from None to WatchingPreRecorded
2009-08-11 11:35:45.163 DPMS Deactivated 
2009-08-11 11:35:45.416 AFD: Opened codec 0x89c5f90, id(H264) type(Video)
2009-08-11 11:35:45.416 AFD: codec AC3 has 2 channels
2009-08-11 11:35:45.417 AFD: Opened codec 0x8fd9d20, id(AC3) type(Audio)
2009-08-11 11:35:45.418 Opening audio device 'default'. ch 2(2) sr 48000
2009-08-11 11:35:45.418 Opening ALSA audio device 'default'.
2009-08-11 11:35:45.450 Mixer unable to find control Master 1
2009-08-11 11:35:45.450 mixer unable to find control Master 1
2009-08-11 11:35:45.596 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-08-11 11:35:45.713 OSD Theme Dimensions W: 1280 H: 720
2009-08-11 11:35:45.730 Unknown altfont: infofont in textarea: callsign
2009-08-11 11:35:45.893 TV: Changing from None to WatchingPreRecorded
2009-08-11 11:35:45.895 Realtime priority would require SUID as root.
2009-08-11 11:35:45.970 [h264 @ 0xb7161850]B picture before any references, skipping
2009-08-11 11:35:45.970 [h264 @ 0xb7161850]decode_slice_header error
2009-08-11 11:35:45.970 [h264 @ 0xb7161850]no frame!
2009-08-11 11:35:45.970 AFD Error: Unknown decoding error
2009-08-11 11:35:45.971 [h264 @ 0xb7161850]B picture before any references, skipping
2009-08-11 11:35:45.971 [h264 @ 0xb7161850]decode_slice_header error
2009-08-11 11:35:45.971 [h264 @ 0xb7161850]no frame!
2009-08-11 11:35:45.971 AFD Error: Unknown decoding error
2009-08-11 11:35:45.971 [h264 @ 0xb7161850]B picture before any references, skipping
2009-08-11 11:35:45.971 [h264 @ 0xb7161850]decode_slice_header error
2009-08-11 11:35:45.971 [h264 @ 0xb7161850]no frame!
2009-08-11 11:35:45.971 AFD Error: Unknown decoding error
2009-08-11 11:35:45.971 [h264 @ 0xb7161850]B picture before any references, skipping
2009-08-11 11:35:45.971 [h264 @ 0xb7161850]decode_slice_header error
2009-08-11 11:35:45.971 [h264 @ 0xb7161850]no frame!
2009-08-11 11:35:45.971 AFD Error: Unknown decoding error
2009-08-11 11:35:45.997 Video timing method: USleep with busy wait
2009-08-11 11:35:47.480 NVP: prebuffering pause
2009-08-11 11:35:48.830 NVP: prebuffering pause
2009-08-11 11:35:50.173 NVP: prebuffering pause
2009-08-11 11:35:51.636 NVP: prebuffering pause
2009-08-11 11:35:52.985 NVP: prebuffering pause
2009-08-11 11:35:54.360 NVP: prebuffering pause
2009-08-11 11:35:55.897 NVP: prebuffering pause
2009-08-11 11:35:57.400 NVP: prebuffering pause
2009-08-11 11:35:58.769 NVP: prebuffering pause
2009-08-11 11:36:00.176 NVP: prebuffering pause
2009-08-11 11:36:01.338 NVP: prebuffering pause
2009-08-11 11:36:02.765 NVP: prebuffering pause
2009-08-11 11:36:04.097 NVP: prebuffering pause
2009-08-11 11:36:05.484 NVP: prebuffering pause
2009-08-11 11:36:06.984 NVP: prebuffering pause
2009-08-11 11:36:08.412 NVP: prebuffering pause
2009-08-11 11:36:09.659 NVP: prebuffering pause
2009-08-11 11:36:10.943 NVP: prebuffering pause
2009-08-11 11:36:12.331 NVP: prebuffering pause
2009-08-11 11:36:13.661 NVP: prebuffering pause
2009-08-11 11:36:15.014 NVP: prebuffering pause
2009-08-11 11:36:15.284 TV: Attempting to change from WatchingPreRecorded to None
2009-08-11 11:36:15.445 TV: Changing from WatchingPreRecorded to None
2009-08-11 11:36:15.830 DPMS Reactivated.

---

