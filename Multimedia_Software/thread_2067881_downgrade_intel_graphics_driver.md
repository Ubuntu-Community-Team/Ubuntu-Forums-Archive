---
title: "downgrade intel graphics driver?"
date: 2012-10-07
forum: Multimedia Software
---

### Post by aem0512 on 2012-10-07
I've had all sorts of problems with the new kernels on my system related to the graphics driver. I have a black screen on boot (which I can get around with a quick press of Fn+contrast keys during boot), but I also hear an annoying whining noise from the GPU with the default driver. If I force it to load up say...the vesa driver, I don't hear the whining noise, but the resolution is messed up, amongst other things. 

Can I downgrade my intel graphics driver to the one that was default in Ubuntu 10.04? I've already tried to update it to version 2.20 through this ppa listed in the following link:
[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

But I still have the black screen on boot issue + whining noise.

---

### Post by bra|10n on 2012-10-07
I don't know that downgrading your graphics driver is the best solution, however your system may respond better to the SNA acceleration method rather than the UXA default mentioned in the link. 
You should post your hardware details here as a first step.

---

### Post by aem0512 on 2012-10-08
Of course, sorry I forgot to add specs.

lspci gives these results:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)

Let me know what other information I can provide. I don't want to overwhelm this post with unnecessary information. 

Also, since I updated to the newest (unstable) intel 2.20 graphics driver from the PPA mentioned in the first post I've been experiencing some trouble with youtube videos also. Other video streaming works fine though. Like Hulu, etc.

---

### Post by dentaku65 on 2012-10-28
You can purge Glasen PPA

```
sudo apt-get install ppa-purge
```
```
sudo ppa-purge ppa:glasen/intel-driver
```

In order to revert intel driver with the distribution one.

by

---

