---
title: "Can't play .avi file"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by kariopto on 2007-05-07
Hi, I'm trying to play a .avi file, I have installed w32codecs, libavcodec0d and libavformat0d. 
When I try to play it with mplayer, I get:
```
libavformat file format detected.
[tiertexseq @ 0x88177e8]Could not find codec parameters (Video: tiertexseqvideo,                                                                                                       256x128)
VIDEO:  []  256x128  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
RAW: depth 0 not supported
VDec: vo config request - 256 x 128 (preferred colorspace: Unknown)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 256 x 128 (preferred colorspace: Packed YUY2)
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 256x128 => 256x128 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 352.8 kbit/100.00% (ratio: 44100->44100)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
A:   0.0 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file) 
```
Am I missing something?
Thanks in advance

---

