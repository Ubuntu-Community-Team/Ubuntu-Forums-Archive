---
title: "Change Metadata"
date: 2014-11-18
forum: Multimedia Software
---

### Post by rocky4 on 2014-11-18
Hello


I wanna change metadata without converting file. 
I only want change the title, i used mkvpropedit (only for mkv), but i want for .mp4, .avi and .mkv.


How can i do it?


Thanks

---

### Post by andrew.46 on 2014-11-19
EasyTag should be able to help you out with most of those...

---

### Post by rocky4 on 2014-11-19
Thanks for you reply.

EasyTag works with .avi?

Thanks!

---

### Post by FakeOutdoorsman on 2014-11-19
You can also use [ffmpeg](http://ffmpeg.org/download.html):
```
ffmpeg -i input -map 0 -c copy -metadata title="New Title" output
```
[list]
[*]**-map 0** will map all input streams to the output. Otherwise the default [stream selection](http://ffmpeg.org/ffmpeg.html#Stream-selection) will only map one stream per stream type (such as if your input has multiple audio streams).
[*]**-c copy** will [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) (re-mux) instead of re-encode.
[*]Ubuntu no longer provides ffmpeg from FFmpeg, but it will return maybe by 15.04, but you can [download](http://johnvansickle.com/ffmpeg/) or [compile](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu) it.
[/list]

---

### Post by andrew.46 on 2014-11-21
> **rocky4 said:**
> EasyTag works with .avi?

My apologies as not for the first time I am talking rubbish! EasyTag will open files in the mp4 container and tag them but primarily of course it is intended for audio file only tagging. It does not understand avi files or mkv files. My apologies again for posting rubbish, I have been concentrating too much on other things lately :(.

---

### Post by rocky4 on 2014-11-26
No problem.

Thanks for all.

---

