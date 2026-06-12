---
title: "How to check if there is an IRQ conflict? (sound problem)"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by AstarothCY on 2007-09-20
I have been having some sound problems, basically I was trying to configure a wireless USB module (ZyXEL G-260) and was listening to music on Amarok at the same time, and suddenly the sound became garbled and was the same in any app i tried. After a reboot there was no sound at all. I have tried every sound problem guide on this forum and reinstalled everything and YES i have checked the volume in alsamixer.

Someone in the ubuntu IRC chat room yesterday suggested that it may be an IRQ conflict between the sound card (SB Audigy) and the wireless module, and that the confilct could persist even if I uninstalled the drivers for the module and unplugged it. 

How do I check for an IRQ conflict, and if one is there, what can I do about it?

---

### Post by MrHippocampus on 2007-09-20
I found [this]("http://linux.about.com/od/gmr_howto/a/hwtgmr09t01.htm") page which tells you how to do it as well as other possible causes of problems with sound cards :)

---

### Post by AstarothCY on 2007-09-20
Thank you so much! Exactly what I was looking for, I will try this when I get home.

---

