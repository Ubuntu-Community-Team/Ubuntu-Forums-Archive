---
title: "[SOLVED] Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)"
date: 2008-10-04
forum: Multimedia Software
---

### Post by known on 2008-10-04
Someone please help me in fixing the sound problem in my Ubuntu Hardy laptop.

**laptop:~/Desktop$ lspci -v**
[COLOR=Blue]00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
        Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device 0401
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at d400 [size=256]
        Memory at dfff0000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

[/COLOR] **laptop:~/Desktop$ alsamixer**
[COLOR=Blue]alsamixer: function snd_ctl_open failed for default: No such file or directory
[/COLOR]
[B]laptop:~/Desktop$ mplayer Talking_budda.3gp
[/B][COLOR=Blue]MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Mobile Intel(R) Celeron(TM) CPU         1333MHz (Family: 6, Model: 11, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Talking budda.3gp.
Cache fill:  1.02% (85292 bytes)
ISO: File Type Major Brand: 3GPP Profile 5
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
MOV: unknown sound atom version (145742000); may not work!
VIDEO:  [s263]  128x96  24bpp  5.319 fps    0.0 kbps ( 0.0 kbyte/s)
dvdsublang...talking budda en
dvdsublang...talking budda en
xscreensaver_disable: xscreensaver wid=8388609.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh263] vfm: ffmpeg (FFmpeg H.263+ decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 128.0 kbit/100.00% (ratio: 16000->16000)
Selected audio codec: [ffamrnb] afm: ffmpeg (AMR Narrowband)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 128 x 96 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 128x96 => 128x96 Planar YV12
V:   8.7  62/ 62  1%  0%  0.0% 0 0 0%

Exiting... (End of file)

[COLOR=DarkSlateGray]**laptop:~/Desktop$ aplay**[/COLOR]
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such file or directory

[/COLOR]

---

### Post by known on 2008-10-06
[SIZE=2]I solved this issue by doing

$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
[SIZE=2]$ sudo apt-get install linux-sound-base alsa-base alsa-utils[/SIZE]
[/SIZE]

---

### Post by JC Cheloven on 2008-10-06
> **known said:**
> [SIZE=2]I solved this issue by doing

$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
[SIZE=2]$ sudo apt-get install linux-sound-base alsa-base alsa-utils[/SIZE]
[/SIZE]

Thank you to take the time to write this potentially useful info. I had [bad experiences]("http://ubuntuforums.org/showthread.php?t=912483") with SiS, myself. Could you please mark your thread as solved? (in the "thread tools" link). Many people search among "solved" threads... 

Thanks.

---

### Post by Mrangel on 2009-03-26
> **JC Cheloven said:**
> Thank you to take the time to write this potentially useful info. I had [bad experiences]("http://ubuntuforums.org/showthread.php?t=912483") with SiS, myself. Could you please mark your thread as solved? (in the "thread tools" link). Many people search among "solved" threads... 

Thanks.

ok how do i get Ubuntu gutsy to pick up sis sound card in desktop?:confused:

---

### Post by Mrangel on 2009-03-26
> **Mrangel said:**
> ok how do i get Ubuntu gutsy to pick up sis sound card in desktop?:confused: I do not want to go back to windows xp yuck.

---

### Post by jperelli on 2009-09-12
great! it worked for me, thanks!! :D

---

