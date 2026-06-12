---
title: "Dual head works with Nouveau but freezes up with nvidia"
date: 2013-03-06
forum: Multimedia Software
---

### Post by Abandon on 2013-03-06
Ubuntu 12.04 & 12.10. Two monitors (IIyama Proolite E2473HDS) are connected (DVI) to an MSI N450GTS Cyclone 1GB GDDR5 card. This setup works fine with Nouveau. After (succesful) installation of the NVidia drivers (nvidia-current) the system freezes up. Sometimes after a few minutes, most of the time while loading GDM/LightDM. The mouse stops working, keyboard doesn't respond. Have tried differtent NVidia drivers, including the ppa:xorg-edgers/ppa but problem does not go away. The only solution is working with the Nouveau driver. I would however like to work with NVidia. Does anybody recognize this problem and is aware of a solution?

---

### Post by Abandon on 2013-04-08
I found the answer myself ;-) Blacklist the nouveau driver first: sudo gedit /etc/modprobe.d/blacklist.conf and add this line at the bottom: blacklist nouveau

---

