---
title: "VLC = sound ok, mplayer = no sound"
date: 2010-03-26
forum: Multimedia Software
---

### Post by Lockheed on 2010-03-26
Sometimes, there I get an avi file (namely, every Mythbusters since months) that plays with no sound on smplayer. The very same file plays just dine in VLC. 

Why is it so and how to mend it?

---

### Post by andrew.46 on 2010-03-26
Hi Lockheed,

> **Lockheed said:**
> Sometimes, there I get an avi file (namely, every Mythbusters since months) that plays with no sound on smplayer. The very same file plays just fine in VLC. 

Sounds a little odd. Could you have a look at the codec details as reported by vlc, thse can be seen from Tools --> Codec Information and post here? Also could you attempt to play the same file with MPlayer from the commandline in the following fashion:

```
mplayer -v **[COLOR="Red"]my_problem_file[/COLOR]**
```

where of course *my_problem_file* needs to be replaced with the real name of your file.

All the best,

Andrew

---

### Post by Lockheed on 2010-03-26
In doing so, I discovered something really weird. Mplayer plays the file with sound, but it is only in smplayer that there is no sound...

---

### Post by andrew.46 on 2010-03-26
Hi Lockheed,

> **Lockheed said:**
> In doing so, I discovered something really weird. Mplayer plays the file with sound, but it is only in smplayer that there is no sound...

and the vital clue should be found in the commandline output of MPlayer :).

Andrew

---

### Post by Lockheed on 2010-03-27
Right, right.
```
mplayer -v Mythbusters.S08E01.HDTV.XviD-aAF.avi 
MPlayer SVN-r29501-4.3.3 (C) 2000-2009 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-60 (Family: 15, Model: 104, Stepping: 2)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowExt SSE SSE2 CMOV
get_path('codecs.conf') -> '/home/juha/.mplayer/codecs.conf'
Reading /home/juha/.mplayer/codecs.conf: Can't open '/home/juha/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --confdir=/etc/mplayer
CommandLine: '-v' 'Mythbusters.S08E01.HDTV.XviD-aAF.avi'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/juha/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/juha/.mplayer/input.conf'
Can't open input config file /home/juha/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
get_path('Mythbusters.S08E01.HDTV.XviD-aAF.avi.conf') -> '/home/juha/.mplayer/Mythbusters.S08E01.HDTV.XviD-aAF.avi.conf'

Playing Mythbusters.S08E01.HDTV.XviD-aAF.avi.
get_path('sub/') -> '/home/juha/.mplayer/sub/'
[file] File size is 367493120 bytes
STREAM: [file] Mythbusters.S08E01.HDTV.XviD-aAF.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: AVI format
AVI file format detected.
list_end=0x2292
======= AVI Header =======
us/frame: 33367  (fps=29.970)
max bytes/sec: 0
padding: 0
MainAVIHeader.dwFlags: (272) HAS_INDEX IS_INTERLEAVED
frames  total: 77660   initial: 0
streams: 2
Suggested BufferSize: 0
Size:  624 x 352
==========================
list_end=0x10F4
==> Found video stream: 0
[aviheader] Video stream found, -vid 0
====== STREAM Header =====
Type: vids   FCC: xvid (64697678)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 30000/1001 = 29.970
Start: 0   Len: 77660
Suggested BufferSize: 56333
Quality 10000
Sample size: 0
==========================
Found 'bih', 40 bytes of 40
======= VIDEO Format ======
  biSize 40
  biWidth 624
  biHeight 352
  biPlanes 1
  biBitCount 12
  biCompression 1145656920='XVID'
  biSizeImage 1317888
===========================
Regenerating keyframe table for MPEG-4 video.
list_end=0x2186
==> Found audio stream: 1
[aviheader] Audio stream found, -aid 1
====== STREAM Header =====
Type: auds   FCC:  (0)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 1
Rate: 48000/1152 = 41.667
Start: 0   Len: 107970
Suggested BufferSize: 768
Quality -1
Sample size: 0
==========================
Found 'wf', 30 bytes of 18
======= WAVE Format =======
Format Tag: 85 (0x55)
Channels: 2
Samplerate: 48000
avg byte/sec: 14691
Block align: 1152
bits/sample: 0
cbSize: 12
mp3.wID=1
mp3.fdwFlags=0x2
mp3.nBlockSize=352
mp3.nFramesPerBlock=1
mp3.nCodecDelay=0
==========================================================================
list_end=0x2292
AVI: dmlh found (size=248) (total_frames=77660)
list_end=0x22B6
hdr=Software  size=15
Software  : Nandub v1.0rc2
list_end=0x15BA2D64
Found movie at 0x280C - 0x15BA2D64
Reading INDEX block, 185630 chunks for 77660 frames (fpos=364522860).
AVI index offset: 0x2808 (movi=0x280C idx0=0x4 idx1=0x18C)
Auto-selected AVI audio ID = 1
Auto-selected AVI video ID = 0
AVI: Searching for audio stream (id:1)
AVI video size=324900916 (77660) audio size=38069280 (107970)
VIDEO:  [XVID]  624x352  12bpp  29.970 fps  1003.1 kbps (122.4 kbyte/s)
Auto-selected AVI audio ID = 1
[V] filefmt:3  fourcc:0x44495658  size:624x352  fps:29.970  ftime:=0.0334
Clip info:
 Software: Nandub v1.0rc2
get_path('sub/') -> '/home/juha/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x800 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[VO_XV] Using Xv Adapter #0 (NV17 Video Texture)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2046x2046
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
dec_audio: Allocating 4096 bytes for input buffer.
dec_audio: Allocating 9216 + 65536 = 74752 bytes for output buffer.
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Trying preferred audio driver 'oss', options '[none]'
ao2: 48000 Hz  2 chans  s16le
audio_setup: using '/dev/dsp' dsp device
audio_setup: using 'hw:0' mixer device
audio_setup: using 'pcm' mixer device
audio_setup: sample format: s16le (requested: s16le)
audio_setup: using 2 channels (requested: 2)
audio_setup: using 48000 Hz samplerate (requested: 48000)
audio_setup: frags:  32/32  (2048 bytes/frag)  free:  65536
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: OSS/ioctl audio output
AO: Author: A'rpi
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
XXX initial  v_pts=0.000  a_pos=6864 (0.467) 
Increasing filtered audio buffer size from 0 to 65536
[mpeg4 @ 0xd90a80]Invalid and inefficient vfw-avi packed B frames detected
[ffmpeg] aspect_ratio: 1.772727
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO Config (624x352->624x352,flags=0,'MPlayer',0x32315659)
VO: [xv] 624x352 => 624x352 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 355 for hw scaling
*** [vo] Allocating (slices) mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
*** [vo] Allocating (slices) mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
Unicode font: 5009 glyphs.
Unicode font: 5009 glyphs.
*** [vo] Allocating (slices) mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
A:   0.0 V:   0.1 A-V: -0.113 ct: -0.008   5/  5 ??% ??% ??,?% 0 0 
A:   0.0 V:   0.1 A-V: -0.113 ct: -0.008   5/  5 ??% ??% ??,?% 0 0 

MPlayer interrupted by signal 2 in module: sleep_timer
Uninit audio filters...-0.113 ct: -0.008   5/  5 ??% ??% ??,?% 0 0 
[libaf] Removing filter dummy 
Uninit audio: libmad
Uninit video: ffmpeg
Successfully enabled DPMS
vo: uninit ...

Exiting... (Quit)
```

---

### Post by andrew.46 on 2010-03-27
Hi Lockheed,

Just from curiosity did you compile this copy of MPlayer? If no sound with this file under SMPlayer have a look at the 'audio out' in:

Options --> Preferences --> General --> Audio --> Output Driver

and select oss. This might be enough to get the sound going for SMPlayer...

All the best,

Andrew

---

### Post by Lockheed on 2010-03-27
It is already OSS. Otherwise, I would not have sound in other movies.

Yes, I compiled this mplayer myself.

---

### Post by andrew.46 on 2010-03-27
Hi Lockheed,

> **Lockheed said:**
> It is already OSS. Otherwise, I would not have sound in other movies.

In that case what do the SMPlayer logs show when the sound fails?

> Yes, I compiled this mplayer myself.

This is quite an old svn version, current is:

```

andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r30960-4.3.3 (C) 2000-2010 MPlayer Team

```

Would you consider compiling again, perhaps against a fuller set of dependencies? I believe there is a guide for this on these forums...

All the best,

Andrew

---

### Post by Lockheed on 2010-03-27
> **andrew.46 said:**
> Hi Lockheed,



In that case what do the SMPlayer logs show when the sound fails?
Nothing. The movie plays perfectly fine, except with no sound and in Audio properties the codec and other values are 0.


> **andrew.46 said:**
> This is quite an old svn version, current is:

```

andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r30960-4.3.3 (C) 2000-2010 MPlayer Team

```

Would you consider compiling again, perhaps against a fuller set of dependencies? I believe there is a guide for this on these forums...
Hmm, I was already following a guide here that explained how to get mplayer+smplayer. Can I just compile mplayer without removing the old version? Will smplayer still work regardless of changes to mplayer?

---

### Post by andrew.46 on 2010-03-27
Hi Lockheed,

> **Lockheed said:**
> Hmm, I was already following a guide here that explained how to get mplayer+smplayer. Can I just compile mplayer without removing the old version? Will smplayer still work regardless of changes to mplayer?

Depends which guide you are using :). Can you give a link, it may be one that I have written...

Andrew

---

### Post by rvm4000 on 2010-03-27
> **Lockheed said:**
> Nothing. The movie plays perfectly fine, except with no sound and in Audio properties the codec and other values are 0.

Take a look at the mplayer log (options -> view logs).

---

### Post by Lockheed on 2010-03-27
> **andrew.46 said:**
> Hi Lockheed,



Depends which guide you are using :). Can you give a link, it may be one that I have written...

Andrew

I think it was yours. I remember your avatar.
Great stuff. Until i followed it, my video playback was far inferior to Windows.

---

### Post by andrew.46 on 2010-03-27
Hi Lockheed,

> **Lockheed said:**
> I think it was yours. I remember your avatar.
Great stuff. Until i followed it, my video playback was far inferior to Windows.

Those guides can be easily update by running *svn up* from the source code and then recompiling. The checkinstall syntax ensures that the new version will update the old. This may not solve your current problem though, this is just an after-thought... It would be interesting to see the MPlayer logs as rvm has suggested.

Andrew

---

### Post by Lockheed on 2010-03-27
> **andrew.46 said:**
> It would be interesting to see the MPlayer logs as rvm has suggested.
Don't you mean SMplayer logs?

---

### Post by andrew.46 on 2010-03-27
Hi Lockheed,

> **Lockheed said:**
> Don't you mean SMplayer logs?

Perhaps we should both watch:

Who's on first?
[http://www.youtube.com/watch?v=sShMA85pv8M](http://www.youtube.com/watch?v=sShMA85pv8M)

just to make it all clearer :). I suspect rvm means the logs of MPlayer available from within SMPlayer, accessed either from the menu or by pressing Ctrl+M during or after playback...

All the best,

Andrew

---

### Post by Lockheed on 2010-03-27
```
mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv -ao oss -zoom -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 98566158 -monitorpixelaspect 1 -noass -subfont-autoscale 1 -subfont-text-scale 5 -subcp CP1250 -vid 0 -aid 0 -subpos 100 -volume 100 -cache 2000 -osdlevel 1 -nocorrect-pts -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 310 af=volume=10:0 /media/d/#Downloaded/Mythbusters.S08E01.HDTV.XviD-aAF.avi

MPlayer SVN-r29501-4.3.3 (C) 2000-2009 MPlayer Team
Terminal type `unknown' is not defined.

Playing af=volume=10:0.
File not found: 'af=volume=10:0'
Failed to open af=volume=10:0.


Playing /media/d/#Downloaded/Mythbusters.S08E01.HDTV.XviD-aAF.avi.

Cache fill:  0.00% (0 bytes)   
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
AVI: invalid audio stream ID: 0 - ignoring (nosound)
VIDEO:  [XVID]  624x352  12bpp  29.970 fps  1003.1 kbps (122.4 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=Nandub v1.0rc2
ID_CLIP_INFO_N=1
ID_FILENAME=/media/d/#Downloaded/Mythbusters.S08E01.HDTV.XviD-aAF.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=1003064
ID_VIDEO_WIDTH=624
ID_VIDEO_HEIGHT=352
ID_VIDEO_FPS=29.970
ID_VIDEO_ASPECT=0.0000
ID_LENGTH=2591.26
ID_SEEKABLE=1
ID_CHAPTERS=0
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
Audio: no sound
Starting playback...
[mpeg4 @ 0xd90a80]Invalid and inefficient vfw-avi packed B frames detected
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7727
[swscaler @ 0xe42a40]No accelerated colorspace conversion found.
[swscaler @ 0xe42a40]using unscaled yuv420p -> rgb24 special converter
VO: [xv] 624x352 => 624x352 Planar YV12  [zoom]
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
Invalid command for bound key m : invalid_command             

```

---

### Post by andrew.46 on 2010-03-27
Hi Lockheed,

And there it is:
```

ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
AVI: invalid audio stream ID: 0 - ignoring (nosound)
```

and this plays perfectly, with sound, from the MPlayer commandline?

Andrew

---

### Post by mc4man on 2010-03-27
Just out of curiosity, it shows in the mplayer log - command,  -aid 0, don't ever remember seeing that in an .avi here, it's always 1
(in the .avi and in smplayer's command to mplayer

---

### Post by Lockheed on 2010-03-28
> **andrew.46 said:**
> and this plays perfectly, with sound, from the MPlayer commandline?

That is correct. In VLC as well.


**mc4man**
Is it a question?

---

### Post by rvm4000 on 2010-03-28
I found two problems:

> **Lockheed said:**
> ```
mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv -ao oss -zoom -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 98566158 -monitorpixelaspect 1 -noass -subfont-autoscale 1 -subfont-text-scale 5 -subcp CP1250 -vid 0 -aid 0 -subpos 100 -volume 100 -cache 2000 -osdlevel 1 -nocorrect-pts -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 310 af=volume=10:0 /media/d/#Downloaded/Mythbusters.S08E01.HDTV.XviD-aAF.avi

MPlayer SVN-r29501-4.3.3 (C) 2000-2009 MPlayer Team
Terminal type `unknown' is not defined.

Playing af=volume=10:0.
File not found: 'af=volume=10:0'
Failed to open af=volume=10:0.

```

This is the first problem. I guess you're passing "af=volume=10:0" in preferences -> advanced, but you're doing wrong. I suggest to remove that option.

> **Lockheed said:**
> [code]
Playing /media/d/#Downloaded/Mythbusters.S08E01.HDTV.XviD-aAF.avi.

Cache fill:  0.00% (0 bytes)   
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
AVI: invalid audio stream ID: 0 - ignoring (nosound)


The 2nd problem is here. smplayer tries to use stream #0 for audio, but the available one is #1.

Go to preferences -> general and uncheck the option "Remember settings for all files", this way smplayer should forget the info about audio tracks. Try to play the file again.

---

### Post by Lockheed on 2010-03-28
> **rvm4000 said:**
> Go to preferences -> general and uncheck the option "Remember settings for all files", this way smplayer should forget the info about audio tracks. Try to play the file again.
Bullseye!

---

