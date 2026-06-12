---
title: "Wireless card recognized by install CD but not after server installed"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by unixlinuxesx on 2010-12-26
I'm working with 10.10 (Maverick) on an older Compaq laptop.
Wireless card is a Cisco Aironet 350.  This card is listed as supported and drivers included in the server distro.

During the Network configuration portion of the install, I selected eth1 (wireless);  the card came active and a valid network connection was established.

However, after the full server installation the interface (eth1) is not seen.

What's confusing is that modprobe -l shows the drivers as present:
kernel/drivers/net/wireless/airo.ko
kernel/drivers/net/wireless/airo_cs.ko

Insertion and removal of the card is noted in /var/log/messages:
pcmcia_socket  pcmcia_socket1 pccard: card ejected from slot 1
pcmcia_socket  pcmcia_socket1 pccard: card inserted into slot 1

I'm probably bone-headedly missing some fundamental step so would really appreciate some info.

(I'd be happy to supply more info, but currently set up with Fluxbox and I'll be darned if I can get copy from the xterm to paste into Firefox...)

Thanks in advance.

---

### Post by rtimai on 2010-12-26
Just my 2 cents, hth.

I experienced this is LXDE too. To copy-paste try leaving the source window open until after you've pasted.

---

