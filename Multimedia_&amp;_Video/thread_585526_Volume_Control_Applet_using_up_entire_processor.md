---
title: "Volume Control Applet using up entire processor"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Mais on 2007-10-21
Hi all! Loving the new Gibbon except for one minor issue.

I use a Logitech headset for audio and don't have any sound cards installed. The volume control acts a bit funny when using it, but the issues are minor and it is still very usable. 

However, I was experiencing a very noticeable performance hitch using the Shift-Switcher in Compiz-Fusion. My system is much beyond qualified for such effects so I opened up the System Monitor. Turns out the Volume Control Applet on the gnome-panel was using 50% of the CPU power. I have a dual-core system so I am assuming that it's using 100% of what it is given by the scheduler.

Does anyone have any suggestions on how to fix this? The problem goes away only when removing the applet, not by removing the USB Headphones and comes back as soon as I re add the applet.

---

### Post by Mais on 2007-10-22
Ok, so for now the command line alsamixer is working just fine. Though if anyone has any idea how I could get a volume applet back I would love to know!

---

