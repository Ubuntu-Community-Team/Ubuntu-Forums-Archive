---
title: "X no longer works after moving graphics card to another pci-e slot [NVIDIA Quadro FX]"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by x37v on 2007-08-21
Hi, so I have an NVidia Quadro FX 5600 graphics card and an HP xw9300 workstation.  I had this card installed in one of the PCI-e slots (x16), but then i needed to move it in order to add a PCI audio card [and there is only 1 PCI slot.. the NVidia card is 2 slots wide so in the one PCI-e slot it covers the only PCI slot.  So I moved the NVidia card to this other PCI-e (x16) slot but now i cannot get X to start.

I've attached my xorg.conf, Xorg.0.log and the output of lspci.

It seems that the card isn't being seen in this slot.  I can run X with the vesa driver, and it works, but I really need to run the proprietary nvidia driver [because I'm doing active stereo graphics, and i have a very new card].

Advice?
-Alex

---

### Post by ddrichardson on 2007-08-21
[Here]("http://ubuntuforums.org/showthread.php?t=510742")

---

### Post by w4ett on 2007-08-21
> **x37v said:**
> Hi, so I have an NVidia Quadro FX 5600 graphics card and an HP xw9300 workstation.  I had this card installed in one of the PCI-e slots (x16), but then i needed to move it in order to add a PCI audio card [and there is only 1 PCI slot.. the NVidia card is 2 slots wide so in the one PCI-e slot it covers the only PCI slot.  So I moved the NVidia card to this other PCI-e (x16) slot but now i cannot get X to start.

I've attached my xorg.conf, Xorg.0.log and the output of lspci.

It seems that the card isn't being seen in this slot.  I can run X with the vesa driver, and it works, but I really need to run the proprietary nvidia driver [because I'm doing active stereo graphics, and i have a very new card].

Advice?
-Alex

When you reconfigure xserver-xorg.conf, does the configurator pick up any PCI bus address?.or does it just leave the bus ID blank?...I don't see the card listed in your lspci.

---

### Post by x37v on 2007-10-08
it picks up a bus but if i leave the bus entry in there PCI:0:5:0 then X won't start, if i take it out, when using the vesa driver, i can start X, but i need to use the nvidia proprietary driver as we're doing active stereo, etc.

-Alex

---

