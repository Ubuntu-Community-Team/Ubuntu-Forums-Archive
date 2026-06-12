---
title: "boosting Atheros 5005G Performance"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by sledgeas on 2009-04-28
Hello,

With Ubuntu Intrepid I cannot connect to a distant (weak Signal) AP (no dhcp responses, NetworkManager gives up). But in Windows I can. How could I update the (which?) driver sets on Ubuntu to improve performance?

On my ACER 5103WLMi I have the following wifi:
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

Which on Windows (PCI VendorID and DevID) is identified as Atheros 5005G.

The further information from Ubuntu:
# dmesg | grep ath
[   13.146319] ath_hal: module license 'Proprietary' taints kernel.
[   13.161623] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.564620] ath_pci: 0.9.4
[   13.564684] ath_pci 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.348078] ath_rate_sample: 1.2 (0.9.4)
[   14.353977] wifi0: Atheros 5212: mem=0xf8110000, irq=22

# lsmod | grep ath
ath_rate_sample        21248  1 
ath_pci               109168  0 
wlan                  234784  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               225904  3 ath_rate_sample,ath_pci

# modprobe -l | grep ath
/lib/modules/2.6.27-11-generic/volatile/ath_hal.ko
/lib/modules/2.6.27-11-generic/volatile/ath_pci.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_amrr.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_minstrel.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_onoe.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_sample.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/infiniband/hw/ipath/ib_ipath.ko

You would be a very much of help, thanks!

-- 
sledge

---

