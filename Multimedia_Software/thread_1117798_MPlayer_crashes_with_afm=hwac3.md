---
title: "MPlayer crashes with afm=hwac3"
date: 2009-04-06
forum: Multimedia Software
---

### Post by MacMiskenn on 2009-04-06
Hello!
My server's hardware died last month, so I decided to build a new, with Media-PC capabilities. So here's the thing, I've bought CoreAVC and now I want to be able to play h.264 content on it, with sound output through s/pdif to my amp, with MPlayer. - This is with Ubuntu 8.04.

I followed this guide to the letter: [http://ubuntuforums.org/showthread.php?t=1034075](http://ubuntuforums.org/showthread.php?t=1034075) and sure CoreAVC works wonderfully, however AC3/DTS output through s/pdif does not.

When I start MPlayer through the terminal this is the output:
```
mark@Adrian:~$ mplayer /home/mark/Skrivebord/random.mkv
MPlayer SVN-rUNKNOWN-4.2.4 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing /home/mark/Skrivebord/random.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x536  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.0
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Dshowserver Connected to host
VDec: vo config request - 1280 x 536 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.39:1 - prescaling to correct movie aspect.
VO: [xv] 1280x536 => 1280x536 Planar YV12 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/)
==========================================================================
==========================================================================
Trying to force audio codec driver family hwac3...
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 640000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
[AO OSS] Can't set audio device /dev/dsp to ac3 output, trying s16le...
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
[format] Sample format big-endian AC3 not yet supported 
[libaf] Reinitialization did not work, audio filter 'format' returned error code -2
Couldn't find matching filter/ao format!
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

```

This is the content of my ~/.mplayer/config:
```

# Write your default config options here!
vc=coreserve,
afm=hwac3

```

I unmuted iec958 in alsamixer, if I remove the afm=hwac3 part from the config sound will work but only 2ch PCM, and I really want to enjoy my movies in surround.

Also if I remove the ~/.mplayer/config entirely, and start through the terminal with: $ mplayer ~/Skrivebord/random.mkv -afm hwac3 -ac coreserve

I will get picture but no sound at all, this is the output:

```
mplayer /home/mark/Skrivebord/random.mkv -afm hwac3 -ac coreserve
MPlayer SVN-rUNKNOWN-4.2.4 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing /home/mark/Skrivebord/random.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x536  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.0
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Dshowserver Connected to host
VDec: vo config request - 1280 x 536 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.39:1 - prescaling to correct movie aspect.
VO: [xv] 1280x536 => 1280x536 Planar YV12 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/)
==========================================================================
==========================================================================
Forced audio codec: coreserve
Cannot find codec for audio format 0x2000.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
pts value < previous ??% ??,?% 0 0                                              
************/  0 15%  2%  0.0% 0 0                                              
in-frames: 73 out-frames: 64
************
Destroying filter
Exiting... (Quit)

```




The specs of the system I'm running this on is: 
Motherboard/CPU: D945GCLF2/Intel Atom 330 1.6ghz
Integrated sound: ALC662
Integrated graphics(vga): Intel GMA 950
RAM: Kingston 2gb

As a side-note: If I install MPlayer through Synaptic, without CoreAVC, the sound outputs in AC3/DTS through s/pdif to my amp, without any hiccups, except that I can't play h.264 content anywhere near smoothly enough to be watchable. I've also tried both Mythbuntu and Ubuntu, and they give the same result.

Any help would be appreciated.
/Mark

---

### Post by robertrej on 2009-05-21
I started having the same problem last month just out of the blue!
I encode my own ac3 5.1 and they sound great but this no longer works, playing them that is.I can encode ac3 stereo ok but prefer
5.1 . Is this a bug ?if so i have found very little help solving
it, I am open to any suggestions . Every problem I have had with
UBUNTU has been solved and hope this forum can aid with this one
as well.

                                  thanks
                                  Bob

---

