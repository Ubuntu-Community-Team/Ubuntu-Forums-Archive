---
title: "REALTEK - wireless problems."
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by Knowledge-is-power on 2011-07-21
**REALTEK driver problems / network problems**             
                                                                [SIZE=2]Hi,
  
I have a serious problem with my wireless...
my laptop has this realtek rtl8191sevb[/SIZE] NIC installed.
I've tryed everything to update it or... find any solutions available that solve my problems...
i keep coming across broadcom drivers and packages in the software center but these wont work for me will they?

 Please can someone help me find a solution for my realtek network card,   it keeps getting worse. now I cant even search for wireless networks  as  they are blacked out... I'm really lost as I've only just started  using  linux for the first time... I'm technically savvy in windows but  I've dived into the  deep end with linux straight a way...

never in my life did i expect more problems then i get with windows...
i guess it's just the compatibility issues to be fair... 


Before i could connect to the router, but without INTERNET access... which to be frank is useless to me.
im writing this hooked up via Ethernet witch is a pain as it's down stairs in a hallway.


as my name suggests, Knowledge is power... and right now I am powerless.
Please, enlighten me!

I would be very greatful!



(reposted thread (apologies it was originally in the wrong place)



results of the commands:

james@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 310M] [10de:0a75] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  05)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
16:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382] (rev 20)
16:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (rev 20)
16:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383] (rev 20)
16:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384] (rev 20)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath  Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
ff:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
ff:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated  Memory Controller Target Address Decoder [8086:2c99] (rev 04)
ff:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
ff:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated  Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
ff:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated  Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
ff:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated  Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
ff:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated  Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev  04)
ff:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated  Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
ff:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated  Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
ff:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated  Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
ff:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated  Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev  04)
james@ubuntu:~$ sudo lshw -C network
[sudo] password for james: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:51:3b:e5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.2.2 latency=0 link=yes  multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:7000(size=256) memory:d3104000-d3104fff memory:d3100000-d3103fff memory:d3120000-d313ffff
  *-network DISABLED
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:d2:04:26
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE  driverversion=0017.0507.2010 firmware=0 ip=192.168.2.3 latency=0 link=no  multicast=yes wireless=802.11bg
       resources: irq:17 ioport:5000(size=256) memory:d7300000-d7303fff
james@ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93525  1 
crc_itu_t              12707  1 udf
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_hdmi     28167  4 
binfmt_misc            17565  1 
snd_hda_codec_realtek   336771  1 
nvidia              10709116  32 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
i7core_edac            27903  0 
r8192se_pci           524220  0 
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
edac_core              53845  3 i7core_edac
psmouse                73535  0 
jmb38x_ms              17596  0 
memstick               16520  1 jmb38x_ms
serio_raw              13166  0 
videodev               82052  1 uvcvideo
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17078  1 videodev
cfg80211              178528  1 r8192se_pci
snd                    67382  14  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13898  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
james@ubuntu:~$

---

### Post by ratcheer on 2011-07-21
Run "sudo lspci -v" to see which, if any, kernel driver is being used. Then check the Realtek web site to make sure it is the correct driver for your NIC. If it is not the correct one, download and install the correct driver from Realtek.

Tim

---

### Post by Knowledge-is-power on 2011-07-21
Thank you for the contribution Tim,
Here is the result of that command;

    I/O ports at 5000 [size=256]
    Memory at d7300000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 88-55-22-fe-ff-4c-e0-00
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci

16:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d5a00300 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

16:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20) (prog-if 01)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: fast devsel, IRQ 16
    Memory at d5a00200 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel modules: sdhci-pci

16:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d5a00100 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

16:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d5a00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0
    Kernel driver in use: i7core_edac
    Kernel modules: i7core_edac

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

james@ubuntu:~$ clear

james@ubuntu:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
    Subsystem: Intel Corporation Device 0000
    Flags: fast devsel
    Capabilities: [40] #00 [0000]

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: d2000000-d30fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: [40] Subsystem: Intel Corporation Device 0000
    Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot+), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0 Len=000 <?>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0 Len=000 <?>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0 Len=000 <?>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
    Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
    Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
    Flags: fast devsel

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d8405000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d8408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at d8400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=0
    I/O behind bridge: 00007000-00008fff
    Memory behind bridge: d7c00000-d83fffff
    Prefetchable memory behind bridge: 00000000d3100000-00000000d39fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device fd30
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=0b, sec-latency=0
    I/O behind bridge: 00005000-00006fff
    Memory behind bridge: d7300000-d7bfffff
    Prefetchable memory behind bridge: 00000000d3a00000-00000000d41fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device fd30
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=10, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d6b00000-d72fffff
    Prefetchable memory behind bridge: 00000000d4200000-00000000d49fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device fd30
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=11, subordinate=15, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d6300000-d6afffff
    Prefetchable memory behind bridge: 00000000d4a00000-00000000d51fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device fd30
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=16, subordinate=1a, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d5a00000-d62fffff
    Prefetchable memory behind bridge: 00000000d5200000-00000000d59fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device fd30
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d8407000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=1b, subordinate=1b, sec-latency=32
    Capabilities: [50] Subsystem: Toshiba America Info Systems Device fd30

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 46
    I/O ports at a048 [size=8]
    I/O ports at a054 [size=4]
    I/O ports at a040 [size=8]
    I/O ports at a050 [size=4]
    I/O ports at a020 [size=32]
    Memory at d8408800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: medium devsel, IRQ 11
    Memory at d8404000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 9000 [size=128]
    [virtual] Expansion ROM at d3080000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 45
    I/O ports at 7000 [size=256]
    Memory at d3104000 (64-bit, prefetchable) [size=4K]
    Memory at d3100000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at d3120000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 56-00-00-00-36-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 5000 [size=256]
    Memory at d7300000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 88-55-22-fe-ff-4c-e0-00
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci

16:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d5a00300 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

16:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20) (prog-if 01)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: fast devsel, IRQ 16
    Memory at d5a00200 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel modules: sdhci-pci

16:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d5a00100 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

16:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
    Subsystem: Toshiba America Info Systems Device fd30
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d5a00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0
    Kernel driver in use: i7core_edac
    Kernel modules: i7core_edac

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

james@ubuntu:~$

---

### Post by nm_geo on 2011-07-21
Wow lots of info..

Ok you have a wireless driver installed and it agrees with your wireless pci.

configuration: broadcast=yes[COLOR=Red] driver=rtl819xSE[/COLOR]   driverversion=0017.0507.2010 firmware=0 ip=[COLOR=Red]192.168.2.3[/COLOR] latency=0 link=no   multicast=yes wireless=802.11bg

and ip assigned 

```
lspci -nn | grep 0280
```

should have given 

07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [[COLOR=Red]10ec:8172[/COLOR]] (rev 1)

hmmm. check this one...

```
rfkill list all


```

---

### Post by ratcheer on 2011-07-21
If you end up needing the driver, it is at:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2)

Tim

---

### Post by Knowledge-is-power on 2011-07-21
Ok so the first command gave me:

"ames@ubuntu:~$ lspci -nn | grep 0280
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)"

and the second command gave me:

"james@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
james@ubuntu:~$ "

thank you both for giving up your time to help me so far.
I think that driver will come in handy.
(although I don't even know how to install it)

---

### Post by nm_geo on 2011-07-21
You have an wireless ip...  So  I would think you have a working driver..
Have you enabled wireless in network manager?

---

### Post by nm_geo on 2011-07-21
out of curiosity try this

```
sudo iwlist scanning
```

---

### Post by Knowledge-is-power on 2011-07-21
It is in enabled but for some reason the "wireless networks" button is blacked out!
therefor, without 3rd party apps like Wicd Network Manager I cant even see any of the local networks 
(within my location) 

Just out of question... I happened to use this DNS service... it gave me a default gateway and an address
208.67.222.222, 
208.67.220.220 (secondary adress)
and a default gateway of 194.145.148.66 <------ that has changed. im sure of it... (since earlier it was 84)
but yeah, could this be the culprit? it works fine with windows... 

I wasn't sure what the service did but it made port forwarding easier for my console or something?

but yeah... im not sure what to do...
i just downloaded Wicd Network manager... and it froze after connecting to SSIDHome (my network)
Hmmmmm...

---

### Post by nm_geo on 2011-07-21
> **Knowledge-is-power said:**
> It is in enabled but for some reason the "wireless networks" button is blacked out!
therefor, without 3rd party apps like Wicd Network Manager I cant even see any of the local networks 
(within my location) 

Just out of question... I happened to use this DNS service... it gave me a default gateway and an address
208.67.222.222, 
208.67.220.220 (secondary adress)
and a default gateway of 194.145.148.66 <------ that has changed. im sure of it... (since earlier it was 84)
but yeah, could this be the culprit? it works fine with windows... 

I wasn't sure what the service did but it made port forwarding easier for my console or something?

but yeah... im not sure what to do...
i just downloaded Wicd Network manager... and it froze after connecting to SSIDHome (my network)
Hmmmmm...

You need to remove network manager if you are going to use wicd. They conflict each other..

Your wireless AP is assigning this one [COLOR=Red]192.168.2.3[/COLOR] .. 
you might boot windows and check the ip there too ..

---

### Post by Knowledge-is-power on 2011-07-21
Ohhh sorry I dint see that last command,
the results are:

james@ubuntu:~$ sudo iwlist scanning
[sudo] password for james: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:B2:34:E5:2E
                    ESSID:"SKY30618"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality=100/100  Signal level=-46 dBm  Noise level=-120 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 9ms ago
          Cell 02 - Address: 08:86:3B:0E:DD:EC
                    ESSID:"SSIDHome"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=100/100  Signal level=-46 dBm  Noise level=-120 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B2860108863B0EDDEC103C000101
                    Extra: Last beacon: 66ms ago
          Cell 03 - Address: 00:17:3F:18:3E:BD
                    ESSID:"Belkin_G_Plus_MIMO_ADSL"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=100/100  Signal level=-46 dBm  Noise level=-120 dBm
                    Extra: Last beacon: 7ms ago
          Cell 04 - Address: 00:26:44:B6:C1:6C
                    ESSID:"PlusnetWirelessB6C16C"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:65 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=100/100  Signal level=-46 dBm  Noise level=-120 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 122ms ago

james@ubuntu:~$ 

(SSIDHome is my home's network)
"Belkin_G_Plus_MIMO_ADSL" is the router.

I don't know why my network has 2, broad casted I haven't seen it anywhere else, but it does.

---

### Post by nm_geo on 2011-07-21
Apparently, your adsl ethernet router has wireless abilities too.. Your Ubuntu box is seeing that the wireless has N capabilities the adsl router only has g capabilities.  Now in my mind if you can scan them the wicd or network manager should let you sign in and take off.

---

### Post by nm_geo on 2011-07-22
**Quality=100/100  Signal level=-46 dBm  Noise level=-120 dBm**

That line looks very weird to me on all the scans.

By the way,  what version of Ubuntu and kernel are we dealing with.

```
cat /etc/lsb-release; uname -r
```

That will tell us.

have you removed nm and got wicd working?

---

### Post by Knowledge-is-power on 2011-07-22
Hmmmm Indeed... it is rather strange...

heres the command result;

james@ubuntu:~$ cat /etc/lsb-release; uname -r
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
2.6.38-10-generic
james@ubuntu:~$ 


I'm a bit worried at how odd this is.
and yes I removed, NM and have installed Wicd working... ish.

theres a lot fields i'm not sure how to fill out... 
under the headings "Use static Ip's"
use static dns...

---

### Post by nm_geo on 2011-07-22
I only use Wicd on a Maverick 10.10 Install on my laptop and I keep it rather simple.
gfk is my ESSID I do not use static ip.   I let my APs do the work of assigning my ips. Here is a screenshot of my Wicd on Maverick. 

Try to boot without your ethernet cable and setup Wicd.

Do an 

```
sudo ifconfig
```

and post results

---

### Post by Knowledge-is-power on 2011-07-22
Ahhhh I see.
I decided on dns because it gives me like double my bandwidth...
4Mb/s instead of 1.8... (I live in the country side you see)

I did a fresh install of Ubuntu 11.04....

---

### Post by Knowledge-is-power on 2011-07-22
Ok... this is getting to the very point where i'm going to snap
36 hours without sleep in attempt to fix this problem...
Very little result...

Thankyou all for trying your best to help but I really don't know what could solve this problem. I spent 2 hours just now going through the other threads with very little sense of solving the problem....

I feel that ubuntu should be able to work with the windows network profile (you can save it to USB) to transfer settings across, if someone made an app that translated the settings apropriotely, it would save all network problems for everyone! which would be fantastic and a feat in itself... I might be new to ubuntu but it doesnt mean i can't contribute developement ideas.

---

### Post by JackerWilliams on 2012-04-20
I had gone through the post. However, with no Internet connection in Open Suse, I'm sure about how to get the respiratory and all that stuff, and not sure exactly what to download. It has been established that I need to update . The adding in of respirators and searching for files is a basic function, one should understand before also ding upgrade.



[IP CCTV Sydney]("http://www.acgfs.com.au/")
[Security Systems Sydney]("http://www.acgfs.com.au/")

---

