---
title: "How to convert flash (flv) video to blackberry?"
date: 2009-10-04
forum: Multimedia Software
---

### Post by PerfectReign on 2009-10-04
I have recently figured out how to convert .avi files to blackberry - [http://ubuntuforums.org/showthread.php?t=1093822&page=4](http://ubuntuforums.org/showthread.php?t=1093822&page=4) - and would now like to convert some flash videos to same.

I've played with teh -ovc option in mencoder. I don't see anything that will help.


kai@r2d2:~/Videos/temp$ mencoder -ovc help
MEncoder 2:1.0~rc2-0ubuntu19+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding


Google hasn't been my friend, either.

Any suggestions?

---

### Post by MartyBuntu on 2009-10-04
Winff has presets for converting to Blackberry compliant.

---

### Post by PerfectReign on 2009-10-04
Ahh, many thanks!  Yes, teh presets - when installed - work like a charm. I was using various options and getting sound but no video. 

Now, I've got it!!!

This helps when taking my dog on his two-mile walk. I'm off now....

---

