---
title: "Where can I find SEDG codecs"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by zumbe on 2007-08-01
Hi. I'm trying to edit the video I filmed with my samsung camera here, in linux, but it tells me that SEDG codes are not supported.

How can I get this codecs? I've searched a lot, but i find nothing.

---

### Post by david_2001 on 2007-08-01
I did a little searching.  It turns out that SEDG is a Samsung implementation of mpeg-4 and the recommendation is to search the video file and replace all instances of SEDG with DIVX.  I have no way of testing this but if you want to try then install the bbe package (it's in the universe repository) and execute the following command, substituting the actual input and output filenames:
```
bbe -e "s/SEDG/DIVX/" SEDGInputFile.avi > DIVXOutputFile.avi
```

---

### Post by zumbe on 2007-08-01
Thanks friend!

It worked. But I still got some problems: 

The qualiy is very poor... do you know if I con controle it when I'm converting the filetype?
And also, now I can see the video, but I'd like to edit it. I found Kino (for DV files), and the program can't work with my files (both files, SEDG and DivX).

Hope anyone can help me.

Thanks a lot!

---

### Post by david_2001 on 2007-08-02
Changing SEDG to XVID in the video file is only changing the codec identification and won't alter the quality of the recorded image.  Conversion from mpeg4 to different video formats, e.g. mpeg2, is something of a dark art but can be done without noticeable loss of quality.  There is no need to use a DV-specific editor for these files.  For simple trimming, cutting and pasting, and format conversion too, you could try avidemux, which is in the multiverse repository.

---

### Post by josir on 2007-12-26
Just to feedback the tip: it worked perfectly on 7.04 - I tested with several videos.

---

