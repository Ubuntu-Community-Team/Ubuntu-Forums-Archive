---
title: "WN311B wireless adapter"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by fms714 on 2011-01-22
I just tried tointall a wifi adapter on my computer running ubuntu 10.10. The adapter has an installation disk but its for windows only. I tried to just plug it in to see what would happen and nothing happened. Seeing as this is my first time installing a wifi adapter and I'm new to linux, I have no clue what I'm doing. Any help would be appreciated.

---

### Post by tnngator on 2011-01-22
fm, install wine  in terminal.... sudo apt-get install wine ,,,then install ndiswrapper ,, sudo apt-get install ndiswrapper ,,, go to ndis page for the rest ,,,[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by amsterdamharu on 2011-01-22
Just noticed the card is a pci card and not usb
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:PCI](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:PCI)
could only find the wn311t but that one seems to work.

Could you execute the following command:
```
sudo lspci -k
```
To execute the command you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: ```
[COLOR=Red]Your pasted stuff[/COLOR]
```

---

### Post by fms714 on 2011-01-23
Heres the output from that command.

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
    Kernel modules: shpchp
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
    Subsystem: Giga-byte Technology Device b002
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Kernel modules: i2c-piix4
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
    Subsystem: Giga-byte Technology Device 5002
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Giga-byte Technology Device a102
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ohci_hcd
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ohci_hcd
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ehci_hcd
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4290]
    Subsystem: Giga-byte Technology Device d000
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Giga-byte Technology Device 960f
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
    Subsystem: Giga-byte Technology Device 5007
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Kernel driver in use: r8169
    Kernel modules: r8169
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394
05:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Kernel driver in use: ahci
    Kernel modules: ahci
05:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron
```

---

### Post by amsterdamharu on 2011-01-23
Your card is not listed in there, I could only find your ethernet card:[FONT=monospace]
[/FONT]Realtek RTL8111/8168B

If you have this thing:
[http://www.netgear.co.uk/rangemaxnext_wirelessadapter_wn311b.php](http://www.netgear.co.uk/rangemaxnext_wirelessadapter_wn311b.php)

It doesn't show up as a pci device.

---

### Post by fms714 on 2011-01-23
oh, fun, now I have a hard drive and a wireless adapter my computer can't recognize.

---

### Post by amsterdamharu on 2011-01-24
Are you sure it's plugged in correctly? The link I posted is your wireless pci device right?

You can look through the list yourself but as far as I can see there is nothing that would indicate a wireless pci device.

---

### Post by fms714 on 2011-01-24
After looking at it, it sort of seems like its upside down, but if i plugged it in the other way the panel thats supposed to be on the back would be facing into my case. Ill try that today and see what happens. I dont think it could be a messed up backwards card but you never know.

---

