---
title: "Problem with MPlayer after configuring CoreAVC"
date: 2009-02-07
forum: Multimedia Software
---

### Post by Rawgers on 2009-02-07
Hello
The thing is, when I use the Mplayer, the CoreAVC codec seems to work but the audio is not working. And if I try to play a video with SMPlayer, the video codec does not work but sound does. Iunno what is causing this but this did not occur before I installed CoreAVC for MPlayer.
I used this [http://ubuntuforums.org/showthread.php?t=1034075]("http://ubuntuforums.org/showthread.php?t=1034075") .

Thanks for any help

---

### Post by mc4man on 2009-02-07
You may get some useful info by running mplayer from the command line and with smplayer use Ctrl+m and Ctrl+s for mplayer and smplayer logs while trying your video.

Did you build mplayer or are you trying using a smplayer package?

---

### Post by Rawgers on 2009-02-08
I installed MPlayer myself (w/ make / make install)

When I play the file on MPlayer, the terminal shows this

```
Playing "..."
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "...", -vid 0
[mkv] Track ID 2: audio (A_AAC) "AAC 2.0", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "***", -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  848x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[***] auto-open
[***] Init
[***] Updating font cache.
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
len: 992
ProductVersion: 1.8.5
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
VDec: vo config request - 848 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 848x480 => 848x480 Planar YV12 
Dshowserver Connected to host
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/)
==========================================================================
==========================================================================
Trying to force audio codec driver family faad...
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
pts value < previousV: -0.029 ct: -0.009   0/  0 ??% ??% ??,?% 0 0              
[Mixer] No hardware mixing, inserting volume filter.  5%  1.0% 2 0              
A:  12.1 V:  12.1 A-V:  0.000 ct: -0.011   0/  0  7%  6%  1.1% 2 0              
  =====  PAUSE  =====

```

and the SMplayer log
```
D_FILENAME=...
ID_DEMUXER=mkv
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=848
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=29.970
ID_VIDEO_ASPECT=1.7667
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_LENGTH=1420.05
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[***] auto-open
Opening video filter: [screenshot]
[***] Init
[***] Updating font cache.
==========================================================================
Forced video codec: coreserve
Cannot find codec matching selected -vo and video format 0x31637661.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=faad
Video: no video
Starting playback...
[AO_ALSA] Unable to find simple control 'PCM',0.
[Mixer] No hardware mixing, inserting volume filter.
[AO_ALSA] Unable to find simple control 'PCM',0.
[A
[KSubtitles: (0) eng
[A
[KVolume: 40 %
[A
[K
[A
[K  =====  PAUSE  =====
ID_PAUSED
```

---

### Post by mc4man on 2009-02-08
I've never used coreavc or played back this or similar formats but there are many people here that do, I wouldn't doubt you'll get a solution.

I'd probably try mplayer from the command line and add -ao alsa to the command and see what happened.
For smplayer I might try creating a codecs.conf if there isn't one and seeing about making an appropriate entry for format 0x31637661.

Just thoughts, nothing I know specifically

(just curious, was the 2nd log you posted the smplayer log or the mplayer log from smplayer?

---

### Post by Rawgers on 2009-02-08
> **mc4man said:**
> I've never used coreavc or played back this or similar formats but there are many people here that do, I wouldn't doubt you'll get a solution.

I'd probably try mplayer from the command line and add -ao alsa to the command and see what happened.
For smplayer I might try creating a codecs.conf if there isn't one and seeing about making an appropriate entry for format 0x31637661.

Just thoughts, nothing I know specifically

(just curious, was the 2nd log you posted the smplayer log or the mplayer log from smplayer?
Okay, when I play mplayer with alsa, it shows this
```
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
No such audio driver 'alsa'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...

```
When the file opens (using mplayer-gui) an error pops up saying Could not open/initalize audio device > no sound.

And for the SMPlayer, that is the MPlayer log.

If this helps, I'm using Ubuntu 8.10
Edit: I fixed the SMPlayer issue with the format 0x316377661, but now when I try to start a file, an error appears saying this-
```
/usr/bin/mplayer -noquiet -nofs -demuxer rawaudio -vc ffh264 -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo xv -ao alsa -zoom -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 67108876 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/*name*/.config/smplayer/styles.*** -fontconfig -font Purisa -subcp ISO-8859-1 -subpos 100 -cache 2000 -osdlevel 1 -no-correct-pts -vf-add screenshot -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -vc coreserve, (My file)

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option -ao needs a parameter at line 75

```

---

### Post by Rawgers on 2009-02-08
Okay, I got SMPlayer's video to work, but now, similar to the MPlayer issue, sound does not work. This is my log
```
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
No such audio driver 'alsa'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
Initialization is complete
Dshowserver Connected to host
Seek now
```

---

### Post by mc4man on 2009-02-08
It seems positive they both have same error, 

Have you tried going into smplayer and switching the audio output to pulse? 

That's what worked here with smplayer till I removed pulse entirely. (IIRC smplayer installed with a default of 'user defined' alsa (which also worked even though the logs showed some errors

---

### Post by Rawgers on 2009-02-09
Mmm. I put "OSS" audio output for both SMPlayer/MPlayer and it worked =)

But, now I'm wondering if this solution will continue to work? Thanks for all the help.

---

