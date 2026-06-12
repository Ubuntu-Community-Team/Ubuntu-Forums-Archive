---
title: "On Board Video to ATI Radeon 9250"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by adlin5000 on 2007-08-24
I recently bought a ATI Radeon 9250 128MB PCI card, and I am having trouble getting it to work. If someone could walk me through this I would be grateful.

My specs are:
HP Pavilion 7935
MB: Asus A7V-ML
On board video: ProSavage KM133 128

I have compiled my own kernel and have included ATI and Savage drivers.

I can put the card in and I have no problems but when I change the BIOS settings to disable the on board video and change to the PCI one I get blank screens on both.

Please let me know if you need any more info.

---

### Post by vpjr on 2007-08-25
hi,

Does your whole setup (I mean with the PCI card) run when you boot using the live CD?

If so, you might find this workaround I recently discovered helpful:

    a. boot using the live CD

    b. mount the harddisk (if not yet mounted)

    c. if you go to /etc/X11, you'll find the xorg.conf that the live CD created.

    d. you can then copy this xorg.conf to your harddisk's /etc/X11, replacing the existing one there. (On the safe side, just "mv xorg.conf xorg.conf.original" (I mean the xorg.conf which is originally in your harddisk.))

    e. boot

Note: You'll have to be root, of course so that the xorg.conf will have root permissions

I hope that helps. Please feedback me.

regards,

ven

---

