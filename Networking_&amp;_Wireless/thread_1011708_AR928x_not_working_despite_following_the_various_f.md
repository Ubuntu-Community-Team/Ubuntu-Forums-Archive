---
title: "AR928x not working despite following the various fixes!"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by Zerimas on 2008-12-15
I followed this fix to get try and get my wireless card working, but for some reason it is ineffective: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

I also checked to make sure the card isn't blacklisted by running ```
grep -r "ath5k" /etc/modprobe.d/
```.  The Atheros driver also doesn't appear in the the proprietary driver manager (only my graphics card does).

Here is the relevant output from ```
lspci -v
```:

```
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a3b:1067
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

``` 

I am pretty much a *nix noob, but why isn't my card functioning?

---

### Post by Zerimas on 2008-12-17
I tried switching my network manager to WICD, but I am still having no luck. :-({|=:cry:  Any help is much appreciated.

---

