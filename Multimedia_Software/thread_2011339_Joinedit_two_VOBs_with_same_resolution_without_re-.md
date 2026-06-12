---
title: "Join/edit two VOB:s with same resolution without re-encoding"
date: 2012-06-27
forum: Multimedia Software
---

### Post by veroslav on 2012-06-27
Hi,

I have two VOB:s with a same resolution, and I would like to use some of the contents of VOB1 and paste them into VOB2 where the same footage is missing. Then I want to save the resulting edited VOB2 in a same resolution WITHOUT encoding again (I want to preserve the video quality).

I read that it should be possible to do it, because the VOB:s have same resolution.

I have been looking into kdenlive and avidemux but haven't manage to do it with these programs (kdenlive re-encodes and avidemux doesn't allow me to copy and paste between the VOB:s).

Does anyone have any suggestions on the workflow and applications needed to accomplish the above?

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by shantiq on 2012-06-27
```
mencoder -oac copy -ovc copy -o 2.vob 1a.vob 1b.vob
```   this might do it for you altho i think it reencodes   [not sure]     works well anyway


2.vob is your new file   1a and 1b your input

---

### Post by evilsoup on 2012-06-27
Shantiq I don't really use mencoder, but wouldn't that just give you a video with two video streams? Rather than placing one after another.

IIRC, .VOB files are actually a variation of MPEG2, so you should be able to use cat. From the commandline, try

cat input1.vob input2.vob > output.vob

(this can have an arbitrary number of inputs)

---

### Post by shantiq on 2012-06-27
> **evilsoup said:**
> Shantiq I don't really use mencoder, but wouldn't that just give you a video with two video streams? Rather than placing one after another.

IIRC, .VOB files are actually a variation of MPEG2, so you should be able to use cat. From the commandline, try

cat input1.vob input2.vob > output.vob

(this can have an arbitrary number of inputs)


no Evilsoup Mencoder does what the asker wants

check your cat file      you will see you have only copied the first file     cat works with   mp3    and ts      but mostly does not work with sound and video files:KS

---

### Post by veroslav on 2012-06-28
Hi again,

thank you both of you, for your replies. What I am looking for is some kind of video editor where you can load both of the mentioned VOB:s, cut and join them, and export the result to a new VOB but without re-encoding.

I will have a look at kdenlive in more detail, I assumed that the DVD/VOB export option always encoded the resulting file again, but perhaps that is not the case when the input resolution is the same for all the files.

Perhaps someone with more experience with kdenlive knows more?

Thanks again!

Kind Regards,
Veroslav

---

