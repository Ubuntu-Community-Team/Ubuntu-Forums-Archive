---
title: "How to merge multiple VOB:s?"
date: 2011-11-14
forum: Multimedia Software
---

### Post by veroslav on 2011-11-14
Hi,

I have a few VOB files that I would like to combine into a single VOB, in order to burn this onto a DVD. I have tried AviDemux (Append option there), but every time I append a VOB, it skips a little bit of the appended VOB's beginning, so that there is a noticable jump in the video at the append point.

Is there any other tool that supports the joining of VOB:s but does not introduce the jump I described above?

I have also read responses that suggest using cat command, but there are some suggestions that say that it corrupts video and/or audio data.

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by FakeOutdoorsman on 2011-11-14
Assuming all of your vob files contain the same number of video and audio streams and same formats you should at least try cat:
```
cat input1.vob input2.vob input3.vob > catoutput.vob
```
or
```
cat *.vob > catoutput.vob
```
If the output does not look correct you can try re-muxing the output from cat with FFmpeg:
```
ffmpeg -i catoutput.vob -vcodec copy -acodec copy output.vob
```

---

### Post by veroslav on 2011-11-15
Thank you for your quick response, I will have a go when I get back home from work.

Kind Regards,
Veroslav

---

### Post by veroslav on 2011-11-18
I just wanted to share how I managed to resolve the problem, so that others can benefit:

I found a Windows program called VobMerge (works perfectly in Wine) and used it to merge the VOB:s. It worked beautifully and there were no jumps afterwards that I described above.

After that I imported the merged VOB into AviDemux for editing, and made a DVD from the edited VOB:s in DeVeDe.

This will be my workflow for now, until AviDemux improves the VOB join feature.

Kind Regards,
Veroslav

---

