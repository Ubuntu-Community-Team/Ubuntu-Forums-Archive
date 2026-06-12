---
title: "ffmpeg command to change bit rate of wmv files"
date: 2011-08-03
forum: Multimedia Software
---

### Post by disha on 2011-08-03
I have a VC-1 file at Simple profile, medium level, bit rate = 236 kbps. I use the following command to change bit rate and frame rate of file 

ffmpeg -i input.wmv -b 128k -r 15 output.wmv 

When I check the information of output file, it shows a file with MPEG-4 Visual format and codec MP43. Is there any way to produce an output file with the  same VC1 Simple profile, medium level information as input file using ffmpeg?

I tried using -f vc1 switch in the command but thats only for having raw vc1 video output.

Thanks,

---

### Post by FakeOutdoorsman on 2011-08-03
I believe FFmpeg (or libav if you're using Natty and up) can't encode to VC-1:
```
$ ffmpeg -codecs 2>&1 | grep -i vc-1
 D V D  vc1             SMPTE VC-1
 D V D  vc1_vdpau       SMPTE VC-1 VDPAU
```
D = Decoding supported
V = Video codec

---

