---
title: "Tearing with 1080i"
date: 2010-07-02
forum: Mythbuntu
---

### Post by barrylumpkin on 2010-07-02
I'm very new to Ubuntu, Linux and MythTV.

I'm viewing and recording using MythTV with some success. Great picture! There seems to be be one hurdle left... I get lots of tearing during movement. For example, last night "The Office" was full of camera panning. It was almost unwatchable... lot's of flickering, tearing, straight verticals lines curving when panning, etc.  :-?

What do I need to do to fix this problem? Wrong settings? Processor too slow?

Using the latest version of MythTV.

ALiveNF7G-HDready with Integrated NVIDIA® GeForce7 Series (NV44) DX9.0 VGA, Pixel Shader 3.0, Max. shared memory 256MB
NVidia server reports: Geforece 7050 PV/nFORCEa (GPU 0) 512mb
Video Driver - Proprietary (version current) [Recommended]
NVidia driver 195.36.24  vbios 05.67.32.10.17
I tried an older driver. No difference.

AMD Athlon 64 x2 Dual Core Processor 4000+ 64 bit 2.1
2GB Ram
FusionHDTV7 Tuner (The problem got worse when I switched from HDHomeRun. I needed a tuner that could handle muti-path better.)
Extra Audio Buffering: Checked

PLAYBACK PROFILES...
High Quality
if REZ >= 1920 1080 -> ffmpeg & vdpau  1
if REZ < 1920 1080 -> ffmpeg & vdpau  2
I tried NVIDA VDPAU Acceleration but I only get a black screen.
I also tried a variety of interlaces and rendering. Mostly the computer couldn't keep up.

Using Toshiba 34" CRT via DVI.

Wouldn't it be great if all I have to do is click in one place.  ;)

---

### Post by ian dobson on 2010-07-02
Hi,

I don't think NVIDIA® GeForce7 Series support vdpau so your system is using software decoding. Maybe try cpu-- or cpu-.

The best would be to buy a cheap NVidia card, anything after a 9300gt should be enough.

Regards
Ian Dobson

---

### Post by barrylumpkin on 2010-07-02
Thanks, Ian.

---

