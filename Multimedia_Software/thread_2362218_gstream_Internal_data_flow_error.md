---
title: "gstream Internal data flow error"
date: 2017-05-25
forum: Multimedia Software
---

### Post by swetha1234 on 2017-05-25
Hi,

Searched a lot on forums but I couldnt find solution.

I am trying to play an m4v video file, on an embedded system running customized Ubuntu software. but gstreamer jsut throws below error.
any mistake I am doing?



root@<>:~# gst-launch-1.0 -v filesrc location=/home/root/sample_iPod.m4v ! streamiddemux name=vpu.imx
Setting pipeline to PAUSED ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
ERROR: from element /GstPipeline:pipeline0/GstFileSrc:filesrc0: Internal data flow error.
Additional debug info:
/home/buildserver/Release_Workspace/R3_0_0/elina-orinoco-gclient/elina-distro/build_RC8_17193A/tmp/work/cortexa9hf-vfp-neon-elina-linux-gnueabi/gstreamer1.0/1.6.0-r0/gstreamer-1.6.0/libs/gst/base/gstbasesrc.c(2943): gst_base_src_loop (): /GstPipeline:pipeline0/GstFileSrc:filesrc0:
streaming task paused, reason not-linked (-1)
Execution ended after 0:00:00.001222333
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
Freeing pipeline ...
root@<>:~#

---

