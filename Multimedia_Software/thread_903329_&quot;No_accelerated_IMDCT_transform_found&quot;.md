---
title: "&quot;No accelerated IMDCT transform found&quot;"
date: 2008-08-28
forum: Multimedia Software
---

### Post by daka on 2008-08-28
{SOLVED]   I changed the audio codec to MP3 and that sorted it.


When converting from .MOV to .avi I get this message:


"No accelerated IMDCT transform found"

There is video but no audio

Any suggestions appreciated

Daka

---

### Post by daka on 2008-08-28
trying converting to MP3 audio codec solved this... thanks for the input!

I still have a question.... I have the output but the file is a bit grainy... poor quality.  Here is my ffmpeg code::::::

ffmpeg -i old.MOD -deinterlace -vcodec h264 -b 4000k -acodec mp3 -ab 192k new.avi

Does anyone have a suggestion how to improve the quality?

Daka

---

