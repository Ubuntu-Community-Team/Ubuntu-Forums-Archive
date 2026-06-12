---
title: "gxine crashes after enabling dvd support"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by suxen on 2007-03-04
hardware: hp-compaq  nx6125 amd64 turion
distro: xubuntu 6.10

i used gxine to watch videos, among others mpeg and avi files, 
and it all worked fine until i recently enabled dvd playback following the howto at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats),

In particular i installed lbdvdcss2 and also 
gstreamer0.10-pitfdll 
gstreamer0.10-ffmpeg 
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-bad-multiverse 
gstreamer0.10-plugins-ugly 
gstreamer0.10-plugins-ugly-multiverse 
gxine libxine-main1 
libxine-extracodecs 

 as was suggested on that page.

now my box ran dvds but gxine crashes when attempting to open one of those avi or mpeg files it used to eat ever before without complaining. 

from

>gxine --verbose example_of_avi_file.avi 

i get the following output 

load_plugins: plugin /usr/lib/xine/plugins/1.1.2/post/xineplug_post_planar.so found
(some more lines of type
load plugins: plugin /path/to/plugin.so found)
...
...
then:

audio_alsa_out : supported modes are 8bit 16bit 24bit 32bit mono stereo (4-channel not enabled in xine config) (4.1-channel not enabled in xine config) (5-channel not enabled in xine config) (5.1-channel not enabled in xine config) (a/52 and DTS pass-through not enabled in xine config)
engine: > executing &#8216;if (__js.v != 1) callback ('widget.__js.wi.set_show (false)');&#8217;...
engine: > executing &#8216;if ((__js.v & ~1) != 2) callback ('widget.__js.wq.set_show (false)');&#8217;...
engine: > executing &#8216;if ((__js.v & ~3) != 4) callback ('widget.__js.ww.set_show (false)');&#8217;...
engine: > executing &#8216;if ((__js.v & ~7) != 8) callback ('widget.__js.we.set_show (false)');&#8217;...
video_out_dxr3: Failed to open control device /dev/em8300-0 (No such file or directory)
video_out_xv: using Xv port 65 from adaptor ATI Radeon Video Overlay for hardware colorspace conversion and scaling.
video_out_xv: this adaptor supports the yuy2 format.
video_out_xv: this adaptor supports the yv12 format.

(gxine:8002): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
video_out_xv: VO_PROP_INTERLACED(0)
video_out_xv: VO_PROP_INTERLACED(0)
video_out_xv: VO_PROP_INTERLACED(0)
video_out_xv: VO_PROP_INTERLACED(0)
video_out_xv: VO_PROP_INTERLACED(0)
video_out_xv: VO_PROP_INTERLACED(0)
CDROMREADTOCHDR: Input/output error
Segmentation fault (core dumped)

That was it.

Can anyone help me?

suxen

---

### Post by madanglian on 2007-03-14
The line:

video_out_dxr3: Failed to open control device /dev/em8300-0 (No such file or directory)

indicates that it expects you to have a Hollywood Plus or DXR3 Hardware DVD decoder card.
If you haven't, that could be the reason it's crashing.
There's probably some setup file you need to edit but I haven't got the experience to tell you which one it is.
HTH
madanglian

---

### Post by suxen on 2007-03-19
madanglian,
thank you for the reply.

but as i said, the problem is not with dvd-playback, its with playing any other video
format, like e.g. mpeg4.

---

