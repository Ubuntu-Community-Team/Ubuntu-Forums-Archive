---
title: "Can not get wireless to work"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by sr212787 on 2009-05-13
Hi, I am new to ubunto. Here is the information said to copy:

> misha@SalsaShark:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1C:DF:B9:76:A1
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=79/70  Signal level=-16 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000041435e0061211a01


misha@SalsaShark:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:0a:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:42:43:c7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:0a:06.0
       logical name: wifi0
       version: 01
       serial: 00:16:ce:77:7e:7c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


misha@SalsaShark:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc Unknown device [1002:5a31] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
0a:00.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
0a:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
0a:06.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)


misha@SalsaShark:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 003: ID 0d62:001c Darfon Electronics Corp. 
Bus 001 Device 001: ID 0000:0000  


misha@SalsaShark:~$ uname -a
Linux SalsaShark 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 GNU/Linux


misha@SalsaShark:~$ dmesg | grep ound
[    0.000000] found SMP MP-table at 000f8620
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[   20.767725] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.352107] PCI: BIOS BUG #81[49435000] found
[   21.401827] pnp: PnP ACPI: found 10 devices
[   23.338709] assign_interrupt_mode Found MSI capability
[   23.339090] assign_interrupt_mode Found MSI capability
[   23.700675] isapnp: No Plug & Play device found
[   23.785056] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   27.512331] hub 1-0:1.0: USB hub found
[   27.671832] hub 2-0:1.0: USB hub found
[   27.931516] hub 3-0:1.0: USB hub found
[   45.461052] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   49.436923] Yenta: CardBus bridge found at 0000:0a:00.0 [1025:0080]
[   61.192303] lp: driver loaded but no devices found
[   65.294586] No dock devices found.
[   67.865638] apm: BIOS not found.


misha@SalsaShark:~$ dmesg | grep witch
[   19.825002] SMP alternatives: switching to UP code
[   21.363487] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   21.510326] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   47.391063] input: Lid Switch as /devices/virtual/input/input7
[   47.410895] ACPI: Lid Switch [LID0]


misha@SalsaShark:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:403451  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

misha@SalsaShark:~$ 




---

### Post by lisati on 2009-05-13
That's the exact same networking chipset (both ethernet and wireless) as in the laptop I'm using at the moment, which worked "out of the box" with Ubuntu.

My $0.02 worth is to check that your Wifi card is switched on. On my laptop there's a switch on the right-hand side - when Wifi is enabled, a light glows orange.

(I'm nearly off to bed, so I might pass the reins on to other users for further suggestions if needed)

---

