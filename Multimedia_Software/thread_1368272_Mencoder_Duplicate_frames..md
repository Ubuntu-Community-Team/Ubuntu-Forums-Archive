---
title: "Mencoder Duplicate frames."
date: 2009-12-30
forum: Multimedia Software
---

### Post by Nate_is_cool on 2009-12-30
Alright I am using a a program called motion that records video when motion is detected. Unfortunately it records in very short videos, and I want one long one each day instead of about 3 hundred up them. I am using a program called mencoder to compile them into one long video and when I do I get the duplicate frames error and it just skips the frame causing a skip in the video. How can I fix this. Motion encodes them in the msmpeg. This is the command I am using : mencoder * -o temp.avi -ovc lavc -nosound

the "-nosound" is there because there is no audio on the videos.

Here is the error 
"
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmp42] vfm: ffmpeg (FFmpeg M$ MPEG-4 v2)
==========================================================================
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
Pos:2112.7s  31411f ( 0%) 216.47fps Trem:   0min   0mb  A-V:0.000 [755:0]
1 duplicate frame(s)!
Pos:2112.9s  31413f ( 1%) 216.47fps Trem: 170min 13643mb  A-V:0.000 [755:0]
1 duplicate frame(s)!
Pos:2113.1s  31415f ( 2%) 216.46fps Trem: 115min 9268mb  A-V:0.000 [755:0]]
1 duplicate frame(s)!
Pos:2113.3s  31417f ( 2%) 216.46fps Trem:  87min 7069mb  A-V:0.000 [755:0]
1 duplicate frame(s)!
Pos:2113.5s  31419f ( 3%) 216.46fps Trem:  70min 5714mb  A-V:0.000 [755:0]
1 duplicate frame(s)!
Pos:2113.7s  31421f ( 4%) 216.46fps Trem:  57min 4746mb  A-V:0.000 [755:0]
1 duplicate frame(s)!
Pos:2113.9s  31423f ( 4%) 216.46fps Trem:  48min 4044mb  A-V:0.000 [755:0]
1 duplicate frame(s)!
Pos:2114.1s  31425f ( 6%) 216.46fps Trem:  37min 3117mb  A-V:0.000 [755:0]
1 duplicate frame(s)!
^Cs:2114.3s  31427f ( 6%) 216.45fps Trem:  32min 2773mb  A-V:0.000 [755:0]
1 duplicate frame(s)!
Pos:2114.4s  31428f ( 7%) 216.45fps Trem:  30min 2630mb  A-V:0.000 [755:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  755.516 kbit/s  (94439 B/s)  size: 199683001 bytes  2114.400 secs  31428 frames
"

Anything will help!

---

### Post by cotcot on 2009-12-30
Maybe it helps by adding -fps 50.
I had a comparable problem encoding the .mts video from a HD camera. Adding -fps 50 solved the problem.

---

