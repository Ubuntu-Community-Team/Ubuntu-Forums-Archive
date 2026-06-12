---
title: "Sound problems on Mplayer 1.0rc1"
date: 2006-11-08
forum: Multimedia &amp; Video
---

### Post by FuzZy2006 on 2006-11-08
I've just installed mplayer 1.0rc1. I downloaded the last mplayer codecs and copied them to the right place. The pb I encounter is that the sound is bery bad (like the one of an old TV using a stupid antenna). This is the output from the console: 
```
fuzzy@fuzzy-desktop:~$ gmplayer 
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE
/usr/share/fonts/truetype/ttf-ubuntu-title/Ubuntu-Title.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/ttf-ubuntu-title/Ubuntu-Title.ttf

Playing /media/hda6/Lynda.com - Macromedia Dreamweaver 8 Essential Training/CD 1/data/movies/chap03/04_02_file_management.mov.
Quicktime/MOV file format detected.
VIDEO:  [SVQ3]  880x660  32bpp  5.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force video codec driver family qtvideo...
Opening video decoder: [qtvideo] Quicktime Video decoder
QuickTime6.3 DLLs found
QuickTime.qts patched!!! old entry=0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
WARNING! Invalid Ptr handle!

### Searching for QuickTime plugins (*.qtx) at /usr/local/lib/codecs...
### FindNext: AvidQTAVUICodec.qtx
### FindNext: BeHereiVideo.qtx
### FindNext: QuickTimeEssentials.qtx
### FindNext: QuickTimeInternetExtras.qtx
theQuickTimeDispatcher catched -> 0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
 6F 00 00 00 53 56 51 33 00 00 00 00 00 00 00 00
 03 00 00 00 20 49 4D 53 00 00 00 00 00 02 00 00
 70 03 94 02 00 00 48 00 00 00 48 00 00 00 00 00
 01 00 10 53 6F 72 65 6E 73 6F 6E 20 56 69 64 65
 6F 20 33 00 00 00 00 00 00 00 00 00 00 00 00 00
 00 00 20 00 FF FF 00 00 00 15 53 4D 49 20 53 45
 51 48 00 00 00 05 E6 E0 52 99 80 00 00 00 00
=============== ImageDescription at 0x8ba05b0 ==================
idSize=0x6F  fourcc=0x33515653
ver=3 rev=0 vendor=0x534D4920
tempQ=0 spatQ=512  dim: 880 x 660  dpi: 4718592 x 4718592  depth: 32
dataSize=0 frameCount=1 clutID=-1
name='Sorenson Video 3'
00 00 00 15 | 53 4D 49 20 | 53 45 51 48 | 00 00 00 05
=========================================================
VDec: vo config request - 880 x 660 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 1 -> 1

SwScaler: BICUBIC scaler, from yuyv422 to bgr24 using MMX2
SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
SwScaler: using n-tap MMX scaler for vertical scaling (BGR)
SwScaler: using MMX2 YV12->BGR24 Converter
SwScaler: 880x660 -> 880x660
VO: [gl2] 880x660 => 880x660 BGR 24-bit 
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9625, but
this client has the version 1.0-9629.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
[gl2] You have OpenGL >= 1.2 capable drivers, GOOD (16bpp and BGR is ok!)
[gl2] antialiasing off
[gl2] bilinear linear
Selected video codec: [qtsvq3] vfm: qtvideo (Win32/QuickTime SVQ3 decoder)
==========================================================================
==========================================================================
Trying to force audio codec driver family qtaudio...
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 56.0 kbit/3.97% (ratio: 7000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
mpg123: Can't rewind stream by 108 bits!   8/  8 12% 72%  2.1% 2 0              
mpg123: Can't rewind stream by 55 bits!4  13/ 13  9% 58%  2.0% 2 0              
mpg123: Can't rewind stream by 70 bits!6  16/ 16  8% 54%  1.9% 2 0              
mpg123: Can't rewind stream by 17 bits!1  17/ 17  8% 53%  1.9% 2 0              
A:   4.0 V:   4.0 A-V:  0.039 ct:  0.100  21/ 21  7% 51%  1.9% 2 0              
Exiting... (Quit)
fuzzy@fuzzy-desktop:~$ gmplayer 
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE
/usr/share/fonts/truetype/ttf-ubuntu-title/Ubuntu-Title.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/ttf-ubuntu-title/Ubuntu-Title.ttf

Playing /media/hda6/Lynda.com - Macromedia Dreamweaver 8 Essential Training/CD 1/data/movies/chap03/04_01_define_site.mov.
Quicktime/MOV file format detected.
VIDEO:  [SVQ3]  880x660  32bpp  5.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force video codec driver family qtvideo...
Opening video decoder: [qtvideo] Quicktime Video decoder
QuickTime6.3 DLLs found
QuickTime.qts patched!!! old entry=0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
WARNING! Invalid Ptr handle!

### Searching for QuickTime plugins (*.qtx) at /usr/local/lib/codecs...
### FindNext: AvidQTAVUICodec.qtx
### FindNext: BeHereiVideo.qtx
### FindNext: QuickTimeEssentials.qtx
### FindNext: QuickTimeInternetExtras.qtx
theQuickTimeDispatcher catched -> 0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
 6F 00 00 00 53 56 51 33 64 61 36 2F 4C 79 6E 64
 03 00 00 00 20 49 4D 53 00 00 00 00 00 02 00 00
 70 03 94 02 00 00 48 00 00 00 48 00 00 00 00 00
 01 00 10 53 6F 72 65 6E 73 6F 6E 20 56 69 64 65
 6F 20 33 00 00 00 00 00 00 00 00 00 00 00 00 00
 00 00 20 00 FF FF 00 00 00 15 53 4D 49 20 53 45
 51 48 00 00 00 05 E6 E0 52 99 80 00 00 00 00
=============== ImageDescription at 0x8c070e8 ==================
idSize=0x6F  fourcc=0x33515653
ver=3 rev=0 vendor=0x534D4920
tempQ=0 spatQ=512  dim: 880 x 660  dpi: 4718592 x 4718592  depth: 32
dataSize=0 frameCount=1 clutID=-1
name='Sorenson Video 3'
00 00 00 15 | 53 4D 49 20 | 53 45 51 48 | 00 00 00 05
=========================================================
VDec: vo config request - 880 x 660 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 1 -> 1

SwScaler: BICUBIC scaler, from yuyv422 to bgr24 using MMX2
SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
SwScaler: using n-tap MMX scaler for vertical scaling (BGR)
SwScaler: using MMX2 YV12->BGR24 Converter
SwScaler: 880x660 -> 880x660
VO: [gl2] 880x660 => 880x660 BGR 24-bit 
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9625, but
this client has the version 1.0-9629.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
[gl2] You have OpenGL >= 1.2 capable drivers, GOOD (16bpp and BGR is ok!)
[gl2] antialiasing off
[gl2] bilinear linear
Selected video codec: [qtsvq3] vfm: qtvideo (Win32/QuickTime SVQ3 decoder)
==========================================================================
==========================================================================
Trying to force audio codec driver family qtaudio...
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
mpg123: Can't rewind stream by 44 bits!2   5/  5 13% 67% 10.8% 0 0              
mpg123: Can't rewind stream by 68 bits!7  11/ 11  8% 50%  5.8% 0 0              
mpg123: Can't rewind stream by 1 bits!64  13/ 13  7% 49%  5.3% 0 0              
mpg123: Can't rewind stream by 22 bits!9  14/ 14  7% 48%  5.1% 0 0              
mpg123: Can't rewind stream by 86 bits!2  17/ 17  7% 46%  4.6% 0 0              
mpg123: Can't rewind stream by 136 bits!  18/ 18  6% 45%  4.5% 0 0              
mpg123: Can't rewind stream by 170 bits!  19/ 19  6% 46%  4.4% 0 0              
mpg123: Can't rewind stream by 80 bits!
mpg123: Can't rewind stream by 32 bits!9  24/ 24  6% 44%  4.0% 0 0              
mpg123: Can't rewind stream by 41 bits!
mpg123: Can't rewind stream by 100 bits!  25/ 25  6% 44%  4.0% 0 0              
mpg123: Can't rewind stream by 50 bits!3  26/ 26  6% 44%  3.9% 0 0              
mpg123: Can't rewind stream by 127 bits!
mpg123: Can't rewind stream by 160 bits!
mpg123: Can't rewind stream by 71 bits!
mpg123: Can't rewind stream by 44 bits!6  28/ 28  6% 43%  3.9% 0 0              
mpg123: Can't rewind stream by 114 bits!
mpg123: Can't rewind stream by 44 bits!0  31/ 31  5% 43%  3.7% 0 0              
mpg123: Can't rewind stream by 30 bits!4  32/ 32  5% 43%  3.8% 0 0              
mpg123: Can't rewind stream by 29 bits!0  34/ 34  5% 44%  4.0% 0 0              
mpg123: Can't rewind stream by 145 bits!
mpg123: Can't rewind stream by 15 bits!4  35/ 35  5% 44%  3.9% 0 0              
mpg123: Can't rewind stream by 27 bits!9  36/ 36  5% 44%  3.9% 0 0              
mpg123: Can't rewind stream by 3 bits!79  37/ 37  5% 45%  3.8% 0 0              
mpg123: Can't rewind stream by 125 bits!  38/ 38  5% 46%  3.8% 0 0              
mpg123: Can't rewind stream by 131 bits!
mpg123: Can't rewind stream by 121 bits!
mpg123: Can't rewind stream by 58 bits!9  39/ 39  5% 47%  3.8% 0 0              
mpg123: Can't rewind stream by 9 bits!
mpg123: Can't rewind stream by 31 bits!9  40/ 40  5% 48%  3.8% 0 0              
mpg123: Can't rewind stream by 24 bits!9  41/ 41  5% 52%  3.7% 0 0              
mpg123: Can't rewind stream by 39 bits!8  42/ 42  5% 52%  3.8% 1 0              
mpg123: Can't rewind stream by 69 bits!5  43/ 43  5% 52%  3.7% 1 0              
mpg123: Can't rewind stream by 17 bits!7  45/ 45  5% 53%  3.8% 2 0              
mpg123: Can't rewind stream by 5 bits!41  46/ 46  5% 53%  3.8% 3 0              
A:   9.8 V:   9.6 A-V:  0.156 ct:  0.478  49/ 49  5% 54%  3.7% 4 0              
Exiting... (Quit)

```if it can help you.

---

### Post by mikhailo666 on 2006-11-24
I've had the same problem, and to resolve it, tested a multitude of players and read several mailing lists, without finding any hint of what might have been wrong.

Finally, here is what I found out by myself: if your audio/video files have been got from an FTP server, they shall not work if you used the "ASCII mode" when downloading them. Use the "automatic" or "binary" mode instead, and the sun will shine again on your desktop :)

---

### Post by gvoima on 2006-12-24
> **FuzZy2006 said:**
> I've just installed mplayer 1.0rc1. I downloaded the last mplayer codecs and copied them to the right place. The pb I encounter is that the sound is bery bad (like the one of an old TV using a stupid antenna). This is the output from the console: 
```
 .... ... .... 
```
if it can help you.
I have the same problem as you, everything went well and video works, but in some videos/mp3's (or in all of em?) the sound is horrible, scrabblet. Haven't found out yet how to fix it though :P

---

### Post by imon9 on 2007-01-17
i am not 100% positive this can help, but uninstall your mixer software and installing other one might help...in my case, i have a Realtek AC 97 soundcard build-in with my twinhead laptop (nevermind if u never heard of it)....as i was saying, i tried ALSAmixer, xfce-mixer, gnome mixer but all somund bad, but when i changed to QAMix, all went to nice normal sound, go try your luck...

my mic however is currently not functional after changing mixer, so be aware of the possible problem with mic recoding for now..

if this workes,  please post a reply..and if it is not too much of toruble, please private massage me too...

i cant keep track where i answer these treads in the forums, so i can't check back wether it is working, but if this solve the problem, i want to write an article for the rest fo the ubuntu commmunity to know it... (and port it in the forum, in hope it can help others)

---

### Post by imon9 on 2007-01-17
i update ALSA and the mic start working flawlessly. Previously, with other mixer, my mic will be hard over my speaker ALL THE TIME no matter how i set to mute it.

Now, it record my sound, but will not echo it over the speaker which is PERFECT.

so, i think changing Mixer software INDEED wll help to fix those bad quality sound...

For other who it didn;t solve it, try update your ALSA driver to the later ones (ALSA 14 RC2, at this moment) and use ALSA instead of OSS or other mechanism for playback... ESD is old sound driver, so it might be the cause of problem if ur machine use it as default

---

