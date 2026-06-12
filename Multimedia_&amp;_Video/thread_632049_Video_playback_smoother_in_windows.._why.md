---
title: "Video playback smoother in windows.. why?"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by lian1238 on 2007-12-05
Hi
When I play vidoes in Ubuntu, VLC, totem movie player, every player I use, there is an apparent line going diagonally from upper-left corner to lower-right corner. It's not a real "line" that always shows. The line can be seen during fast scenes, as the screen refreshes.

In Windows, I don't see this line at all; the video is very smooth.

How can I make video playback as smooth as in Windows?
This is a laptop with nvidia.

---

### Post by eye208 on 2007-12-05
Smooth video playback without frame tearing requires a graphics driver with XVideo extension. Make sure the Nvidia driver is installed and the playback application is using XVideo instead of OpenGL or X11 output.

(Most players use XVideo by default when available.)

---

### Post by lian1238 on 2007-12-05
> **eye208 said:**
> Smooth video playback without frame tearing requires a graphics driver with XVideo extension. Make sure the Nvidia driver is installed and the playback application is using XVideo instead of OpenGL or X11 output.

(Most players use XVideo by default when available.)

I'm using VLC with the XVideo extension. With OpenGL, it'll just close on playback. With X11, the image is pixelated on fullscreen or any size bigger than the actual size.

I also have XGL installed. Is that affecting the video playback?

---

### Post by shirilover on 2007-12-05
Yes, it is high likely that XGL or a compositing desktop(desktop effects) is affecting your video playback.
If you wish video playback to be smooth, you will likely need to disable XGL.

---

### Post by pinow on 2007-12-18
> **shirilover said:**
> Yes, it is high likely that XGL or a compositing desktop(desktop effects) is affecting your video playback.
If you wish video playback to be smooth, you will likely need to disable XGL.
So this means I'll have to disable compiz to watch my vids properly? :confused:

---

### Post by pinow on 2007-12-24
> **pinow said:**
> So this means I'll have to disable compiz to watch my vids properly? :confused:
Bump..

---

