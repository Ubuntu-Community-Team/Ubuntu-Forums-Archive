---
title: "pvr-usb2 vs pvr-350 panning and motion recording quality"
date: 2008-06-20
forum: Mythbuntu
---

### Post by danbodoh on 2008-06-20
I've recently upgraded my mythtv hardware, and moved from the Hauppauge PVR-350 to the PVR-USB2.

I've noticed that for the same bitrate (4500/6000 peak), recordings from the new PVR-USB2 has poorer quality than recordings from the PVR-350 (both displayed on my new hardware).

The difference occurs during slow panning scenes.  On the PVR-USB2 recording, the panning pauses, or jerks, several times each second.  The PVR-350 recordings might have some pause, but it is very hard to detect.

Anyone have any ideas why, and how I can correct this?  Is there a hardware difference in the MPEG encoder?  Perhaps the VBR algorithm in the PVR-USB2 too easily reduces the bitrate?  Does the pvrusb2 driver have different defaults than the ivtv driver?  

I've been experimenting with higher bitrates, which seem to alleviate the problem at the expense of more disk space.

Dan Bodoh

---

### Post by danbodoh on 2008-06-22
*Edit: Well, this panning and motion problem still exists, even with the workaround below.  Note that the workaround referenced below does fix other issues, however.*

I believe that I have found the solution.  See the separate thread [http://ubuntuforums.org/showthread.php?t=837607](http://ubuntuforums.org/showthread.php?t=837607)

Dan Bodoh

---

