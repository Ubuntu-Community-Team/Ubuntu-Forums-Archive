---
title: "[SOLVED] DVDs won't play"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by Mateo on 2008-01-19
Ok, i've looked at other similar topics and they don't help me.  Some run-down first:

[LIST]
[*]Medibuntu.org repos - installed
[*]libdvdcss2 - installed
[*]libdvdnav4 - installed
[*]libdvdread3 - installed
[*]ffmpeg - installed
[*]mplayer-nogui - installed
[/LIST]

at the terminal I type "mplayer dvd://" and get:

```
Playing dvd://.
Couldn't open DVD device: /dev/dvd
[file] No filename
Failed to open dvd://.

```

ok, i do some research and it seems my dvd player is located at /dev/scd0.  So at the terminal I type: "mplayer /dev/scd0" and I get:

```
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick

Playing /dev/scd0.


```

with a blinking cursor at the bottom.  No mplayer screen pops up or anything.  I have tried several different DVDs all with the same result.  Currently I am testing with a dvd I know should work, as I've played it using mplayer in the past.  So..... ideas anyone? ;)

*note: please do not recommend alternative players.*

---

### Post by Mateo on 2008-01-19
FYI:  this is the fstab entry for the dvd player:

```
/dev/scd0       /media/dvdrom   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by Mateo on 2008-01-19
```
Playing /dev/scd0.
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  4587.2 kbps (573.4 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4

SwScaler: BICUBIC scaler, from yuv420p to bgr24 using MMX2
SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
SwScaler: using n-tap MMX scaler for vertical scaling (BGR)
SwScaler: using MMX2 YV12->BGR24 Converter
SwScaler: 720x480 -> 720x540
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5   8/  8 ??% ??% ??,?% 0 0 
gnome_screensaver_control()
Exiting... (End of file)
matthew@matthew-desktop:~$ 

```

---

### Post by Mateo on 2008-01-20
bump

---

### Post by Mateo on 2008-01-25
bump

---

### Post by Lord Illidan on 2008-01-25
What about Xine, Vlc or totem-xine? Same problems?

---

### Post by Mateo on 2008-01-26
bump.

---

### Post by Mateo on 2008-01-26
wrong thread, sorry

---

### Post by oldos2er on 2008-01-26
According to your fstab, the mount point for your dvd drive is /media/dvdrom, have you tried that?

---

### Post by Mateo on 2008-01-26
this works:

```
totem /media/dvdrom
```

but the same command doesn't work in mplayer.  I get this message:

```
matthew@matthew-desktop:~$ mplayer /media/dvdrom/
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick

Playing /media/dvdrom/.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Seek failed



```

---

### Post by Mateo on 2008-01-26
well, at least some progress.  now when I do this:

```
mplayer /dev/scd0
```

a window opens that appears to be playing pixelated garbage that can't be made out.  here's the terminal output:

```
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing /dev/scd0.
MPEG-PS file format detected.
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  4587.2 kbps (573.4 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.0   1/  1 ??% ??% ??,?% 0 0 [J
V:   0.5   2/  2 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5   3/  3 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5   4/  4 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5   5/  5 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5   6/  6 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5   7/  7 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5   8/  8 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5   9/  9 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5  10/ 10 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5  11/ 11 ??% ??% ??,?% 0 0 [J
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x480 => 720x540 Planar YV12  [zoom]
V:   0.5  12/ 12 ??% ??% ??,?% 0 0 [J
V:   0.5  13/ 13 ??% ??% ??,?% 0 0 [J
V:   0.6  14/ 14 ??% ??% ??,?% 0 0 [J
V:   0.2  15/ 15 ??% ??% ??,?% 0 0 [J
V:   0.2  16/ 16 24%  9%  0.0% 0 0 [J
V:   0.3  17/ 17 22%  9%  0.0% 0 0 [J
V:   0.3  18/ 18 21% 10%  0.0% 0 0 [J
V:   0.3  19/ 19 20% 10%  0.0% 0 0 [J
V:   0.4  20/ 20 22% 10%  0.0% 0 0 [J
V:   0.7  21/ 21 21% 10%  0.0% 0 0 [J
V:   0.7  22/ 22 20% 11%  0.0% 0 0 [J
V:   0.8  23/ 23 19% 11%  0.0% 0 0 [J
V:   0.8  24/ 24 19% 11%  0.0% 0 0 [J
V:   0.8  25/ 25 18% 11%  0.0% 0 0 [J
V:   0.9  26/ 26 17% 11%  0.0% 0 0 [J
V:   0.9  27/ 27 17% 11%  0.0% 0 0 [J
V:   0.9  28/ 28 16% 12%  0.0% 0 0 [J
V:   1.0  29/ 29 16% 12%  0.0% 0 0 [J
V:   1.0  30/ 30 16% 12%  0.0% 0 0 [J
V:   1.0  31/ 31 15% 12%  0.0% 0 0 [J
V:   1.1  32/ 32 15% 12%  0.0% 0 0 [J
V:   1.1  33/ 33 15% 12%  0.0% 0 0 [J
V:   1.1  34/ 34 15% 12%  0.0% 0 0 [J
V:   1.2  35/ 35 15% 12%  0.0% 0 0 [J
V:   1.2  36/ 36 15% 12%  0.0% 0 0 [J
V:   1.2  37/ 37 15% 12%  0.0% 0 0 [J
V:   1.2  38/ 38 15% 12%  0.0% 0 0 [J
V:   1.3  39/ 39 14% 13%  0.0% 0 0 [J
V:   1.3  40/ 40 14% 13%  0.0% 0 0 [J
V:   1.3  41/ 41 14% 13%  0.0% 0 0 [J
V:   1.4  42/ 42 14% 13%  0.0% 0 0 [J
V:   1.4  43/ 43 14% 13%  0.0% 0 0 [J
V:   1.4  44/ 44 14% 13%  0.0% 0 0 [J
V:   1.5  45/ 45 14% 13%  0.0% 0 0 [J
V:   1.5  46/ 46 14% 13%  0.0% 0 0 [J
V:   1.7  47/ 47 14% 13%  0.0% 0 0 [J
V:   1.7  48/ 48 14% 13%  0.0% 0 0 [J
V:   1.8  49/ 49 14% 13%  0.0% 0 0 [J
V:   1.8  50/ 50 14% 13%  0.0% 0 0 [J
V:   1.8  51/ 51 14% 13%  0.0% 0 0 [J
V:   1.9  52/ 52 13% 13%  0.0% 0 0 [J
V:   1.9  53/ 53 13% 13%  0.0% 0 0 [J
V:   1.9  54/ 54 13% 13%  0.0% 0 0 [J
V:   2.0  55/ 55 13% 13%  0.0% 0 0 [J
V:   2.0  56/ 56 13% 13%  0.0% 0 0 [J
V:   2.0  57/ 57 13% 13%  0.0% 0 0 [J
V:   2.2  58/ 58 13% 13%  0.0% 0 0 [J
V:   2.2  59/ 59 13% 13%  0.0% 0 0 [J
V:   2.3  60/ 60 13% 14%  0.0% 0 0 [J
V:   2.3  61/ 61 13% 14%  0.0% 0 0 [J
V:   2.3  62/ 62 13% 14%  0.0% 0 0 [J
V:   2.4  63/ 63 13% 14%  0.0% 0 0 [J
V:   2.4  64/ 64 13% 14%  0.0% 0 0 [J
V:   2.4  65/ 65 13% 14%  0.0% 0 0 [J
V:   2.7  66/ 66 13% 14%  0.0% 0 0 [J
V:   2.7  67/ 67 13% 14%  0.0% 0 0 [J
V:   2.8  68/ 68 13% 14%  0.0% 0 0 [J
V:   2.8  69/ 69 13% 14%  0.0% 0 0 [J
V:   2.8  70/ 70 13% 14%  0.0% 0 0 [J
V:   2.9  71/ 71 13% 14%  0.0% 0 0 [J
V:   2.9  72/ 72 13% 14%  0.0% 0 0 [J
V:   2.9  73/ 73 13% 14%  0.0% 0 0 [J
V:   3.0  74/ 74 13% 14%  0.0% 0 0 [J
V:   3.0  75/ 75 13% 14%  0.0% 0 0 [J
V:   3.0  76/ 76 13% 14%  0.0% 0 0 [J
V:   3.1  77/ 77 13% 14%  0.0% 0 0 [J
V:   3.2  78/ 78 13% 14%  0.0% 0 0 [J
V:   3.2  79/ 79 13% 14%  0.0% 0 0 [J
V:   3.3  80/ 80 13% 14%  0.0% 0 0 [J
V:   3.3  81/ 81 12% 14%  0.0% 0 0 [J
V:   3.3  82/ 82 12% 14%  0.0% 0 0 [J
V:   3.4  83/ 83 12% 14%  0.0% 0 0 [J
V:   3.4  84/ 84 12% 14%  0.0% 0 0 [J
V:   3.4  85/ 85 12% 14%  0.0% 0 0 [J
V:   3.5  86/ 86 12% 14%  0.0% 0 0 [J
V:   3.5  87/ 87 12% 14%  0.0% 0 0 [J
V:   3.5  88/ 88 12% 14%  0.0% 0 0 [J

Exiting... (Quit)
```

---

### Post by Mateo on 2008-01-28
bump

---

### Post by mc4man on 2008-01-28
I'm not big on mplayer but if your going to run it from the command line then you have to specify what you want.(and know what it is you want to do) Keeping in mind it doesn't play menus you'll need to pick a track (title). for simple dvd playback
```
mplayer dvd://1
``` will work if main movie is title1.
If the video is still pixelated then change your video driver

edit: if your just using mplayer to view dvd's then use the gui or for a little more control install smplayer

---

### Post by Mateo on 2008-01-31
^^ that doesn't work.

any other ideas?

---

### Post by rvm4000 on 2008-01-31
Maybe the first title in the DVD is not the movie.

Try with 
**mplayer dvd://2** 
**mplayer dvd://3**
...

By the way, I read in you first post that you tried **mplayer /dev/scd0**. I think this is not right. Try with
**mplayer -dvd-device /dev/scd0 dvd://**

---

### Post by ubuntu-freak on 2008-01-31
You should be using VLC to play DVD's as it plays them well. It also fully supports menus.
 
Check out part 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) as it helps you make VLC default for DVD's and shows you how to enable encrypted DVD playback. It's worth a look.
 
Nathan

---

### Post by Mateo on 2008-02-01
> **reassuringlyoffensive said:**
> You should be using VLC to play DVD's as it plays them well. It also fully supports menus.
 
Check out part 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) as it helps you make VLC default for DVD's and shows you how to enable encrypted DVD playback. It's worth a look.
 
Nathan

> **Mateo said:**
> *note: please do not recommend alternative players.*

Not looking for general DVD play, looking for specifically mplayer DVD play.  I probably should have put that in the title.

---

### Post by Mateo on 2008-02-01
> **rvm4000 said:**
> Maybe the first title in the DVD is not the movie.

Try with 
**mplayer dvd://2** 
**mplayer dvd://3**
...

By the way, I read in you first post that you tried **mplayer /dev/scd0**. I think this is not right. Try with
**mplayer -dvd-device /dev/scd0 dvd://**

that actually makes a huge difference.  in fact, it seems to work.

Ok, for the final phase of this mission.... how do I get mplayer to recognize the command "mplayer dvd://"  as meaning "mplayer -dvd-device /dev/scd0 dvd://"?

---

### Post by ubuntu-freak on 2008-02-02
I love MPlayer but it's possibly the worst program to play DVD's with. I don't understand why you're determined to use it.
 
Good luck though.
 
Nathan

---

### Post by rvm4000 on 2008-02-02
> **Mateo said:**
> Ok, for the final phase of this mission.... how do I get mplayer to recognize the command "mplayer dvd://"  as meaning "mplayer -dvd-device /dev/scd0 dvd://"?

I think you can add a line like
```
dvd-device=/dev/scd0
``` 
to your ~/ .mplayer/config

---

### Post by mc4man on 2008-02-02
If you have 2 dvd devices and 1 isn't asscoiated with /dvd then use
```
mplayer -dvd-device /dev/scd0 dvd://1
```
where 1 is the # of the track (title) you want to play and scdx is the device (ie. either 0 or1)

---

### Post by Mateo on 2008-02-02
> **rvm4000 said:**
> I think you can add a line like
```
dvd-device=/dev/scd0
``` 
to your ~/ .mplayer/config

works!!  any way to make this system-wide?  if i put that into /etc/mplayer/mplayer.conf, would that do the trick?

---

### Post by rvm4000 on 2008-02-02
Yes I think so.

From the [mplayer manpage](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html):

> 
You can put all of the options in configuration files which will be read every time MPlayer/MEncoder is run. The system-wide configuration file &#8217;mplayer.conf&#8217; is in your configuration directory (e.g. /etc/ mplayer or /usr/local/etc/mplayer), the user specific one is &#8217;~/ .mplayer/config&#8217;.


---

### Post by Mateo on 2008-02-03
great!  thread solved!

---

### Post by starwars on 2008-02-03
With all codecs installed, I tried this and it worked with my gutsy,
"$sudo totem /media/dvdrom"
Although totem player posted some plug-in error,  it played vt_s perfectly!
If you tried it already, sorry I`m just a newbee!

---

### Post by rich_phoenix on 2008-02-04
My system doesn't have a scd0. I did a 'cat /var/log/messages | grep DVD' to find this:

Feb  4 13:53:31 ubuntu kernel: [   21.850346] hda: SONY DVD RW DRU-710A, ATAPI CD/DVD-ROM drive
Feb  4 13:53:31 ubuntu kernel: [   22.534590] hda: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)

so, I thought I would tweak your command:

mplayer -dvd-device /dev/hda0 dvd://1

MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 79, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
Couldn't open DVD device: /dev/hda0
No stream found to handle url dvd://1

Exiting... (End of file)

ok, how about: 

 mplayer -dvd-device /dev/hda dvd://1

MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 79, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 17 titles on this DVD.
There are 51 chapters in this DVD title.
There are 3 angles in this DVD title.
libdvdread: Invalid IFO for title 6 (VTS_06_0.IFO).
libdvdread: Invalid IFO for title 6 (VTS_06_0.BUP).
Cannot open the IFO file for DVD title 6.
No stream found to handle url dvd://1

well, that was closer to what was needed...

---

