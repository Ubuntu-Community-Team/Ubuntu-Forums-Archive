---
title: "Ubuntu 11.04 slow to connect to wireless network"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by nicki20048 on 2011-04-29
Hi, I have just installed ubuntu 11.04.

When first starting up I am not able to get a wireless connection, network manager says that wireless is disabled. Then some time later (can be up to five minutes after starting up) it will finally start working.

I have tried rfkill list all, but it shows:

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

So I don't see any problems there.

Is anybody having the same problem? it is rather annoying having to wait 5 minutes to connect to the internet.

---

### Post by nicki20048 on 2011-04-30
bump

---

### Post by nicki20048 on 2011-05-01
Just posting with some more info. As you can see the ath5k module is loaded, but when I initially startup im not getting any wifi connection, then after a few minutes it suddenly appears.  

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
    Subsystem: Acer Incorporated [ALI] Device 009f
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Kernel modules: shpchp
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
    Subsystem: ATI Technologies Inc IXP SB400 Serial ATA Controller
    Kernel driver in use: sata_sil
    Kernel modules: sata_sil
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: ohci_hcd
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
    Subsystem: Acer Incorporated [ALI] Device 009f
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device 0418
    Kernel driver in use: ath5k
    Kernel modules: ath5k
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 009f
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 009f
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 009f
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

```

Hopefully somebody will have some ideas

---

### Post by oscarmeyer51 on 2011-05-02
Same issue with the atheros chipset here.

Network Manager shows no wireless connections for about 5 (or more) minutes, then all that are available appear (in an apartment. there are always at least 6 networks that I see when I open nework manager).

Also, page refresh times are less than half (estimated) from 10.10.

Does someone need to goose this narwhale??

---

### Post by oscarmeyer51 on 2011-05-02
I found a solution (for me).

Deleted Unity (completely).

Installed kubuntu (just in case I could not get back in to Gnome classic.

rebooted.

Selected "gnome classic (with no effects)" when signing on.

This is also after editing the /etc/NetworkManager/NetworkManager.conf, changed the lines from:

################
[ifupdown]
managed=false
################

to:

################
[ifupdown]
managed=true
################

Not sure if those will work for you or not, the first is what got me connected immediately and where the internet seems responsive again.

The edit change was suggested from other searches as it was noted that Natty sets your internet connections to not be managed by default (why the drop down menu does not show wireless networks and is initially grayed out).

You need to reboot after the edit changes and/or the removal of Unity.

Good Luck !!

---

### Post by oscarmeyer51 on 2011-05-08
ERROR !!

My correction above only worked for a single login!

Since then, I am unable to establish and keep a wireless connection.

Worse than that, when I connect in a wired fashion, the connection does not last longer than a few minutes before disconnecting.

Really interesting side effect though... when connected via wired, I can start Virtual Box and stay connected in the virtual machine (Win XP).

Hope this is being actively worked on - it sucks rocks.

Am on now only by booting with 10.10 Live CD.

Sorry for the mis-direction earlier on what I thought was a solution.

Am searching launchpad to see if there is a thread or solution.

Will post if/when I find one.

---

