---
title: "Help with 64-bit desktop Gutsy and NVidia drivers"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by scottsre on 2008-03-06
I just installed a 64-bit version of Gutsy on a system with an NVidia Quadro FX 3450/4000 DVI card, with both ports being used by LCD displays via DVI cables.

I obtained the special nvidia restricted kernel via apt-get, and both monitors are properly showing video at their highest resolution, with a desktop that spans across them.

The problems:

- Upon reboot, some video customizations, including resolution settings, seem to get reset to defaults

- I can't figure out how to tell the system, when expanding a window to full/ maximum view, to not span across both monitors, but instead, expand in just the monitor it is in.  This is how the NVidia driver (from Nvidia's site) works under CentOS with the similar setup.

Thanks for any leads/help.

Scott

---

### Post by iansane on 2008-03-23
I had same problem with restoring to default after using envy to install the nvidia driver. Removed it and went back to using the ubuntu restricted driver and problem persists. Never had problem with 32 bit. Maybe it's a problem with 64 bit driver?

---

