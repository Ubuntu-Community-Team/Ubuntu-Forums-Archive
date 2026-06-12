---
title: "Not network connection, ifconfig doesn't show eth0."
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by pygy on 2011-05-23
Hello,

I'm painfully installing Ubuntu 11.04 on a new machine. I've at last managed to get it to boot (using LILO).

Now, Ubuntu boots (in command line mode, dunno why), but I don't have any wireless connectivity.

lspci shows my Ethernet controller (Realtek RTL8111/8168B PCIe), which is supported by linux (actually, it was working dring the installation procedure).

However, ifconfig only shows the loopback "adapter", and attempts to ping the modem yield a "connect: Network is unreachable" error.

What can I do (I'd rather not re-install).

TIA,
--Pygy

---

