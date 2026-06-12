---
title: "Update kernel ? mythbuntu 7.1 and nova 500-t"
date: 2008-07-23
forum: Mythbuntu
---

### Post by perhagge on 2008-07-23
I'm running mythbuntu 7.1 and upgraded to 0.21 mythtv. I use Nova 500-t card foe DVB-T.
To get the card working I followed this [[COLOR="Blue"]guide[/COLOR]]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI") and now it's working good. Have disconnected the ir cable for the remote as found in this forum. The machine is now acting mainly as an backend and a XBOX as frontend.

However the update manger in mythbuntu wants to upgrade the kernel, will this "destroy" the steps in the guide? Do I need to do it all over again if I upgrade?

I'm waiting with upgrading to 8.04 as I can read about some issues in the forum with 8.04 and the nova 500 card.

/Pär

---

### Post by perhagge on 2008-07-23
Found some answers by myself.

According to [COLOR="Blue"]**[linuxtv]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500")**[/COLOR] the nova 500 card should get to work in 8.04.

If I upgrade the kernel I need to do the steps in the mythtv wiki for nova 500t again.

The big question is should I go all the way and go for mythbuntu 8.04 ?
Any one used the auto upgrade from 7.1 to 8.04 with the nova 500t?

---

### Post by funkydan2 on 2008-07-24
Yep, if you install (and boot) a new kernel you'll have to recompile these modules.

If everything's working okay you can either
1.) Install the new kernel, boot into it and then make the new modules
2.) Not run the new kernel.  This probably means that there's some security risk that your machine will be exposed to, but you may decide that this risk is smaller than the effort require to rebuild the updated modules.  (You can either not run the update, or update but tell GRUB to keep booting your current kernel.)

---

### Post by AJ1000 on 2008-07-26
I just installed mythbuntu 8.04.1 and the nova t 500 worked. The only issue was the lna activation, so I had to do this:

In /etc/modprobe.d/options add:

options dvb_usb_dib0700 force_lna_activation=1

The nova T 500 works great. (Mine is the earlier version of the card).

---

