---
title: "Choppy Fullscreen Video"
date: 2009-09-21
forum: Multimedia Software
---

### Post by theGlitch on 2009-09-21
When I try to watch any video in full screen it will be intermittently choppy. This occurs only in full screen versions and is fine in smaller screens. It happens both on the internet and on movie player. I've checked the hardware drivers are fine according to the GUI found in the admin section

---

### Post by tkoco on 2009-09-22
Are you using 3D acceleration on the video driver? Your description sounds like the video is non-accelerated. > **theGlitch said:**
> When I try to watch any video in full screen it will be intermittently choppy. This occurs only in full screen versions and is fine in smaller screens. It happens both on the internet and on movie player. I've checked the hardware drivers are fine according to the GUI found in the admin section

---

### Post by theGlitch on 2009-09-22
I appreciate your quick response! I'm not sure if it is or now, how would I go about checking that?

EDIT:

I just ran
```
glxinfo | grep rendering
```

and it returned yes, meaning I have 3d acceleration engaged. Any other suggestions would be greatly appreciated

---

### Post by KCormier on 2009-09-28
run the following command and post the output

```

lspci -k

```

---

### Post by tuxxy on 2009-09-28
I had a lot of issues with fullscreen video and ATI drivers, are you using an ATI video card by any chance?  If so you may want to check the post I just made about my problems [here]("http://ubuntuforums.org/showthread.php?t=1277877")

---

### Post by theGlitch on 2009-09-28
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    Kernel modules: intelfb
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
    Kernel modules: iTCO_wdt
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
    Kernel driver in use: ata_piix
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Kernel modules: i2c-i801
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
    Kernel driver in use: tg3
    Kernel modules: tg3
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945


tuxxy: i was actually reading your post before and i don't see any sort of solution... just sort of advice... I thank you if you can help though!

---

