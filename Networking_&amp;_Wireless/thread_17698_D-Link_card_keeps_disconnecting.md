---
title: "D-Link card keeps disconnecting"
date: 2005-03-02
forum: Networking &amp; Wireless
---

### Post by brockmeister on 2005-03-02
I have a D-Link DWL-G520 PCI wireless card, with an Atheros chipset.

It works in Warty with the default driver (probably madwifi) but only just - if I'm surfing the web, it loses the connection every ten seconds or so, and it takes about another twenty seconds to reconnect to the server. This makes downloading files virtually impossible.

I can't figure out how to get it to work properly with this driver, although I've had it working fine with ndiswrapper in Fedora, Knoppix and Gentoo. I've grabbed ndiswrapper-utils using Synaptic, loaded the Window$ driver (it says 'hardware present' when I list the loaded drivers) gone 'modprobe ndiswrapper' and 'ndiswrapper -m'. The new device (should be wlan0) isn't appearing in iwconfig, although the one using the old driver (ath0) is still there.

I called up the system log (dmesg) and it has these two lines:
> ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
ndiswrapper: driver a3ab.sys (D-Link,10/22/2003,3.0.0.44) added 
but it doesn't say 'ethernet device wlan0 at address xx.xx.xx.xx.xx.xx' or anything, like it has done for me before.

Does anyone know either how to get ndiswrapper to work (maybe by removing the old device) or stop the old driver from lagging?

---

### Post by brockmeister on 2005-03-02
Well I've got ndiswrapper working now - just unloaded the kernel modules for the old driver:
> modprobe -r ath_hal
modprobe -r ath_pci 
I had to actually delete the .ko files from the modules directory to stop them from being loaded when I boot - is there a cleaner way?

---

