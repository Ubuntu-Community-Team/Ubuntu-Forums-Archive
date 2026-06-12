---
title: "VLC cannot open TV capture device, but OK with channels.conf"
date: 2011-11-18
forum: Multimedia Software
---

### Post by jcoles on 2011-11-18
I can watch TV on my HVR-2250 card using "vlc channels.conf", but this method doesn't let me choose which of the card's two tuners I use. So, it's the same as having only a single tuner.

If I try to use vlc's Media > Open Capture Device function and specify /dev/video0, the result is "VLC is unable to open he MRL 'v4l2:///dev/video0'. Check the log for details." 

Not clear exactly which log is meant. Checked syslog, fixed a problem with encoder_buffers. Now syslog shows no relevant messages.

vlc console (started it from command line) shows:
[0x1f6b4f0] v4l2 demux error: cannot set standard (Invalid argument)
[0x1f6b4f0] v4l2 demux error: cannot set standard (Invalid argument)
[0x23f8f90] v4l2 access error: cannot set standard (Invalid argument)
[0x23f8f90] v4l2 access error: cannot set standard (Invalid argument)
[0x23eab80] main input error: open of `v4l2:///dev/video0' failed: (null)

The standard is ATSC_8_VSB. It must be supported as there's no problem viewing ATSC by running "vlc channels.conf", so what am I missing or doing wrong?

---

