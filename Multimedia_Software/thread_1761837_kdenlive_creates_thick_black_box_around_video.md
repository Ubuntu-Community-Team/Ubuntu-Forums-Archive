---
title: "kdenlive creates thick black box around video"
date: 2011-05-18
forum: Multimedia Software
---

### Post by Mariane on 2011-05-18
Hi, 

I am trying to extract a few segments from a long recording and to group them together as a .avi file. I used kdenlive but it created a huge black frame around the video. This remains even in full screen playback with vlc. I tried rendering (this means saving except it takes longer) in 3 formats: .m2t, .avi and .flv and the black frame is always there. 

Online I found a workaround: 
[code]
Use Avidemux as a postproduction tool, load rendered movie, use filters to remove border + resize to original size (PAL in my case) and reencode.
Not ideal - double reencoding + waste of time and disk space - but workable.
I simply add two more filters ;-)
[code]

But this answer dates from 2007 and when I tried it Avidemux told me "Video filters cannot be applied in copy mode. To apply filters the video must be transcoded". This sounds strange to me because the file I opened was the one in .avi format. AFAIK transcoding is used to save a DVD to as an .avi movie. Why should I have to transcode a movie which is already in .avi format and what format should I transcode it into??? 

Online I found someone saying "for video use MPEG-4 ASP (Xvid) instead of copy". This activates the filters but the resize filter does not resize. Whatever values I give it resets to width=720 and height=576 when I click on "apply". 

All suggestions welcome. 

Mariane

---

### Post by no2498 on 2011-05-19
if you look close you will see two small box's with numbers in them
i set mine to 0
no more frame or between gray/black

hope this helps you

---

### Post by Mariane on 2011-05-24
Where did you see these boxes please?  :confused: 

Mariane

---

### Post by Mariane on 2011-06-03
Solution I found is not to use default settings for rendering (HDV) but to select AVI DV. Then there is no more thick black frame. 

Mariane

---

