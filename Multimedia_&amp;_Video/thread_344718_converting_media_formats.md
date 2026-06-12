---
title: "converting media formats"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by Kulgan on 2007-01-23
I'm sure that just by reading the title, many are already going "aw, not another of those...", but I'm not quite sure if that's right. 

I have seen several posts where people get help converting wma into mp3, avi into.... but is there one app that will do it all? 

My personal interest in all this (it never goes past that :p ) is that I'm trying to append a win media movie to an mpeg TS in avidemux... and it's not really working too well. Duh. Yes, we have all heard of the magical command line, that will do anything, but how, is the question. 

If there is one, should it be more famous, if there isn't, should someone make one? I'd go into it myself if I thought there were any point. And of course, if I knew how O_o

-K

---

### Post by kingmonkey on 2007-01-23
mplayer & mencoder are the best thing for this kind of job, and it is widely used and very "famous".

I dont think you can just append one video format to the end of another like glue, because of meta information.

---

### Post by majoridiot on 2007-01-24
> **kingmonkey said:**
> mplayer & mencoder are the best thing for this kind of job, and it is widely used and very "famous".

very true... although the man pages are way beyond daunting for most people.

> **Kulgan said:**
> I'm trying to append a win media movie to an mpeg TS in avidemux... 
-K

the best way to do this is to convert the wmv to a TS first, then do the append.  whenever
mixing media formats like this in avidemux, it's best to convert the individual component files
to whatever the final format will be before stringing them together.  i.e.- in this case, if you
wanted to append the TS and WMV and output the final as XVID, convert each to XVID first,
then append them.

---

### Post by Kulgan on 2007-01-24
> very true... although the man pages are way beyond daunting for most people.

Damn right! :D

Solved the problem by getting someone with skillz (and a mac) to do it... :-# 

-K

---

