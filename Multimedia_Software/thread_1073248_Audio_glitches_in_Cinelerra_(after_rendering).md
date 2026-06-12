---
title: "Audio glitches in Cinelerra (after rendering)"
date: 2009-02-18
forum: Multimedia Software
---

### Post by bug80 on 2009-02-18
I have problems with Cinelerra (version 2.1CV) in Ubuntu (8.04) when I try to export a video which consists of multiple smaller clips. At each transition between two clips, the rendered audio goes bad, in the form of hickups and/or glitches.

I found the following workaround: when I first convert the (compressed) audio from the video clips to (uncompressed) WAVE using ffmpeg from the command-line, re-import these WAVE files into the Cinelerra project, and re-render the project using these new files there are NO problems.

So, it seems that the glitches occur because of problems with decoding compressed audio in Cinelerra. Apparently there is a bug with dealing transitions between clips in the decoder.

So far I tried the following things to overcome this problem, until now to no avail:

* Apply audio crossovers between the clips

Under settings --> preferences --> performance:
* Increase the "cache size"
* Increase the "seconds to preroll render"

Under settings --> preferences --> playback
* Change the audio buffer size
* Increase "preload buffer for quicktime"

Anyone has other ideas?

---

### Post by stoogiebuncho on 2009-03-23
I had a similar problem.  Then I tried rendering the audio with the dithering options selected, and it did much better.

I don't know if that would help in your situation or not.

---

