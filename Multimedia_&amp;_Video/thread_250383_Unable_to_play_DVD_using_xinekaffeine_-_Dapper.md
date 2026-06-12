---
title: "Unable to play DVD using xine/kaffeine - Dapper"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by lpc on 2006-09-04
Hello,

I recently changed from Hoary to Dapper in my Aspire 3002WLCi. Everything seemed to work fine until I tried to play a DVD. Using xine or Kaffeine the video was choppy and out of synchrony with the sound.  In Hoary, xine worked just fine.

I tried adding these lines to /etc/hdparm.conf
/dev/cdrom {
dma = on
}
and uncommenting the line mult_sect_io = 32

But didn't work.

The only way I could play the movie was using "mplayer dvd:// -alang en -cache 8192 -ao sdl -ni -vo x11" otherwise mplayer will output the message copied below.

However mplayer doesn't show the menu and doesn't play full screen.

Anyone knows how to get xine or kaffeine to play DVDs in Dapper? 

Thanks!



____________________________________________

MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://.
libdvdread: Using libdvdcss version 1.2.8 for DVD access
Reading disc structure, please wait...
There are 9 titles on this DVD.
There are 16 chapters in this DVD title.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000196
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000572
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001c36bb
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  384.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
SDL: Using driver: x11
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed : (
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [sdl] 720x480 => 854x480 Planar YV12
A:   0.9 V:   0.5 A-V:  0.394 ct:  0.037  15/ 12 ??% ??% ??,?% 11 0
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.A:   3.0 V:   2.3 A-V:  0.631 ct:  0.224  60/ 57 12% 95%  2.4% 50 0

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

No bind found for key 'MOUSE_BTN0'                         .0% 128 0
alsa-uninit: pcm closed 0.005 ct:  0.048 345/342  6% 59%  1.0% 128 0

_____________________________________

---

### Post by kairu0 on 2006-09-04
> **lpc said:**
> ,
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
SDL: Using driver: x11


The problem is that you don't have XV output support. That's probably the default in those players. The X11 output that you are using is generally slow and choppy.

Are you using the correct X server?

---

### Post by lpc on 2006-09-04
Hi Kairu0,

Thanks for replying my post!

Hmmm.. I don't know if I am using the correct X server. Do you know how I can find that out?

Here is xvinfo output:

$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

and here is the version I have installed:

$sudo aptitude show  xserver-xorg-core | grep Version

Version: 1:1.0.2-0ubuntu10.4

---

### Post by kairu0 on 2006-09-04
In your /etc/X11/xorg.conf file, find the Device section. You should see a driver line in that section. That's your X server.

If you are using the VESA driver, then you should probably switch to a more specific server to get better results.

---

### Post by lpc on 2006-09-04
Hi,

Yes, the driver is vesa.  Sorry, to keep asking but I know nothing about the xserver.  Which server would be good to use? What should I write in the driver line?

Thanks!

---

### Post by lpc on 2006-09-04
Got it! The driver should be "sis". I just followed the instructions to reconfigure the xserver available here: [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC)

and now I can watch dvds using Kaffeine with fullscreen view! :)

Thanks!

---

### Post by kairu0 on 2006-09-06
Glad it's working for you now.

---

