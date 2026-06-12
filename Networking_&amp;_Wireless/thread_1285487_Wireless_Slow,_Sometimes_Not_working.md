---
title: "Wireless Slow, Sometimes Not working"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by Aayn on 2009-10-07
Before this thread I posted one with similar problems here 

[http://ubuntuforums.org/showthread.php?t=1280945](http://ubuntuforums.org/showthread.php?t=1280945)

On that thread my wired and wireless were not functioning properly, but I was finally able to get the wired to work. 

So, I am posting a thread on just the wireless problem.

Here's a list of my pc specs.

Model ~
Brand ASUS
Series G Series
Model G1S-B1

Operating System Ubuntu 9.04 64bit !!!!! ...and vista....
CPU Type Intel Core 2 Duo T7700 2.4G
Screen 15.4" WSXGA+
Memory Size 2GB DDR2 667
Hard Disk 200GB 7200RPM
Optical Drive DVD Super Multi
Graphics Card NVIDIA GeForce 8600M GT
Video Memory 256MB GDDR3 VRAM, TurboCache up to 512MB
Communication Modem, Gigabit LAN and WLAN
Card slot 1 x Express Card

My wireless card uses the intel 4965 drivers.

I have been having very very very slow wireless speeds. I also have Vista installed... and I don't get any problems at all with my networking and internet there.

When I was trying to update it went even slower and synaptic downloads at 15kbs. At it's highest download rate I get 30kbs in synaptic, but that doesn't last very long.

My vista speeds are over 500kbs....


Things I have tried so far... I will continue to update what I have tried.

This seems to disable ipv6 as I do not get an output from ( lsmod | grep inet6 ) when I run it.

echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

So, ipv6 does not seem to be the problem.

I have tried changing the bit rate with ( sudo iwconfig wlan0 rate 5.5M ) and still a no go...

I have tried changing the /etc/nsswitch.conf ( hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 ) and replacing it with ( hosts: files dns ). Still a no go....

I have tried changing the MTU settings and still a no go....

I have been trying to get ndiswrapper to work and have not yet been successful.  I am currently still trying to load my driver in there and get it to work.  While installing and trying to get ndiswrapper to work my wireless went totally down, but I was able to get it working again using (( sudo ifup wlan0 )).

So, here are some reads on my system. 


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(( ifconfig ))
~~~~~~~~~~~~~~
[HTML]eth0      Link encap:Ethernet  HWaddr 00:1d:60:dc:c7:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0xa000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:60:dc:c7:94  
          inet addr:169.254.9.114  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:249 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3853 (3.8 KB)  TX bytes:3853 (3.8 KB)

pan0      Link encap:Ethernet  HWaddr da:de:35:52:c7:60  
          inet6 addr: fe80::d8de:35ff:fe52:c760/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:11229 (11.2 KB)

pan0:avahi Link encap:Ethernet  HWaddr da:de:35:52:c7:60  
          inet addr:169.254.7.59  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:ce:3f:b9  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fece:3fb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2045835 (2.0 MB)  TX bytes:315016 (315.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-CE-3F-B9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/HTML]

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(( iwconfig ))
~~~~~~~~~~~~~~
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ElaTioN"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:6F:61:96   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-43 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/HTML]


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(( lsmod )) 
~~~~~~~~~~~
[HTML]Module                  Size  Used by
arc4                   10240  2 
ecb                    11392  2 
iwlagn                114820  0 
iwlcore               106624  1 iwlagn
mac80211              253832  2 iwlagn,iwlcore
cfg80211               43552  3 iwlagn,iwlcore,mac80211
nls_iso8859_1          13440  1 
nls_cp437              15104  1 
vfat                   21120  1 
fat                    65840  1 vfat
binfmt_misc            18828  1 
ppdev                  16904  0 
bridge                 64160  0 
stp                    11268  1 bridge
bnep                   23168  2 
input_polldev          12816  0 
lp                     20676  0 
parport                50188  2 ppdev,lp
snd_hda_intel         557236  5 
snd_pcm_oss            52352  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                98056  3 snd_hda_intel,snd_pcm_oss
mmc_block              19336  2 
snd_seq_dummy          11524  0 
snd_seq_oss            42496  0 
snd_seq_midi           15872  0 
snd_rawmidi            33664  1 snd_seq_midi
snd_seq_midi_event     16640  2 snd_seq_oss,snd_seq_midi
snd_seq                66848  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              33544  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 20864  0 
snd                    79432  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci              16896  0 
iTCO_wdt               21632  0 
soundcore              17312  1 snd
intel_agp              39280  0 
sdhci                  27396  1 sdhci_pci
iTCO_vendor_support    12420  1 iTCO_wdt
btusb                  22040  2 
snd_page_alloc         18832  2 snd_hda_intel,snd_pcm
nvidia               8124728  38 
uvcvideo               69768  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45312  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
psmouse                64028  0 
serio_raw              14468  0 
pcspkr                 11136  0 
video                  29204  6 
output                 11648  1 video
asus_laptop            27996  0 
led_class              13064  2 iwlcore,asus_laptop
ndiswrapper           258104  0 
usbhid                 47296  0 
usb_storage            94912  2 
ohci1394               42548  0 
ieee1394              110176  1 ohci1394
r8169                  46724  0 
mii                    14464  1 r8169
fbcon                  50048  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
[/HTML]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(( lspci ))
~~~~~~~~~~~
[HTML]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
07:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)[/HTML]

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(( lshw -C network ))
~~~~~~~~~~~~~~~~~~~~~
[HTML]*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:dc:c7:94
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:ce:3f:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.3 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: da:de:35:52:c7:60
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/HTML]

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(( dmesg ))
~~~~~~~~~~~

[HTML][    2.467656] pci_express 0000:00:1c.4:pcie03: allocate port service
[    2.467755] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.468595] pciehp 0000:00:01.0:pcie02: HPC vendor_id 8086 device_id 2a01 ss_vid 0 ss_did 0
[    2.468655] pciehp 0000:00:01.0:pcie02: service driver pciehp loaded
[    2.469115] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 283f ss_vid 0 ss_did 0
[    2.469169] pciehp 0000:00:1c.0:pcie02: service driver pciehp loaded
[    2.469605] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 2841 ss_vid 0 ss_did 0
[    2.469657] pciehp 0000:00:1c.1:pcie02: service driver pciehp loaded
[    2.470105] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 2843 ss_vid 0 ss_did 0
[    2.470158] pciehp 0000:00:1c.2:pcie02: service driver pciehp loaded
[    2.470595] pciehp 0000:00:1c.3:pcie02: HPC vendor_id 8086 device_id 2845 ss_vid 0 ss_did 0
[    2.470645] pciehp 0000:00:1c.3:pcie02: service driver pciehp loaded
[    2.471094] pciehp 0000:00:1c.4:pcie02: HPC vendor_id 8086 device_id 2847 ss_vid 0 ss_did 0
[    2.471147] pciehp 0000:00:1c.4:pcie02: service driver pciehp loaded
[    2.471154] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.471343] ACPI: AC Adapter [AC0] (on-line)
[    2.508260] ACPI: Battery Slot [BAT0] (battery present)
[    2.508324] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.508326] ACPI: Power Button (FF) [PWRF]
[    2.508377] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    2.508383] ACPI: Sleep Button (CM) [SLPB]
[    2.508423] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    2.510472] ACPI: Lid Switch [LID]
[    2.511215] ACPI: SSDT 7FFC63A0, 02C8 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    2.511769] ACPI: SSDT 7FFC6700, 0712 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    2.512727] Monitor-Mwait will be used to enter C-1 state
[    2.512729] Monitor-Mwait will be used to enter C-2 state
[    2.512742] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.512767] processor ACPI_CPU:00: registered as cooling_device0
[    2.512770] ACPI: Processor [P001] (supports 8 throttling states)
[    2.513146] ACPI: SSDT 7FFC62D0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    2.513553] ACPI: SSDT 7FFC6670, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    2.514570] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    2.514587] processor ACPI_CPU:01: registered as cooling_device1
[    2.514590] ACPI: Processor [P002] (supports 8 throttling states)
[    2.521740] thermal LNXTHERM:01: registered as thermal_zone0
[    2.522819] ACPI: Thermal Zone [THRM] (94 C)
[    2.545457] Linux agpgart interface v0.103
[    2.545460] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.546422] brd: module loaded
[    2.546742] loop: module loaded
[    2.546807] Fixed MDIO Bus: probed
[    2.546812] PPP generic driver version 2.4.2
[    2.546862] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.546888] Driver 'sd' needs updating - please use bus_type methods
[    2.546896] Driver 'sr' needs updating - please use bus_type methods
[    2.546938] ahci 0000:07:00.0: version 3.0
[    2.546952] ahci 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.558277] ahci 0000:07:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    2.558280] ahci 0000:07:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.558285] ahci 0000:07:00.0: setting latency timer to 64
[    2.558424] scsi0 : ahci
[    2.558485] ata1: SATA max UDMA/133 abar m8192@0xfe9fe000 port 0xfe9fe100 irq 16
[    2.863026] ata1: SATA link down (SStatus 0 SControl 300)
[    2.885047] ata_piix 0000:00:1f.1: version 2.12
[    2.885052] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.885085] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.885194] scsi1 : ata_piix
[    2.885250] scsi2 : ata_piix
[    2.885982] ata2: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.885984] ata3: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.056335] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NR02, max UDMA/33
[    3.062274] ata2.00: configured for UDMA/33
[    3.075277] ata3: port disabled. ignoring.
[    3.086039] isa bounce pool size: 16 pages
[    3.089097] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NR02 PQ: 0 ANSI: 5
[    3.099987] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.099989] Uniform CD-ROM driver Revision: 3.20
[    3.100069] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.100110] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    3.100128] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    3.100131] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.251271] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.251347] scsi3 : ata_piix
[    3.251402] scsi4 : ata_piix
[    3.252622] ata4: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 20
[    3.252627] ata5: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 20
[    4.013057] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.013067] ata4.01: SATA link down (SStatus 0 SControl 300)
[    4.016394] ata4.00: ATA-8: Hitachi HTS722020K9SA00, DC4OC54P, max UDMA/133
[    4.016396] ata4.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.022661] ata4.00: configured for UDMA/133
[    4.654050] ata5.00: SATA link down (SStatus 0 SControl 300)
[    4.654058] ata5.01: SATA link down (SStatus 0 SControl 0)
[    4.665312] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HTS72202 DC4O PQ: 0 ANSI: 5
[    4.665397] sd 3:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    4.665412] sd 3:0:0:0: [sda] Write Protect is off
[    4.665414] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.665438] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.665491] sd 3:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    4.665504] sd 3:0:0:0: [sda] Write Protect is off
[    4.665506] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.665529] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.665532]  sda: sda1 sda2 < sda5 sda6 >
[    5.019013] sd 3:0:0:0: [sda] Attached SCSI disk
[    5.019052] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    5.019652] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.019668] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.019680] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.019683] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.019739] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    5.023636] ehci_hcd 0000:00:1a.7: debug port 1
[    5.023641] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    5.023679] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfebff400
[    5.033258] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    5.033331] usb usb1: configuration #1 chosen from 1 choice
[    5.033354] hub 1-0:1.0: USB hub found
[    5.033361] hub 1-0:1.0: 4 ports detected
[    5.033461] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.033470] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.033473] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.033515] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    5.037431] ehci_hcd 0000:00:1d.7: debug port 1
[    5.037436] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.037470] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebff000
[    5.047258] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.047305] usb usb2: configuration #1 chosen from 1 choice
[    5.047326] hub 2-0:1.0: USB hub found
[    5.047332] hub 2-0:1.0: 6 ports detected
[    5.047414] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.047428] uhci_hcd: USB Universal Host Controller Interface driver
[    5.047448] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.047453] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.047455] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.047502] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    5.047524] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    5.047588] usb usb3: configuration #1 chosen from 1 choice
[    5.047608] hub 3-0:1.0: USB hub found
[    5.047614] hub 3-0:1.0: 2 ports detected
[    5.047687] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.047692] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    5.047694] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.047737] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    5.047791] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000dc00
[    5.047853] usb usb4: configuration #1 chosen from 1 choice
[    5.047874] hub 4-0:1.0: USB hub found
[    5.047879] hub 4-0:1.0: 2 ports detected
[    5.047953] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.047959] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.047961] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.048001] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    5.048022] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    5.048086] usb usb5: configuration #1 chosen from 1 choice
[    5.048105] hub 5-0:1.0: USB hub found
[    5.048110] hub 5-0:1.0: 2 ports detected
[    5.048185] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.048190] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.048193] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.048234] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    5.048293] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    5.048356] usb usb6: configuration #1 chosen from 1 choice
[    5.048378] hub 6-0:1.0: USB hub found
[    5.048383] hub 6-0:1.0: 2 ports detected
[    5.048454] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.048459] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.048461] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.048502] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    5.048523] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    5.048587] usb usb7: configuration #1 chosen from 1 choice
[    5.048607] hub 7-0:1.0: USB hub found
[    5.048612] hub 7-0:1.0: 2 ports detected
[    5.048722] usbcore: registered new interface driver libusual
[    5.048753] usbcore: registered new interface driver usbserial
[    5.048764] USB Serial support registered for generic
[    5.048777] usbcore: registered new interface driver usbserial_generic
[    5.048779] usbserial: USB Serial Driver core
[    5.048820] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    5.051262] i8042.c: Detected active multiplexing controller, rev 1.1.
[    5.051935] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.051939] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    5.051941] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    5.051943] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    5.051944] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    5.063039] mice: PS/2 mouse device common for all mice
[    5.111057] rtc_cmos 00:03: RTC can wake from S4
[    5.111098] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    5.111144] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    5.111173] device-mapper: uevent: version 1.0.3
[    5.111229] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    5.112303] device-mapper: multipath: version 1.0.5 loaded
[    5.112306] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.112404] cpuidle: using governor ladder
[    5.112479] cpuidle: using governor menu
[    5.112856] TCP cubic registered
[    5.112888] NET: Registered protocol family 10
[    5.113275] lo: Disabled Privacy Extensions
[    5.113542] NET: Registered protocol family 17
[    5.113560] Bluetooth: L2CAP ver 2.11
[    5.113561] Bluetooth: L2CAP socket layer initialized
[    5.113564] Bluetooth: SCO (Voice Link) ver 0.6
[    5.113565] Bluetooth: SCO socket layer initialized
[    5.113588] Bluetooth: RFCOMM socket layer initialized
[    5.113597] Bluetooth: RFCOMM TTY layer initialized
[    5.113599] Bluetooth: RFCOMM ver 1.10
[    5.114623] registered taskstats version 1
[    5.114756]   Magic number: 13:273:689
[    5.114833] rtc_cmos 00:03: setting system clock to 2009-10-07 15:41:26 UTC (1254930086)
[    5.114835] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.114836] EDD information not available.
[    5.114877] Freeing unused kernel memory: 528k freed
[    5.115091] Write protecting the kernel read-only data: 6816k
[    5.143344] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    5.335015] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    5.463105] usb 1-1: configuration #1 chosen from 1 choice
[    5.500888] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.500913] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.500935] r8169 0000:02:00.0: setting latency timer to 64
[    5.501099] r8169 0000:02:00.0: irq 2297 for MSI/MSI-X
[    5.501645] eth0: RTL8168b/8111b at 0xffffc2000007a000, 00:1d:60:dc:c7:94, XID 38000000 IRQ 2297
[    5.525046] ohci1394 0000:08:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.567282] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    5.607368] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.681618] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 0, changing to 9
[    5.681621] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x2 has an invalid bInterval 0, changing to 9
[    5.682068] usb 1-2: configuration #1 chosen from 1 choice
[    5.835276] usb 2-3: new high speed USB device using ehci_hcd and address 3
[    5.950169] usb 2-3: configuration #1 chosen from 1 choice
[    5.954147] Initializing USB Mass Storage driver...
[    5.954275] scsi5 : SCSI emulation for USB Mass Storage devices
[    5.954412] usbcore: registered new interface driver usb-storage
[    5.954416] USB Mass Storage support registered.
[    5.954570] usb-storage: device found at 3
[    5.954573] usb-storage: waiting for device to settle before scanning
[    5.976019] usbcore: registered new interface driver hiddev
[    5.976085] usbcore: registered new interface driver usbhid
[    5.976088] usbhid: v2.6:USB HID core driver
[    6.031266] PM: Starting manual resume from disk
[    6.031268] PM: Resume from partition 8:5
[    6.031270] PM: Checking hibernation image.
[    6.031476] PM: Resume from disk failed.
[    6.052016] usb 2-4: new high speed USB device using ehci_hcd and address 4
[    6.081587] kjournald starting.  Commit interval 5 seconds
[    6.081597] EXT3-fs: mounted filesystem with ordered data mode.
[    6.169365] usb 2-4: configuration #1 chosen from 1 choice
[    6.177284] scsi6 : SCSI emulation for USB Mass Storage devices
[    6.181439] usb-storage: device found at 4
[    6.181440] usb-storage: waiting for device to settle before scanning
[    6.489014] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    6.653154] usb 5-1: configuration #1 chosen from 1 choice
[    6.672336] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input5
[    6.690049] generic-usb 0003:046D:C01E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[    6.869106] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003b0a87f]
[    6.896018] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    7.127393] usb 7-2: configuration #1 chosen from 1 choice
[    8.727083] usb 2-3: USB disconnect, address 3
[    8.959016] usb 2-3: new high speed USB device using ehci_hcd and address 6
[    9.074113] usb 2-3: configuration #1 chosen from 1 choice
[    9.074285] scsi7 : SCSI emulation for USB Mass Storage devices
[    9.074435] usb-storage: device found at 6
[    9.074437] usb-storage: waiting for device to settle before scanning
[    9.406829] usb 2-3: USB disconnect, address 6
[    9.639012] usb 2-3: new high speed USB device using ehci_hcd and address 7
[    9.754107] usb 2-3: configuration #1 chosen from 1 choice
[    9.754285] scsi8 : SCSI emulation for USB Mass Storage devices
[    9.754424] usb-storage: device found at 7
[    9.754426] usb-storage: waiting for device to settle before scanning
[   11.023227] usb 2-3: USB disconnect, address 7
[   11.141148] udev: starting version 141
[   11.181123] usb-storage: device scan complete
[   11.181598] scsi 6:0:0:0: Direct-Access     WD       6400AAK External 1.05 PQ: 0 ANSI: 4
[   11.182788] sd 6:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[   11.184670] sd 6:0:0:0: [sdb] Write Protect is off
[   11.184673] sd 6:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   11.184675] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.185333] sd 6:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[   11.186085] sd 6:0:0:0: [sdb] Write Protect is off
[   11.186087] sd 6:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   11.186089] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   11.186092]  sdb:<6>usb 2-3: new high speed USB device using ehci_hcd and address 8
[   11.370327] usb 2-3: configuration #1 chosen from 1 choice
[   11.376269] ndiswrapper version 1.53 loaded (smp=yes, preempt=rt)
[   11.376359] scsi9 : SCSI emulation for USB Mass Storage devices
[   11.377772] usb-storage: device found at 8
[   11.377773] usb-storage: waiting for device to settle before scanning
[   11.563795] asus-laptop: Asus Laptop Support version 0.42
[   11.569814] asus-laptop:   G1S model detected
[   11.571602] asus-laptop: Brightness ignored, must be controlled by ACPI video driver
[   11.571644] Registered led device: asus::mail
[   11.571676] Registered led device: asus::touchpad
[   11.571708] Registered led device: asus::gaming
[   11.591515] acpi device:07: registered as cooling_device2
[   11.591699] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input6
[   11.606135] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.656428] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   11.768257] Linux video capture interface: v2.00
[   11.791954] uvcvideo: Found UVC 1.00 device USB2.0 1.3M UVC WebCam  (04f2:b012)
[   11.793056] input: USB2.0 1.3M UVC WebCam  as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input8
[   11.800358] usbcore: registered new interface driver uvcvideo
[   11.800361] USB Video Class driver (v0.1.0)
[   11.879500] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.160580] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   12.160588] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   12.160596] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   12.160602] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   12.160607] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   12.160611] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   12.160615] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   12.160622] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   12.160629] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   12.160634] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   12.160638] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   12.160653] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   12.160658] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   12.160662] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   12.160677] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   12.160685] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   12.160690] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   12.160694] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   12.160699] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   12.160703] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   12.160708] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   12.160712] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   12.160716] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   12.160721] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   12.160725] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   12.160729] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   12.160734] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   12.160739] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   12.160743] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netw4v64'
[   12.161492] ndiswrapper (load_wrap_driver:108): couldn't load driver netw4v64; check system log for messages from 'loadndisdriver'
[   12.176293] usbcore: registered new interface driver ndiswrapper
[   12.778997] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   12.779123] usbcore: registered new interface driver btusb
[   12.793047] iTCO_vendor_support: vendor-support=0
[   12.824183] sdhci: Secure Digital Host Controller Interface driver
[   12.824185] sdhci: Copyright(c) Pierre Ossman
[   12.832748] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   12.853228] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.853484] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   12.853499] iTCO_wdt: No card detected
[   12.855424] sdhci-pci 0000:08:01.1: SDHCI controller found [1180:0822] (rev 22)
[   12.855438] sdhci-pci 0000:08:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.874309] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   12.879087] mmc0: SDHCI controller on PCI [0000:08:01.1] using PIO
[   12.971144] mmc0: new SD card at address 1924
[   12.977997] mmcblk0: mmc0:1924 SD02G 1.87 GiB 
[   12.978063]  mmcblk0: p1
[   13.035106] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.035118] nvidia 0000:01:00.0: setting latency timer to 64
[   13.036262] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   13.045506] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.047830] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.279354] lp: driver loaded but no devices found
[   13.408733] Adding 2931852k swap on /dev/sda5.  Priority:-1 extents:1 across:2931852k
[   13.947702] EXT3 FS on sda6, internal journal
[   14.961567] type=1505 audit(1254955296.346:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2344
[   15.002747] type=1505 audit(1254955296.387:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2348
[   15.002834] type=1505 audit(1254955296.387:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2348
[   15.002868] type=1505 audit(1254955296.387:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2348
[   15.002900] type=1505 audit(1254955296.387:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2348
[   15.099394] type=1505 audit(1254955296.484:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2353
[   15.099575] type=1505 audit(1254955296.484:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2353
[   15.122759] type=1505 audit(1254955296.507:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2357
[   15.501039] r8169: eth0: link down
[   15.501392] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.377400] usb-storage: device scan complete
[   16.378023] scsi 9:0:0:0: Direct-Access     WD       3200BMV External 1.05 PQ: 0 ANSI: 4
[   16.538279]  sdb1
[   16.538408] sd 6:0:0:0: [sdb] Attached SCSI disk
[   16.538481] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   16.539253] sd 9:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   16.540012] sd 9:0:0:0: [sdc] Write Protect is off
[   16.540014] sd 9:0:0:0: [sdc] Mode Sense: 21 00 00 00
[   16.540016] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[   16.540623] sd 9:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   16.541879] sd 9:0:0:0: [sdc] Write Protect is off
[   16.541882] sd 9:0:0:0: [sdc] Mode Sense: 21 00 00 00
[   16.541884] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[   16.541888]  sdc: sdc1
[   20.371438] sd 9:0:0:0: [sdc] Attached SCSI disk
[   20.371516] sd 9:0:0:0: Attached scsi generic sg3 type 0
[   20.614021] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.614023] Bluetooth: BNEP filters: protocol multicast
[   20.630957] Bridge firewalling registered
[   22.334498] ppdev: user-space parallel port driver
[   31.617258] pan0: no IPv6 routers present
[   40.416951] usb 2-3: USB disconnect, address 8
[   40.665016] usb 2-3: new high speed USB device using ehci_hcd and address 9
[   40.780140] usb 2-3: configuration #1 chosen from 1 choice
[   40.789173] scsi10 : SCSI emulation for USB Mass Storage devices
[   40.789494] usb-storage: device found at 9
[   40.789496] usb-storage: waiting for device to settle before scanning
[   45.828973] usb-storage: device scan complete
[   45.829488] scsi 10:0:0:0: Direct-Access     WD       3200BMV External 1.05 PQ: 0 ANSI: 4
[   45.830851] sd 10:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   45.833780] sd 10:0:0:0: [sdc] Write Protect is off
[   45.833783] sd 10:0:0:0: [sdc] Mode Sense: 21 00 00 00
[   45.833785] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[   45.834480] sd 10:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   45.839500] sd 10:0:0:0: [sdc] Write Protect is off
[   45.839503] sd 10:0:0:0: [sdc] Mode Sense: 21 00 00 00
[   45.839505] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[   45.839510]  sdc: sdc1
[   45.841111] sd 10:0:0:0: [sdc] Attached SCSI disk
[   45.841187] sd 10:0:0:0: Attached scsi generic sg3 type 0
[   56.797699] usb 2-3: USB disconnect, address 9
[   57.032013] usb 2-3: new high speed USB device using ehci_hcd and address 10
[   57.147136] usb 2-3: configuration #1 chosen from 1 choice
[   57.151688] scsi11 : SCSI emulation for USB Mass Storage devices
[   57.152646] usb-storage: device found at 10
[   57.152647] usb-storage: waiting for device to settle before scanning
[   62.152126] usb-storage: device scan complete
[   62.152609] scsi 11:0:0:0: Direct-Access     WD       3200BMV External 1.05 PQ: 0 ANSI: 4
[   62.154223] sd 11:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   62.154973] sd 11:0:0:0: [sdc] Write Protect is off
[   62.154975] sd 11:0:0:0: [sdc] Mode Sense: 21 00 00 00
[   62.154977] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[   62.155593] sd 11:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   62.156344] sd 11:0:0:0: [sdc] Write Protect is off
[   62.156346] sd 11:0:0:0: [sdc] Mode Sense: 21 00 00 00
[   62.156347] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[   62.156350]  sdc: sdc1
[   62.202860] sd 11:0:0:0: [sdc] Attached SCSI disk
[   62.202934] sd 11:0:0:0: Attached scsi generic sg3 type 0
[  405.603311] cfg80211: Calling CRDA to update world regulatory domain
[  405.725836] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[  405.725839] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[  405.725920] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  405.725927] iwlagn 0000:03:00.0: setting latency timer to 64
[  405.725975] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[  405.766653] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[  405.766717] iwlagn 0000:03:00.0: irq 2296 for MSI/MSI-X
[  405.767850] phy0: Selected rate control algorithm 'iwl-agn-rs'
[  577.728323] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[  577.976490] Registered led device: iwl-phy0:radio
[  577.976506] Registered led device: iwl-phy0:assoc
[  577.976520] Registered led device: iwl-phy0:RX
[  577.976533] Registered led device: iwl-phy0:TX
[  578.024700] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  579.408818] wlan0: direct probe to AP 00:09:5b:6f:61:96 try 1
[  579.410294] wlan0 direct probe responded
[  579.410296] wlan0: authenticate with AP 00:09:5b:6f:61:96
[  579.412096] wlan0: authenticated
[  579.412099] wlan0: associate with AP 00:09:5b:6f:61:96
[  579.414064] wlan0: RX AssocResp from 00:09:5b:6f:61:96 (capab=0x15 status=0 aid=9)
[  579.414066] wlan0: associated
[  579.433657] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  589.703261] wlan0: no IPv6 routers present[/HTML]

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Any help is much appreciated!!! :KS

Thank you in advance!!!:)

---

### Post by Aayn on 2009-10-07
I have been playing with ndiswrapper and it seems to be installed correctly.

Here is an output from ndiswrapper:

(( ndiswrapper -l ))
[HTML]
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netw4v64 : driver installed
	device (8086:4229) present (alternate driver: iwlagn)[/HTML]


I just can't seem to get the intel drivers loaded right to see if they work.  It says they are installed too.

From output:

(( sudo ndiswrapper -i ~/drivers/NETw4v64.inf ))
[HTML]
driver netw4v64 is already installed[/HTML]


So, my question is... How do I get the wifi drivers I have installed to register?  Do I have to blacklist iwlagn?  If so, I have already tried that and my wireless stopped working until I defaulted the blacklist.conf file.

---

### Post by Aayn on 2009-10-07
Here is my blacklist file.

{ etc/modprobe.d/blacklist.conf }

[HTML]# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist ssb

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac[/HTML]

The only things I have changed in this file at the moment is ~~> 

blacklist b43
blacklist ssb

---

