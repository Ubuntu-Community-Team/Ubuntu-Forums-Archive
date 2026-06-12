---
title: "Blank screen after closing Mplayer."
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by Alex Carroll on 2007-12-26
When opening a video in Mplayer (I use the KMplayer GUI) I am able to watch the video, but when I close the window, my screen will turn black temporarily, then return to normal, just like it is changing resolution. This also happens when opening and closing a video with the Mplayer Firefox Plugin.

I've recently bought a new widescreen monitor and had to reconfigure xorg.conf using the "sudo dpkg-reconfigure xserver-xorg" command to get the resolution and refresh rate that I needed. I had no problems before this.

I am using the latest (I think) flgrx ATi driver, installed for me by Envy and am running Gutsy 7.10 64-bit. No changes were made to the drivers either before or after the monitor's installation.

Thanks for any help.

---

### Post by anubhavrocks on 2007-12-26
Try changing the Video Out device

---

### Post by Alex Carroll on 2007-12-27
I changed the video driver to OpenGL and that fixed it. Thanks for your help.

---

