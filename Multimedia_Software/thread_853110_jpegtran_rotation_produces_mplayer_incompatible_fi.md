---
title: "jpegtran rotation produces mplayer incompatible files"
date: 2008-07-08
forum: Multimedia Software
---

### Post by danielsbrewer on 2008-07-08
A bit of background.  My digital camera produces video in the MJPEG format which is basically a series of jpegs embedded in an avi.  I want to rotate some of these videos from landscape to portrait WITHOUT losing quality.  I am getting somewhere using [http://pieleric.free.fr/junk/mjpgrot](http://pieleric.free.fr/junk/mjpgrot) and the almara tools, which converts the video to jpegs, rotates using jpegtrans, then recompiles them.

The resulting movie cannot not be played by mplayer. I have isolated the problem to jpegtrans, which when rotating seems to strip the colourspace information. This is the output when mplayer "plays" the rotated images:

VDec: vo config request - 480 x 640 (preferred colorspace: Unknown 0x0000)
[PP] Using external postprocessing filter, max q = 6.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.

Compared to the unrotated:
VDec: vo config request - 640 x 480 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)

Any ideas how I can fix this colorspace issue?

Thanks

---

