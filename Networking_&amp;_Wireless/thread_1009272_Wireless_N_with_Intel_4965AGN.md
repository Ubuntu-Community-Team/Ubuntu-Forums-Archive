---
title: "Wireless N with Intel 4965AGN"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by bjdekruif on 2008-12-12
Hello, 

I just bought a Linksys WRT610N router in order to have fast wireless internet. However, I can only connect with speeds up to 60 Mb/sec. I hoped I would get connection speeds  as fast as 300 Mb/sec, but anything above 100 Mb/sec would be great. 

I am using an Intel 4965AGN card for the connection. The output to 
lshw -C network is:
```

   description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:22:47:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.100 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```

I use the iwlagn module. The output of lspci -k:
```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
```

I am running 8.10, and installed the backport-modulels to avoid the kernel-panic. The strength of the signal is very good. It is somewhere between 80% and 100%. 

Is there anyway to increase my connection speed? 
I read somewhere that I should use the ndiswrapper, will this work? Or will this issue be addressed somewhere in the future? 

Thanks for all the help!

---

### Post by qbox on 2008-12-12
Still. Wireles N cards isnt supported. The chipset is broadcom. You need to wait for a new drivers I think. Im waiting almost 3 years :D

---

### Post by qbox on 2008-12-12
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by bjdekruif on 2008-12-12
Oi, 

Thanks for your quick reply. It is too bad that the N speed is not supported!

What I don't understand is that I can connect to my network, also when I force the router in N-mode. So the connection is there, but the speed isn't.

In you reply you say it is the Broadcom chipset, but I think I have a Intel chipset?? In the 8.04 I connected with iwl4965, which is for Intel. Does this intel driver support the N-speed? Or is it the same, and you I just not understand it?

Thanks

---

