---
title: "Fresh install - no component tv out"
date: 2011-03-22
forum: Mythbuntu
---

### Post by knp54 on 2011-03-22
All right, so, I downloaded Mythbuntu 10.10, burned it to a CD, and installed it on my previous computer.

After  answering a few basic questions, I have to chose between the Open  source or the ATI graphic card driver. Since the Open source driver did  not let me chose tv-out as an option, I chose the ATI driver which lets  me select Component output in HD480i.

Once the installation  process finished, I unplugged the box, moved it into the living room,  plugged it to my TV, and boot it up. Mythbuntu boots fine (I think!),  but I don't get any picture.

What did I do wrong?

Please  note that the connection between the TV and computer is fine, I  previously tested the component tv-out with windows 7 right before I  formatted the drive and installed Mythbuntu.

Here are my specs:

cpu: Amd Athlon X2 6400+ downclocked to 2.6ghz (I want to keep that system cool)
mobo: Asus M2NBP-VM CSM
ram: 4 sticks of Corsair 1GB DDR2 (4GB total)
video card: ATI Radeon X700 Pro (from ATI) PCIe 16x
tuner: Haupaugge HVR-1250 PCIe 1x with remote control
network: Trendnet TEW-423PI PCI wireless card
hdd1: Maxtor 120GB ide
hdd2: Western Digital 200GB ide
optical: LG dvd-rw ide

---

### Post by uteck on 2011-04-05
The system probably detected your monitor and configured the display to use that and not the TV out.  
If the system has /etc/X11/xorg.conf, try adding *[COLOR="Lime"]Option         "TVOutFormat" "COMPONENT"[/COLOR]* to the "Device" section.
If that does not do it, the try removing xorg.conf and restarting so it re-detects the display.

---

