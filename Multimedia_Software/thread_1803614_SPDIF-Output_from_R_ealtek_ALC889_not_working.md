---
title: "S/PDIF-Output from R ealtek ALC889 not working"
date: 2011-07-13
forum: Multimedia Software
---

### Post by QNo on 2011-07-13
Hi all,

Mainboard is a Gigabyte GA-790FXTA-UD5, Audio Chip is shown by alsamixer as HDA-Intel - HDA ATI SB, Realtek ALC889. Analog Audio is working fine. Now i tried to use the digital output. And it did not work. AVR and cable are working fine.

Software is Ubuntu 11.04.

TIA
Chris

---

### Post by lidex on 2011-07-14
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=6stack-dig" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Now use alsamixer to enable (unmute) spdif.
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

