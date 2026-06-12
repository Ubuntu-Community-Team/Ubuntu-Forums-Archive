---
title: "Query about viewing on an LCD TV"
date: 2007-11-05
forum: Mythbuntu
---

### Post by JustInterested on 2007-11-05
Hi hope someone can steer me in the right direction...

Currently I'm using my PC LCD monitor to watch TV (BenQ FP17E+) but I want to attach it to the lounge TV - a Panasonic 32" LCD TV.

Do I need to do anything special (e.g. change xorg file, other files or MythTV setup) to attach to the TV? TV runs at 1366 x 768 native resolution but LCD monitor is 1024 x 720... 

I can use either the VGA/D-SUB on back of TV or maybe get a DVI-to-HDMI to connect.

Some advice?

Thanks in advance!

---

### Post by superm1 on 2007-11-05
That all depends on how you configured the LCD in the first place, what connections you used etc.

If you installed the nvidia driver from the installer at the beginning, switching over to vga or dvi/hdmi on the tv should be no issue.  If you installed it post install, you may need to modify your xorg.conf to add the right resolution or at least "nvidia-auto-select"

---

### Post by JustInterested on 2007-11-05
Yep I selected the nvidia driver when I installed (with MythBuntu 7.10) and had LCD connected via DVI.

Will the nvidia driver automatically select the best possible resolution (i.e. closest to 1366 x 768 ) or revert to 1024 x 720?

I'm going to try it today just to see how it goes.

Thanks for the info and I'll report back to this thread with results hopefully a good one.

cheers
:grin:

---

### Post by superm1 on 2007-11-05
All depends on your TV and how well it spits out EDID info.

---

