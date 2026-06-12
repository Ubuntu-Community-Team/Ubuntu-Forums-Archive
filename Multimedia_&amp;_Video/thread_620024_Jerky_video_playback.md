---
title: "Jerky video playback"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by mgbridges on 2007-11-22
Hi,

I recently did a clean install of 7.10 64-bit version and I've been trying various things to install the ATI driver. I have an Asus M2a-VM HDMI motherboard which has ATi Radeon X1250 graphics on-board.

I'm not 100% sure that the driver installation has worked. The output from fglrxinfo is:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.0.6958 Release

Anyway, payback of any video files seems to be quite jerky. I'm viewing on a large LG plasma display connected to the DVI output from the motherboard.

Any ideas?

Martin

---

### Post by mdpalow on 2007-11-22
You mentioned new install, but didn't mention anything about installing these video playback files. Did you install the proper Codecs files for your 64-bit OS? 

If not, click link in my signature and see if that helps.

---

### Post by ze_otter on 2007-11-22
You might need to make sure your system uses Xvideo by doing "sudo aticonfig --ovt Xv" and restarting X. Doing that fixed the problems I had with jerky fullscreen video playback in Kaffeine.

---

### Post by mgbridges on 2007-11-22
Thanks folks - I've sorted it. I finally managed to do a clean install of the latest ATi video driver and that seems to have solved the problem.

Thanks for the various ssuggestions.

Martin

---

### Post by tuxmas on 2007-11-23
Hi,

what do you mean with installing the latest ati driver?
Catalyt 7.11 or 7.10 (8.42.3)?

With the 8.42.3 version of the driver I had no success in getting videooverlay working...

Regards

---

### Post by mgbridges on 2007-11-25
I installed 7.11.

I haven't tested all aspects of video performance, but the jerky playback of media files was my biggest concern and that seems to have been resolved.

Martin

---

