---
title: "Dell Dimension L800r Graphics problems"
date: 2009-09-09
forum: Multimedia Software
---

### Post by sloppyc on 2009-09-09
I've just installed Ubuntu 9.04 Jaunty on this machine, got WiFi up and running, only problem:  graphics.  

It is odd, when I installed, it was connected via a KVM switch to a different monitor (and key/mouse, of course) and everything was great; 1600x1200 resolution (same as the resolution on the other PC connected to the switch, for what it's worth), window borders and everything were present... now that I don't need the Ethernet connection I've moved the PC outdoors where it connects via WiFi.

No window borders, when I load a terminal it's blank, can't choose a resolution higher than 1024x768... I'd like to blame a lack of proper drivers, but am thrown off by its good behaviour whilst connected to the KVM.

I don't have a PCI video card to throw in to test aside from an old 4MB Matrox card that's probably worse than whatever integrated graphics came with this box.

xorg.conf is pretty sparse and a "dpkg-reconfigure -phigh xorg.xserver" didn't help, either.

Suggestions?  I'm 99% sure it's an Intel chipset, being a PIII Dell board.


EDIT:  Stupid me didn't see the giant sticky thread at the top.  It's probably related.  Still, I'm confused as to why it worked before, while connected to the other monitor through the KVM.

---

### Post by sloppyc on 2009-09-13
Meh, went with the old Matrox Millennium II card.  It displays at the resolutions I like, but MAME ROMs only play in a tiny window instead of fullscreen.  I suppose a better (Nvidia) PCI card may be the way to go.

---

