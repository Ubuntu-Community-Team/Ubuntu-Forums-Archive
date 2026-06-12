---
title: "Forcing X to use an AGP card over a PCI card"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by 13thMonkey on 2007-02-12
Is it possible to get Ubuntu to 'uninstall' a PCI graphics card from the command line without physically removing the card?

Currently I'm playing around with an Ubuntu Edgy server/XP dual boot on a PC with an ATI 9800 AGP and an ATI 7000 PCI and all is fine until I try to install X windows since it always defaults to the 7000 and then complains. My main monitor runs off the dvi connector on the 9800 and I have two other monitors running off the 7000. 

I can get both the 7000 and the 9800 working fine on their own with the latest drivers (no multiple monitors - that's for another day :-? ) but since I'm just playing around, learning and reinstalling regularly (for the day when my XP box replaces my current Ubuntu server)  I'd quite like to have the install ignore the 7000 when I do so. 

I realise I could just copy over a working Xorg.conf file with the 9800 setup or edit it manually, but for my own gratification and interest, is there way of forcing Linux to use the AGP card over the PCI card?

---

