---
title: "Building ALSA"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by kiplingw on 2006-08-05
So I've checked the change log for 1.0.12rc2 and my card has *FINALLY* been implemented. Up until now, it was using the wrong chipset (ALC882 instead of ALC883). My sound works, just not out the back speakers.

Anyways, my Ubuntu 6.06 system comes with ALSA 1.0.10 prebuilt, already configured, and good to go (though with the ALC882). I want to build the newer ALSA now. I know how to build it for my card, as I have done it before, but I am afraid I might screw something up with Ubuntu's currently working installation.

Is there anything I should know first before I build it? Should I simply run make uninstall for driver, library, and utilities after configuring? Would that be sufficient for safely removing the old installation and not screw anything up?

Kip

---

