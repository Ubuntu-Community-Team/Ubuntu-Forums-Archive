---
title: "Wireless not working - Intep PRO Wireless - Oneiric 11.10 -Gateway 4520"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by PsychicNut on 2011-11-07
Intep PRO Wireless - Oneiric 11.10 -Gateway 4520
Hello. I have been using Ubuntu for years on my notebook but am a newbie at troubleshooting.

I have upgraded every time a new version of Ubuntu comes out. This time I decided to do a fresh install from Live CD dual booted with Windows XP. Things look good except wireless doesn't work. Hardwire DOES work and on the XP side wireless works per normal.

I have gone through the WirelessTroubleShootingGuide wiki to check the basic stuff and found no problems.

Please let me know what to do. Below are the results of the suggested commands (attached document also has the results)
Thanks
PsychicNut

(PS: I am in Oneiric not Gutsy Gibbon as it says on my profile.)

Machine Brand and Model (PC/Laptop):
Gateway 4520 Notebook



```
lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04b3:310b IBM Corp. Red Wheel Mouse

```


```
lspci -nvn | grep -i net
02:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:09.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:10:6a:9a  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe10:6a9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5421398 (5.4 MB)  TX bytes:626707 (626.7 KB)
          Interrupt:10 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:28:05:5d  
          inet6 addr: fe80::20e:35ff:fe28:55d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:278 dropped:278 overruns:0 frame:0
          TX packets:603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:134901 (134.9 KB)
          Interrupt:10 Base address:0xa000 Memory:e0200000-e0200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18624 (18.6 KB)  TX bytes:18624 (18.6 KB)
```


```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  0 
lib80211_crypt_wep     12746  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39822  0 
ipw2200               146148  0 
snd_timer              28932  2 snd_pcm,snd_seq
libipw                 46701  1 ipw2200
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  2 ipw2200,libipw
yenta_socket           27428  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
i915                  505108  2 
binfmt_misc            17292  1 
psmouse                73673  0 
soundcore              12600  1 snd
lib80211               14570  3 lib80211_crypt_wep,ipw2200,libipw
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
8139too                23283  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
8139cp                 22636  0 
usbhid                 41905  0 
hid                    77367  1 usbhid

```

lsmod | grep "wlan_module_name" doesn't do anything


dmesg is too long for me to copy and paste it all. Here is what I got:
```
[    0.103969] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.103973] PCI: setting IRQ 10 as level-triggered
[    0.103979] pci 0000:02:07.1: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.103985] pci 0000:02:07.1: setting latency timer to 64
[    0.103991] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.103995] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.104000] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.104004] pci_bus 0000:02: resource 1 [mem 0xe0200000-0xe02fffff]
[    0.104008] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.104012] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.104016] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.104020] pci_bus 0000:03: resource 0 [io  0x3400-0x34ff]
[    0.104024] pci_bus 0000:03: resource 1 [io  0x3800-0x38ff]
[    0.104028] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.104032] pci_bus 0000:03: resource 3 [mem 0x2c000000-0x2fffffff]
[    0.104036] pci_bus 0000:07: resource 0 [io  0x3c00-0x3cff]
[    0.104040] pci_bus 0000:07: resource 1 [io  0x1400-0x14ff]
[    0.104044] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.104048] pci_bus 0000:07: resource 3 [mem 0x30000000-0x33ffffff]
[    0.104121] NET: Registered protocol family 2
[    0.104226] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.104481] Switched to NOHz mode on CPU #0
[    0.104590] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.104741] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.104893] TCP: Hash tables configured (established 16384 bind 16384)
[    0.104897] TCP reno registered
[    0.104902] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.104916] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.105048] NET: Registered protocol family 1
[    0.105080] pci 0000:00:02.0: Boot video device
[    0.105281] PCI: CLS 64 bytes, default 64
[    0.105382] Simple Boot Flag at 0x36 set to 0x1
[    0.105778] audit: initializing netlink socket (disabled)
[    0.105795] type=2000 audit(1320578572.103:1): initialized
[    0.138161] Trying to unpack rootfs image as initramfs...
[    0.179528] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.187545] VFS: Disk quotas dquot_6.5.2
[    0.187655] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.188941] fuse init (API version 7.16)
[    0.189107] msgmni has been set to 900
[    0.200521] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.204124] io scheduler noop registered
[    0.204131] io scheduler deadline registered
[    0.204195] io scheduler cfq registered (default)
[    0.204448] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.204487] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.204868] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.205067] ACPI: AC Adapter [AC] (on-line)
[    0.205181] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.205891] ACPI: Lid Switch [LID0]
[    0.205973] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.205982] ACPI: Sleep Button [SLPB]
[    0.206046] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.206051] ACPI: Power Button [PWRB]
[    0.206126] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.206131] ACPI: Power Button [PWRF]
[    0.206163] ACPI: acpi_idle registered with cpuidle
[    0.206405] Marking TSC unstable due to TSC halts in idle
[    0.212492] thermal LNXTHERM:00: registered as thermal_zone0
[    0.212498] ACPI: Thermal Zone [THRM] (64 C)
[    0.212538] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.212580] ERST: Table is not found!
[    0.212738] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.214597] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.214607] serial 0000:00:1f.6: PCI INT B disabled
[    0.214772] Linux agpgart interface v0.103
[    0.214849] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[    0.214877] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.215383] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.215561] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.221681] brd: module loaded
[    0.222623] loop: module loaded
[    0.222905] ata_piix 0000:00:1f.1: version 2.13
[    0.222923] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.223097] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    0.223104] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    0.223159] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.223873] isapnp: Scanning for PnP cards...
[    0.276188] scsi0 : ata_piix
[    0.276396] scsi1 : ata_piix
[    0.277356] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.277361] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.278050] Fixed MDIO Bus: probed
[    0.278092] PPP generic driver version 2.4.2
[    0.278203] tun: Universal TUN/TAP device driver, 1.6
[    0.278206] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.278358] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.278499] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 3
[    0.278504] PCI: setting IRQ 3 as level-triggered
[    0.278511] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 3 (level, low) -> IRQ 3
[    0.278537] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.278542] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.278596] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.278638] ehci_hcd 0000:00:1d.7: debug port 1
[    0.282534] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.288866] ehci_hcd 0000:00:1d.7: irq 3, io mem 0xe0100000
[    0.304221] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.304539] hub 1-0:1.0: USB hub found
[    0.304548] hub 1-0:1.0: 6 ports detected
[    0.304673] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.304714] uhci_hcd: USB Universal Host Controller Interface driver
[    0.304981] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[    0.304986] PCI: setting IRQ 5 as level-triggered
[    0.304993] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    0.305007] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.305012] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.305091] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.305126] uhci_hcd 0000:00:1d.0: irq 5, io base 0x00001820
[    0.305321] hub 2-0:1.0: USB hub found
[    0.305327] hub 2-0:1.0: 2 ports detected
[    0.305407] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.305415] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.305420] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.305469] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.305495] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    0.305677] hub 3-0:1.0: USB hub found
[    0.305683] hub 3-0:1.0: 2 ports detected
[    0.305762] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    0.305771] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.305775] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.305827] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.305852] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001860
[    0.306033] hub 4-0:1.0: USB hub found
[    0.306039] hub 4-0:1.0: 2 ports detected
[    0.306193] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.309837] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.309854] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.313183] mousedev: PS/2 mouse device common for all mice
[    0.315031] rtc_cmos 00:01: RTC can wake from S4
[    0.315379] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.315402] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    0.315622] device-mapper: uevent: version 1.0.3
[    0.315752] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.315808] EISA: Probing bus 0 at eisa.0
[    0.315818] Cannot allocate resource for EISA slot 1
[    0.315822] Cannot allocate resource for EISA slot 2
[    0.315825] Cannot allocate resource for EISA slot 3
[    0.315847] EISA: Detected 0 cards.
[    0.315865] cpufreq-nforce2: No nForce2 chipset.
[    0.315918] cpuidle: using governor ladder
[    0.315995] cpuidle: using governor menu
[    0.315998] EFI Variables Facility v0.08 2004-May-17
[    0.321150] TCP cubic registered
[    0.321952] NET: Registered protocol family 10
[    0.323268] ACPI: Battery Slot [BAT0] (battery present)
[    0.323819] NET: Registered protocol family 17
[    0.323856] Registering the dns_resolver key type
[    0.323894] Using IPI No-Shortcut mode
[    0.324106] PM: Hibernation image not present or could not be loaded.
[    0.324124] registered taskstats version 1
[    0.480635] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0P34, max UDMA/33
[    0.480756] ata1.00: ATA-5: HITACHI_DK23FA-60, 00M4A0A2, max UDMA/100
[    0.480761] ata1.00: 117210240 sectors, multi 16: LBA 
[    0.532418] ata1.00: configured for UDMA/100
[    0.532650] ata2.00: configured for UDMA/33
[    0.735788] isapnp: No Plug & Play device found
[    0.736087] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23FA-6 00M4 PQ: 0 ANSI: 5
[    0.736405] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.736642] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    0.736717] sd 0:0:0:0: [sda] Write Protect is off
[    0.736722] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.736755] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.753372] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0P34 PQ: 0 ANSI: 5
[    0.759382] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.759389] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.759617] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.759750] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.760103] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.841925]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    0.842737] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.924214] usb 2-1: new low speed USB device number 2 using uhci_hcd
[    1.019720] Freeing initrd memory: 13304k freed
[    1.042697]   Magic number: 3:469:377
[    1.042896] rtc_cmos 00:01: setting system clock to 2011-11-06 11:22:53 UTC (1320578573)
[    1.043454] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.043457] EDD information not available.
[    1.043654] Freeing unused kernel memory: 696k freed
[    1.044125] Write protecting the kernel text: 5332k
[    1.044180] Write protecting the kernel read-only data: 2188k
[    1.066567] udevd[82]: starting version 173
[    1.280357] input: HID 04b3:310b as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5
[    1.280561] generic-usb 0003:04B3:310B.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:1d.0-1/input0
[    1.280594] usbcore: registered new interface driver usbhid
[    1.280598] usbhid: USB HID core driver
[    1.323824] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.323870] 8139cp 0000:02:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.351983] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.352138] 8139too 0000:02:08.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    1.353249] 8139too 0000:02:08.0: eth0: RealTek RTL8139 at 0x3000, 00:03:25:10:6a:9a, IRQ 10
[    1.356460] firewire_ohci 0000:02:07.2: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    1.420217] firewire_ohci: Added fw-ohci device 0000:02:07.2, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x1
[    1.920217] firewire_core: created device fw0: GUID 00032521350027d2, S400
[    1.932785] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   21.537601] udevd[291]: starting version 173
[   21.596893] lp: driver loaded but no devices found
[   21.703613] Adding 488444k swap on /dev/sda9.  Priority:-1 extents:1 across:488444k 
[   21.783341] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   21.798201] acpi device:04: registered as cooling_device1
[   21.798458] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   21.798618] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   21.926157] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   21.952629] [drm] Initialized drm 1.1.0 20060810
[   22.178826] intel_rng: FWH not detected
[   22.191078] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.366622] type=1400 audit(1320596594.820:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=568 comm="apparmor_parser"
[   22.367882] type=1400 audit(1320596594.820:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=568 comm="apparmor_parser"
[   22.368393] type=1400 audit(1320596594.824:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=568 comm="apparmor_parser"
[   22.434149] lib80211: common routines for IEEE802.11 drivers
[   22.434156] lib80211_crypt: registered algorithm 'NULL'
[   22.450656] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[   22.450667] i915 0000:00:02.0: setting latency timer to 64
[   22.561202] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   22.561207] [drm] Driver supports precise vblank timestamp query.
[   22.561318] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   22.625665] yenta_cardbus 0000:02:07.0: CardBus bridge found [161f:203a]
[   22.719740] cfg80211: Calling CRDA to update world regulatory domain
[   22.749204] libipw: 802.11 data/management/control stack, git-1.1.13
[   22.749210] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   22.756381] yenta_cardbus 0000:02:07.0: ISA IRQ mask 0x0090, PCI irq 11
[   22.756388] yenta_cardbus 0000:02:07.0: Socket status: 30000006
[   22.756394] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   22.756409] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   22.756415] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff
[   22.803937] fixme: max PWM is zero.
[   22.806037]  0x3c00-0x3cff
[   22.806941] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge window: [mem 0xe0200000-0xe02fffff]
[   22.806948] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0200000-0xe02fffff: excluding 0xe0200000-0xe020ffff
[   22.806965] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   22.806970] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   22.839367] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   22.839373] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   22.859123] yenta_cardbus 0000:02:07.1: CardBus bridge found [161f:203a]
[   22.987186] yenta_cardbus 0000:02:07.1: ISA IRQ mask 0x0090, PCI irq 10
[   22.987193] yenta_cardbus 0000:02:07.1: Socket status: 30000006
[   22.987199] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   22.987215] yenta_cardbus 0000:02:07.1: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   22.987221] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x3fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   23.081155] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008/0x0
[   23.119980] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   23.151237] 8139too 0000:02:08.0: eth0: link down
[   23.151776] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.178858] 
[   23.178872] yenta_cardbus 0000:02:07.1: pcmcia: parent PCI bridge window: [mem 0xe0200000-0xe02fffff]
[   23.178880] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe0200000-0xe02fffff: excluding 0xe0200000-0xe020ffff
[   23.178898] yenta_cardbus 0000:02:07.1: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   23.178903] pcmcia_socket pcmcia_socket1: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   23.231758] ipw2200 0000:02:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   23.231800] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.285041] type=1400 audit(1320596595.740:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=692 comm="apparmor_parser"
[   23.294148] type=1400 audit(1320596595.748:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=693 comm="apparmor_parser"
[   23.298822] type=1400 audit(1320596595.752:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=693 comm="apparmor_parser"
[   23.299348] type=1400 audit(1320596595.752:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=693 comm="apparmor_parser"
[   23.327734] type=1400 audit(1320596595.780:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=695 comm="apparmor_parser"
[   23.354575] type=1400 audit(1320596595.808:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=695 comm="apparmor_parser"
[   23.370934] type=1400 audit(1320596595.824:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=695 comm="apparmor_parser"
[   23.764558] init: apport pre-start process (758) terminated with status 1
[   23.765026] init: alsa-restore main process (766) terminated with status 19
[   23.818582] init: apport post-stop process (794) terminated with status 1
[   23.917905] [drm] initialized overlay support
[   24.231377] cfg80211: World regulatory domain updated:
[   24.231383] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.231389] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.231393] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.231397] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.231402] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.231406] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.321963] fbcon: inteldrmfb (fb0) is primary device
[   24.322911] Console: switching to colour frame buffer device 128x48
[   24.322961] fb0: inteldrmfb frame buffer device
[   24.322964] drm: registered panic notifier
[   24.323032] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.323931] [drm] Changing LVDS panel from (+hsync, +vsync) to (-hsync, -vsync)
[   24.325601] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   24.325639] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   24.500633] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   24.502298] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   24.503017] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   24.503617] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   24.504489] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   24.506145] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   24.506864] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   24.507464] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   24.509687] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   24.509765] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   24.509839] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   24.509919] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   24.510694]  clean.
[   24.510765] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   24.510841] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   24.510915] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
[   24.510994] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   24.512695] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   24.512701] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512705] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   24.512710] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512714] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   24.512718] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512722] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   24.512726] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512730] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   24.512735] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512739] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   24.512743] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512747] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   24.512751] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512755] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   24.512760] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512764] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   24.512768] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512772] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   24.512776] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.512780] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   24.512785] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   24.517405] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   25.085569] Bluetooth: Core ver 2.16
[   25.085668] NET: Registered protocol family 31
[   25.085671] Bluetooth: HCI device and connection manager initialized
[   25.085676] Bluetooth: HCI socket layer initialized
[   25.085679] Bluetooth: L2CAP socket layer initialized
[   25.090414] Bluetooth: SCO socket layer initialized
[   25.115694] Bluetooth: RFCOMM TTY layer initialized
[   25.115705] Bluetooth: RFCOMM socket layer initialized
[   25.115709] Bluetooth: RFCOMM ver 1.11
[   25.129817] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.129824] Bluetooth: BNEP filters: protocol multicast
[   25.296053] intel8x0_measure_ac97_clock: measured 55327 usecs (2666 samples)
[   25.296059] intel8x0: clocking to 48000
[   25.304246] lib80211_crypt: registered algorithm 'WEP'
[   25.505641] ppdev: user-space parallel port driver
[   26.806367] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   27.066623] init: plymouth-stop pre-start process (1144) terminated with status 1
[   30.047567] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   36.400029] eth1: no IPv6 routers present
[   60.016075] eth1: no IPv6 routers present
[   84.320032] eth1: no IPv6 routers present
[  108.160041] eth1: no IPv6 routers present
[  145.286704] audit_printk_skb: 21 callbacks suppressed
[  145.286717] type=1400 audit(1320596717.738:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1662 comm="apparmor_parser"
[  145.295536] type=1400 audit(1320596717.746:20): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1663 comm="apparmor_parser"
[  145.297613] type=1400 audit(1320596717.750:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1663 comm="apparmor_parser"
[  145.298724] type=1400 audit(1320596717.750:22): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1663 comm="apparmor_parser"
[  145.314299] type=1400 audit(1320596717.766:23): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=1664 comm="apparmor_parser"
[  145.324448] type=1400 audit(1320596717.778:24): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=1664 comm="apparmor_parser"
[  145.330282] type=1400 audit(1320596717.782:25): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=1664 comm="apparmor_parser"
[  145.339410] type=1400 audit(1320596717.790:26): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/mission-control-5" pid=1666 comm="apparmor_parser"
[  145.340516] type=1400 audit(1320596717.794:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-*" pid=1666 comm="apparmor_parser"
[  145.346185] type=1400 audit(1320596717.798:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1667 comm="apparmor_parser"
[  145.453928] init: apport pre-start process (1691) terminated with status 1
[  145.493815] init: apport post-stop process (1709) terminated with status 1
[  145.874252] init: plymouth-stop pre-start process (1794) terminated with status 1
[  214.092455] 8139too 0000:02:08.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  214.092599] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  224.736063] eth0: no IPv6 routers present
[  625.760036] eth1: no IPv6 routers present
[  649.760050] eth1: no IPv6 routers present
[  673.920053] eth1: no IPv6 routers present
[  697.528053] eth1: no IPv6 routers present
[  917.825330] 8139too 0000:02:08.0: eth0: link down
[ 1007.774505] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1008.523359] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1018.656050] eth1: no IPv6 routers present
[ 1042.784048] eth1: no IPv6 routers present
[ 1052.679698] 8139too 0000:02:08.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1068.048046] eth1: no IPv6 routers present
[ 1091.840057] eth1: no IPv6 routers present
[ 1849.656047] eth1: no IPv6 routers present
[ 1872.928052] eth1: no IPv6 routers present
[ 1898.680029] eth1: no IPv6 routers present
[ 1923.088043] eth1: no IPv6 routers present
[ 2508.960056] eth1: no IPv6 routers present
[ 2533.200048] eth1: no IPv6 routers present
[ 2557.120043] eth1: no IPv6 routers present
[ 2581.392041] eth1: no IPv6 routers present
[ 3169.128048] eth1: no IPv6 routers present
[ 3192.624056] eth1: no IPv6 routers present
[ 3217.184045] eth1: no IPv6 routers present
[ 3241.008047] eth1: no IPv6 routers present
[ 3589.328054] eth1: no IPv6 routers present

```

```
 sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 10
       serial: 00:03:25:10:6a:9a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:10 ioport:3000(size=256) memory:e0201800-e02018ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:28:05:5d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:e0200000-e0200fff
```

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:C0:49:F0:76:32
                    ESSID:"underwood5"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-52 dBm  
                    Extra: Last beacon: 60ms ago
          Cell 02 - Address: 00:13:F7:B6:CC:C4
                    ESSID:"Fred"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 148ms ago
          Cell 03 - Address: 70:71:BC:47:DF:2A
                    ESSID:"Teggfeig"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-57 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 188ms ago
          Cell 04 - Address: 00:13:F7:AD:0A:20
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-59 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2564ms ago
          Cell 05 - Address: 00:22:2D:16:3E:26
                    ESSID:"Frederickst"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-57 dBm  
                    Extra: Last beacon: 108ms ago
```

```
lsb_release -d
Description:	Ubuntu 11.10

```

```
uname -mr
3.0.0-12-generic i686

```

```
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
```

---

### Post by praseodym on 2011-11-07
Hi,

there is a firmware bug for this driver. Update it:

[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)

Version 3.0. Save it in /home and unpack it:

```
sudo tar -xvf ipw2200-fw-3.0 -C /lib/firmware
```
Shut off the notebook and take out the battery for completely unloading the current firmware

---

### Post by PsychicNut on 2011-11-08
Hi, Thanks for getting back to me so fast. I downloaded version 3.0 and followed your code but got an error (below). I included a dir to show that the file is actually there. I downloaded it twice.

There is a version 3.1 on the website - should I download that?

Thanks again for your help.
:)
Psychic

```
$ dir
Desktop    Downloads	     ipw2200-fw-3.0.tgz  Pictures  Templates	Videos
Documents  examples.desktop  Music		 Public    Ubuntu\ One


$ sudo tar -xvf ipw2200-fw-3.0 -C /lib/firmware
[sudo] password for ...: 
tar: ipw2200-fw-3.0: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

```

---

### Post by PsychicNut on 2011-11-08
Hi again Praseodym,
Even when I copy the tgz file to /lib/firmware and unpack from there I get the same error.
Hrumph!
Thanks for your help on this
:)
Psychic

---

### Post by PsychicNut on 2011-11-08
Hi Praseodym,
That ipw2200-fw-3.0 file seems like an old file (2007). My wireless was working for the last two years under Ubuntu. My wireless stopped working when I did a fresh install with Oneiric. 

Is it that the latest version of the driver (that perhaps comes with Oneiric) doesn't work and you are having me download an older version that DOES work?
Just checking...
Thanks again
:)
Psychic

---

### Post by PsychicNut on 2011-11-08
Hi there,
I finally unpacked it with Archive Manager and in terminal used sudo to copy the files to the /lib/firmware. I used dir -l to make sure the three files were overwritten. Then I shut off the notebook and took out the battery.
No luck.
I really appreciate your help on this.
Thanks
Psychic

---

### Post by praseodym on 2011-11-09
Try the package "linux-firmware" from Oneiric. I **dont** recommend an older version of this package because of the other firmware therein.

---

### Post by PsychicNut on 2011-11-10
Hi Praseodym,

> **praseodym said:**
> Try the package "linux-firmware" from Oneiric. I **dont** recommend an older version of this package because of the other firmware therein.

In synaptic, linux-firmware version 1.60 is already installed (green box).

Earlier you said to download the version 3.0 of the firmware driver. There is a later version listed at the site you recommended. There is a version 3.1 listed there as well. Should I try that one? 


Here is the results from the sudo lshw -C network command:
```
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 10
       serial: 00:03:25:10:6a:9a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:10 ioport:3000(size=256) memory:e0201800-e02018ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:28:05:5d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:e0200000-e0200fff

```
Looks like the firmware version went 
from firmware=ABG:9.0.5.27 (Dec 12 2007)
to firmware=ABG:9.0.2.6 (Mar 22 2005)

It appears to have gone back a version.
Should I download and install firmware version 3.1?

I have been following another thread that you have replied to. It is called "Inspiron 6000 - can't enable wireless"
In there you suggest to change the network manager to wicd. That was for someone with Xubuntu. Do you think that would apply also to me (in Ubuntu Oneiric with same Intel 2200BG wireless)?

Thanks again for working on this
:)
PsychicNut

---

### Post by PsychicNut on 2011-11-10
Hi Praseodym,
My wireless seems to be working now. Not sure what exactly caused it to work. I had followed your instructions here and also your suggestions under that other thread "Inspiron 6000 - can't enable wireless"

Also I changed my wireless security settings:
Wireless --> Edit Connections-->Wireless tab 
Clicked on my router name
Clicked edit
Clicked on the "wireless security" tab, 
I changed the "security" setting 
from WEP 128 bit passphrase
to WEP 40/128-bit Key (Hex or ASCII) 
(neither of these settings worked before)
(I am using WEP on my router)
and it worked.
I rebooted to make sure and it seems to work well.
Thanks again for all your help
Take care
:)
PsychicNut

---

