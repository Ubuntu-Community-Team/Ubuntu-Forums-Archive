---
title: "OpenCL with avconv, MLT, KDEnLive?"
date: 2014-08-02
forum: Multimedia Software
---

### Post by sgofferj on 2014-08-02
So I got myself a shiny new workstation for video editing with a Core I7, 32GB RAM and an Nvidia GTX770 (plus an additional GTX560) and changed from Opensuse to kubuntu, just to find out that my workflow with KDEnLive is as lame as on my shabby old Phenom2 machine. Well, the final rendering is a bit faster, but first and foremost, KDEnLive struggles heavily to display AVCHD files and if you apply even simple filters or transistions, it stutters badly. That should look quite different! If I activate OpenGL playback, it gets even worse.
After some testing, I'm fairly convinced that libav and MLT (which KDEnLive bases the playback and effects on) do not utilize OpenGL/OpenCL properly although they should - in theory. Unless, of course, the Ubuntu packages are compiled with OpenCL disabled. OpenCL is set up properly on the system and e.g. darktable uses it without problems.

Can anybody provide some insight into this matter?

---

### Post by FakeOutdoorsman on 2014-08-02
Does Kdenlive struggle with a different format? You can try a lossless intermediate that may be easier on the editor, but file size may be huge:
```
ffmpeg -i input -c:v utvideo -c:a pcm_s16le output.mkv
```
If it doesn't like utvideo try huffyuv.
If it doesn't like mkv try avi.

This command is for ffmpeg (from FFmpeg), which unfortunately Ubuntu no longer uses (but a return may be "soon"). You can get a static build to test with via the [FFmpeg Download](https://ffmpeg.org/download.html) page.

---

### Post by sgofferj on 2014-08-02
I am already transcoding all input material to DNxHD - which uses about 2GB per minute (!)... With that, it works fairly fluent but also, when I add a couple of filters - typically tone curve and such for grading - it starts stuttering at some point. All signs of absent hardware acceleration.
Shotcut (the new editor from the MLT project) e.g. is ragingly fast but unfortunetaly, it's in a rather early development stage and yet missing a number of essential filters and effects.

---

