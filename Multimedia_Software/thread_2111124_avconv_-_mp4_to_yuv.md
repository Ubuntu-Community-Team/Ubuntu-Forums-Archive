---
title: "avconv - mp4 to yuv"
date: 2013-02-01
forum: Multimedia Software
---

### Post by Utahoma on 2013-02-01
Hello everybody,
I hope you could help me :)
I am new in Ubuntu and video coding, and my native language is not English, so please forgive me if my questions are too trivial, or you don't understand them. I will do my best to explain it thoroughly. 

I am testing a tool for QoE assessment of video delivery in IP networks named QoE monitor. My platform is Ubuntu 12.04, with NS-3.13 and libav packages: 
[LIST]
[*]libav-dbg
[*]libav-source
[*]libav-tools
[*] libavcodec-dev
[*]libavcodec53
[*]libavdevice-dev
[*]libavdevice53
[*]libavfilter2
[*] libavformat-dev
[*]libavformat53
[*]libavutil-dev
[*]libavutil51
[/LIST]
The simulation works like this: because of possible packet losses due to the transmission and the coding process, on the receivers side, for each lost packet in mp4 video the corresponding amount of dummy data is embedded. But when I convert that received mp4 video to yuv with:
avconv -i highway.received.mp4 highway.received.yuv
I get:

avconv version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:50:25 with gcc 4.6.3

Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'highway.received.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512

    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf53.21.0
  Duration: 00:01:20.04, start: 0.000000, bitrate: 1033 kb/s
    Stream #0.0(und): Video: h264 (Constrained Baseline), yuv420p, 352x288, 1031 kb/s, 24.99 fps, 25 tbr, 25 tbn, 50 tbc
File 'highway.received.yuv' already exists. Overwrite ? [y/N] y
[buffer @ 0x83c0780] w:352 h:288 pixfmt:yuv420p
Output #0, rawvideo, to 'highway.received.yuv':
  Metadata:
    major_brand     : isom
    minor_version   : 512

    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf53.21.0
    Stream #0.0(und): Video: rawvideo, yuv420p, 352x288, q=2-31, 200 kb/s, 90k tbn, 25 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> rawvideo)
Press ctrl-c to stop encoding
[h264 @ 0x83c1300] AVC: nal size 0
[h264 @ 0x83c1300] no frame!
Error while decoding stream #0:0
AVC: nal size 0=  0 q=0.0 size=   65934kB time=17.76 bitrate=30412.8kbits/s    
[h264 @ 0x83c1300] no frame!
Error while decoding stream #0:0
corrupted macroblock 3 13 (total_coeff=-1)time=32.08 bitrate=30412.8kbits/s    
[h264 @ 0x83c1300] error while decoding MB 3 13
[h264 @ 0x83c1300] concealing 156 DC, 156 AC, 156 MV errors
[h264 @ 0x83c1300] corrupted macroblock 5 11 (total_coeff=-1)
[h264 @ 0x83c1300] error while decoding MB 5 11
[h264 @ 0x83c1300] concealing 198 DC, 198 AC, 198 MV errors
Invalid level prefixq=0.0 size=  214434kB time=57.76 bitrate=30412.8kbits/s    
[h264 @ 0x83c1300] error while decoding MB 9 12
[h264 @ 0x83c1300] concealing 172 DC, 172 AC, 172 MV errors
AVC: nal size 0=480 q=0.0 size=  254678kB time=68.60 bitrate=30412.8kbits/s    
[h264 @ 0x83c1300] no frame!
Error while decoding stream #0:0
frame= 1983 fps=391 q=0.0 Lsize=  294476kB time=79.32 bitrate=30412.8kbits/s    
video:294476kB audio:0kB global headers:0kB muxing overhead 0.000000%

In order for simulation to give correct comparison between sent and received yuv video, both files need to have the same number of frames. In my case, sent file has 2000 frames, and the output yuv file has 1983 frames. Apparently, my codec doesn't recognize those dummy data frames and deletes them.
My question is: Is there some option that I can use in avconv command, or something else to do about my codec, so it keeps those frames in the output yuv file too. In that way my sent and received yuv files will both have 2000  frames, and simulation will give the correct frame comparison.

 
Please help.
Thank you :)

---

