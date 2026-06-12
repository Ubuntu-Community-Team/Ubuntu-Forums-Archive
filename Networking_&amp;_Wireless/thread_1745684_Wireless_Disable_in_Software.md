---
title: "Wireless Disable in Software"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by lordluis2000 on 2011-05-01
Hello Everyone,

I am new on Linux. I used to have Kubuntu 10.04 Yesterday the software asked me for an update and after that. My wireless interface is disable. And every-time I try to check the enable wireless is became uncheck again. And I do have the possibility to go wired.

I have a laptop Gateway LT3201h. 

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
03:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


I tried 

sudo service network-manager stop
 sudo rm /var/lib/NetworkManager/NetworkManager.state
 sudo service network-manager start

After I did
sudo ifconfig wlan0 up
Did not work any of them



Someone can help me?

---

### Post by northd_tech on 2011-05-01
> **lordluis2000 said:**
> 
03:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
06:00.0 Network controller: **Atheros Communications Inc. AR928X Wireless** Network Adapter (PCI-Express) (rev 01)

Here is a recent thread about the Atheros AR928x wireless, and it sounds like there are some issues with 802.11n that are partially "solved" by forcing 802.11b or 802.11g wireless communication in the wireless router setup (see posts 15, 16 and 19):

[http://ubuntuforums.org/showthread.php?t=1742274&highlight=atheros+AR928x&page=2](http://ubuntuforums.org/showthread.php?t=1742274&highlight=atheros+AR928x&page=2)

I have read before that some of the "software" wireless interfaces apparently require you to go into Windows 7 (or Vista) to enable the wireless- it's like the wireless firmware only communicates with Windows for some reason.  If you still have dual-boot with windows, that might be worth a try also.

---

### Post by lordluis2000 on 2011-05-02
The curious of the case is that before was working perfectly. After login I have to check it, because always started disabled. But now never come to active state anymore

---

