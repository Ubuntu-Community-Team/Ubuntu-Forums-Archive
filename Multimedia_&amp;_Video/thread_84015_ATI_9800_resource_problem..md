---
title: "ATI 9800 resource problem."
date: 2005-10-30
forum: Multimedia &amp; Video
---

### Post by sdo on 2005-10-30
Hi all.
My problem is with my 9800 pro 256MB
I was getting very poor dvd playback performance so i followed mlomker's instructions from here [http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378) to the letter.
The drivers are working, sort of, as you can see from below the fglrx driver is installed fine, and I get very good fps from glxgears.

fglrxinfo:
shado@kubuntu:/etc/X11$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

glxgears -iacknowledgethatthistoolisnotabenchmark:
shado@kubuntu:/etc/X11$ glxgears -iacknowledgethatthistoolisnotabenchmark
23538 frames in 5.0 seconds = 4707.580 FPS
22532 frames in 5.0 seconds = 4506.251 FPS
31449 frames in 5.0 seconds = 6289.679 FPS
40831 frames in 5.0 seconds = 8166.155 FPS
40938 frames in 5.0 seconds = 8187.411 FPS
40917 frames in 5.0 seconds = 8183.277 FPS
40968 frames in 5.0 seconds = 8193.489 FPS


The problem comes when I try to play any kind of video file.. these are the errors I get from MPlayer & Kaffeine:

MPlayer:
Error opening/initializing the selected video_out (-vo) device.

Kaffeine:
Resource busy or not available.
(Details)
xvimagesink.c(740): gst_xvimagesink_get_xv_support: /internal_thread/thread_textbin/textbin/vbin/videosink:
No port available

When running dpkg-reconfigure xserver-xorg I went with all the defaults, except the driver, obviously.

Anyone able to shed some light on the problem?

Thanks in advance,

sdo

edit: I gues I should mention that I'm using Kubuntu 5.10 ;)

---

