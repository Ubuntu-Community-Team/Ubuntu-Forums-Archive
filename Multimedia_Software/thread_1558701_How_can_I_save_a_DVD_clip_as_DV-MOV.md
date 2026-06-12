---
title: "How can I save a DVD clip as DV-MOV?"
date: 2010-08-22
forum: Multimedia Software
---

### Post by curiousnoob on 2010-08-22
I need to save some clips from a DVD as either a DV-AVI or DV-MOV format.  
What program can I use to do this?

---

### Post by curiousnoob on 2010-08-24
Bump?

---

### Post by hsoulen on 2010-08-24
This is a very interesting question. Before I try to answer I need a bit more clarification:

You would like to take the MPEG2 video from an (assuming unencrypted) DVD and save it as a DV capture in either Quicktime DV or Microsoft DV-AVI format?

Can you briefly describe why you would like that as the output format?

I am not trying to be difficult I just want to formulate and answer that makes sense as there are many other formats that you can edit in (with Kino/Pitivi etc.) without the need to have them in "raw DV' format.

Cheers,

Hank

---

### Post by curiousnoob on 2010-09-08
> **hsoulen said:**
> This is a very interesting question. Before I try to answer I need a bit more clarification:

You would like to take the MPEG2 video from an (assuming unencrypted) DVD and save it as a DV capture in either Quicktime DV or Microsoft DV-AVI format?

Can you briefly describe why you would like that as the output format?

I am not trying to be difficult I just want to formulate and answer that makes sense as there are many other formats that you can edit in (with Kino/Pitivi etc.) without the need to have them in "raw DV' format.

Cheers,

Hank
It is part of a presentation that someone else is doing and they requested the DV-AVI format.
I have tried importing the vob file using kino but for some reason the sound does not sync up when I do that.

---

### Post by hsoulen on 2010-09-09
Sorry that the import of the VOB into Kino is causing sound sync issues, I have to be honest I do not do a lot of work with VOB files just raw DV.

I found this thread referring to using ffmpeg to convert VOB streams to raw DV format video, you can then edit this video in Kino as discussed:

[http://ubuntuforums.org/showthread.php?t=525674](http://ubuntuforums.org/showthread.php?t=525674)

The part that is most interesting is:


[LIST=1]
[*]Install ffmpeg (synaptic will help with this, ignore the referances to "medibuntu" as this is applicable to all "buntu" variants)
[*]"ffmpeg -i input.vob -target ntsc-dv output.dv"
[/LIST]
Hope I am not heading you down the wrong path.

Hank

---

