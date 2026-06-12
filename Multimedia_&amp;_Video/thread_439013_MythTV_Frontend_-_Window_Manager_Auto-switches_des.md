---
title: "MythTV Frontend - Window Manager Auto-switches desktops"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by dmfrey on 2007-05-10
I have two Myth boxes setup.  The backend sits in a back room and the Frontend sits in the entertainment center.  They are both running Feisty and were setup using the community docs [Here]("https://help.ubuntu.com/community/MythTV_Feisty").

The issue I am having is, periodically, when the TV has been off for some time, the OpenBox WM decides to auto-switch the desktop.  When I turn the TV on again, a secondary desktop is displayed with the MythTV logo displayed.

Here are a few questions:
1. Is it possible in OpenBox to only load 1 desktop?
2. If no, is there any workaround to prevent the WM from automatically switching desktops?

I would also like to know if anyone has run into this issue?

Thanks

---

### Post by urukrama on 2007-05-12
I think it should be possbile to use only one desktop with Openbox. Haven't tried it, but you could change the number of dekstops through Obconf, or by manually editing the rc.xml file in /home/USERNAME/.config/openbox/ 

I've never encountered Openbox changing desktops automatically. Strange. I've never used MythTV either, though.

---

