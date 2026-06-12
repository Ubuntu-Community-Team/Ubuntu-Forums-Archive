---
title: "Not Recoginzing Tuner Card"
date: 2008-07-23
forum: Mythbuntu
---

### Post by Bballen023 on 2008-07-23
When i go into the backend to setup my capture card on my mythbuntubox it says under Probe info: failed to open. Any suggestions on how to fix this so i can set up my tuner card? Btw it's a PVR-350

---

### Post by jaakan on 2008-07-23
[EDIT] look here [http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card)

---

### Post by SiHa on 2008-07-24
I found that Mythtv was picky about what was on the PCI bus when detecting my cards. I have a WinTV single tuner, a NovaT-500, and an nVidia PCI-E card for the TV-out. In order for them to be detected properly, I had to add them in this order:

Install Ubuntu + Mythtv, use crappy ATI integrated graphics WITHOUT the restricted drivers

WinTV in PCI Slot 1
Run backend setup, add capture card 0 and setup video surce, input connection & channels.

Nova-T 500 in Slot 2
Run backend setup again and add cards 1 & 2.

Install PCI-E card
Enable restricted drivers for nVidia.

I imagine it's all down to them sharing an interrupt. I excpect I could have assigned different IRQ's n the BIOS, but this seemed a simpler option.

HTH,

Simon

---

### Post by jaakan on 2008-07-24
make sure your install is up to date.

My card didn't show up until after I updated everything.

[http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-350](http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-350)

---

