---
title: "ethernet not working after upgrade breezy&gt;dapper"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by antimatter on 2006-06-05
Hi!
Upgraded to dapper this morning and everything seemed to have worked fine. My 3com pcmcia card Model 3CCFE574BT worked under breezy, but now with dapper it was renamed from eth0 to eth1(i think) and it also stopped working. i've tried ifdown eth1 ifup eth1 but that didnt work. it would just say, no dhcpoffers received. so i figured, hey you could try the old kernel, so i booted that one. ifup eth0(and not eth1)!! and voila, it worked. ideas anyone?

here is some stuff i tried


root@ly:/home/stefan # ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

root@ly:/home/stefan # ifup eth1
ifup: interface eth1 already configured

root@ly:/home/stefan # ifconfig
eth1      Link encap:Ethernet  HWaddr 00:50:04:8C:06:D6
          inet6 addr: fe80::250:4ff:fe8c:6d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:300 (300.0 b)
          Interrupt:3 Base address:0x300

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:89324 (87.2 KiB)  TX bytes:89324 (87.2 KiB)

root@ly:/home/stefan # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

root@ly:/home/stefan # ifdown eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:50:04:8c:06:d6
Sending on   LPF/eth1/00:50:04:8c:06:d6
Sending on   Socket/fallback
root@ly:/home/stefan # ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:50:04:8c:06:d6
Sending on   LPF/eth1/00:50:04:8c:06:d6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


root@ly:/home/stefan # lspci
0000:00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82440MX ISA Bridge (rev 01)
0000:00:07.1 IDE interface: Intel Corporation 82440MX EIDE Controller
0000:00:07.2 USB Controller: Intel Corporation 82440MX USB Universal Host Controller
0000:00:07.3 Bridge: Intel Corporation 82440MX Power Management Controller
0000:00:09.0 VGA compatible controller: Silicon Motion, Inc. SM712 LynxEM+ (rev a0)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1211
0000:00:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)






The dmesg output :



root@ly:/home/stefan # dmesg
[4294667.296000] Linux version 2.6.15-23-686 (buildd@rothera) (gcc version 4.0.3  (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000bff0000 (usable)
[4294667.296000]  BIOS-e820: 000000000bff0000 - 000000000bfffc00 (ACPI data)
[4294667.296000]  BIOS-e820: 000000000bfffc00 - 000000000c000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 191MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 49136
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 45040 pages, LIFO batch:7
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x00 0f6c90
[4294667.296000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0bffcd07
[4294667.296000] ACPI: FADT (v001 IBM    TP240    0x06040000 PTL  0x000f4240) @ 0x0bfffb65
[4294667.296000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0bfffbd9
[4294667.296000] ACPI: DSDT (v001    PTL    BX-TJ 0x06040000 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is requir ed to enable ACPI
[4294667.296000] ACPI: Disabling ACPI support
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3 f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable i t with "lapic"
[4294667.296000] mapped APIC to ffffd000 (011f2000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 497.930 MHz processor.
[  987.650621] Using tsc for high-res timesource
[  987.652395] Console: colour VGA+ 80x25
[  987.653465] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[  987.654358] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[  987.684131] Memory: 183528k/196544k available (2101k kernel code, 12484k rese rved, 592k data, 332k init, 0k highmem)
[  987.684147] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  987.743823] Calibrating delay using timer specific routine.. 996.76 BogoMIPS (lpj=498381)
[  987.743978] Security Framework v1.0.0 initialized
[  987.744006] SELinux:  Disabled at boot.
[  987.744064] Mount-cache hash table entries: 512
[  987.744398] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 000 00000 00000000 00000000 00000000
[  987.744427] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 0000 0000 00000000 00000000 00000000
[  987.744461] CPU: L1 I cache: 16K, L1 D cache: 16K
[  987.744472] CPU: L2 cache: 256K
[  987.744483] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 0 0000000 00000000 00000000
[  987.744539] mtrr: v2.0 (20020519)
[  987.744558] Enabling fast FPU save and restore... done.
[  987.744568] Enabling unmasked SIMD FPU exception support... done.
[  987.744582] Checking 'hlt' instruction... OK.
[  987.748037] SMP alternatives: switching to UP code
[  987.748782] checking if image is initramfs... it is
[  989.886001] Freeing initrd memory: 6809k freed
[  989.933214] CPU0: Intel Pentium III (Coppermine) stepping 03
[  989.933240] SMP motherboard not detected.
[  989.933251] Local APIC not detected. Using dummy APIC emulation.
[  989.933500] Brought up 1 CPUs
[  989.934787] NET: Registered protocol family 16
[  989.934919] EISA bus registered
[  989.935925] PCI: PCI BIOS revision 2.10 entry at 0xfd9df, last bus=0
[  989.935947] PCI: Using configuration type 1
[  989.937610] ACPI: Subsystem revision 20051216
[  989.937621] ACPI: Interpreter disabled.
[  989.937632] Linux Plug and Play Support v0.97 (c) Adam Belay
[  989.937682] pnp: PnP ACPI: disabled
[  989.937696] PnPBIOS: Scanning system for PnP BIOS support...
[  989.937763] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6d30
[  989.937777] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xac8b, dseg 0x400
[  989.942259] PnPBIOS: Unknown tag '0x82', length '25'.
[  989.944755] PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
[  989.944807] PCI: Probing PCI hardware
[  989.944821] PCI: Probing PCI hardware (bus 00)
[  989.945365] Boot video device is 0000:00:09.0
[  989.946864] PCI: Using IRQ router PIIX/ICH [8086/7198] at 0000:00:07.0
[  989.948187] pnp: 00:00: ioport range 0x398-0x399 has been reserved
[  989.948231] pnp: 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[  989.948243] pnp: 00:0b: ioport range 0x8000-0x803f has been reserved
[  989.948256] pnp: 00:0b: ioport range 0x2180-0x218f has been reserved
[  989.949041] PCI: Ignore bogus resource 6 [0:0] of 0000:00:09.0
[  989.949075] PCI: Bus 1, cardbus bridge: 0000:00:0a.0
[  989.949085]   IO window: 00001400-000014ff
[  989.949097]   IO window: 00001800-000018ff
[  989.949109]   PREFETCH window: 10000000-11ffffff
[  989.949121]   MEM window: 12000000-13ffffff
[  989.949157] PCI: Found IRQ 11 for device 0000:00:0a.0
[  989.949393] Simple Boot Flag at 0x41 set to 0x1
[  989.950961] audit: initializing netlink socket (disabled)
[  989.950995] audit(1149534110.168:1): initialized
[  989.951401] VFS: Disk quotas dquot_6.5.1
[  989.951486] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  989.951728] Initializing Cryptographic API
[  989.951743] io scheduler noop registered
[  989.951772] io scheduler anticipatory registered
[  989.951794] io scheduler deadline registered
[  989.951844] io scheduler cfq registered
[  989.952384] isapnp: Scanning for PnP cards...
[  990.308290] isapnp: No Plug & Play device found
[  990.369985] Real Time Clock Driver v1.12
[  990.370628] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[  990.374663] serio: i8042 AUX port at 0x60,0x64 irq 12
[  990.374982] serio: i8042 KBD port at 0x60,0x64 irq 1
[  990.375119] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing  enabled
[  990.395173] pnp: Device 00:0e activated.
[  990.395616] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  990.397780] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc ksize
[  990.397954] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  990.397969] ide: Assuming 33MHz system bus speed for PIO modes; override with  idebus=xx
[  990.398454] mice: PS/2 mouse device common for all mice
[  990.399213] EISA: Probing bus 0 at eisa.0
[  990.399235] Cannot allocate resource for EISA slot 1
[  990.399309] Cannot allocate resource for EISA slot 8
[  990.399318] EISA: Detected 0 cards.
[  990.399581] NET: Registered protocol family 2
[  990.409524] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[  990.410015] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[  990.410521] TCP bind hash table entries: 8192 (order: 4, 98304 bytes)
[  990.410984] TCP: Hash tables configured (established 8192 bind 8192)
[  990.410995] TCP reno registered
[  990.411553] TCP bic registered
[  990.411614] NET: Registered protocol family 1
[  990.411642] NET: Registered protocol family 8
[  990.411651] NET: Registered protocol family 20
[  990.411734] Using IPI No-Shortcut mode
[  990.411906] Freeing unused kernel memory: 332k freed
[  990.441008] input: AT Translated Set 2 keyboard as /class/input/input0
[  990.606162] Capability LSM initialized
[  992.551690] PIIX4: IDE controller at PCI slot 0000:00:07.1
[  992.551734] PIIX4: chipset revision 0
[  992.551744] PIIX4: not 100% native mode: will probe irqs later
[  992.551768]     ide0: BM-DMA at 0x1020-0x1027, BIOS settings: hda:DMA, hdb:pi o
[  992.551808]     ide1: BM-DMA at 0x1028-0x102f, BIOS settings: hdc:pio, hdd:pi o
[  992.551838] Probing IDE interface ide0...
[  992.814972] hda: HITACHI_DK23DA-20, ATA DISK drive
[  993.426697] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[  993.427433] Probing IDE interface ide1...
[  993.963238] hda: max request size: 128KiB
[  993.965065] hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63 , UDMA(33)
[  993.965324] hda: cache flushes supported
[  993.966039]  hda: hda1 hda2 hda3
[  994.450902] usbcore: registered new driver usbfs
[  994.452178] usbcore: registered new driver hub
[  994.460357] USB Universal Host Controller Interface driver v2.3
[  994.461721] PCI: Found IRQ 11 for device 0000:00:07.2
[  994.461775] uhci_hcd 0000:00:07.2: UHCI Host Controller
[  994.463172] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus numbe r 1
[  994.463204] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001000
[  994.464748] hub 1-0:1.0: USB hub found
[  994.464789] hub 1-0:1.0: 2 ports detected
[  994.634055] Probing IDE interface ide1...
[  995.243767] Attempting manual resume
[  995.275185] ReiserFS: hda2: found reiserfs format "3.6" with standard journal
[  997.039055] ReiserFS: hda2: using ordered data mode
[  997.067434] ReiserFS: hda2: journal params: device hda2, size 8192, journal f irst block 18, max trans len 1024, max batch 900, max commit age 30, max trans a ge 30
[  997.074156] ReiserFS: hda2: checking transaction log (hda2)
[  997.150703] ReiserFS: hda2: Using r5 hash to sort names
[ 1013.910446] IBM TrackPoint firmware: 0x0b, buttons: 3/3
[ 1013.926679] input: TPPS/2 IBM TrackPoint as /class/input/input1
[ 1014.233083] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[ 1014.233100] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may co rrupt your serial eeprom! Refusing to load module!
[ 1014.233205] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[ 1014.452918] PCI: Found IRQ 5 for device 0000:00:0b.0
[ 1014.529224] PCI: Found IRQ 11 for device 0000:00:0a.0
[ 1014.529275] Yenta: CardBus bridge found at 0000:00:0a.0 [1014:019a]
[ 1014.529304] Yenta: Using CSCINT to route CSC interrupts to PCI
[ 1014.529313] Yenta: Routing CardBus interrupts to PCI
[ 1014.529326] Yenta TI: socket 0000:00:0a.0, mfunc 0x012c1272, devctl 0x64
[ 1014.752688] Yenta: ISA IRQ mask 0x0698, PCI irq 11
[ 1014.752704] Socket status: 30000010
[ 1015.003537] gameport: CS4281 Gameport is pci0000:00:0b.0/gameport0, speed 229 4kHz
[ 1015.264394] input: PC Speaker as /class/input/input2
[ 1015.481468] pccard: PCMCIA card inserted into slot 0
[ 1016.032887] irda_init()
[ 1016.032947] NET: Registered protocol family 23
[ 1016.068828] PnPBIOS: Unknown tag '0x82', length '25'.
[ 1016.081235] pnp: Device 00:0f activated.
[ 1016.081252] nsc_ircc_pnp_probe() : Found cfg_base 0x000 ; firbase 0x2F8 ; irq  3 ; dma 1.
[ 1016.081264] nsc-ircc, Found chip at base=0x000
[ 1016.081299] nsc-ircc, driver loaded (Dag Brattli)
[ 1016.081570] IrDA: Registered device irda0
[ 1016.081639] nsc-ircc, Found dongle: Sharp RY5HD01
[ 1016.081708] nsc-ircc, Found chip at base=0x398
[ 1016.081742] nsc-ircc, driver loaded (Dag Brattli)
[ 1016.081756] nsc_ircc_open(), can't get iobase of 0x2f8
[ 1016.222032] Unable to handle kernel NULL pointer dereference at virtual addre ss 00000004
[ 1016.222145]  printing eip:
[ 1016.222191] c013c886
[ 1016.222198] *pde = 00000000
[ 1016.222263] Oops: 0002 [#1]
[ 1016.222324] PREEMPT SMP
[ 1016.222455] Modules linked in: irtty_sir sir_dev nsc_ircc irda crc_ccitt pcsp kr yenta_socket rsrc_nonstatic pcmcia_core snd_cs4281 gameport snd_rawmidi snd_a c97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss i2c_piix4 snd_pcm snd_page_allo c snd_opl3_lib i2c_core snd_seq_device snd_timer snd_hwdep psmouse serio_raw snd  soundcore evdev reiserfs ide_generic uhci_hcd usbcore ide_disk piix generic pro cessor fbcon tileblit font bitblit softcursor capability commoncap
[ 1016.224281] CPU:    0
[ 1016.224285] EIP:    0060:[<c013c886>]    Not tainted VLI
[ 1016.224290] EFLAGS: 00010092   (2.6.15-23-686)
[ 1016.224485] EIP is at finish_wait+0x36/0x70
[ 1016.224553] eax: 00000202   ebx: cab2ffd8   ecx: 00000000   edx: 00000000
[ 1016.224630] esi: cab2ffcc   edi: cca572a8   ebp: 00000000   esp: cab2ffb4
[ 1016.224704] ds: 007b   es: 007b   ss: 0068
[ 1016.224773] Process kIrDAd (pid: 2867, threadinfo=cab2e000 task=c13d7ab0)
[ 1016.224830] Stack: cab2e000 cab2ffcc 00000000 cca53b83 cca54b20 00000000 0000 0000 c13d7ab0
[ 1016.225242]        c011f4e0 00000000 00000000 cca53ae0 00000000 c0101525 cae8 3f74 00000000
[ 1016.225652]        00000000 00000000 00000000
[ 1016.225857] Call Trace:
[ 1016.225977]  [<cca53b83>] irda_thread+0xa3/0xe0 [sir_dev]
[ 1016.226152]  [<c011f4e0>] default_wake_function+0x0/0x20
[ 1016.226316]  [<cca53ae0>] irda_thread+0x0/0xe0 [sir_dev]
[ 1016.226469]  [<c0101525>] kernel_thread_helper+0x5/0x10
[ 1016.226618] Code: 24 04 89 d6 89 7c 24 08 89 c7 b8 00 e0 ff ff 21 e0 8b 00 c7  00 00 00 00 00 3b 5a 0c 74 2f 89 f8 e8 a0 fe 1c 00 8b 53 04 8b 4e 0c <89> 51 04  89 0a 89 c2 89 f8 89 5e 0c 89 5b 04 8b 1c 24 8b 74 24
[ 1016.229045]  <6>note: kIrDAd[2867] exited with preempt_count 1
[ 1016.335814] Floppy drive(s): fd0 is 1.44M
[ 1016.350210] FDC 0 is a National Semiconductor PC87306
[ 1016.731016] pnp: Device 00:14 activated.
[ 1016.731096] parport: PnPBIOS parport detected.
[ 1016.731214] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 1016.939342] ts: Compaq touchscreen protocol output
[ 1017.051575] cs: IO port probe 0x100-0x4ff: clean.
[ 1017.053025] cs: IO port probe 0xc00-0xcf7: clean.
[ 1017.053868] cs: IO port probe 0xa00-0xaff: clean.
[ 1017.054720] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[ 1017.059636] pcmcia: registering new device pcmcia0.0
[ 1017.445378]   ASIC rev 1,<6>eth0: Megahertz 574B at io 0x300, irq 3, hw_addr 00:50:04:8C:06:D6.
[ 1017.455026]  64K FIFO split 1:1 Rx:Tx, autoselect MII interface.
[ 1018.702003] lp0: using parport0 (interrupt-driven).
[ 1019.150514] Adding 423352k swap on /dev/hda3.  Priority:-1 extents:1 across:4 23352k
[ 1019.743038] NET: Registered protocol family 17
[ 1020.576778] eth1: found link beat
[ 1020.576870] eth1: autonegotiation complete: 100baseT-FD selected
[ 1023.574648] eth1: interrupt(s) dropped!
[ 1027.638134] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@red hat.com
[ 1028.272260] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[ 1028.272345] md: bitmap version 4.39
[ 1034.511461] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[ 1034.898222] ReiserFS: hda1: using ordered data mode
[ 1034.914860] ReiserFS: hda1: journal params: device hda1, size 8192, journal f irst block 18, max trans len 1024, max batch 900, max commit age 30, max trans a ge 30
[ 1034.921191] ReiserFS: hda1: checking transaction log (hda1)
[ 1034.968207] ReiserFS: hda1: Using r5 hash to sort names
[ 1037.474123] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[ 1040.577131] pnp: Device 00:0f cannot be configured because it is in use.
[ 1040.577622] pnp: Device 00:0f cannot be configured because it is in use.
[ 1055.459685] ppdev: user-space parallel port driver
[ 1058.185406] IBM machine detected. Enabling interrupts during APM calls.
[ 1058.185825] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 1060.172049] Non-volatile memory driver v1.2
[ 1060.193511] input: /usr/sbin/thinkpad-keys as /class/input/input3
[ 1061.027407] nsc-ircc, unable to allocate irq=3
[ 1073.329988] NET: Registered protocol family 10
[ 1073.330567] lo: Disabled Privacy Extensions
[ 1073.331134] IPv6 over IPv4 tunneling driver
[ 1073.959710] Bluetooth: Core ver 2.8
[ 1073.959735] NET: Registered protocol family 31
[ 1073.959744] Bluetooth: HCI device and connection manager initialized
[ 1073.959778] Bluetooth: HCI socket layer initialized
[ 1074.061235] Bluetooth: L2CAP ver 2.8
[ 1074.061256] Bluetooth: L2CAP socket layer initialized
[ 1074.206970] Bluetooth: RFCOMM socket layer initialized
[ 1074.207019] Bluetooth: RFCOMM TTY layer initialized
[ 1074.207029] Bluetooth: RFCOMM ver 1.7
[ 1083.443255] eth1: no IPv6 routers present


any help appreciated cause this renders my laptop completely useless

---

### Post by fraco on 2006-06-06
I had a network problem when going from Breezy->Dapper
My eth0 was gone. I figured out that it was renamed to eth1 (by looking in the grarphical network manager), and bringing eth1 online fixed the problem. 
The reason the interface was renamed was an entry in /etc/iftab that listed eth0 as the interface with a particular MAC address. 
Aparantly the driver changed the MAC address, but no the /etc/iftab entry.

maybe you have the same issue, and your ethernet adapter is now eth2?

it might help, or it might be completely unrelated.

kind regards

Tim

---

### Post by lkluc on 2006-06-06
Hi pals,

   I updated to Dapper and I had no problem on my main computer.

   However, I had the same problem you described on my laptop. I got puzzuled for a long while... why would Ubuntu changed my MAC address ? :confused: Especially this is supposed to be fixed in the hardware. Even the label on the bottom of my laptop is showing the original MAC address...

   ...then I remembered, after 2-3 hours of search on the several forums that I had my laptop fixed a couples of month ago, they must have replaced the motherboard along with the network adapter, hence the MAC address changed ! ](*,) Even my Linksys was reporting the new address.

   I guess then Dapper is just more picky about the MAC address written in the /etc/iftab than was Breezy. I changed to the new address and VOILA !

   So did you guys got your computer fixed lately or changed your netword card and forgot about it ? :-\"  

Luc.

---

### Post by Xoctor on 2006-06-09
I've got the same problem. My old PII-266 Dell Inspiron 8000 laptop worked beautifully under Breezy, so I installed Dapper in server mode but the network wont come up. Nothing has changed hardware wise. It uses a Xircom modem/ethernet PCMCIA card for the network.

ifup eth0 causes a "SIOCSIFADDR: No such device" error.

Any help greatly appreciated.

---

### Post by efreddi on 2006-06-10
Similar issue: moving to Dapper on my Dell Latitude C600 the Xircom modem/ethernet seems recognized in the Device Manager but is not listed as available in the Network Setting. Making an hot unplug/pug and then activating it in the Network Setting everything goes fine.  Strange procudeure, I would not like to have to do it always :-(

Really no issue instead with Breezy.

---

### Post by pnael on 2006-06-10
from what you provide you don't have an eth0 but only eth1 provided
on your system. The mac address 00:50:04:8c:06:d6 means it is a 3com card.

eth1 seems to be work correctly since it up, but it does not get any
ip address from dhclient. Are you sure you have a dhcp server
running on your network ?

---

### Post by bdmp on 2006-06-10
I have the same exact problem as the first guy.

---

### Post by Xoctor on 2006-06-10
Thanks efreddi - that hot unplug/plug procedure worked for me, which is a start. Not quite the slick user friendliness I've come to expect from Ubuntu though.

---

### Post by bdmp on 2006-06-10
What is "hot unplug/plug procedure"?

---

### Post by Xoctor on 2006-06-10
[QUOTE=bdmp]What is "hot unplug/plug procedure"?[/QUOTE]

It means that after the OS has booted, eject the PCMCIA card for a few seconds and push it back in.

---

### Post by bdmp on 2006-06-10
[QUOTE=Xoctor]It means that after the OS has booted, eject the PCMCIA card for a few seconds and push it back in.[/QUOTE]
Merci EDIT: Everytime I do that my comp freezes. I can't it to work. 

Also, do you all have "HWaddr 00:00:00:00:00:00" for the new eth1. If I boot the old kernel I get eth0 instead and its is "00:90:99:BC:AE:C7". If I change the HWaddr in eth1 to that will my network work? If so how do I do that?

---

### Post by efreddi on 2006-06-10
Exact, "hot unplug/plug" means that after the boot of the SO I remove the pcmcia card and then after 10 second I plug it again.
I don't know for what reason, but it works. Initially I thiought about some problem on the management of the pcmcia, but the device is correcly recognized and listed in the Device Manager but not available in the Network Settings...
I will try to work a little to understand what's going on.

---

### Post by James Keating on 2006-06-10
This sounds like what happened to me. It seems common, and appears to be due to a kernel bug.

I tried many approaches, but the one that worked for me came from Daniel Carrera on another Ubuntu thread. The kernel disables the PCMCIA port during boot because nothing is using it then. You have to insert the modules by hand, then start cardmgr to watch the card.

sudo modprobe pcmcia && modprobe pcmcia_core
sudo cardmgr

Some people say you need to eject and insert the card after activating the modules, but I didn't need to.

---

### Post by bdmp on 2006-06-10
pcmcia cards are on laptops right? I have a desktop. My card is a pci card. How can I fix this if I have a pci card?

---

### Post by James Keating on 2006-06-10
This thread was about PCMCIA cards, at least at the beginning. PCI cards I know not. Still, something like this may work for you. I gather from looking around that the new kernel, as part of a change in the way hotplugs are dealt with, scans ports on boot. For PCMCIA cards, at least, if the port is not active on boot, the kernel closes the port and doesn't start the module. You need to insert the module yourself, then activate cardmgr so it watches over that port -- ejecting and inserting the card works for some people because then cardmgr says aha, there is a card, and takes the last step to activate it. I guess.

You may have different modules. You can list them with lsmod (and make a file from the list with lsmod > filename. In my case, the modules were listed even though they weren't working. In any case, you should be able to find out what the relevant modules are by looking around the forum or searching Google. After trying dozens of approaches, the solution for me turned out to be very simple, and I hope something similar may help you too.

---

### Post by Xoctor on 2006-06-10
The HWaddr is the MAC ID of the ethernet interface. Every ethernet device has a unique MAC ID - you can't change it. The fact that its coming up zeroed means that your ethernet adapter is not being recognised. Sorry, but I don't know the solution.

---

### Post by bdmp on 2006-06-10
Thanks.

---

### Post by antimatter on 2006-06-11
the problem is solved
i had to add "irqpolling" to the kernel boot line
i still have to manually fire up the device though... anyone know whats up with that?

---

### Post by efreddi on 2006-06-12
Hi antimatter,

where did you add "irqpolling"? In */boot/grub/menu.lst*? To manually activate the card would be an acceptable solution, just to avoid the "hardawre" activation...
Regs


Elia

---

### Post by uliba on 2006-06-15
I had a similar problem, I switch to the "dhcp-client" (the ver 2 of the client) instead of the default dhclient3 and it works ok!

---

### Post by dafnis on 2006-06-16
I had a similar problem when upgrading to Dapper, my pcmcia wifi card and the pci soundcard didn't work.
It took a lot of time for a newbie to find the relevant information in the dmesg output:

[4294667.296000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[4294667.296000] ACPI: Disabling ACPI support

adding the acpi=force parameter to /boot/grub/menu.lst solved the issue

If lspci doesn't list your inserted pcmcia card, dmesg/Yenta complains about "cardbus support disabled" and you have an old laptop like mine, perhaps this can help.

dafnis

---

### Post by otaviofcs on 2006-06-20
thanks ikluc. I changed my rtl8139 to a via-rhine and it has stoped working. After read your tip i've made a:
#dmesg | grep eth
and got my new MAC. So i've altered the /etc/iftab entry (just changed my mac address) and reboot. It starts work just fine.

---

### Post by dro0g on 2006-06-30
I had a similar problem with my fileserver which is an old PII 350MHZ. I upgraded from hoary to dapper and networking tanked. dmesg didn't show anything for the NIC, which is a 10/100 PCI card using the DEC Tulip chipset. 

I logged in from the console (grumble grumble, this thing lives headless in a closet so this meant dragging over a monitor and keyboard) and ran **modprobe tulip**. dmesg then showed the card loaded. I did an **ifconfig eth0 up** and then **/etc/init.d/network restart** and boom, we're in business. 

I added tulip to **/etc/modules** but I have no idea why it didn't load automatically. I verified that this solved the issue between reboots.

---

### Post by efreddi on 2006-07-29
> **Xoctor said:**
> Thanks efreddi - that hot unplug/plug procedure worked for me, which is a start. Not quite the slick user friendliness I've come to expect from Ubuntu though.

Hi Xoctor, I made a sort of workaround, you can find the details here:
[http://www.ubuntuforums.org/showthread.php?t=207023]("http://www.ubuntuforums.org/showthread.php?t=207023")

Best regards




Elia Freddi

---

### Post by runzau on 2006-09-06
Hi,

I also had problems with eth0 recognition on my machine as soon as I upgraded to Dapper. 

To fix the problem I did the following:

1.Run *ip link*  and the result was: 

1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether **00:0c:f1:af:b8:6c** brd ff:ff:ff:ff:ff:ff
3: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0

2.Run *vi /etc/iftab*
Inside the file compare the original mac address with the one highlighted in step 1.
If different change to the ether highlighted above.

For reference i had the following:
#eth0 mac 00:11:d8:84:e3:f9
eth0 mac 00:0c:f1:af:b8:6c

Hope that helps! :)

---

### Post by john280z on 2006-09-12
It helped me, thanks!

johnm

---

