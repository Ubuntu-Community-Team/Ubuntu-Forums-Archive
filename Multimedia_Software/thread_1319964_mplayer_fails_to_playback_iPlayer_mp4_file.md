---
title: "mplayer fails to playback iPlayer mp4 file"
date: 2009-11-08
forum: Multimedia Software
---

### Post by Jose Catre-Vandis on 2009-11-08
Grabbed a decent version of the first episode of Spooks using get_iplayer, but mplayer fails to play it. VLC plays back fine and Totem too (although with green line at bottom).

Here is the output from mediainfo on the file:
```
General
Complete name                    : Spooks-SE8-E01.mp4
Format                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 352 MiB
Duration                         : 59mn 15s
Overall bit rate                 : 831 Kbps
Encoded date                     : UTC 1970-01-01 00:00:00
Tagged date                      : UTC 1970-01-01 00:00:00
Writing application              : Lavf52.31.0

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 2 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 59mn 15s
Bit rate mode                    : Variable
Bit rate                         : 698 Kbps
Width                            : 640 pixels
Height                           : 360 pixels
Display aspect ratio             : 16:9
Frame rate mode                  : Variable
Frame rate                       : 25.000 fps
Minimum frame rate               : 25.000 fps
Maximum frame rate               : 50.000 fps
Standard                         : PAL
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.121
Stream size                      : 296 MiB (84%)
Encoded date                     : UTC 1970-01-01 00:00:00
Tagged date                      : UTC 1970-01-01 00:00:00

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 59mn 15s
Bit rate mode                    : Variable
Bit rate                         : 125 Kbps
Channel(s)                       : 2 channels
Channel positions                : L R
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 53.2 MiB (15%)
Encoded date                     : UTC 1970-01-01 00:00:00
Tagged date                      : UTC 1970-01-01 00:00:00
```

and here is some mplayer output:
```
jose@xjax:$ mplayer Spooks-SE8-E01.mp4
MPlayer SVN-r29328-4.3.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Spooks-SE8-E01.mp4.

libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [avc1]  640x360  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Opening video filter: [pp=lb/hb/vb/dr]
Opening video filter: [pullup]
Opening video filter: [softskip]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 360 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 640x360 => 640x360 Planar YV12 
A:   0.5 V:   0.0 A-V:  0.529 ct:  0.021   0/  0 ??% ??% ??,?% 50 0 96% 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

pts after filters MISSING.869 ct:  0.021   0/  0 ??% ??% ??,?% 140 0 91% 
pts after filters MISSING.889 ct:  0.022   0/  0 ??% ??% ??,?% 140 0 91% 
pts after filters MISSING.898 ct:  0.022   0/  0 ??% ??% ??,?% 141 0 91% 
pts after filters MISSING.898 ct:  0.022   0/  0 ??% ??% ??,?% 142 0 91% 
pts after filters MISSING.899 ct:  0.021   0/  0 ??% ??% ??,?% 143 0 91% 
pts after filters MISSING.910 ct:  0.021   0/  0 ??% ??% ??,?% 144 0 90% 
pts after filters MISSING.910 ct:  0.021   0/  0 ??% ??% ??,?% 145 0 90% 
pts after filters MISSING.911 ct:  0.021   0/  0 ??% ??% ??,?% 146 0 90% 
pts after filters MISSING.911 ct:  0.021   0/  0 ??% ??% ??,?% 147 0 90% 
pts after filters MISSING.952 ct:  0.021   0/  0 ??% ??% ??,?% 148 0 90% 
pts after filters MISSING.954 ct:  0.021   0/  0 ??% ??% ??,?% 149 0 90% 
pts after filters MISSING.955 ct:  0.021   0/  0 ??% ??% ??,?% 150 0 90% 
pts after filters MISSING.955 ct:  0.021   0/  0 ??% ??% ??,?% 151 0 90% 
pts after filters MISSING.976 ct:  0.021   0/  0 ??% ??% ??,?% 152 0 90% 
pts after filters MISSING.993 ct:  0.021   0/  0 ??% ??% ??,?% 153 0 89% 
pts after filters MISSING.994 ct:  0.021   0/  0 ??% ??% ??,?% 154 0 89% 
pts after filters MISSING.994 ct:  0.021   0/  0 ??% ??% ??,?% 155 0 89% 
pts after filters MISSING.020 ct:  0.021   0/  0 ??% ??% ??,?% 156 0 89% 
pts after filters MISSING.025 ct:  0.021   0/  0 ??% ??% ??,?% 157 0 89% 
pts after filters MISSING.026 ct:  0.021   0/  0 ??% ??% ??,?% 158 0 89% 
pts after filters MISSING.026 ct:  0.021   0/  0 ??% ??% ??,?% 159 0 89% 
pts after filters MISSING.026 ct:  0.021   0/  0 ??% ??% ??,?% 160 0 89% 
pts after filters MISSING.031 ct:  0.021   0/  0 ??% ??% ??,?% 161 0 89% 
pts after filters MISSING.031 ct:  0.021   0/  0 ??% ??% ??,?% 162 0 89% 
pts after filters MISSING.031 ct:  0.021   0/  0 ??% ??% ??,?% 163 0 89% 
pts after filters MISSING.031 ct:  0.021   0/  0 ??% ??% ??,?% 164 0 89% 
pts after filters MISSING.075 ct:  0.021   0/  0 ??% ??% ??,?% 164 0 89% 
pts after filters MISSING.080 ct:  0.021   0/  0 ??% ??% ??,?% 165 0 89% 
pts after filters MISSING.081 ct:  0.021   0/  0 ??% ??% ??,?% 166 0 89% 
pts after filters MISSING.081 ct:  0.021   0/  0 ??% ??% ??,?% 167 0 89% 
pts after filters MISSING.087 ct:  0.021   0/  0 ??% ??% ??,?% 168 0 89% 
pts after filters MISSING.087 ct:  0.021   0/  0 ??% ??% ??,?% 169 0 89% 
pts after filters MISSING.087 ct:  0.021   0/  0 ??% ??% ??,?% 170 0 89% 
pts after filters MISSING.087 ct:  0.021   0/  0 ??% ??% ??,?% 171 0 89% 
pts after filters MISSING.097 ct:  0.021   0/  0 ??% ??% ??,?% 172 0 89% 
pts after filters MISSING.097 ct:  0.021   0/  0 ??% ??% ??,?% 173 0 89% 
pts after filters MISSING.097 ct:  0.021   0/  0 ??% ??% ??,?% 174 0 89% 
pts after filters MISSING.143 ct:  0.021   0/  0 ??% ??% ??,?% 175 0 89% 
pts after filters MISSING.154 ct:  0.021   0/  0 ??% ??% ??,?% 176 0 89% 
pts after filters MISSING.162 ct:  0.021   0/  0 ??% ??% ??,?% 177 0 89% 
pts after filters MISSING.197 ct:  0.021   0/  0 ??% ??% ??,?% 178 0 89% 
pts after filters MISSING.205 ct:  0.021   0/  0 ??% ??% ??,?% 179 0 89% 
pts after filters MISSING.225 ct:  0.021   0/  0 ??% ??% ??,?% 180 0 89% 
pts after filters MISSING.232 ct:  0.021   0/  0 ??% ??% ??,?% 181 0 89% 
pts after filters MISSING.263 ct:  0.021   0/  0 ??% ??% ??,?% 182 0 89% 
pts after filters MISSING.287 ct:  0.021   0/  0 ??% ??% ??,?% 183 0 89% 
pts after filters MISSING.295 ct:  0.021   0/  0 ??% ??% ??,?% 184 0 89% 
pts after filters MISSING.302 ct:  0.021   0/  0 ??% ??% ??,?% 185 0 88% 
pts after filters MISSING.333 ct:  0.021   0/  0 ??% ??% ??,?% 186 0 88% 
pts after filters MISSING.333 ct:  0.021   0/  0 ??% ??% ??,?% 187 0 88% 
pts after filters MISSING.340 ct:  0.021   0/  0 ??% ??% ??,?% 188 0 88% 
pts after filters MISSING.340 ct:  0.021   0/  0 ??% ??% ??,?% 189 0 88% 
pts after filters MISSING.366 ct:  0.021   0/  0 ??% ??% ??,?% 190 0 88% 
pts after filters MISSING.382 ct:  0.021   0/  0 ??% ??% ??,?% 191 0 88% 
pts after filters MISSING.390 ct:  0.021   0/  0 ??% ??% ??,?% 192 0 88% 
pts after filters MISSING.418 ct:  0.021   0/  0 ??% ??% ??,?% 193 0 88% 
pts after filters MISSING.424 ct:  0.021   0/  0 ??% ??% ??,?% 194 0 88% 
pts after filters MISSING.424 ct:  0.021   0/  0 ??% ??% ??,?% 195 0 88% 
pts after filters MISSING.425 ct:  0.021   0/  0 ??% ??% ??,?% 196 0 88% 
pts after filters MISSING.425 ct:  0.021   0/  0 ??% ??% ??,?% 197 0 88% 
pts after filters MISSING.431 ct:  0.021   0/  0 ??% ??% ??,?% 198 0 88% 
pts after filters MISSING.433 ct:  0.021   0/  0 ??% ??% ??,?% 199 0 88% 
pts after filters MISSING.433 ct:  0.021   0/  0 ??% ??% ??,?% 200 0 88% 
pts after filters MISSING.473 ct:  0.021   0/  0 ??% ??% ??,?% 201 0 88% 
pts after filters MISSING.473 ct:  0.021   0/  0 ??% ??% ??,?% 202 0 88% 
pts after filters MISSING.473 ct:  0.021   0/  0 ??% ??% ??,?% 203 0 88% 
pts after filters MISSING.473 ct:  0.021   0/  0 ??% ??% ??,?% 204 0 88% 
pts after filters MISSING.489 ct:  0.021   0/  0 ??% ??% ??,?% 205 0 88% 
pts after filters MISSING.489 ct:  0.021   0/  0 ??% ??% ??,?% 206 0 88% 
pts after filters MISSING.490 ct:  0.021   0/  0 ??% ??% ??,?% 207 0 88% 
pts after filters MISSING.490 ct:  0.021   0/  0 ??% ??% ??,?% 208 0 88% 
pts after filters MISSING.497 ct:  0.021   0/  0 ??% ??% ??,?% 209 0 88% 
pts after filters MISSING.518 ct:  0.021   0/  0 ??% ??% ??,?% 210 0 88% 
pts after filters MISSING.519 ct:  0.021   0/  0 ??% ??% ??,?% 211 0 88% 
pts after filters MISSING.519 ct:  0.021   0/  0 ??% ??% ??,?% 212 0 88% 
pts after filters MISSING.529 ct:  0.021   0/  0 ??% ??% ??,?% 213 0 88% 
pts after filters MISSING.554 ct:  0.021   0/  0 ??% ??% ??,?% 214 0 88% 
pts after filters MISSING.554 ct:  0.021   0/  0 ??% ??% ??,?% 215 0 88% 
pts after filters MISSING.555 ct:  0.021   0/  0 ??% ??% ??,?% 216 0 88% 
pts after filters MISSING.555 ct:  0.021   0/  0 ??% ??% ??,?% 217 0 88% 
pts after filters MISSING.563 ct:  0.021   0/  0 ??% ??% ??,?% 218 0 88% 
pts after filters MISSING.564 ct:  0.021   0/  0 ??% ??% ??,?% 219 0 88% 
pts after filters MISSING.564 ct:  0.021   0/  0 ??% ??% ??,?% 220 0 88% 
pts after filters MISSING.564 ct:  0.021   0/  0 ??% ??% ??,?% 221 0 88% 
pts after filters MISSING.596 ct:  0.021   0/  0 ??% ??% ??,?% 222 0 87% 
pts after filters MISSING.596 ct:  0.021   0/  0 ??% ??% ??,?% 223 0 87% 
pts after filters MISSING.596 ct:  0.021   0/  0 ??% ??% ??,?% 224 0 87% 
pts after filters MISSING.596 ct:  0.021   0/  0 ??% ??% ??,?% 225 0 87% 
pts after filters MISSING.606 ct:  0.021   0/  0 ??% ??% ??,?% 226 0 87% 
pts after filters MISSING.606 ct:  0.021   0/  0 ??% ??% ??,?% 227 0 87% 
pts after filters MISSING.606 ct:  0.021   0/  0 ??% ??% ??,?% 228 0 87% 
pts after filters MISSING.606 ct:  0.021   0/  0 ??% ??% ??,?% 229 0 87% 
pts after filters MISSING.636 ct:  0.021   0/  0 ??% ??% ??,?% 230 0 87% 
pts after filters MISSING.637 ct:  0.021   0/  0 ??% ??% ??,?% 231 0 87% 
pts after filters MISSING.638 ct:  0.021   0/  0 ??% ??% ??,?% 232 0 87% 
pts after filters MISSING.638 ct:  0.021   0/  0 ??% ??% ??,?% 233 0 87% 
pts after filters MISSING.655 ct:  0.021   0/  0 ??% ??% ??,?% 234 0 87% 
pts after filters MISSING.691 ct:  0.021   0/  0 ??% ??% ??,?% 235 0 87% 
pts after filters MISSING.702 ct:  0.021   0/  0 ??% ??% ??,?% 236 0 86% 
pts after filters MISSING.732 ct:  0.021   0/  0 ??% ??% ??,?% 237 0 86% 
pts after filters MISSING.752 ct:  0.021   0/  0 ??% ??% ??,?% 238 0 86% 
pts after filters MISSING.777 ct:  0.021   0/  0 ??% ??% ??,?% 239 0 86% 
pts after filters MISSING.786 ct:  0.021   0/  0 ??% ??% ??,?% 240 0 86% 
pts after filters MISSING.818 ct:  0.021   0/  0 ??% ??% ??,?% 241 0 86% 
pts after filters MISSING.832 ct:  0.021   0/  0 ??% ??% ??,?% 241 0 86% 
pts after filters MISSING.862 ct:  0.021   0/  0 ??% ??% ??,?% 242 0 86% 
pts after filters MISSING.872 ct:  0.021   0/  0 ??% ??% ??,?% 243 0 86% 
pts after filters MISSING.906 ct:  0.021   0/  0 ??% ??% ??,?% 244 0 86% 
pts after filters MISSING.929 ct:  0.021   0/  0 ??% ??% ??,?% 245 0 86% 
pts after filters MISSING.938 ct:  0.021   0/  0 ??% ??% ??,?% 246 0 86% 
pts after filters MISSING.948 ct:  0.021   0/  0 ??% ??% ??,?% 247 0 86% 
pts after filters MISSING.985 ct:  0.021   0/  0 ??% ??% ??,?% 248 0 86% 
pts after filters MISSING.006 ct:  0.021   0/  0 ??% ??% ??,?% 249 0 85% 
pts after filters MISSING.016 ct:  0.021   0/  0 ??% ??% ??,?% 250 0 85% 
pts after filters MISSING.053 ct:  0.021   0/  0 ??% ??% ??,?% 251 0 85% 
pts after filters MISSING.066 ct:  0.021   0/  0 ??% ??% ??,?% 252 0 85% 
pts after filters MISSING.097 ct:  0.021   0/  0 ??% ??% ??,?% 253 0 85% 
pts after filters MISSING.106 ct:  0.021   0/  0 ??% ??% ??,?% 254 0 85% 
pts after filters MISSING.132 ct:  0.021   0/  0 ??% ??% ??,?% 255 0 85% 
pts after filters MISSING.140 ct:  0.021   0/  0 ??% ??% ??,?% 256 0 85% 
pts after filters MISSING.175 ct:  0.021   0/  0 ??% ??% ??,?% 257 0 85% 
pts after filters MISSING.185 ct:  0.021   0/  0 ??% ??% ??,?% 258 0 85% 
pts after filters MISSING.209 ct:  0.021   0/  0 ??% ??% ??,?% 259 0 85% 
pts after filters MISSING.234 ct:  0.021   0/  0 ??% ??% ??,?% 260 0 85% 
pts after filters MISSING.256 ct:  0.021   0/  0 ??% ??% ??,?% 261 0 84% 
pts after filters MISSING.264 ct:  0.021   0/  0 ??% ??% ??,?% 262 0 84% 
pts after filters MISSING.288 ct:  0.021   0/  0 ??% ??% ??,?% 263 0 84% 
pts after filters MISSING.313 ct:  0.021   0/  0 ??% ??% ??,?% 264 0 84% 
pts after filters MISSING.322 ct:  0.021   0/  0 ??% ??% ??,?% 265 0 84% 
pts after filters MISSING.345 ct:  0.021   0/  0 ??% ??% ??,?% 266 0 84% 
pts after filters MISSING.361 ct:  0.021   0/  0 ??% ??% ??,?% 267 0 84% 
pts after filters MISSING.394 ct:  0.021   0/  0 ??% ??% ??,?% 268 0 84% 
pts after filters MISSING.402 ct:  0.021   0/  0 ??% ??% ??,?% 269 0 84% 
pts after filters MISSING.425 ct:  0.021   0/  0 ??% ??% ??,?% 270 0 84% 
pts after filters MISSING.426 ct:  0.021   0/  0 ??% ??% ??,?% 271 0 84% 
pts after filters MISSING.433 ct:  0.021   0/  0 ??% ??% ??,?% 272 0 84% 
pts after filters MISSING.433 ct:  0.021   0/  0 ??% ??% ??,?% 273 0 84% 
pts after filters MISSING.434 ct:  0.021   0/  0 ??% ??% ??,?% 274 0 84% 
pts after filters MISSING.457 ct:  0.021   0/  0 ??% ??% ??,?% 275 0 84% 
pts after filters MISSING.458 ct:  0.021   0/  0 ??% ??% ??,?% 276 0 84% 
pts after filters MISSING.466 ct:  0.021   0/  0 ??% ??% ??,?% 277 0 84% 
pts after filters MISSING.466 ct:  0.021   0/  0 ??% ??% ??,?% 278 0 84% 
pts after filters MISSING.466 ct:  0.021   0/  0 ??% ??% ??,?% 279 0 84% 
pts after filters MISSING.496 ct:  0.021   0/  0 ??% ??% ??,?% 280 0 84% 
pts after filters MISSING.496 ct:  0.021   0/  0 ??% ??% ??,?% 281 0 84% 
pts after filters MISSING.503 ct:  0.021   0/  0 ??% ??% ??,?% 282 0 84% 
pts after filters MISSING.503 ct:  0.021   0/  0 ??% ??% ??,?% 283 0 84% 
A:   2.5 V:   0.0 A-V:  2.532 ct:  0.021   0/  0 ??% ??% ??,?% 284 0 84% 
Exiting... (Quit) 
```

I've ignored the "your system is too slow" bit as it plays back fine with VLC. I am fully loaded with encoders and decoders as far as I know. Why no playback with mplayer?

---

### Post by Jose Catre-Vandis on 2009-11-14
I'm a plank!

To try to resolve I went back to basics, followed FakeOutdoorsMan's howto in Tuts to install x264 from git and ffmpeg from svn, then updated my mplayer svn and reinstalled that. Still no useful playback of anything encoded with x264.

Then (and only then!) did I think of checking my local config file for mplayer.

A little while back I had added a couple of extra items to the vf line I had in there, namely **softskip** and **pullup**. On removing these I then had perfect mp4/mkv playback.

I am a plank! ;)

Serves as a reminder, though, to check the little things first.....

---

### Post by phenest on 2010-04-05
I have a HD mp4 that I dowloaded using BBC's iPlayer and only plays using BBC's iPlayer. All other apps refuse claiming a lack of codecs.

Output from ffmpeg:
```
[aac @ 0x2b501e0]Reserved bit set.
[aac @ 0x2b501e0]channel element 2.4 is not allocated
[aac @ 0x2b501e0]Input buffer exhausted before END element found
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x2b46420]max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 25000.00 (25000/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'b00rs63k_hd_151390971.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
  Duration: 01:04:35.11, start: 0.000000, bitrate: 2806 kb/s
    Stream #0.0(eng): Video: AVC Coding, 1280x720, 2703 kb/s, 25 fps, 25 tbr, 25k tbn, 25k tbc
    Stream #0.1(eng): Audio: aac, 24000 Hz, stereo, s16, 99 kb/s

```
I'm reckoning that the fourcc is deliberately wrong.

---

### Post by andrew.46 on 2010-04-05
Hi phenest,

> **phenest said:**
> I'm reckoning that the fourcc is deliberately wrong.

Looks a little odd, but if FFmpeg can identify this file perhaps ffplay can play it?

Andrew

---

