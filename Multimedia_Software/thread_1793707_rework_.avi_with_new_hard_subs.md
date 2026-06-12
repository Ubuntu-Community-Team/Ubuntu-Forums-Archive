---
title: "rework .avi with new hard subs"
date: 2011-06-29
forum: Multimedia Software
---

### Post by Dimoutlook on 2011-06-29
Is it possible to rework an .avi to include hard subs from a .srt file I would really like to do this with ffmpeg but it seems that -newsubtitle doesn't  work  for me.
This is the command line so far

ffmpeg -i infile.avi -vtag xvid -b1550k -r 23.970  -newsubtitle infile.srt -acodec libmp3lame -ac 2 -ab 128k -ar 48000 outfile.avi

I keep getting no output specified 

Thanks to all who reply

Dimoutlook

---

### Post by Dimoutlook on 2011-06-30
I actually figured this out on my own I used avidemux subtitle filter to add the subs back into the avi

Dimoutlook

---

