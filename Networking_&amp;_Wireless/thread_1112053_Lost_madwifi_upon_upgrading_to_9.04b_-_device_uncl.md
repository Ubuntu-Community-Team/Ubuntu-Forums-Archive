---
title: "Lost madwifi upon upgrading to 9.04b - device unclaimed"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by qwavel on 2009-03-31
I had a working 8.10 installation that used madwifi for my AR5001X+ wireless device.

I upgraded to 9.04 beta and everything went fine except that my wireless device is now "unclaimed".  The kernel module 'ath_pci' is still there but is somehow not working anymore.

Some might suggest that I switch from madwifi to ath5k and maybe that is good advice, but it would be good to know how to get my device to use the madwifi drivers again (that was working well for me).

Below I've pasted some further information.

Thanks for any suggestions.
Tom.

```
root@DoltU:/home/tom# lshw -C network
  *-network:0        
       description: Ethernet interface
	...
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
root@DoltU:/home/tom# 
root@DoltU:/home/tom# 
root@DoltU:/home/tom# lspci -k
...
03:03.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Kernel modules: ath_pci
root@DoltU:/home/tom# 
root@DoltU:/home/tom# lsmod | grep ath
root@DoltU:/home/tom#
```

---

### Post by qwavel on 2009-03-31
I've figured it out.

Because madwifi has a binary blob it is considered proprietary*, so I needed to go to System->Admin->Hardware Drivers and 'activate' it.

I would suggest that there should be a better way to notify the user that they need to do this ('activate' the driver).



*There is now a madwifi-free driver that replaces the binary blob with an open-source one, but that is not widely used yet.

---

