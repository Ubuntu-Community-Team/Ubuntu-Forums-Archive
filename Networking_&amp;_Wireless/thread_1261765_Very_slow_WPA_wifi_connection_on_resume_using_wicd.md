---
title: "Very slow WPA wifi connection on resume using wicd."
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by olho on 2009-09-09
Hello all. I'm wondering if anybody else has been completely successful getting stable WPA connections from the RaLink RT2860 wireless card.

The standard Network Manager would stall attempting to connect to WPA and only allow WEP connections. Using wicd I can now connect using WPA. I was very pleased it looked like we were getting somewhere and wished I'd heard of wicd a long time ago.

On boot the connection (it's designated 'Automatically connect') is alive before I get to the desktop. That's far more impressive than NM. But ... On resume it can take anything up to three minutes to connect to the same network. This is very frustrating as I'm frequently resuming rather than re/booting. And why would it be so quick at boot and so slow on resume?

It's not a scanning issue on resume I don't think. It seems to see the list quickly and then take all that time negotiating the connection. I've tried forcing a scan (sudo iwlist scan) but that makes no difference.

So I wondered if any of you have had similar experiences or have any tips. Thanks so much if you do.

Mark.

Now for some stuff you'll ask me for if I don't provide it up front:

Asus EeePC 901 running Ubuntu Jaunty, 9.04 with 2.6.28-15-generic i686 kernel. The access point is running DHCP and this machine is assigned a static IP (192.168.0.50).

The following were output while I am connected.

Output of lspci -v

```
01:00.0 Network controller: RaLink RT2860
	Subsystem: RaLink Device 2790
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fbef0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta
```

Output of lshw -C network

```
 *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:00:90:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.0.50 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
```

Output from modinfo rt2860sta

```
filename:       /lib/modules/2.6.28-15-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        1.8.0.0
license:        GPL
srcversion:     41B325B81DD5210E4BAE315
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.28-15-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)
```

I'm aware that driver version 1.7.1.1 is supposed to give better support. I have this .deb package on my desktop but as WPA is working using 1.8.0.0 I don't want to break it and, anyway, any kernel update will reset it to 1.8.0.0 which is included in the generic kernel.

---

### Post by olho on 2009-09-11
Nobody I guess. :( Never mind. It seems like a bit of an all-round bugger that RaLink card.

---

### Post by marcoftheknight on 2010-05-04
check my post maybe that will help on wifi

---

