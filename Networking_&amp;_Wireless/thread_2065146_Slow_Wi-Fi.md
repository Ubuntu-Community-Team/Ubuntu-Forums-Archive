---
title: "Slow Wi-Fi"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by MicroMina on 2012-10-01
Hello there,
I'm on xubuntu 12.04 and I'm javing two problems with Wi-Fi. First one is that the Wi-Fi doesn't start on startup right away. I have to wait about 10 seconds for the Wi-Fi to start searching networks.
Second, is that it is slow.
 
I've read other threads but none of the suggestions seem to be working.

Here are all the details:

```
sudo lshw -C network

  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: c0:14:3d:d9:ff:e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.118 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f2d00000-f2d03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: b8:88:e3:35:a5:9d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0c04000-f0c04fff memory:f0c00000-f0c03fff

rfkill list

0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no

sudo iwlist scanning

lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:60:64:56:4E:3E
                    ESSID:"bobby"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1E:E5:8F:0E:9E
                    ESSID:"Linksys"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-40 dBm  Noise level:-96 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:24:B2:1F:D1:BC
                    ESSID:"OPTUSA1FD1BA"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-93 dBm
                    IE: Unknown: DD8C0050F204104A00011010440001021041000100103B00010310470010C996901D79F38A87318237C9CD40CD2D102100074E45544745415210230009444738333447557635102400094447383334475576351042000A313233343536373839301054000800060050F2040001101100174447383334475576352028576972656C65737320415029100800020086
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

eth0      Interface doesn't support scanning.


cat /etc/network/interfaces

auto lo
iface lo inet loopback


cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1c.4 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 5 [8086:1e18] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e57] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5229] (rev 01)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)

lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:21f4 Broadcom Corp. 
Bus 001 Device 004: ID 147e:1002 Upek 
Bus 002 Device 003: ID 5986:02d2 Acer, Inc 

uname -a

Linux thinkpad 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

dmesg | egrep "8180|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt5|rt6|rt7|usb|witch|wl"

[    0.000000] No AGP bridge found
[    0.000000] found SMP MP-table at [ffff8800000f0100] f0100
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.515001] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.476495] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    1.476497] HEST: Table not found.
[    1.506766] i2c-core: driver [aat2870] using legacy suspend method
[    1.506767] i2c-core: driver [aat2870] using legacy resume method
[    1.506896] usbcore: registered new interface driver usbfs
[    1.506903] usbcore: registered new interface driver hub
[    1.506922] usbcore: registered new device driver usb
[    1.509853] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.511866] Switching to clocksource hpet
[    1.518640] pnp: PnP ACPI: found 12 devices
[    1.552648] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.552875] ACPI: Lid Switch [LID0]
[    1.556117] ERST: Table is not found!
[    1.680594] ata2: SATA max UDMA/133 abar m2048@0xf3718000 port 0xf3718180 irq 40
[    1.699693] hub 1-0:1.0: USB hub found
[    1.719656] hub 2-0:1.0: USB hub found
[    1.720047] hub 3-0:1.0: USB hub found
[    1.720218] hub 4-0:1.0: USB hub found
[    1.767536] usbcore: registered new interface driver libusual
[    1.786013] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.000261] ata1.00: ATA-8: SAMSUNG MZ7PC128HAFU-000L1, CXM04L1Q, max UDMA/133
[    2.001254] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MZ7PC128 CXM0 PQ: 0 ANSI: 5
[    2.011194] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.123708] r8169 0000:04:00.0: eth0: RTL8168evl/8111evl at 0xffffc90000642000, b8:88:e3:35:a5:9d, XID 0c900800 IRQ 42
[    2.123712] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.143512] hub 1-1:1.0: USB hub found
[    2.254874] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.391356] hub 2-1:1.0: USB hub found
[    2.452512] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.462694] usb 1-1.3: new full-speed USB device number 3 using ehci_hcd
[    2.490800] lp: driver loaded but no devices found
[    2.526517] Switching to clocksource tsc
[    2.544289] wl: module license 'MIXED/Proprietary' taints kernel.
[    2.548885] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.548894] wl 0000:03:00.0: setting latency timer to 64
[    2.670426] usb 1-1.4: new full-speed USB device number 4 using ehci_hcd
[    2.730343] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[    2.730482] usbcore: registered new interface driver btusb
[    2.732450] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    2.834216] usb 2-1.6: new high-speed USB device number 3 using ehci_hcd
[    2.994581] uvcvideo: Found UVC 1.00 device Integrated Camera (5986:02d2)
[    2.998813] input: Integrated Camera as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input5
[    2.999193] usbcore: registered new interface driver uvcvideo
[    3.270516] Console: switching to colour frame buffer device 200x56
[    3.358386] r8169 0000:04:00.0: eth0: link down
[    3.358631] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.361229] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.965086] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    3.965179] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    3.965267] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    3.965343] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.309546] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   16.534507] input: ThinkPad Bluetooth Laser Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/bluetooth/hci0/hci0:11/input13
[   35.340040] eth1: no IPv6 routers present

sudo dmidecode|egrep "Manufact|Product"

	Manufacturer: Intel(R) Corporation
	Manufacturer: Samsung
	Manufacturer: Not Specified
	Manufacturer: LENOVO
	Product Name: 3364CTO
	Manufacturer: LENOVO
	Product Name: 3364CTO
	Manufacturer: LENOVO
	Manufacturer: SMP
	SBDS Manufacture Date: 2012-07-25

iwconfig

lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:210  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.


sudo lsmod

Module                  Size  Used by
hidp                   22628  1 
hid                    99559  1 hidp
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
joydev                 17693  0 
bnep                   18281  2 
uvcvideo               72627  0 
parport_pc             32866  0 
rfcomm                 47604  16 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
ppdev                  17113  0 
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          81819  1 
btusb                  18288  4 
bluetooth             180104  28 hidp,bnep,rfcomm,btusb
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17390  0 
psmouse                97362  0 
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2568210  0 
wmi                    19256  0 
i915                  473240  2 
snd                    78855  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
nvram                  14413  1 thinkpad_acpi
lib80211               14381  2 lib80211_crypt_tkip,wl
tpm_tis                18804  0 
soundcore              15091  1 snd
mac_hid                13253  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 

cat /var/lib/NetworkManager/NetworkManager.state


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


```

Any help would be greatly appreciated. Thank you.

---

### Post by MicroMina on 2012-10-02
Ahh, changed the DNS servers in Network Manager to Google's (8.8.8.8, 8.8.4.4) Speeds are all good now.
Anyone know why my Wi-Fi isn't ready on startup right away? I have to wait about 10 seconds for it to start searching for networks.

---

