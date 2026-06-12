---
title: "Multiple graphics cards, different drivers"
date: 2012-03-19
forum: Multimedia Software
---

### Post by mark_d100 on 2012-03-19
Hi all,

Have had a bit of a look around here and other sites but can't find an answer to this seemingly unusual problem. My machine has two graphics cards, an onboard integrated Intel Chipset and an nVidia 7600. 

Until now I have used two monitors on the NV card, but have just acquired a third which I would like to see if I can get working. Unfortunately, I use the nVidia settings tool to get the existing configuration working and obviously it can't configure an Intel card. 

I have tried briefly handcrafting an xorg.conf file which I thought should do the trick, but no luck. I think I should be able to use both as the new monitor displayed the 'Ubuntu' logo when first connected to the Intel integrated card, but that's about as far as I've got. The handmade xorg.conf just messed up the existing two desktops.

I've also tried the GNOME Monitor Preferences tool, which isn't much use in this case.

Any advice would be much appreciated - I'm sure 3 monitors over two cards can't be *that* uncommon! Attached is the xorg.conf as unmodified for two monitors and my lspci output (lines 3 and 21 seeming most pertinent).

Thanks!

UPDATE - Moving to 'Hardware issues' - didn't spot that category before

---

