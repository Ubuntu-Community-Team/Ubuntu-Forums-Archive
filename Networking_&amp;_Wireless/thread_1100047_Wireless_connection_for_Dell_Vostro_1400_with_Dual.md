---
title: "Wireless connection for Dell Vostro 1400 with Dual bootup vista and Ubuntu 8.10"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by radmedico on 2009-03-18
[SIZE="5"][SIZE="6"][FONT="Comic Sans MS"][FONT="Comic Sans MS"]hi,
    I have installed dual boot up with windows vista and ubuntu 8.10. I am able to connect to wired network. I have trouble connecting to wireless as i find wireless drivers are disabled ( 802.11b g)...i have tried many ways to install wireless drivers but was not successful.... i have tried hard but no use can i get help please.[/FONT][/FONT][/SIZE][/SIZE][SIZE="4"][/SIZE][SIZE="4"][/SIZE]

---

### Post by radmedico on 2009-03-18
craftyquack@craftyquack-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.


craftyquack@craftyquack-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:1A:A0:FD:14:C6

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         146.7.114.77
    Prefix:          23 (255.255.254.0)
    Gateway:         146.7.115.254

    DNS:             146.7.4.129
    DNS:             146.7.4.130


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            NULL(info.linux.driver)
  State:             unavailable
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Supported:       yes

  Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points


craftyquack@craftyquack-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

craftyquack@craftyquack-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


craftyquack@craftyquack-laptop:~$ 
craftyquack@craftyquack-laptop:~$ uname -a
Linux craftyquack-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
craftyquack@craftyquack-laptop:~$ dmesg | grep ound
[    1.185912] pnp: PnP ACPI: found 12 devices
[    2.410930] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.411354] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.411758] pcieport-driver 0000:00:1c.3: found MSI capability
[    2.412162] pcieport-driver 0000:00:1c.5: found MSI capability
[    2.767157] isapnp: No Plug & Play device found
[    2.827152] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.831458] hub 1-0:1.0: USB hub found
[    3.933656] hub 2-0:1.0: USB hub found
[    3.940542] No dock devices found.
[    4.071848] hub 3-0:1.0: USB hub found
[    4.176722] hub 4-0:1.0: USB hub found
[    4.280681] hub 5-0:1.0: USB hub found
[    4.384826] hub 6-0:1.0: USB hub found
[    4.512263] hub 7-0:1.0: USB hub found
[    4.672198] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   16.993272] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   17.231287] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   17.556445] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   17.613895] b43-phy0: Broadcom 4311 WLAN found
[   19.960094] lp: driver loaded but no devices found
[   23.370203] apm: BIOS not found.
[   31.970847] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   32.222611] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[16886.467712] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
craftyquack@craftyquack-laptop:~$ dmesg | grep witch
[    1.196044] Switched to high resolution mode on CPU 0
[    1.196810] Switched to high resolution mode on CPU 1
[   15.832510] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[   15.833192] ACPI: Lid Switch [LID]
craftyquack@craftyquack-laptop:~$

---

