---
title: "Have hybrid graphics - how to switch graphics cards"
date: 2011-03-13
forum: Multimedia Software
---

### Post by bastones on 2011-03-13
Hi,

I have hybrid graphics with an Intel GMA 3150 and NVIDIA ION graphics cards, is there any way of switching to one or the other graphics card via Kubuntu? I will want to run the higher performance NVIDIA ION for online games at some point and I'm wondering whether it is possible to switch between both cards via Kubuntu? The output of the lspci command is below:

> 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
**00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)**
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82552 10/100 Network Connection (rev 02)
**02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 305M] (rev a2)**
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


Thanks.

---

### Post by Yellow Pasque on 2011-03-13
You can only do so with the open-source nvidia driver (nouveau) using the vga_switcheroo script. You may be able to turn off the Intel IGP at boot in the BIOS, but you would almost have to keep a separate install with nvidia proprietary drivers (or be constantly installing/uninstalling the nvidia driver on one install).

---

### Post by bastones on 2011-03-13
> **Temüjin said:**
> You can only do so with the open-source nvidia driver (nouveau) using the vga_switcheroo script. You may be able to turn off the Intel IGP at boot in the BIOS, but you would almost have to keep a separate install with nvidia proprietary drivers (or be constantly installing/uninstalling the nvidia driver on one install).

Thanks for your response. How do I use 'vga_switcheroo' in order to switch the graphics card used by Kubuntu, and would I need to logout/restart when switching using vga_switcheroo. If I don't need to logout/restart, does the switch only apply until I logout/restart or until a switch the graphics card again through vga_switcheroo?

Thanks.

---

