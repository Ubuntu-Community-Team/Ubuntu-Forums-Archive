---
title: "Video Capturing Software"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by BnetTheAwesome on 2007-08-21
I'm trying to capture video from a webcam and I've tried most everything (Kino, XawTV etc) and nothing works. I'm trying to start a show on blip.tv and any help would be good.

---

### Post by dabl on 2007-08-21
First, make sure your webcam is recognized correctly in the hardware.  In the console, enter ```
lsusb
``` and see if it appears on the list.

Assuming it looks correct on your list of USB devices, the simplest webcam package is camorama, to simply show the stream, or to capture single frames.  vlc might or might not work -- I haven't tried it with my webcam, but it should build an mpg file for you, if that's what you want to do.  :)

---

### Post by mattbarlow on 2007-08-21
Did you try mencoder?

$> mencoder tv:// -tv driver=v4l:device=/dev/video0:width=640:height=480:forceaudio -ovc lavc -oac lavc -lavcopts vcodec=mpeg4:acodec=mp3 -ffourcc divx -o output.avi

You can stop it with Ctrl-C.

$> mplayer output.avi to see what you recorded.

Of course you must make sure your webcam is recognised by your kernel first. That is, find which driver supports your camera, and then

#> modprobe <driver name>

---

