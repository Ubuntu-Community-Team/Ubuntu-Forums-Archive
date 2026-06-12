---
title: "ffmpeg x11grab capture freezing. Any idea why?"
date: 2014-06-05
forum: Multimedia Software
---

### Post by tsh206 on 2014-06-05
Hi Guys,

I've been having this unsolvable issue with screen capture via x11grab on 12.04. The source is running at 60fps and here is my ffmpeg capture command: "ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x720 -i :0.0+nomouse -vcodec libx264 -crf 18 -vsync 0 -threads 0 -pix_fmt yuv420p -f mp4 #{@filename}"

Keeps happening and I have no idea why. Also seems to be happening at the same spot. I tried capturing at 60fps same issue. tried with -framerate 60 and same issue.

Anybody else faced the same problem, any solution?

Any help would be greatly appreciated, I've been stuck on this one for a while.

Thanks!

---

### Post by FakeOutdoorsman on 2014-06-06
Please include the complete ffmpeg console output that results from your command.

---

### Post by tsh206 on 2014-06-06
Attached log file.

Thanks!

---

### Post by FakeOutdoorsman on 2014-06-06
Thanks for the output, although increasing the loglevel verbosity actually makes it harder to find issues. Also, I forgot to ask, what is the actual issue?

---

### Post by tsh206 on 2014-06-08
Let me know if there is a way to reduce the verbosity in the log, will regenerate one. The issue I'm seeing screen freezes when the capture is happening on a GPU instance, though I don't see the same issue on a CPU instance that lacks a GPU but has more CPU cores. I doubt this is a performance issue as the GPU should be more than powerful for the capture.

Any ideas?

---

### Post by FakeOutdoorsman on 2014-06-08
I'm not sure why it was so verbose because I didn't see -loglevel or -v being used. "-loglevel info" is the default.

ffmpeg does not use the GPU for capturing.

Does it make a difference if you replace "-r 30" with "-framerate 30"? Does the freezing occur if you reduce the capture size? Change "-s 1280x720" to "-video_size 640x360" just to test.

Are you sure it is not the output file itself that is being jerky due to playback issues and not due to the actual capturing or encoding?

---

### Post by tsh206 on 2014-06-08
Tried the -framerate 30 change already didn't change much. The video size change either. I am also sure it is not my output file as I have captured dozens of files this way. Do you think any of the settings that have in there might have a performance hit on the capture? I appreciate your help on this.

---

### Post by FakeOutdoorsman on 2014-06-09
Things you could try/test:

[list]
[*]Use a recent build ([re-compile ffmpeg](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu) and x264 using source from git head).
[*]Omit audio.
[*]Try without "-vsync 0".
[*]Try a faster encoder: ```
-i :0.0+nomouse -vcodec libx264 -preset ultrafast -qp 0 output.mp4
```
[/list]

---

