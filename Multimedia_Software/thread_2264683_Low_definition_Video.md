---
title: "Low definition Video"
date: 2015-02-09
forum: Multimedia Software
---

### Post by Robbyx on 2015-02-09
Are there any Ub programs that automatically enhance video definition? I am hoping someone knows of a program than I can run on a video file that will improve its quality and definition by applying some AI rules.

R

---

### Post by FakeOutdoorsman on 2015-02-09
Unfortunately you can't get a quality improvement from a crappy input, but you can apply some postprocessing to make it possibly more visually appealing. ffmpeg can do this with various [postprocessing filters](https://trac.ffmpeg.org/wiki/Postprocessing). Ubuntu however does not provide ffmpeg from FFmpeg anymore, but it will in a future release. Until then you can download a recent [static build](http://johnvansickle.com/ffmpeg/) and experiment.

If the filter is fast enough and your machine can handle it then you can use a recent ffplay to filter upon playback if you don't want to have to re-encode a file:
```
ffplay -vf "pp=hb/vb/dr/fq|8" input.mpg
```

Or if you do want to re-encode:
```
ffmpeg -i input.mpg -vf "pp=hb/vb/dr/fq|8" -c:v libx264 -crf 18 -preset fast -c:a copy output.mkv
```

I have no idea how slow the filtering may be. Some other players may also offer similar features but I'm unsure about that.

---

### Post by Robbyx on 2015-02-09
Thank you for replying. Some of the postprocessing output is obviously out of focus, but many of the others have left me unsure which is the best. Would you mind commenting upon which of the options give the best results? Part of my problem is that they did not provide a high def example with which to compare the outputs.

---

### Post by FakeOutdoorsman on 2015-02-09
I've actually never used it until I tested the command in my last post. You'll just have to experiment to see what works best with your input files and your eyes since it could be so subjective.

---

### Post by Robbyx on 2015-02-09
I will try it and see. Thank you very much for investigating the options for me. Much appreciated.

---

### Post by Rob Sayer on 2015-02-11
Yes, you can apply some filtering to make some low quality crappily encoded video work better.  But you need to know what you're doing.  There aren't any magic settings/filters that will work for all source videos.  That's true for encoding in general.

But no, there is no way to upscale SD to HD with good quality.  You can't just put in information that's not there.  I think you're vastly overrating AI here.

---

### Post by Robbyx on 2015-02-11
So the next best thing is to be able to preview the effect of different settings on a specific file using a gui. Do you know of such a gui?

---

### Post by FakeOutdoorsman on 2015-02-11
I think ffplay as shown above would be the easiest method. Anyway, I am unsure of a GUI.

---

