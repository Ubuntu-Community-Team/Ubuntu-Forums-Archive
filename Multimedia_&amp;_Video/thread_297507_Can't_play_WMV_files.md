---
title: "Can't play WMV files"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by Jonathan Métillon on 2006-11-11
Hi,

I installed everything win32 codecs and things to play all restricted formats.

I try to play high definition WMV files (1280x720), and it fails. Here's what happens when I try to play with vlc from command line:

```
VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86
```With mplayer:

```
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           U1400  @ 1.20GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


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

Playing 169_msgundam_ps3_gp_110206m2.wmv.
ASF file format detected.
VIDEO:  [WMV3]  1280x720  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20001->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:2764800  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1280 x 720 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed
```With gxine:

```
(gxine:1146): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
CDROMREADTOCHDR: Input/output error
WARN: could not retrieve file info for `image.nrg': No such file or directory
WARN: can't open nrg image file image.nrg for reading
External func OLEAUT32.dll:8
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:2764800  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU      
Decoder is capable of YUV output (flags 0x1b)
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 456 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```And Totem:

```
External func OLEAUT32.dll:8
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:2764800  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU      
Decoder is capable of YUV output (flags 0x1b)
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 90 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```How can I fix that? Do I really have not enough memory? Maybe I should set a value for VideoRam in the Device section of my xorg.conf ?

I'm using Ubuntu 6.10 with xorg 7.1.1 and I use a multihead setup, without Xinerama. My graphic chipset is an Intel GMA950, which can borrow up to 224 MB of shared memory. I have 1 GB RAM.

---

### Post by Jonathan Métillon on 2006-11-14
I just tried to play the same videos with only one screen, no dual screen. I got the same out of memory error. Any clue?

---

### Post by Jonathan Métillon on 2006-11-22
I updated xorg.conf so it now tries to increase the video memory. I added this line to the two Device sections:

```
VideoRam    131072
```And now the log says:

```
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
...
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(**) I810(0): VideoRAM: 131072 kByte
...
(--) I810(1): Pre-allocated VideoRAM: 7932 kByte
(**) I810(1): VideoRAM: 131072 kByte
```But I still have this BadAlloc error, even with videos that play for sure when I'm not using dual screen.

How can I really force it to borrow more memory? Or get rid of this BadAlloc error?

---

### Post by Jonathan Métillon on 2006-11-22
I discoverd the CacheLines option and played with the numbers. Now the log says:

```
(**) I810(0): VideoRAM: 262144 kByte
(**) I810(0): Requested 8192 cache lines
```It seems enormous but now I can play my 720x576 MPEG-2 and DV files, and edit in Kino.

Also I could play the Miami Vice 720p trailer (1280x544) but not the 1080p version (1920x792). These are Quicktime files and I could play them with Totem.

I could also play some PS3 Gamespot HD videos (1280x720), but not with Totem. These are Windows Media Video files and I could play them with MPlayer and VLC.

---

### Post by Grey on 2007-07-24
I fully realize that I'm not being very helpful, but I just wanted to pop in and complain about this as well.  This has been going on for a LONG time on my laptop.  My specs are very similar, and the symptoms are the same.  Bad Allocs, and no real reason for it.

I find that when this happens though, you can click on the file a whole bunch of times, to open up about 4 copies of VLC playing the same video, and one of them will actually remain open.

---

### Post by Jonathan Métillon on 2007-07-24
Thank you for bumping the thread.

Hope someone with the skills will come up with some enlightenment! ):P

---

### Post by xineoph on 2007-08-14
I had exactly the same problem! Searching a bit around I found [a  wiki]("http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ") which tells that you have to put this line into your device-section in the xorg.conf:

Option "LinearAlloc" "8192"

For me it works now :-) Hope that helps you too!
Grzz

---

### Post by victorawesome on 2007-08-19
So I was getting the badalloc error on vlc ... but I have beryl running on my notebook

I fixed this by selecting the metacity (gnome window manager) instead of the Beryl window manager ... so hopefully that works for you (if you have beryl running)

If you don't ... maybe disable the desktop effects (if you have that enabled)

Its not the best solution b/c it pretty much disables beryl ...but you don't really need fancy windows and stuff when watching vids :)

---

### Post by RomeReactor on 2007-08-19
Hi. As **victorawesome** says, the issue might have to do with having Desktop Effects (Compiz) or Beryl running while trying to play the video. It might have to do with this [bug]("https://bugs.launchpad.net/xorg-server/+bug/111257"). Try the solutions in this section of [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback").

---

