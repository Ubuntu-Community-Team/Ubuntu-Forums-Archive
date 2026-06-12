---
title: "Intel HDA no sound - guide tried"
date: 2009-05-19
forum: Multimedia Software
---

### Post by nwwoods on 2009-05-19
Jaunty fresh install on an Asus P5E.  Intel HDA is built-in on this motherboard.  Connections run from both the coaxial digital output and the optical digital output.  Per the guide:

1.  aplay -l says no soundcards found.
2.  lspci -v shows the Intel HD Audio device, & lists driver snd-hda-intel.
3.  driver confirmed on alsa-project.org.
4.  sudo modprobe snd-hda-intel gives only the warning about filename extensions not .conf will be ignored in the future (so the driver is loaded).
     snd-hda-intel added to the end of /etc/modules.
     snd-hda-intel also added to /etc/modprobe.d/alsa-base.conf.
5.  alsamixer says no such file or directory (ie it thinks nothing is loaded).  aplay -l still insists that no soundcards exist.
6.  remove/reinstall seems inappropriate since this is a clean install.

Other --
verified the HD Audio is enabled in the bios.
lsmod shows snd-hda-intel and all dependent modules as well.

??? help please.

---

### Post by nwwoods on 2009-05-21
bump

---

