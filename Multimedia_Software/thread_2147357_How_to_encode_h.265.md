---
title: "How to encode h.265"
date: 2013-05-21
forum: Multimedia Software
---

### Post by raptorhunter on 2013-05-21
I've been looking through the mencoder docs, but I can't find a way to encode h.265 video for my Galaxy S4. How do I do this?

---

### Post by cipherboy_loc on 2013-05-21
[SIZE=5]Edit: Misread--my bad. [/SIZE]

So you want video...Video codec is specificed by the **-ovc** option in the mencoder options list. To figure out which codecs you have installed, run:
```

$ mencoder -ovc help
MEncoder svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   xvid     - XviD encoding
   x264     - H.264 encoding

```

Thus you would specify **-ovc x264** on the command line for h.265 video. 


Thanks,
Cipherboy LOC

---

### Post by raptorhunter on 2013-05-21
> **cipherboy_loc said:**
> So you want video...Video codec is specificed by the **-ovc** option in the mencoder options list. To figure out which codecs you have installed, run:
```

$ mencoder -ovc help
MEncoder svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   xvid     - XviD encoding
   x264     - H.264 encoding

```

Thus you would specify **-ovc x264** on the command line for h.265 video. 


Thanks,
Cipherboy LOC

That makes no sense. How does -ov x26**4** give you h.26**5**?

---

### Post by cipherboy_loc on 2013-05-21
I misread--my bad. However, according to [Wikipedia]("http://en.wikipedia.org/wiki/High_Efficiency_Video_Coding"), which could be wrong, it appears that the standard has not yet been finalized and as such, likely not to have support yet. I guess patience is expected here. In the meantime, perhaps you could find a different option that would work for your Galaxy S4? 


Thanks,
Cipherboy

---

### Post by andrew.46 on 2013-05-22
I suspect that MEncoder would be unlikely to ever support HEVC, and FFmpeg has not joined the bandwagon yet. Interestingly enough some samples here:

[http://www.elecard.com/en/download/videos.html](http://www.elecard.com/en/download/videos.html)

I gather that you will need [their player ]("http://www.elecard.com/en/technology/researchlab/hevc-player.html")as well.

---

### Post by raptorhunter on 2013-06-12
> **andrew.46 said:**
> I suspect that MEncoder would be unlikely to ever support HEVC, and FFmpeg has not joined the bandwagon yet. Interestingly enough some samples here:

[http://www.elecard.com/en/download/videos.html](http://www.elecard.com/en/download/videos.html)

I gather that you will need [their player ]("http://www.elecard.com/en/technology/researchlab/hevc-player.html")as well.

Why not?

---

### Post by andrew.46 on 2013-06-12
> **raptorhunter said:**
> Why not?

MENcoder has not been developed for years and is unlikely to restart development. Most are using FFmpeg which is very, very actively developed.

---

### Post by josir on 2013-07-09
To find if a file is really h.264, try this command:

   ffprobe -show_streams "file.mp4"

---

