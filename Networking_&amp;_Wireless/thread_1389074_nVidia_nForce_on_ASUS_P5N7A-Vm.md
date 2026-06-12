---
title: "nVidia nForce on ASUS P5N7A-Vm"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by jbuturff on 2010-01-23
I have an ASUS P5N7A-VM motherboard, with built-in nVidia nForce ethernet port.  I have successfully been running Windows on the box, so I know the hardware all works. 

I am trying to switch to Ubuntu 9.10 x64.  Everything works great except my ethernet adapter.  During setup, the DHCP config failed.  I've tried hardcoding the parameters.  Nothing seems to work.

The FORCEDETH driver is loading.

~$ lsmod | grep -i forced
forcedeth              61292  0 

~$ lspci | grep -i ethernet
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
01:05.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)

(I currently have an old SMC card in so I can access the internet).

I've tried some other forum hints of adding options to the FORCEDETH module (msi=0  msix=0).  Still nothing works.

Anyone have any other hints to try to troubleshoot the FORCEDETH driver on an nVidia nForce ethernet controller?

Thanks,

Jeff

---

