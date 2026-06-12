---
title: "Prepping DV for burning to DVD"
date: 2008-07-16
forum: Multimedia Software
---

### Post by longhaired1 on 2008-07-16
Finally have had great success editing a music video in Cinelerra. The resultant rendered files was close to a gig (for a 4 minute song) when rendered in Raw DV format. 

What should I do to prepare/convert that video for burning to a CD? For the time being I need to move the file to my Windows machine to burn the DVD. The Raw DV file isn't working out for that. I can view it, with sound, on my Windows machine but the burned version is not working. 

Thanks. 

BTW, it took a while to get Cinelerra to work for me, but now that it's up and running I love it.

---

### Post by mateuszbaranski on 2008-09-11
> **longhaired1 said:**
> 
What should I do to prepare/convert that video for burning to a CD? 

You have only rendered the file, now you have to encode the file to MPEG1 format (VIDEOCD) or MPEG2 (DVD). You can use many programs - among others:
FFMPEG, mpeg2enc, mplayer (with transcode) and some others. They are usable in command line. There are some GUI for these tools. Why don't you encode directly during rendering in Cinelerra?
> **longhaired1 said:**
> 
The Raw DV file isn't working out for that. I can view it, with sound, on my Windows machine but the burned version is not working. 

It's obvious - DVD format needs MPEG2 encoded stream of video & music - you cannot just burn DV file on DVDROM. You have to encode it to MPEG2 and **author the dvd** (convert to VOBs).

---

