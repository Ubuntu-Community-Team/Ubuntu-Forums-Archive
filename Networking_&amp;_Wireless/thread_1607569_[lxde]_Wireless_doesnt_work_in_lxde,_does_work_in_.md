---
title: "[lxde] Wireless doesnt work in lxde, does work in gnome"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by Yondergod22 on 2010-10-27
I installed lxde, but my wireless internet doesn't work. I can switch back to gnome and it works perfectly.
I tried wicd and manually connecting with the command line.
Both fail while trying to get an ip.

has anyone heard of anyone else having this problem and/or knows how to fix it?

Thanks

---

### Post by Yondergod22 on 2010-10-30
we're allowed to bump right? I don't see anything about it in the code of conduct or faq.

---

### Post by zealibib slaughter on 2010-10-30
I had the same problem.  Had to manually bring the wireless card up with ifup <interface>, find the network with iwlist scan and manually configure my connection with ifconfig before doing a command line connection.  I dumped ldxe for xfce and the network manager gui works great in it.

---

