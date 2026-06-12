---
title: "Color Problems video playback ubuntu intrepid"
date: 2008-11-07
forum: Multimedia Software
---

### Post by lhiggin on 2008-11-07
Hi all,

I installed intrepid no problems then installed ubuntu studio desktop and now my movies all have blue skin etc... uninstalled it and re installed ubuntu desktop only to find no change.  Have tried uninstalling all gstreamers and reinstalling them to no avail.  Any ideas.

Thanx Lonnie

Problem disappears when accelerated desktop is removed. However cant play alien arena without nvidia drivers using envyng to install nvidia drivers so is it the drivers or compiz thats the issue bet its the kernel any ideas how to mesh them to work together???

---

### Post by cor2y on 2008-11-07
IF your videocard/chipset is a latter (8XXX series and above) nvidia card and you are using the closed source nividia binary.
Edit the hue settings (Edit->Preferences->Display) in totem to either the max or minimum settings that should solve the problem if its a Nvidia card.
Its the driver not something in linux, something nvidia did.

---

### Post by Caseyjp on 2008-11-07
See this thread for more info on this annoying problem.
[http://www.nvnews.net/vbulletin/showthread.php?t=107009]("http://www.nvnews.net/vbulletin/showthread.php?t=107009")

So per the nvidia dev:   "He's right, it's not libXv's fault, it's a bug in either Totem or GStreamer."

---

### Post by cor2y on 2008-11-08
I would probably agree with that were it not for the fact the opennv drivers have no such problem.
This only happens using the closed binary blob from nvidia.
In another nvidia forum it was reported that nvidia themselves reversed the hue settings which is why all the trouble started.

---

### Post by sonicb00m on 2008-11-12
The hue bug seemed fix then another set of updates has broken it again.

If i just load the nvidia settings program the hue fixes automatically. It's odd.

---

