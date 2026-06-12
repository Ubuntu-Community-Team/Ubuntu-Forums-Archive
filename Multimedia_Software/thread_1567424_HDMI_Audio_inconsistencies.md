---
title: "HDMI Audio inconsistencies"
date: 2010-09-03
forum: Multimedia Software
---

### Post by richlowe101 on 2010-09-03
Hi all, 

Have setup HDMI audio quite happily using ALSA in stereo, however I recently upgraded to surround (4.0) and cannot get consistent results with digital out.

```
$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

$aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

```

with an asoundrc file set up as follows:
```

$cat .asoundrc
pcm.!default {
	type hw
	card 0
	device 3
}

```

so if I play surround files through aplay as follows:

```
aplay Norranda.wav
```

it lights up the correct digital light on my amp and I get correct passthrough. However, using mplayer with:
```
mplayer -ao alsa:device=hdmi Norrlanda.wav
```
only gives me stereo, as expected as there is no codec specified.
Adding "-ac hwdts" crashes mplayer, adding "-ac hwac3" results in no playback.
VLC tries to play it but fails to even output sound at all.

I'm stumped by all this, but it seems to me as if I have it configured correctly as aplay can manage it, I just fail to see what option I'm missing with mplayer.

For completeness, here is the output from mplayer when it crashes with the -ac hwdts option set:
```

$mplayer -ao alsa:device=hdmi -ac hwdts -v Norrlanda.wav 

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 5
CPU: AMD Athlon(tm) II X2 245 Processor (Family: 16, Model: 6, Stepping: 2)
extended cpuid-level: 27
extended cache-info: 67141952
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/pegasus/.mplayer/codecs.conf'
Reading /home/pegasus/.mplayer/codecs.conf: Can't open '/home/pegasus/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-ao' 'alsa:device=hdmi' '-ac' 'hwdts' '-v' 'Norrlanda.wav'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/pegasus/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/pegasus/.mplayer/input.conf'
Can't open input config file /home/pegasus/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not open config files /home/pegasus/.lircrc and /etc/lirc//lirc/lircrc
mplayer: No such file or directory
Failed to read LIRC config file ~/.lircrc.
get_path('Norrlanda.wav.conf') -> '/home/pegasus/.mplayer/Norrlanda.wav.conf'

Playing Norrlanda.wav.
get_path('sub/') -> '/home/pegasus/.mplayer/sub/'
[file] File size is 46747692 bytes
STREAM: [file] Norrlanda.wav
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: WAV format
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename Norrlanda.wav ext: .wav
Trying demuxer 17 based on filename extension
==> Found audio stream: 0
======= WAVE Format =======
Format Tag: 1 (0x1)
Channels: 2
Samplerate: 44100
avg byte/sec: 176400
Block align: 4
bits/sample: 16
cbSize: 0
==========================================================================
[demux_audio] DTS audio in wav, 14 bit, LE
demux_audio: audio data 0x2C - 0x2C9502C  
Audio only file format detected.
==========================================================================
Forced audio codec: hwdts
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
dec_audio: Allocating 8192 bytes for input buffer.
dec_audio: Allocating 16384 + 65536 = 81920 bytes for output buffer.
No accelerated IMDCT transform found
hwac3: switched to DTS, 1411200 bps, 44100 Hz
AUDIO: 44100 Hz, 2 ch, ac3, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [hwdts] afm: hwac3 (DTS through S/PDIF)
==========================================================================
Building audio filter chain for 44100Hz/2ch/ac3 -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/ac3
[dummy] Was reinitialized: 44100Hz/2ch/ac3
Trying preferred audio driver 'alsa', options 'device=hdmi'
alsa-init: requested format: 44100 Hz, 2 channels, 100
alsa-init: using ALSA 1.0.22
alsa-spdif-init: playing AC3, 2 channels
alsa-init: using device hdmi
alsa-init: pcm opened in blocking mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa-init: got period size 1024
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 44100Hz/2ch/ac3 -> 48000Hz/2ch/ac3...
[dummy] Was reinitialized: 44100Hz/2ch/ac3
[libaf] Adding filter lavcresample 
[libaf] Adding filter format 
[format] Sample format big-endian AC3 not yet supported 
Couldn't find matching filter/ao format!
Video: no video
Freeing 0 unused video chunks.
Starting playback...


MPlayer interrupted by signal 11 in module: decode_audio
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]


```

Appears to me like mplayer is trying to decode the audio even though it is flagged as passthrough. Any help on this would be hugely appreciated.

---

