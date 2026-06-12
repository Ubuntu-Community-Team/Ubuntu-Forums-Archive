---
title: "Video Plays For a Second, Then Dies"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by rebolyte on 2008-02-09
No video. At all. Not even Ogg. It's really driving me nuts. Especially because videos used to work on here (but that was long ago...).

When I open a video file (be it .ogg, .mp4, .wmv, .mpg, anything) in either Totem or MPlayer, it opens the program, and then immediately closes it. Sometimes it will start the first half-second of the video before it dies. So I know it's not a codec error, because it *does * start playing the video.

When I run Totem against a sample .ogg video that came with Ubuntu in the terminal, I get this error:
```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 103 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
When I run MPlayer against the same file, I get this error:
```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8.1 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 2)
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
Playing Experience ubuntu.ogg.
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  360x288  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [libvorbis] Ogg/Vorbis audio decoder
AUDIO: 22050 Hz, 2 ch, s16le, 128.0 kbit/18.14% (ratio: 16000->88200)
Selected audio codec: [vorbis] afm: libvorbis (OggVorbis Audio Decoder)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x86fe468]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 360 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 360x288 => 384x288 Planar YV12
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 22050 Hz/2 channels/4 bpf/30104 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 22050Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
Starting playback...
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed
```
I've re-installed MPlayer and everything in the [RestrictedFormats page]("https://help.ubuntu.com/community/RestrictedFormats") but that didn't seem to make any difference.

The [FONT="Courier New"]X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0[/FONT] error seems to be the culprit. On [this page]("http://www.centos.org/modules/newbb/viewtopic.php?topic_id=12253"), people said that this is a bug in xorg-x11-server 1.4, and that it was fixed in version 1.5. How can I find out what version of that part of X I am running? Can I update to 1.5 to fix this? Any suggestions?

---

### Post by rebolyte on 2008-02-18
I've tried [this solution]("http://ubuntuforums.org/showthread.php?t=480357#post2892802"), but to no avail. I get the same error as above when I run gXine.

Ideas?

---

### Post by rebolyte on 2008-03-02
> **rebolyte said:**
> I've tried [this solution]("http://ubuntuforums.org/showthread.php?t=480357#post2892802"), but to no avail. I get the same error as above when I run gXine.


OK, apparently I hadn't followed the MPlayer section of that solution correctly, because now MPlayer works. I still get the error with Totem and gXine, but thankfully MPlayer works now. Changing the driver to "X11 (XImage/Shm)" did the trick.

Any ideas for the other players? Is this really an bug in X?

---

### Post by naits1986 on 2008-03-26
I have exactly the same problem.. No picture:( Seems like noone knows what to do about this:/

---

