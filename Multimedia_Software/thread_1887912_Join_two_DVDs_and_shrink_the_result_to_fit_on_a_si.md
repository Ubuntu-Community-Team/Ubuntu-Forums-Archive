---
title: "Join two DVD:s and shrink the result to fit on a single 4.7 GB DVD"
date: 2011-11-28
forum: Multimedia Software
---

### Post by veroslav on 2011-11-28
Hi,

I have two dvd:s on the harddisk that I would like to join, shrink the resulting dvd, and burn it onto only one DVD. Each of the two DVD:s is around 4 GB and is saved in a separate VIDEO_TS folder respectively. I have tried the following but could not get it working:

1. Join all VOB:s from both DVD:s to a single VOB-file (around 8 GB) in AviDemux
2. Make a double-layer DVD in DeVeDe from the joined VOB above
3. Import the large VOB above into K9Copy and shrink it to around 4 GB in order to fit on a single DVD
4. Burn the ISO

The resulting DVD stutters quite badly, however, each 3-4 seconds, and is VERY noticable.

Could anyone give me any feedback on how to do this correctly and whether my approach is correct?

Thank you in advance!

Kind Regards,
Veroslav

---

### Post by crazy bird on 2011-11-28
What you shoudl try is shrink the 2 VOB files seperatly and then merge it with Devede. I'm not sure whether Devede can shrink them for you, but when i use Devede and add some .vob files, there's an option which allows you to choose between different cd/dvd sizes. if you made your choice, there's on the rigth side of the bar in the middle an option to fit everything on that chosen cd/dvd size. You could try that.

---

### Post by veroslav on 2011-11-28
Thank you for your reply, I will try to shrink each DVD separately, haven't tried that before, might help.

May I ask you what application do you use for shrinking, K9Copy or something else?

I recall trying to "Adjust disk size"-option in DeVeDe but I also remember that I've got an error when I tried to build a DVD from that, not sure what the error was though.

Thanks again!

Kind Regards,
Veroslav

---

### Post by SeijiSensei on 2011-11-28
I think this is going to be difficult to accomplish unless you re-encode the source material to a different format.  You might see whether converting them with Handbrake using H.264 gives you small enough images to place them both together on a single disc.  The MPEG2 standard used on DVDs is very inefficient compared to H.264.  You can also dial down the output bit rate to shrink the resulting files as well, giving up some resolution as a result.

---

### Post by veroslav on 2011-11-28
Thank you for you reply, SeijiSensei.

I didn't think it would be that difficult, sorry to hear that. The reason for trying to fit both dvd:s on a single dvd was to rebuild a dvd structure with menus and all, in order to avoid changing the disks in the middle of the footage.

If I understand it correctly, after converting the dvd:s to H.264, I will have to join these somehow if I want to have a continuous stream of video? Is it possible to do this without loosing the video quality and skip reencoding?

Thank you again.

Regards,
Veroslav

---

### Post by SeijiSensei on 2011-11-28
> **veroslav said:**
> I didn't think it would be that difficult, sorry to hear that.

DVDs were designed to fit a two-hour movie using MPEG2.  In general, two hours of content should occupy about 4GB of space.  Unless these are very short movies, two of them won't fit on one DVD.

How big are the files in the VIDEO_TS and AUDIO_TS directories for each film?  Unless they sum to less than 4.5 GB or so, they won't both fit on a single DVD.

> If I understand it correctly, after converting the dvd:s to H.264, I will have to join these somehow if I want to have a continuous stream of video? Is it possible to do this without loosing the video quality and skip reencoding?

I don't think so.  You could use DeVeDe to construct a single DVD from the compressed files after re-encoding.

---

### Post by veroslav on 2011-11-29
Thank you again for your reply.

Perhaps I will leave it as it is, two DVD:s that is.

I would like to avoid the quality loss at all costs so for me, that is more important than to have everything being fitted on one DVD.

And it seems that the conversion methosd that were discussed, all lead to quality loss, in one way or the other.

Thanks again for your help.

Regards,
Veroslav

---

