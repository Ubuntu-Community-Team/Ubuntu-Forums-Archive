---
title: "Ubuntu on i.mx51"
date: 2010-01-20
forum: Multimedia Software
---

### Post by xin85 on 2010-01-20
hi all,

In ARM i.mx51 environment. With VLC player playing video(ITU H.264 20fps 640x480) display flicker madly , video output:X11. Flicker became more frequent on moving mouse, CPU reaches tip. However with freescale custom build image video display smoothly.
Any clue how to increase the video output performance? 

Best Regards & Thanks,
Xin

---

### Post by lmougen5 on 2010-03-09
No flicker on my i.mx515 after loading a few gstreamer codecs that utilize the hardware acceleration.  CPU is at around 5-15% during 720P video playback of h.264.  I'll try 640x480 this week to see if I have the same issue.

---

### Post by xin85 on 2010-07-02
Could you please give me an idea what packages of gstreamer you installed to get it running?
I installed the following packages:

imx-lib_09.12.00-1_armel.deb

amd-gpu-x11-bin-mx51_09.12.00-1_armel.deb

imx-test_09.12.00-1_armel.deb

kernel_2.6.31-imx_09.12.00_armel.deb

libz160-bin_09.12.00-2_armel.deb

modeps_09.12.00-1_armel.deb

xserver-xorg-video-imx_09.12.00-2_armel.deb

libfsl-mm-core1

libgst-fsl-mm-plugins

libgstreamer-plugins-base0.10-0

gstreamer0.10-plugins-base

gstreamer0.10-plugins-good

totem-plugins

However the OS overload and stall when I play video. Following are the error messages:

 

#gst-launch playbin uri=file:///home/mch/Video/test.avi

(gst-launch-0.10:1568): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gs
treamer-0.10/libmfw_gst_ac3dec.so': lib_ac3_dec_arm11_elinux.so: cannot open sha
red object file: No such file or directory

(gst-launch-0.10:1568): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gs
treamer-0.10/libmfw_gst_radec.so': lib_realaudio_dec_arm11_elinux.so: cannot ope
n shared object file: No such file or directory

(gst-launch-0.10:1568): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gs
treamer-0.10/libmfw_gst_rmdemuxer_plugin.so': lib_rm_parser_arm11_elinux.so: can
not open shared object file: No such file or directory

(gst-launch-0.10:1567): GLib-WARNING **: g_set_prgname() called multiple times

=system stall= 

 

Any hints will be greatly appreciated

---

