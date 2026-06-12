---
title: "Help with MENcoder"
date: 2009-07-26
forum: Multimedia Software
---

### Post by hambos22 on 2009-07-26
I'm trying to embedded subtitles to an *.avi file with MENcoder..
Well cause i'm greek the encodeing of srt file must be ISO-8859-7.
I wrote in terminal
```
 mencoder -sub subtitle.srt -fontconfig -font /usr/share/fonts/TTF/liberation/LiberationSans-Regular.ttf _**-iso-8859-7**_ -subfont-text-scale 3  -oac mp3lame -lameopts cbr:br=128 -ovc xvid -xvidencopts bitrate=900 video.avi -o output.avi

```
and it gives me this
> MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  T2410  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-iso-8859-7 is not an MEncoder option


i tried [U][B]-iso88597
-iso-88597
-iso8859-7[/B][/U]

but nothing... any help?

thanks

---

