---
title: "Ibex 8.10 and RadeonHD 1.2.3?"
date: 2008-11-06
forum: Multimedia Software
---

### Post by zonyl on 2008-11-06
I have a Radeon 2600 HD which I would like to get working with Xvideo on my Ibex system.   The current Ibex ships with RadeonHD ver 1.2.1 and 1.2.2/3 have been released relatively recently with Xvideo support.

Does anyone know of a resource on the internet to install the newer RadeonHD drivers?  I tried to compile the GIT version without any success.

---

### Post by another_sam on 2008-11-16
try now [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) .

it was updated on 2008-11-14 (the last Friday).

---

### Post by zonyl on 2008-12-25
Thank you very much! I painlessly installed the binary package from the Volden PPA and Xvideo works great.  My Mythbuntu box is finally HDMI.

Now if only the audio was working on the card I could ditch the elaborate sound routing I have through my receiver.  Still futzing with that.

---

### Post by zonyl on 2008-12-26
Got audio working as well!  (Scared me to death when I finally got it working as I hadnt ever routed sound into my TV before and the volume was set at the MAX)

Had to create a xorg.conf file (was using the xorg configless before) containing just the following:


Section "Device"
  Identifier  "Radeon Driver"
  Driver  "radeonhd"
  Option  "Audio"  "on"
  Option  "HDMI"  "all"
EndSection

I thought Id never see the day when I would have Ubuntu playing Movies with HDMI w/audio at 1080p.  Thanks again for the link and to those who are working on the RadeonHD project!

---

### Post by zonyl on 2008-12-26
Sadly, while everything appeared to be working, I soon discovered that different resolution videos in Xvid caused the audio / video to be out of sync by several seconds.  Not sure how to resolve this one.

---

