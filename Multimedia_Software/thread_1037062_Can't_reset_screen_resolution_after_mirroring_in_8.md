---
title: "Can't reset screen resolution after mirroring in 8.10"
date: 2009-01-11
forum: Multimedia Software
---

### Post by Liver4ever on 2009-01-11
I have an old laptop, HP-NX7010 with an ATI Mobility Radeon 9200 graphix card. Running Ubuntu 8.10.

The native resolution of my laptop screen is 1680x1050, wich was working just fine after install, and looked good. Then I tried mirroring monitors, using an external monitor with a resolution of 1280x1024. 

Doing this, Ubuntu changed the resolution of my laptop to 1280x1024, and now i can't change back to what I used to have. In the screen resolution options there are several resolutions to choose from, but they either screw up the video or just look crappy. 1680x1050 just isn't there. The closest I get is 1600x1024, which doesn't really work.

What can I do? I know the resolution I want works, because it was there to begin with.

Any suggestions?

**Edit:**
OK, I figured this one out for myself. After some research I found out about the xorg.conf-file. It turned out Ubuntu had changed it, but also created a backup of the original file.

I just exchanged the new xorg.conf with the original, and hey presto, the right resolutions appeared like magic. Had to do a reboot to make it look right though.

---

