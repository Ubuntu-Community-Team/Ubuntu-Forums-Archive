---
title: "ASUS USB-N10 Wireless speed unstable on Ubuntu 11.04"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by jarrodr on 2011-07-30
Hi guys,

I am a newbie at Ubuntu, I installed Ubuntu 11.04 64bit. My intention is to use my microserver as a Media Server.
I am having endless issues with my wireless speeds when I try to stream media from Ubuntu but when using a wired connection (at 100Mbps) everything works perfect.

Now for the details:

**Machine Brand and Model (PC/Laptop)**:
HP ProLiant MicroServer

[B]Wireless Brand, Model and Wireless Chipset:
[/B]```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
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
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)
``````

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04d9:a06b Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0b05:1786 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```[B]check interface:
[/B]```

wlan0     IEEE 802.11bgn  ESSID:"Access Denied"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: D8:5D:4C:D3:99:7C   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=61/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```[B]Check for modules:
[/B]```

Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
radeon                982152  2 
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
r8712u                307592  0 
drm                   227495  4 radeon,ttm,drm_kms_helper
joydev                 17606  0 
i2c_algo_bit           13400  1 radeon
amd64_edac_mod         28428  0 
ghes                   13658  0 
shpchp                 37297  0 
edac_core              53845  3 amd64_edac_mod
sp5100_tco             13744  0 
edac_mce_amd           23464  1 amd64_edac_mod
i2c_piix4              13303  0 
hed                    13226  1 ghes
k10temp                13119  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  2 
tg3                   141750  0 
libahci                26642  1 ahci
pata_atiixp            13165  0 
jarrod@NinjaBox:~$ lsmod | grep wlan0
jarrod@NinjaBox:~$ lsmod | grep "wlan0"
jarrod@NinjaBox:~$ lsmod | grep "rtl_wifi"
jarrod@NinjaBox:~$ lsmod | grep rtl_wifi
jarrod@NinjaBox:~$ lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
radeon                982152  2 
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
r8712u                307592  0 
drm                   227495  4 radeon,ttm,drm_kms_helper
joydev                 17606  0 
i2c_algo_bit           13400  1 radeon
amd64_edac_mod         28428  0 
ghes                   13658  0 
shpchp                 37297  0 
edac_core              53845  3 amd64_edac_mod
sp5100_tco             13744  0 
edac_mce_amd           23464  1 amd64_edac_mod
i2c_piix4              13303  0 
hed                    13226  1 ghes
k10temp                13119  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  2 
tg3                   141750  0 
libahci                26642  1 ahci
pata_atiixp            13165  0 

```Sorry if I did not provide all information, most of the commands didn't work:confused:.

---

### Post by jarrodr on 2011-07-31
Sorry for the BUMP. Really need help. I've install Ubuntu like 5 times. Considering going the Windows route.

---

