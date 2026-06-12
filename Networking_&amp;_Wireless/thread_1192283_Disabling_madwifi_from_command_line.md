---
title: "Disabling madwifi from command line"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by frunze on 2009-06-19
I installed ubuntu jaunty on a laptop with atheros AR242x 802.11abg Wireless PCI Express Adapter (rev 01). It worked fine with ath5k driver, but I wanted to try madwifi. So I enabled it in hardware drivers applet. After restart the system reported that there are no wireless adapters installed. No matter what I did, no wireless. And what funny it said "no proprietary drivers are in use on the system". So obviously madwifi didn't only not recognized wireless, but disabled it altogether.
So I blacklisted madwifi and commented the blacklist for ath5k. 

Here are the files from /etc/modprobe.d

**blacklist-ath_pci.conf**
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
#blacklist ath5k

```

**madwifi.conf**
```
## ath5k (mac80211)
## Comment out the following line, and uncomment all of the
## madwifi modules below to use the athk module
#blacklist ath5k

## madwifi (non-free)
blacklist ath_hal
blacklist ath_pci
blacklist ath_rate_amrr
blacklist ath_rate_onoe
blacklist ath_rate_sample
blacklist wlan
blacklist wlan_acl
blacklist wlan_ccmp
blacklist wlan_scan_ap
blacklist wlan_scan_sta
blacklist wlan_tkip
blacklist wlan_wep
blacklist wlan_xauth
```

So now the wireless works relatively fine, using ath5k driver. But in hardware drivers it says proprietary madwifi active but not in use (because I blacklisted it). I can't deactivate it, after reboot it again says "active but not currently in use".

So the question is, how to (if possible at all) to disable (or uninstall) madwifi from command line so it's not active anymore.

It says something about using Jokey, how do I do that?

Thanks a lot.

---

### Post by oodlesOfmoodles on 2009-06-19
You can try
```
sudo modprobe -r madwifi
```

---

### Post by frunze on 2009-06-19
Here is the output:
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module madwifi not found.
```

---

### Post by oodlesOfmoodles on 2009-06-19
Ok run

```
lspci -k
```

and paste the output here. This shows the drivers your hardware is using.

---

### Post by frunze on 2009-06-19
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Kernel driver in use: uhci_hcd
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k
```

---

### Post by oodlesOfmoodles on 2009-06-19
It says that the madwifi driver is not in use at all.

What exactly is the problem you're having?

---

### Post by frunze on 2009-06-19
Madwifi shows as active in hardware drivers.

---

### Post by frunze on 2009-06-19
I think I will ignore it for now. Thanks for your help though!

---

