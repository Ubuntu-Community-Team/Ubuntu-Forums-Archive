---
title: "AR5001 problems in Karmic got much worse in Lucid"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by whakim on 2010-04-18
Hi,

So in Karmic, I was unable to connect to a WPA2 network using the Atheros AR5001 wireless card on a Compaq notebook. I could connect to unsecured networks, but not secured ones. I tried madwifi, compat-wireless, and all the backports, but they only made things worse, to the point where the system would instantly freeze on boot. 

In frustration I installed Lucid beta 2. Everything works great *except* the wireless. In fact, the hardware switch for wireless simply refuses to turn on & off. It appears to be in the on position & the LED light indicates on but rfkill says:

rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

So obviously it is not turning the switch on. The wireless was greyed out in Network Manager. I installed wicd & linux-backports-modules-wireless-lucid-generic but no luck; wicd will not recognize wireless networks either. 

from  lshw -C Network, I get: 

  *-network DISABLED      
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:95:6f:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.32-21-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:51300000-5130ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:ed:5b:f7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:1000(size=256) memory:51200000-512000ff

so as you can see the wireless just doesn't turn on even though the switch says it is. I booted into Windows to confirm it is not a hardware problem; the wireless works fine in Windows & the switch turns on & off like it should.

lspci says: 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


and from dmesg | grep ath* I get: 

[    0.000000]  BIOS-e820: 000000003f6bf000 - 000000003f700000 (ACPI data)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000]  modified: 000000003f6bf000 - 000000003f700000 (ACPI data)
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] found SMP MP-table at [c00fe270] fe270
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32109 pages, LIFO batch:7
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] allocated 5194120 bytes of page_cgroup
[    0.000000] Memory: 1007980k/1038824k available (4673k kernel code, 29860k reserved, 2122k data, 656k init, 129448k highmem)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000] Hierarchical RCU implementation.
[    0.000000] Fast TSC calibration using PIT
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.06 BogoMIPS (lpj=6384120)
[    0.036018] ftrace: allocating 21771 entries in 43 pages
[    0.040075] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.168136] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172026] Total of 2 processors activated (6384.02 BogoMIPS).
[    0.172458] CPU0 attaching sched-domain:
[    0.172474] CPU1 attaching sched-domain:
[    0.172599] regulator: core version 0.5
[    0.172599] Time:  1:04:12  Date: 04/18/10
[    0.172599] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172599] PCI: MCFG area at e0000000 reserved in E820
[    0.172599] PCI: Using configuration type 1 for base access
[    0.176158] bio: create slab <bio-0> at 0
[    0.345337] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.346475] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.347718] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
[    0.349448] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.358231] libata version 3.00 loaded.
[    0.358893] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.358900] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.457781]   alloc kstat_irqs on node -1
[    0.457800] pci 0000:00:1c.0: setting latency timer to 64
[    0.457812] pci 0000:00:1e.0: setting latency timer to 64
[    0.460010] Simple Boot Flag at 0x44 set to 0x1
[    0.472992] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.476250] io scheduler anticipatory registered
[    0.476497]   alloc kstat_irqs on node -1
[    0.476527] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.546009] Monitor-Mwait will be used to enter C-1 state
[    0.546050] Monitor-Mwait will be used to enter C-2 state
[    0.546083] Monitor-Mwait will be used to enter C-3 state
[    0.620765] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.620887] ata_piix 0000:00:1f.1: version 2.13
[    0.620908]   alloc kstat_irqs on node -1
[    0.620917] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.620965] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.621070] scsi0 : ata_piix
[    0.621170] scsi1 : ata_piix
[    0.621832] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30a0 irq 14
[    0.621837] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30a8 irq 15
[    0.622502]   alloc kstat_irqs on node -1
[    0.622526] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.640129] usb usb1: configuration #1 chosen from 1 choice
[    0.640312]   alloc kstat_irqs on node -1
[    0.640330] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.640538] usb usb2: configuration #1 chosen from 1 choice
[    0.640641]   alloc kstat_irqs on node -1
[    0.640655] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.640860] usb usb3: configuration #1 chosen from 1 choice
[    0.640969] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.641171] usb usb4: configuration #1 chosen from 1 choice
[    0.641331] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.669067] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.669075] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.671959] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.672063] device-mapper: multipath: version 1.1.0 loaded
[    0.672067] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.672211] EISA: Probing bus 0 at eisa.0
[    0.672220] Cannot allocate resource for EISA slot 1
[    0.672222] Cannot allocate resource for EISA slot 2
[    0.672225] Cannot allocate resource for EISA slot 3
[    0.674993] registered taskstats version 1
[    0.675480] EDD information not available.
[    0.689948] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.747930] ACPI: Battery Slot [BAT0] (battery present)
[    0.805428] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, HS02, max MWDMA2
[    0.837331] ata1.00: configured for MWDMA2
[    0.989140] Write protecting the kernel read-only data: 1840k
[    1.165356] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.165940]   alloc kstat_irqs on node -1
[    1.166003]   alloc kstat_irqs on node -1
[    1.166110] ahci 0000:00:1f.2: setting latency timer to 64
[    1.166841] ata3: SATA max UDMA/133 abar m2048@0x52404000 port 0x52404100 irq 25
[    1.166845] ata4: DUMMY
[    1.166847] ata5: DUMMY
[    1.168777]   alloc kstat_irqs on node -1
[    1.168798] 8139too 0000:02:01.0: setting latency timer to 64
[    1.170469] eth0: RealTek RTL8139 at 0x1000, 00:1b:38:ed:5b:f7, IRQ 16
[    1.648092] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.648807] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.648814] ata3.00: ATA-8: FUJITSU MHY2120BH, 890B, max UDMA/100
[    1.648818] ata3.00: 234441648 sectors, multi 16: LBA48 
[    1.649619] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.649651] ata3.00: configured for UDMA/100
[    2.458518] EXT3-fs: mounted filesystem with ordered data mode.
[   18.870264] type=1505 audit(1271570670.692:2):  operation="profile_load" pid=618 name="/sbin/dhclient3"
[   18.871131] type=1505 audit(1271570670.692:3):  operation="profile_load" pid=618 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.871592] type=1505 audit(1271570670.692:4):  operation="profile_load" pid=618 name="/usr/lib/connman/scripts/dhclient-script"
[   18.899985] i915 0000:00:02.0: setting latency timer to 64
[   18.908238]   alloc kstat_irqs on node -1
[   19.304563] cfg80211: Calling CRDA to update world regulatory domain
[   19.347122] cfg80211: World regulatory domain updated:
[   19.393226] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input6
[   19.429250] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[   19.676428]   alloc kstat_irqs on node -1
[   19.676492] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.769885] ath5k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.769903] ath5k 0000:01:00.0: setting latency timer to 64
[   19.769962] ath5k 0000:01:00.0: registered as 'phy0'
[   20.272307] ath: EEPROM regdomain: 0x64
[   20.272310] ath: EEPROM indicates we should expect a direct regpair map
[   20.272315] ath: Country alpha2 being used: 00
[   20.272317] ath: Regpair used: 0x64
[   20.279669] phy0: Selected rate control algorithm 'minstrel'
[   20.280735] Registered led device: ath5k-phy0::rx
[   20.280757] Registered led device: ath5k-phy0::tx
[   20.280761] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   20.333994] EXT3-fs: mounted filesystem with ordered data mode.
[   21.348454] EXT3-fs: mounted filesystem with ordered data mode.
[   26.565177] type=1505 audit(1271570678.388:5):  operation="profile_load" pid=835 name="/usr/share/gdm/guest-session/Xsession"
[   26.567411] type=1505 audit(1271570678.388:6):  operation="profile_replace" pid=836 name="/sbin/dhclient3"
[   26.568348] type=1505 audit(1271570678.392:7):  operation="profile_replace" pid=836 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.568820] type=1505 audit(1271570678.392:8):  operation="profile_replace" pid=836 name="/usr/lib/connman/scripts/dhclient-script"
[   26.573339] type=1505 audit(1271570678.396:9):  operation="profile_load" pid=837 name="/usr/bin/evince"
[   26.584480] type=1505 audit(1271570678.408:10):  operation="profile_load" pid=837 name="/usr/bin/evince-previewer"
[   26.591384] type=1505 audit(1271570678.412:11):  operation="profile_load" pid=837 name="/usr/bin/evince-thumbnailer"
[   26.601143] type=1505 audit(1271570678.424:12):  operation="profile_load" pid=839 name="/usr/lib/cups/backend/cups-pdf"
[   26.602173] type=1505 audit(1271570678.424:13):  operation="profile_load" pid=839 name="/usr/sbin/cupsd"
[   26.605257] type=1505 audit(1271570678.428:14):  operation="profile_load" pid=840 name="/usr/sbin/tcpdump"
[   36.450973] type=1503 audit(1271570688.272:15):  operation="open" pid=1290 parent=1275 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"


Also, here is the output from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

ifconfig does not show the wlan0 at all:

eth0      Link encap:Ethernet  HWaddr 00:1b:38:ed:5b:f7  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:feed:5bf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7475 errors:0 dropped:0 overruns:2 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7837056 (7.8 MB)  TX bytes:1515028 (1.5 MB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


And what may well be the most bizarre of all, when I try to use the command line to bring up the connection:
w**@wanderer:$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132



I am at my wits end. I am afraid to install the madwifi drivers because of how catastrophically they blew up in Karmic. Any help would be much, much appreciated.

Thanks in advance!

---

### Post by ed-rapley on 2010-05-25
Take a look at this thread, with posts 3 and four, i got my fujitsu amilo wifi working.

[http://ubuntuforums.org/showthread.php?p=9354354#post9354354](http://ubuntuforums.org/showthread.php?p=9354354#post9354354)

good luck.

---

### Post by drpjkurian on 2010-05-26
Hi
Pleaase give a try to my thread and let me know if it worked for you.

[http://ubuntuforums.org/showthread.php?t=1484242](http://ubuntuforums.org/showthread.php?t=1484242)

---

### Post by kndlewis on 2010-05-30
YES! YES! Thank you drpjkurian!  I have bookmarked your page and that will be my first stop after the next kernel upgrade.
For the record, I have a Cisco AIR-CB21AG-A-K9 cardbus adapter.  Following your instructions, I was able to get my wireless working.  I won't get into how long I spent searching the web (and these forums) looking for a solution.
Thank you for the clear step-by-step instructions.

---

### Post by drpjkurian on 2010-06-01
Thanks buddy

---

