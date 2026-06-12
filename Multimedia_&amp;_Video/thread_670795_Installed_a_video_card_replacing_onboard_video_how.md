---
title: "Installed a video card replacing onboard video how does xserver find the new device"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by Ron Byers on 2008-01-17
I just installed a new Nvidia video card in a pci 16 slot. I had been using the onboard video on my Asus V8N-MV board.  I get all the way to loading xserver and receive the following message. NVidia: No matching device found for instance(BusID PCI:3:0:0) found.  Do I edit /etc/X11/xconf or is there a way to modprobe ?

---

### Post by mouseboyx on 2008-01-17
sudo grep vesa /etc/X11/xorg.conf

Should give an easy way to reconfigure X without much work.

---

### Post by Ron Byers on 2008-01-17
Thanks. I will keep that in mind. I solved the problem by editing Device in /etc/X11/xorg.conf. I merely pointed xserver at the new card.  Of course I updated to the latest nvidia drivers. It worked great. Thanks.

---

