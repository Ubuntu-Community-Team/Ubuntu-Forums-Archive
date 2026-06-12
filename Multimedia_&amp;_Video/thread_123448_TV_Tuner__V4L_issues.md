---
title: "TV Tuner / V4L issues"
date: 2006-01-30
forum: Multimedia &amp; Video
---

### Post by ThorPrime on 2006-01-30
I'm having issues with V4L and my TV Tuner card.
I havea winfast 2000 tuner, Nvidia GeForce 6600GT.

The setup worked initially in TVTime, but at some point, it just stopped.
I've tried re-installing TVTime, V4L, Nvidia Drivers, bit it doesn't seem to help.

Here are some of the errors various programs give me.

** (zapping:12301): WARNING **: GConf key '/apps/zapping/plugins/deinterlace/method' is unset and has no default. Schemas incomplete or not installed?

(C) 2000-2004 Iñaki G. Etxebarria, Michael H. Schimek.
This program is freely redistributable under the terms
of the GNU General Public License.

Using video device '/dev/video0', display ':0.0', screen 0.
Querying frame buffer parameters from X server.
DMA not possible on screen 0.
Setup failed. Try -vv for details.

This is xawtv-3.94, running on Linux/i686 (2.6.12-9-386)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
Xlib:  extension "GLX" missing on display ":0.0".
station "next" not found
v4l2: read: Input/output error

TvTime doesn't give an error, it just displays it's big blue screen, even as the audio plays back fine.

and finally, here is the top of my V4l-info dump:
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
	driver                  : "bttv"
	card                    : "BT878 video (Leadtek WinFast 20"
	bus_info                : "PCI:0000:01:07.0"
	version                 : 0.9.15
	capabilities            : 0x5010015 [VIDEO_CAPTURE,VIDEO_OVERLAY,VBI_CAPTURE,TUNER,READWRITE,STREAMING]



Anyone got any ideas?

---

