---
title: "M-Player does not seem to recognize Nvidia"
date: 2009-02-08
forum: Multimedia Software
---

### Post by drucer on 2009-02-08
Hello - could anybody help please. Just installed Ubuntu 8.10 and upgraded it with the latest upgrade packages so I should have up-to-date system here. Problem - MPlayer does not seem to be able to display video files - this happens with stock MPlayer Ubuntu package (installed with add/remove software functionality) and also when I tried to manually compile MPlayer from the source code.

I have a strong Linux background and usually I've been using "-vo xv" option to output video to my screen with Nvidia hardware acceleration.

I currently have a new video card - it's Club Nvidia 6200 AGP. Why can't I find "xv" output option on Mplayer? Why only these output options with this Nvidia card?

rasta@freedom:~$ mplayer -vo help
MPlayer SVN-r28470 (C) 2000-2007 MPlayer TeamCPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
Available video output drivers:
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	v4l2	V4L2 MPEG Video Decoder Output
	cvidix	console VIDIX
	null	Null video output
	mpegpes	MPEG-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame

rasta@freedom:~$

---

