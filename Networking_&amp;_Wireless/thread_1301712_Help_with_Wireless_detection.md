---
title: "Help with Wireless detection"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by kimano on 2009-10-26
I'm running 9.04 on a Lenovo Z61m laptop.
Chipset:
Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

The interface *should* be wlan0, but when I run "iwconfig wlan0" I get "No such device."

Network Config
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:4c:00:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11b

I've tried restarting the network, but nothing I do seems to get wlan0 to restart. Any advice?

Edit: Just wanted to add, I CAN connect to the Internet, but only over Ethernet, as I'm doing now.

---

### Post by t0mppa on 2009-10-27
> **kimano said:**
> The interface *should* be wlan0, but when I run "iwconfig wlan0" I get "No such device."

Wireless is only shown as wlan0, when you're using drivers that are built on the mac80211 stack. If you want Atheros drivers that do that, then you should use ath5k or ath9k instead.

> **kimano said:**
> Network Config
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:4c:00:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=ath_pci[/COLOR] latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11b

Ath_pci means that you have the older driver (perhaps better known as Madwifi) active, which uses the ieee80211 stack and thus the logical names of the user and master interfaces are ath0 (instead of wlan0) and wifi0 (instead of wmaster0). This should still be a perfectly working configuration in theory. So, if you want to play with this one, you just replace wlan0 with ath0 in what you're doing and all should go peachy.

If it's not working, then you can just try unloading the ath_pci and enabling ath5k instead to see if that brightens your day. To do that, run the following commands:```
sudo modprobe -r ath_pci ath5k
sudo modprobe ath5k
```

Afterwards run *lshw* again and see if the driver is changed. If it is, then you should have your wlan0 back. So, try these and report back how it goes.

---

