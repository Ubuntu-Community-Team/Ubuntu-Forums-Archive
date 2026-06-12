---
title: "Produce web compatible video from jpegs using imagemagick and avconv"
date: 2014-01-29
forum: Multimedia Software
---

### Post by jamesw-6 on 2014-01-29
I have a requirement to generate videos from jpg's for viewing on any device over the web.
For the website side of things I have chosen to go with the jquery video player medielement.js and to supply vidoes in the format of mp4, webm, ogv and a fallback for flash in swf format.

After a lot of researching and trial and error I have come up with the following

I am using imagemagick mogrify command to prepare the jpg's for processing by avconv using the following command
```
mogrify -resize 480x320! *.jpg
```

Then I morph thrm using convert
```
convert *.jpg -delay 0 -morph 0 %05d.morph.jpg
```

Then I run avconv against the morphed images once for each format

```
avconv -r 6 -qscale 1 -i %05d.morph.jpg -vcodec libx264 -profile:v baseline skit.mp4
avconv -r 6 -qscale 1 -i %05d.morph.jpg -vcodec libvpx -acodec libvorbis skit.webm
avconv -r 6 -qscale 1 -i %05d.morph.jpg -vcodec libtheora -acodec libvorbis skit.ogv
avconv -r 6 -qscale 1 -i %05d.morph.jpg skit.swf

```

The output from the code that runs this process is as follows

```
avconv version 0.8.9-6:0.8.9-0ubuntu0.13.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:09:48 with gcc 4.7.3
Input #0, image2, from '/home/jamie/Development/Rails/skitit/skits/2/20/tmp/%05d.morph.jpg':
  Duration: 00:00:03.33, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj420p, 480x320 [PAR 72:72 DAR 3:2], 6 fps, 6 tbr, 6 tbn, 6 tbc
[buffer @ 0x18d4d80] w:480 h:320 pixfmt:yuvj420p
[libx264 @ 0x18e7a80] using SAR=1/1
[libx264 @ 0x18e7a80] using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x18e7a80] profile Constrained Baseline, level 2.1
[libx264 @ 0x18e7a80] 264 - core 123 r2189 35cf912 - H.264/MPEG-4 AVC codec - Copyleft 2003-2012 - http://www.videolan.org/x264.html - options: cabac=0 ref=3 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=1 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=6 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
Output #0, mp4, to '/home/jamie/Development/Rails/skitit/skits/2/20/tmp/skit.mp4':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libx264, yuvj420p, 480x320 [PAR 72:72 DAR 3:2], q=-1--1, 6 tbn, 6 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (mjpeg -> libx264)
Press ctrl-c to stop encoding
frame=   20 fps=  0 q=-1.0 Lsize=      23kB time=3.33 bitrate=  56.0kbits/s    
video:22kB audio:0kB global headers:0kB muxing overhead 4.116676%
[libx264 @ 0x18e7a80] frame I:1     Avg QP:18.96  size:  3896
[libx264 @ 0x18e7a80] frame P:19    Avg QP:21.85  size:   941
[libx264 @ 0x18e7a80] mb I  I16..4: 93.0%  0.0%  7.0%
[libx264 @ 0x18e7a80] mb P  I16..4:  1.0%  0.0%  1.1%  P16..4:  4.5%  0.6%  0.4%  0.0%  0.0%    skip:92.4%
[libx264 @ 0x18e7a80] coded y,uvDC,uvAC intra: 17.5% 14.9% 13.4% inter: 1.4% 0.9% 0.7%
[libx264 @ 0x18e7a80] i16 v,h,dc,p: 92%  2%  5%  0%
[libx264 @ 0x18e7a80] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 15% 12% 28% 10%  9%  7%  7%  6%  7%
[libx264 @ 0x18e7a80] i8c dc,h,v,p: 88%  5%  6%  2%
[libx264 @ 0x18e7a80] ref P L0: 76.4% 17.1%  6.5%
[libx264 @ 0x18e7a80] kb/s:52.26
avconv version 0.8.9-6:0.8.9-0ubuntu0.13.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:09:48 with gcc 4.7.3
Input #0, image2, from '/home/jamie/Development/Rails/skitit/skits/2/20/tmp/%05d.morph.jpg':
  Duration: 00:00:03.33, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj420p, 480x320 [PAR 72:72 DAR 3:2], 6 fps, 6 tbr, 6 tbn, 6 tbc
Incompatible pixel format 'yuvj420p' for codec 'libvpx', auto-selecting format 'yuv420p'
[buffer @ 0x1029640] w:480 h:320 pixfmt:yuvj420p
[avsink @ 0x1029400] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x1017320] w:480 h:320 fmt:yuvj420p -> w:480 h:320 fmt:yuv420p flags:0x4
[libvpx @ 0x1028a80] v1.1.0
Output #0, webm, to '/home/jamie/Development/Rails/skitit/skits/2/20/tmp/skit.webm':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libvpx, yuv420p, 480x320 [PAR 1:1 DAR 3:2], q=-1--1, 200 kb/s, 1k tbn, 6 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (mjpeg -> libvpx)
Press ctrl-c to stop encoding
frame=   20 fps=  0 q=0.0 Lsize=      41kB time=3.33 bitrate= 100.9kbits/s    
video:40kB audio:0kB global headers:0kB muxing overhead 1.502343%
avconv version 0.8.9-6:0.8.9-0ubuntu0.13.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:09:48 with gcc 4.7.3
Input #0, image2, from '/home/jamie/Development/Rails/skitit/skits/2/20/tmp/%05d.morph.jpg':
  Duration: 00:00:03.33, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj420p, 480x320 [PAR 72:72 DAR 3:2], 6 fps, 6 tbr, 6 tbn, 6 tbc
Incompatible pixel format 'yuvj420p' for codec 'libtheora', auto-selecting format 'yuv420p'
[buffer @ 0x1640dc0] w:480 h:320 pixfmt:yuvj420p
[avsink @ 0x1654460] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x16421c0] w:480 h:320 fmt:yuvj420p -> w:480 h:320 fmt:yuv420p flags:0x4
Output #0, ogg, to '/home/jamie/Development/Rails/skitit/skits/2/20/tmp/skit.ogv':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libtheora, yuv420p, 480x320 [PAR 1:1 DAR 3:2], q=2-31, 200 kb/s, 6 tbn, 6 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (mjpeg -> libtheora)
Press ctrl-c to stop encoding
frame=   20 fps=  0 q=0.0 Lsize=      57kB time=3.33 bitrate= 139.9kbits/s    
video:53kB audio:0kB global headers:3kB muxing overhead 0.524237%
avconv version 0.8.9-6:0.8.9-0ubuntu0.13.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:09:48 with gcc 4.7.3
Input #0, image2, from '/home/jamie/Development/Rails/skitit/skits/2/20/tmp/%05d.morph.jpg':
  Duration: 00:00:03.33, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj420p, 480x320 [PAR 72:72 DAR 3:2], 6 fps, 6 tbr, 6 tbn, 6 tbc
Incompatible pixel format 'yuvj420p' for codec 'flv', auto-selecting format 'yuv420p'
[buffer @ 0x8a2fe0] w:480 h:320 pixfmt:yuvj420p
[avsink @ 0x8b3460] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x8a11c0] w:480 h:320 fmt:yuvj420p -> w:480 h:320 fmt:yuv420p flags:0x4
Output #0, swf, to '/home/jamie/Development/Rails/skitit/skits/2/20/tmp/skit.swf':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: flv, yuv420p, 480x320 [PAR 1:1 DAR 3:2], q=2-31, 200 kb/s, 90k tbn, 6 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (mjpeg -> flv)
Press ctrl-c to stop encoding
frame=   20 fps=  0 q=2.0 Lsize=      84kB time=3.33 bitrate= 206.4kbits/s    
video:84kB audio:0kB global headers:0kB muxing overhead 0.503605%

```

The resulting video seems to play fine when viewd in Firefox and Chrome but mobile devices browser crash

For completeness sake the code for the HTML page is as follows

[HTML]                <video width="220" height="160" poster=<%=skit.frames.first.frame unless skit.frames.empty?%> controls="controls" preload="none">
                    <source type="video/mp4" src=<%=skit.video_mp4.url%> />
                    <source type="video/webm" src=<%=skit.video_webm.url%> />
                    <source type="video/ogg" src=<%=skit.video_og.url%> />

                    <object width="220" height="160" type="application/x-shockwave-flash" data=<%=skit.video_swf.url%>>
                        <param name="movie" value=<%=skit.video_swf.url%> />
                        <param name="flashvars" value="controls=true&file=<%=skit.video_mp4.url%>" />
                        <!-- Image as a last resort -->
                        <img src=<%=skit.frames.first.frame unless skit.frames.empty?%> width="110" height="110" title="No video playback capabilities"/>
                    </object>

                </video>
[/HTML]

Can anyone spot if there is anything I am doing wrong?

---

