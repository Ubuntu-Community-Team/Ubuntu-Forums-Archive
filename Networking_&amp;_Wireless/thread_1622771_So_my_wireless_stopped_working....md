---
title: "So my wireless stopped working..."
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by Windows Nerd on 2010-11-15
Hey all,

My wireless internet just recently stopped working out of the blue. It has thus far "just worked". I use WICD for connecting, because, well, Network Manager kind of sucks. 

So, today when I decided to turn my laptop on and log in, after logging in, I did notice something different. There was a little window that popped up (that I have never seen before) that said:

"Wicd needs to access your network cards." And was prompting me for the password. I entered in my user password that I use to log in, and the pop-up window went away. 

Now it just refuses to connect, Wicd just saying that there is a bad password. I did not change _any_ settings for wicd. Any the password has worked thus far.

The ESSID of my network is "Gigaset23F", on WPA-PSK TKIP. WICD is set to connect to the network automatically. I have a wireless card with a rtl 8187 chipset, which works just fine with everything. 

Some information:

These commands were run right after booting and entering the password for wicd. I apologize for making dmesg so friggin' huge, but there is some stuff relating to the wireless card up near the beginning, and I didn't want to miss it. 

This is on a Gatewatay MT6709 Laptop with Ubuntu 10.04 LTS

```
~$eth0      Link encap:Ethernet  HWaddr 00:e0:b8:c5:c0:eb
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:167235 (167.2 KB)  TX bytes:167235 (167.2 KB)
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Gigaset23F"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
        
```
~$ dmesg | tail -300
[    0.313732] tty tty35: hash matches
[    0.313815] rtc_cmos 00:06: setting system clock to 2010-11-16 01:19:12 UTC (1289870352)
[    0.313819] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.313821] EDD information not available.
[    0.348987] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.349527] ACPI: Battery Slot [BAT1] (battery present)
[    0.455933] Freeing initrd memory: 7774k freed
[    0.462110] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PG02, max UDMA/33
[    0.476324] ata1.00: configured for UDMA/33
[    0.616033] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    0.651441] isapnp: No Plug & Play device found
[    0.655396] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PG02 PQ: 0 ANSI: 5
[    0.667171] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.667176] Uniform CD-ROM driver Revision: 3.20
[    0.667321] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.667562] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.667659] Freeing unused kernel memory: 656k freed
[    0.668482] Write protecting the kernel text: 4684k
[    0.668544] Write protecting the kernel read-only data: 1840k
[    0.689751] udev: starting version 151
[    0.754670] usb 1-5: configuration #1 chosen from 1 choice
[    0.834549] ahci 0000:00:1f.2: version 3.0
[    0.834581] ahci 0000:00:1f.2: power state changed by ACPI to D0
[    0.834592] ahci 0000:00:1f.2: power state changed by ACPI to D0
[    0.834607] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.834662]   alloc irq_desc for 25 on node -1
[    0.834665]   alloc kstat_irqs on node -1
[    0.834682] ahci 0000:00:1f.2: irq 25 for MSI/MSI-X
[    0.834795] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    0.834800] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    0.834807] ahci 0000:00:1f.2: setting latency timer to 64
[    0.844129] scsi2 : ahci
[    0.851561] sky2 driver version 1.25
[    0.851615] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.851633] sky2 0000:02:00.0: setting latency timer to 64
[    0.851671] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    0.851783]   alloc irq_desc for 26 on node -1
[    0.851786]   alloc kstat_irqs on node -1
[    0.851804] sky2 0000:02:00.0: irq 26 for MSI/MSI-X
[    0.862180] scsi3 : ahci
[    0.862388] scsi4 : ahci
[    0.862524] scsi5 : ahci
[    0.862699] ata3: SATA max UDMA/133 abar m1024@0xd4444400 port 0xd4444500 irq 25
[    0.862703] ata4: DUMMY
[    0.862707] ata5: SATA max UDMA/133 abar m1024@0xd4444400 port 0xd4444600 irq 25
[    0.862709] ata6: DUMMY
[    0.863625] sky2 eth0: addr 00:e0:b8:c5:c0:eb
[    1.180054] ata5: SATA link down (SStatus 0 SControl 300)
[    1.180087] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.180683] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.228678] ata3.00: ATA-7: WDC WD1600BEVS-22RST0, 04.01G04, max UDMA/133
[    1.228682] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.229565] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.229875] ata3.00: configured for UDMA/133
[    1.244194] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-2 04.0 PQ: 0 ANSI: 5
[    1.244414] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.244455] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.244555] sd 2:0:0:0: [sda] Write Protect is off
[    1.244559] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.244593] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.244776]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.290141] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.294718] ohci1394 0000:03:09.1: enabling device (0000 -> 0002)
[    1.294730] ohci1394 0000:03:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.294741] ohci1394 0000:03:09.1: setting latency timer to 64
[    1.348079] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[d4005000-d40057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.620179] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80366091ac8]
[    6.704651] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    9.604244] udev: starting version 151
[   10.602443] type=1505 audit(1289870362.786:2):  operation="profile_load" pid=560 name="/sbin/dhclient3"
[   10.603159] type=1505 audit(1289870362.786:3):  operation="profile_load" pid=560 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.603547] type=1505 audit(1289870362.786:4):  operation="profile_load" pid=560 name="/usr/lib/connman/scripts/dhclient-script"
[   10.961975] tifm_7xx1 0000:03:09.2: enabling device (0000 -> 0002)
[   10.961990] tifm_7xx1 0000:03:09.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.962000] tifm_7xx1 0000:03:09.2: setting latency timer to 64
[   11.001783] intel_rng: FWH not detected
[   11.016610] Linux agpgart interface v0.103
[   11.092270] yenta_cardbus 0000:03:09.0: CardBus bridge found [107b:0366]
[   11.092300] yenta_cardbus 0000:03:09.0: Using CSCINT to route CSC interrupts to PCI
[   11.092303] yenta_cardbus 0000:03:09.0: Routing CardBus interrupts to PCI
[   11.092311] yenta_cardbus 0000:03:09.0: TI: mfunc 0x01ac1b22, devctl 0x64
[   11.120793] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   11.146862] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   11.147266] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   11.151135] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   11.155554] acpi device:07: registered as cooling_device2
[   11.156572] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input6
[   11.156766] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.288578] lp: driver loaded but no devices found
[   11.306118] cfg80211: Calling CRDA to update world regulatory domain
[   11.324819] yenta_cardbus 0000:03:09.0: ISA IRQ mask 0x0cf8, PCI irq 17
[   11.324825] yenta_cardbus 0000:03:09.0: Socket status: 30000006
[   11.324832] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   11.324843] yenta_cardbus 0000:03:09.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   11.324848] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   11.325137] yenta_cardbus 0000:03:09.0: pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd40fffff
[   11.325141] yenta_cardbus 0000:03:09.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   11.418474] [drm] Initialized drm 1.1.0 20060810
[   11.696013] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.696023] i915 0000:00:02.0: setting latency timer to 64
[   11.700065] [drm] set up 7M of stolen space
[   11.792857] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   11.803332] [drm] initialized overlay support
[   11.831901] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   12.024336] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.026642] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   12.027611] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.028416] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.029448] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.352849] cfg80211: World regulatory domain updated:
[   12.352855] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.352859] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.352862] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.352866] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.352869] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.352873] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.431219] fb0: inteldrmfb frame buffer device
[   12.431224] registered panic notifier
[   12.431234] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.637883] phy0: Selected rate control algorithm 'minstrel'
[   12.638783] phy0: hwaddr 00:c0:a8:de:d7:67, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   12.654444] rtl8187: Customer ID is 0x00
[   12.654563] Registered led device: rtl8187-phy0::tx
[   12.654903] Registered led device: rtl8187-phy0::rx
[   12.655311] rtl8187: wireless switch is on
[   12.655348] usbcore: registered new interface driver rtl8187
[   12.730597] vga16fb: initializing
[   12.730602] vga16fb: mapped to 0xc00a0000
[   12.730608] vga16fb: not registering due to another framebuffer present
[   13.560566]   alloc irq_desc for 22 on node -1
[   13.560571]   alloc kstat_irqs on node -1
[   13.560580] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.560629] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.793683] Console: switching to colour frame buffer device 160x50
[   14.168530] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.228340] type=1505 audit(1289870368.414:5):  operation="profile_load" pid=838 name="/usr/share/gdm/guest-session/Xsession"
[   16.230684] type=1505 audit(1289870368.414:6):  operation="profile_replace" pid=841 name="/sbin/dhclient3"
[   16.231414] type=1505 audit(1289870368.414:7):  operation="profile_replace" pid=841 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.231808] type=1505 audit(1289870368.414:8):  operation="profile_replace" pid=841 name="/usr/lib/connman/scripts/dhclient-script"
[   16.579363] type=1505 audit(1289870368.762:9):  operation="profile_load" pid=842 name="/usr/bin/evince"
[   16.588710] type=1505 audit(1289870368.774:10):  operation="profile_load" pid=842 name="/usr/bin/evince-previewer"
[   16.594443] type=1505 audit(1289870368.778:11):  operation="profile_load" pid=842 name="/usr/bin/evince-thumbnailer"
[   17.341473] type=1505 audit(1289870369.526:12):  operation="profile_load" pid=851 name="/usr/lib/cups/backend/cups-pdf"
[   17.342344] type=1505 audit(1289870369.526:13):  operation="profile_load" pid=851 name="/usr/sbin/cupsd"
[   17.432591] type=1505 audit(1289870369.618:14):  operation="profile_load" pid=860 name="/usr/sbin/tcpdump"
[   59.049699] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   61.155731] sky2 eth0: enabling interface
[   61.155961] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   69.469661] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.673078] sky2 eth0: disabling interface
[   69.679844] sky2 eth0: enabling interface
[   69.680074] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   72.077617] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.805270] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[   77.004057] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[   77.205070] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[   77.404044] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[   88.705286] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[   88.904043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[   89.104040] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[   89.304048] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  100.605301] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  100.804044] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  101.004042] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  101.204044] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  112.509312] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  112.708054] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  112.908070] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  113.108042] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  118.301787] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  118.357246] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  118.357290] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  118.357369] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  118.460049] sky2 eth0: disabling interface
[  118.467003] sky2 eth0: enabling interface
[  118.467230] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  120.833715] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  120.893197] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  120.970425] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  123.265656] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  123.325279] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  123.397062] sky2 eth0: disabling interface
[  123.404097] sky2 eth0: enabling interface
[  123.404328] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  123.524050] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  123.724037] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  123.924046] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  125.204285] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  125.257343] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  125.456046] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  125.656039] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  125.856045] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  137.165359] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  137.364047] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  137.564043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  137.764041] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  155.973345] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  156.172047] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  156.372043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  156.572044] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  168.305781] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  168.361239] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  168.361277] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  168.361341] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  168.457063] sky2 eth0: disabling interface
[  168.463836] sky2 eth0: enabling interface
[  168.464064] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  170.841696] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  170.897318] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  170.978966] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  173.277646] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  173.333275] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  173.453063] sky2 eth0: disabling interface
[  173.460020] sky2 eth0: enabling interface
[  173.460248] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  173.532051] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  173.732035] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  173.932041] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  175.212287] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  175.265342] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  175.464041] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  175.664039] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  175.864042] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  194.081330] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  194.280038] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  194.480043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  194.680037] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  212.889314] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  213.088043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  213.288043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  213.488042] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  218.233649] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  218.289355] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  218.289400] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  218.289481] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  218.384047] sky2 eth0: disabling interface
[  218.391001] sky2 eth0: enabling interface
[  218.391231] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  220.729688] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  220.789310] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  220.839431] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  223.141634] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  223.197266] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  223.264048] sky2 eth0: disabling interface
[  223.271085] sky2 eth0: enabling interface
[  223.271347] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  223.396040] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  223.596041] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  223.796042] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  225.360257] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  225.413342] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  225.612038] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  225.812040] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  226.012050] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  237.309355] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  237.508043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  237.708043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  237.908041] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  256.117340] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  256.316051] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  256.516043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  256.716041] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  266.293661] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  266.488049] sky2 eth0: disabling interface
[  266.494905] sky2 eth0: enabling interface
[  266.495133] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  421.081696] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  421.421324] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  421.620043] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  421.820041] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  422.020047] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  623.225732] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  623.289361] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  623.409077] sky2 eth0: disabling interface
[  623.416120] sky2 eth0: enabling interface
[  623.416350] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  623.420960] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  625.825808] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  625.886316] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  626.084045] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  626.284044] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  626.484061] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  628.200269] wlan0: deauthenticating from e8:be:81:f2:42:44 by local choice (reason=3)
[  628.253273] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  628.452042] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  628.652039] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  628.852049] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  646.480348] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[  646.993258] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  647.192046] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  647.392040] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  647.592041] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  658.829265] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 1)
[  659.028047] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 2)
[  659.228045] wlan0: direct probe to AP e8:be:81:f2:42:44 (try 3)
[  659.428043] wlan0: direct probe to AP e8:be:81:f2:42:44 timed out
[  668.261732] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  668.468047] sky2 eth0: disabling interface
[  668.475077] sky2 eth0: enabling interface
[  668.475406] ADDRCONF(NETDEV_UP): eth0: link is not ready
scott@scott-laptop:~$ 
```

If you need any more specifics just let me know. The laptop does connect with wired perfectly fine.

Scott

---

### Post by claracc on 2010-11-16
When I upgraded my karmic koala (for me best ubuntu distro till now, solid rocks) to lucid lynx, I found the same problem, wicd asked for root password, unless I introduced the correct one, wicd said it was invalid.

Here there is a link, [http://ubuntuforums.org/showthread.php?t=1243485&page=2](http://ubuntuforums.org/showthread.php?t=1243485&page=2) where it is explained howto fix if the problem is redundant brackets in /etc/wicd/wired-settings.conf.

If this is not the problem ( as it was my case, I have wireless too, no wired), you can add at the end of file /etc/init/networking.conf the line exec wicd, then you write in xterm, wicd-client to run the daemon to see if the problem is fixed.

I hope it can help

---

### Post by Windows Nerd on 2010-11-21
It seemed that starting WICD with ```
wicd-client
``` did it properly after killing all wicd processes.

Strange, but it worked.

---

