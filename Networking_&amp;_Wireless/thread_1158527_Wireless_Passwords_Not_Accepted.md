---
title: "Wireless Passwords Not Accepted"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by fleasbaby on 2009-05-13
Hi All,

I am brand new to the whole Ubuntu thing, but really excited to be trying out something other than "the big two". I thought I would dip my toes in the water with a Wubi install on my HP dv4 laptop that originally came with 64 bit Vista Home.

All went fine, except I am having trouble accessing the internet when I boot into Ubuntu (I can still get on in Vista fine). I click on the icon in the top right of the screen, select my wireless network and wait....nothing happens for a while and then I get a screen that asks me to provide my passwords and select 

I ran the command "ifconfig" and got the following:

bruce@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:e3:5d:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:248 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:6e:e4:18  
          inet6 addr: fe80::221:ff:fe6e:e418/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:67340
          TX packets:59 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:20650 (20.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

I ran "iwconfig" and got this:

bruce@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

Would anyone be able to assist at all?

Thank you, and much appreciated.

Bruce

---

### Post by HankB on 2009-05-13
Long shot here - I had trouble when I had my access point configured for WPA2/TKIP+AES. Switching to WPA2/AES worked around the bug.

It would help to know what the wireless H/W is. You can identify it by running the command 'sudo lshw -c net' and looking for the appropriate entry.

Another thing you can do is post the output of 'dmesg' - just the stuff that gets written between the time the network manager asks for the password, tries and asks again. There is probably something there that will provide a clue why it doesn't connect.

(If you post command output in code blocks using the '#' button above, it will be easier to visually parse.)

-hank

---

### Post by fleasbaby on 2009-05-14
Hi Hank,

Thanks for the help, its much appreciated....I have the outputs you asked for...trying the WPA thing didn't help much...

Here is what I got for the hardware:

  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:6e:e4:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:e3:5d:92
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:30:fb:14:63:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I did get a connection just plugging my ethernet cable in so I suspect we are on the right track with the wireless card....I got the ndiswrapper app in, but wasn't too sure how to find my .inf files...

Again, I really appreciate any advice :).

---

### Post by fleasbaby on 2009-05-14
And the real long one I got for the message is as follows (sorry, I wasn't too sure how to do the # thing...)

[    1.143397] pci 0000:00:1c.3:   IO window: 0x3000-0x3fff
[    1.143403] pci 0000:00:1c.3:   MEM window: 0xd8500000-0xd94fffff
[    1.143407] pci 0000:00:1c.3:   PREFETCH window: 0x000000d3400000-0x000000d43fffff
[    1.143415] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
[    1.143418] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    1.143423] pci 0000:00:1c.4:   MEM window: 0xd7500000-0xd84fffff
[    1.143428] pci 0000:00:1c.4:   PREFETCH window: 0x000000d4400000-0x000000d53fffff
[    1.143435] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:06
[    1.143438] pci 0000:00:1c.5:   IO window: 0x1000-0x1fff
[    1.143443] pci 0000:00:1c.5:   MEM window: 0xd6500000-0xd74fffff
[    1.143448] pci 0000:00:1c.5:   PREFETCH window: 0x000000d5400000-0x000000d63fffff
[    1.143455] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    1.143456] pci 0000:00:1e.0:   IO window: disabled
[    1.143462] pci 0000:00:1e.0:   MEM window: disabled
[    1.143466] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.143482] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.143486] pci 0000:00:1c.0: setting latency timer to 64
[    1.143496] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.143500] pci 0000:00:1c.1: setting latency timer to 64
[    1.143509] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.143513] pci 0000:00:1c.2: setting latency timer to 64
[    1.143522] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.143527] pci 0000:00:1c.3: setting latency timer to 64
[    1.143535] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.143540] pci 0000:00:1c.4: setting latency timer to 64
[    1.143548] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.143553] pci 0000:00:1c.5: setting latency timer to 64
[    1.143560] pci 0000:00:1e.0: setting latency timer to 64
[    1.143564] bus: 00 index 0 io port: [0x00-0xffff]
[    1.143566] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    1.143568] bus: 01 index 0 io port: [0x6000-0x6fff]
[    1.143569] bus: 01 index 1 mmio: [0xdb500000-0xdc4fffff]
[    1.143571] bus: 01 index 2 mmio: [0xd0400000-0xd13fffff]
[    1.143573] bus: 01 index 3 mmio: [0x0-0x0]
[    1.143574] bus: 02 index 0 io port: [0x5000-0x5fff]
[    1.143576] bus: 02 index 1 mmio: [0xda500000-0xdb4fffff]
[    1.143578] bus: 02 index 2 mmio: [0xd1400000-0xd23fffff]
[    1.143579] bus: 02 index 3 mmio: [0x0-0x0]
[    1.143581] bus: 03 index 0 io port: [0x4000-0x4fff]
[    1.143582] bus: 03 index 1 mmio: [0xd9500000-0xda4fffff]
[    1.143584] bus: 03 index 2 mmio: [0xd2400000-0xd33fffff]
[    1.143585] bus: 03 index 3 mmio: [0x0-0x0]
[    1.143587] bus: 04 index 0 io port: [0x3000-0x3fff]
[    1.143589] bus: 04 index 1 mmio: [0xd8500000-0xd94fffff]
[    1.143590] bus: 04 index 2 mmio: [0xd3400000-0xd43fffff]
[    1.143592] bus: 04 index 3 mmio: [0x0-0x0]
[    1.143593] bus: 05 index 0 io port: [0x2000-0x2fff]
[    1.143595] bus: 05 index 1 mmio: [0xd7500000-0xd84fffff]
[    1.143596] bus: 05 index 2 mmio: [0xd4400000-0xd53fffff]
[    1.143598] bus: 05 index 3 mmio: [0x0-0x0]
[    1.143600] bus: 06 index 0 io port: [0x1000-0x1fff]
[    1.143601] bus: 06 index 1 mmio: [0xd6500000-0xd74fffff]
[    1.143603] bus: 06 index 2 mmio: [0xd5400000-0xd63fffff]
[    1.143604] bus: 06 index 3 mmio: [0x0-0x0]
[    1.143606] bus: 09 index 0 mmio: [0x0-0x0]
[    1.143607] bus: 09 index 1 mmio: [0x0-0x0]
[    1.143608] bus: 09 index 2 mmio: [0x0-0x0]
[    1.143610] bus: 09 index 3 io port: [0x00-0xffff]
[    1.143611] bus: 09 index 4 mmio: [0x000000-0xffffffffffffffff]
[    1.143619] NET: Registered protocol family 2
[    1.176054] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.176562] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    1.178580] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.179113] TCP: Hash tables configured (established 262144 bind 65536)
[    1.179116] TCP reno registered
[    1.188134] NET: Registered protocol family 1
[    1.188250] checking if image is initramfs... it is
[    1.889497] Freeing initrd memory: 8028k freed
[    1.893430] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    1.893433] Simple Boot Flag at 0x44 set to 0x1
[    1.893737] audit: initializing netlink socket (disabled)
[    1.893753] type=2000 audit(1242317990.892:1): initialized
[    1.902047] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.903213] VFS: Disk quotas dquot_6.5.1
[    1.903263] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.903785] fuse init (API version 7.10)
[    1.903857] msgmni has been set to 7718
[    1.904010] alg: No test for stdrng (krng)
[    1.904019] io scheduler noop registered
[    1.904021] io scheduler anticipatory registered
[    1.904023] io scheduler deadline registered
[    1.904059] io scheduler cfq registered (default)
[    1.904070] pci 0000:00:02.0: Boot video device
[    9.904006] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   17.904006] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   18.137489] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[   18.137539] pcieport-driver 0000:00:1c.0: found MSI capability
[   18.137575] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[   18.137591] pci_express 0000:00:1c.0:pcie00: allocate port service
[   18.137603] pci_express 0000:00:1c.0:pcie02: allocate port service
[   18.137614] pci_express 0000:00:1c.0:pcie03: allocate port service
[   18.137690] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[   18.137737] pcieport-driver 0000:00:1c.1: found MSI capability
[   18.137770] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[   18.137786] pci_express 0000:00:1c.1:pcie00: allocate port service
[   18.137797] pci_express 0000:00:1c.1:pcie03: allocate port service
[   18.137868] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[   18.137917] pcieport-driver 0000:00:1c.2: found MSI capability
[   18.137950] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[   18.137965] pci_express 0000:00:1c.2:pcie00: allocate port service
[   18.137976] pci_express 0000:00:1c.2:pcie02: allocate port service
[   18.137986] pci_express 0000:00:1c.2:pcie03: allocate port service
[   18.138058] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[   18.138107] pcieport-driver 0000:00:1c.3: found MSI capability
[   18.138139] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[   18.138155] pci_express 0000:00:1c.3:pcie00: allocate port service
[   18.138166] pci_express 0000:00:1c.3:pcie02: allocate port service
[   18.138176] pci_express 0000:00:1c.3:pcie03: allocate port service
[   18.138251] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[   18.138299] pcieport-driver 0000:00:1c.4: found MSI capability
[   18.138332] pcieport-driver 0000:00:1c.4: irq 2299 for MSI/MSI-X
[   18.138347] pci_express 0000:00:1c.4:pcie00: allocate port service
[   18.138359] pci_express 0000:00:1c.4:pcie02: allocate port service
[   18.138369] pci_express 0000:00:1c.4:pcie03: allocate port service
[   18.138443] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[   18.138492] pcieport-driver 0000:00:1c.5: found MSI capability
[   18.138525] pcieport-driver 0000:00:1c.5: irq 2298 for MSI/MSI-X
[   18.138540] pci_express 0000:00:1c.5:pcie00: allocate port service
[   18.138551] pci_express 0000:00:1c.5:pcie02: allocate port service
[   18.138562] pci_express 0000:00:1c.5:pcie03: allocate port service
[   18.138643] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.138829] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[   18.268089] ACPI: AC Adapter [AC] (on-line)
[   18.748787] ACPI: Battery Slot [BAT0] (battery present)
[   18.748862] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[   18.748865] ACPI: Power Button (FF) [PWRF]
[   18.748906] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[   18.748908] ACPI: Power Button (CM) [PWRB]
[   18.748948] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[   18.749032] ACPI: Lid Switch [LID0]
[   18.749073] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   18.749083] ACPI: Sleep Button (CM) [SLPB]
[   18.793488] fan PNP0C0B:00: registered as cooling_device0
[   18.793493] ACPI: Fan [FAN] (on)
[   18.794347] ACPI: SSDT BDB6EC18, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20060912)
[   18.794945] ACPI: SSDT BDB6C618, 05B3 (r1  PmRef  Cpu0Cst     3001 INTL 20060912)
[   18.795517] Monitor-Mwait will be used to enter C-1 state
[   18.795520] Monitor-Mwait will be used to enter C-2 state
[   18.795522] Monitor-Mwait will be used to enter C-3 state
[   18.795534] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.795551] processor ACPI_CPU:00: registered as cooling_device1
[   18.795555] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.796095] ACPI: SSDT BDB6DE18, 01CF (r1  PmRef    ApIst     3000 INTL 20060912)
[   18.796630] ACPI: SSDT BDB6EF18, 008D (r1  PmRef    ApCst     3000 INTL 20060912)
[   18.797297] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   18.797314] processor ACPI_CPU:01: registered as cooling_device2
[   18.797317] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.954060] thermal LNXTHERM:01: registered as thermal_zone0
[   18.982262] ACPI: Thermal Zone [THRM] (43 C)
[   19.016743] Linux agpgart interface v0.103
[   19.016751] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   19.017660] brd: module loaded
[   19.017958] loop: module loaded
[   19.018014] Fixed MDIO Bus: probed
[   19.018019] PPP generic driver version 2.4.2
[   19.018071] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[   19.018097] Driver 'sd' needs updating - please use bus_type methods
[   19.018105] Driver 'sr' needs updating - please use bus_type methods
[   19.018143] ahci 0000:00:1f.2: version 3.0
[   19.018159] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   19.018196] ahci 0000:00:1f.2: irq 2297 for MSI/MSI-X
[   19.018279] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[   19.018282] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ems 
[   19.018287] ahci 0000:00:1f.2: setting latency timer to 64
[   19.018564] scsi0 : ahci
[   19.018648] scsi1 : ahci
[   19.018695] scsi2 : ahci
[   19.018745] scsi3 : ahci
[   19.018798] scsi4 : ahci
[   19.018846] scsi5 : ahci
[   19.019018] ata1: SATA max UDMA/133 abar m2048@0xdc504000 port 0xdc504100 irq 2297
[   19.019021] ata2: SATA max UDMA/133 abar m2048@0xdc504000 port 0xdc504180 irq 2297
[   19.019023] ata3: DUMMY
[   19.019024] ata4: DUMMY
[   19.019026] ata5: SATA max UDMA/133 abar m2048@0xdc504000 port 0xdc504300 irq 2297
[   19.019029] ata6: SATA max UDMA/133 abar m2048@0xdc504000 port 0xdc504380 irq 2297
[   19.500016] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.500909] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.501012] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.501113] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.501115] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   19.501216] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.501316] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.501320] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[   19.501322] ata1.00: 488397168 sectors, multi 0: LBA48 
[   19.502276] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.502381] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.502482] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.502484] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   19.502585] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.502685] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.502702] ata1.00: configured for UDMA/100
[   20.000020] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.015940] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.016353] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 succeeded
[   20.016758] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 succeeded
[   20.016760] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   20.017165] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 succeeded
[   20.017628] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 succeeded
[   20.030752] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633L, 0400, max UDMA/100
[   20.046224] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.046637] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 succeeded
[   20.047044] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 succeeded
[   20.047047] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   20.047446] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 succeeded
[   20.060276] ata2.00: configured for UDMA/100
[   20.396016] ata5: SATA link down (SStatus 0 SControl 300)
[   20.732015] ata6: SATA link down (SStatus 0 SControl 300)
[   20.748097] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[   20.748180] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   20.748195] sd 0:0:0:0: [sda] Write Protect is off
[   20.748197] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.748221] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.748280] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   20.748293] sd 0:0:0:0: [sda] Write Protect is off
[   20.748295] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.748318] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.748321]  sda: sda1 sda2
[   21.027285] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.027330] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.029563] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633L  0400 PQ: 0 ANSI: 5
[   21.035617] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.035620] Uniform CD-ROM driver Revision: 3.20
[   21.035701] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.035734] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   21.036367] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   21.036387] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   21.036404] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[   21.036408] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   21.036463] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   21.040385] ehci_hcd 0000:00:1a.7: debug port 1
[   21.040391] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[   21.040405] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xdc504c00
[   21.052009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[   21.052064] usb usb1: configuration #1 chosen from 1 choice
[   21.052090] hub 1-0:1.0: USB hub found
[   21.052097] hub 1-0:1.0: 4 ports detected
[   21.052192] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   21.052201] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   21.052204] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.052241] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   21.056162] ehci_hcd 0000:00:1d.7: debug port 1
[   21.056169] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   21.056182] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdc504800
[   21.072008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   21.072055] usb usb2: configuration #1 chosen from 1 choice
[   21.072076] hub 2-0:1.0: USB hub found
[   21.072082] hub 2-0:1.0: 8 ports detected
[   21.072175] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.072189] uhci_hcd: USB Universal Host Controller Interface driver
[   21.072207] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.072215] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[   21.072218] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   21.072259] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   21.072294] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000070e0
[   21.072361] usb usb3: configuration #1 chosen from 1 choice
[   21.072385] hub 3-0:1.0: USB hub found
[   21.072392] hub 3-0:1.0: 2 ports detected
[   21.072473] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.072479] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[   21.072483] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   21.072525] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   21.072558] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000070c0
[   21.072628] usb usb4: configuration #1 chosen from 1 choice
[   21.072649] hub 4-0:1.0: USB hub found
[   21.072655] hub 4-0:1.0: 2 ports detected
[   21.072733] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   21.072738] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   21.072742] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.072777] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   21.072803] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000070a0
[   21.072871] usb usb5: configuration #1 chosen from 1 choice
[   21.072891] hub 5-0:1.0: USB hub found
[   21.072897] hub 5-0:1.0: 2 ports detected
[   21.072974] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   21.072980] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   21.072983] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.073018] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   21.073051] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00007080
[   21.073119] usb usb6: configuration #1 chosen from 1 choice
[   21.073140] hub 6-0:1.0: USB hub found
[   21.073146] hub 6-0:1.0: 2 ports detected
[   21.073223] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   21.073229] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   21.073232] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   21.073270] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   21.073298] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00007060
[   21.073363] usb usb7: configuration #1 chosen from 1 choice
[   21.073386] hub 7-0:1.0: USB hub found
[   21.073392] hub 7-0:1.0: 2 ports detected
[   21.073468] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   21.073474] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   21.073477] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   21.073519] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[   21.073553] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00007040
[   21.073621] usb usb8: configuration #1 chosen from 1 choice
[   21.073642] hub 8-0:1.0: USB hub found
[   21.073650] hub 8-0:1.0: 2 ports detected
[   21.073772] usbcore: registered new interface driver libusual
[   21.073802] usbcore: registered new interface driver usbserial
[   21.073811] USB Serial support registered for generic
[   21.073824] usbcore: registered new interface driver usbserial_generic
[   21.073826] usbserial: USB Serial Driver core
[   21.073870] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[   21.118759] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.118764] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.128032] mice: PS/2 mouse device common for all mice
[   21.188062] rtc_cmos 00:03: RTC can wake from S4
[   21.188092] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[   21.188123] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[   21.188175] device-mapper: uevent: version 1.0.3
[   21.188256] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[   21.188319] device-mapper: multipath: version 1.0.5 loaded
[   21.188321] device-mapper: multipath round-robin: version 1.0.0 loaded
[   21.188458] cpuidle: using governor ladder
[   21.188555] cpuidle: using governor menu
[   21.188929] TCP cubic registered
[   21.188984] NET: Registered protocol family 10
[   21.189350] lo: Disabled Privacy Extensions
[   21.189607] NET: Registered protocol family 17
[   21.189623] Bluetooth: L2CAP ver 2.11
[   21.189624] Bluetooth: L2CAP socket layer initialized
[   21.189627] Bluetooth: SCO (Voice Link) ver 0.6
[   21.189628] Bluetooth: SCO socket layer initialized
[   21.189653] Bluetooth: RFCOMM socket layer initialized
[   21.189658] Bluetooth: RFCOMM TTY layer initialized
[   21.189659] Bluetooth: RFCOMM ver 1.10
[   21.190237] Marking TSC unstable due to TSC halts in idle
[   21.190332] registered taskstats version 1
[   21.190473]   Magic number: 9:14:338
[   21.190498] tty tty59: hash matches
[   21.190584] rtc_cmos 00:03: setting system clock to 2009-05-14 16:20:10 UTC (1242318010)
[   21.190586] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.190588] EDD information not available.
[   21.190651] Freeing unused kernel memory: 536k freed
[   21.190855] Write protecting the kernel read-only data: 6708k
[   21.218919] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[   21.456549] usb 2-5: new high speed USB device using ehci_hcd and address 3
[   21.565271] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   21.565328] r8169 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   21.565449] r8169 0000:04:00.0: setting latency timer to 64
[   21.566627] r8169 0000:04:00.0: irq 2296 for MSI/MSI-X
[   21.567461] eth0: RTL8102e at 0xffffc2000007c000, 00:1e:ec:e3:5d:92, XID 24a00000 IRQ 2296
[   21.618205] usb 2-5: configuration #1 chosen from 1 choice
[   21.856554] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   22.000515] Clocksource tsc unstable (delta = -103920147 ns)
[   22.032721] usb 5-1: configuration #1 chosen from 1 choice
[   22.048284] usbcore: registered new interface driver hiddev
[   22.061139] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input6
[ 22.084656] generic-usb 0003:046D:C019.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[   22.084682] usbcore: registered new interface driver usbhid
[   22.084686] usbhid: v2.6:USB HID core driver
[   22.232202] kjournald starting.  Commit interval 5 seconds
[   22.232214] EXT3-fs: mounted filesystem with ordered data mode.
[   27.605994] udev: starting version 141
[   27.708495] lis3lv02d: laptop model unknown, using default axes configuration
[   27.720635] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
[   27.745321] lis3lv02d driver loaded.
[   27.756866] acpi device:04: registered as cooling_device3
[   27.757256] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input8
[   27.788716] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   27.789182] leds-hp-disk driver loaded.
[   27.886466] agpgart-intel 0000:00:00.0: Intel Mobile IntelÂ® GM45 Express Chipset
[   27.887139] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   27.891911] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   27.933837] iTCO_vendor_support: vendor-support=0
[   27.953635] sdhci: Secure Digital Host Controller Interface driver
[   27.953638] sdhci: Copyright(c) Pierre Ossman
[   28.177018] sdhci-pci 0000:05:00.0: SDHCI controller found [197b:2382] (rev 0)
[   28.177041] sdhci-pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.177112] sdhci-pci 0000:05:00.0: setting latency timer to 64
[   28.177182] mmc0: SDHCI controller on PCI [0000:05:00.0] using ADMA
[   28.177192] sdhci-pci 0000:05:00.2: SDHCI controller found [197b:2381] (rev 0)
[   28.177208] sdhci-pci 0000:05:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.177214] sdhci-pci 0000:05:00.2: Refusing to bind to secondary interface.
[   28.177221] sdhci-pci 0000:05:00.2: PCI INT A disabled
[   28.211524] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   28.211675] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[   28.211763] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   28.231605] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   28.281327] ieee80211_crypt: registered algorithm 'NULL'
[   28.284646] wl: module license '' taints kernel.
[   28.286749] wl 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   28.286760] wl 0000:03:00.0: setting latency timer to 64
[   28.506348] ieee80211_crypt: registered algorithm 'TKIP'
[   28.506661] eth1: Broadcom BCM432b 802.11 Wireless Controller 5.10.79.10
[   28.738450] Linux video capture interface: v2.00
[   28.806467] uvcvideo: Found UVC 1.00 device HP Webcam  (046d:09b8)
[   28.812602] input: HP Webcam  as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input10
[   28.825392] usbcore: registered new interface driver uvcvideo
[   28.825429] USB Video Class driver (v0.1.0)
[   28.983404] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   28.983414] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   28.983504] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   28.990470] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   29.945359] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input11
[   30.016507] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   30.018651] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[   30.088703] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input13
[   30.348583] lp: driver loaded but no devices found
[   30.942156] EXT3 FS on loop0, internal journal
[   34.730075] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k
[ 34.915259] type=1505 audit(1242343224.221:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2224
[   34.953024] type=1505 audit(1242343224.261:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2228
[   34.953134] type=1505 audit(1242343224.261:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2228
[ 34.953170] type=1505 audit(1242343224.261:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2228
[ 34.953207] type=1505 audit(1242343224.261:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2228
[ 35.059031] type=1505 audit(1242343224.365:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2233
[   35.059182] type=1505 audit(1242343224.365:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2233
[   35.083307] type=1505 audit(1242343224.389:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2237
[   37.206911] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.206914] Bluetooth: BNEP filters: protocol multicast
[   37.225935] Bridge firewalling registered
[   38.527161] ppdev: user-space parallel port driver
[   39.786000] [drm] Initialized drm 1.1.0 20060810
[   39.797349] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.797354] pci 0000:00:02.0: setting latency timer to 64
[   39.797626] pci 0000:00:02.0: irq 2295 for MSI/MSI-X
[   39.797713] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   39.799303] [drm:i915_setparam] *ERROR* unknown parameter 4
[   42.691779] r8169: eth0: link down
[   42.692444] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.320045] eth1: no IPv6 routers present
[   59.014653] CPU0 attaching NULL sched-domain.
[   59.014658] CPU1 attaching NULL sched-domain.
[   59.032081] CPU0 attaching sched-domain:
[   59.032085]  domain 0: span 0-1 level MC
[   59.032088]   groups: 0 1
[   59.032093] CPU1 attaching sched-domain:
[   59.032095]  domain 0: span 0-1 level MC
[   59.032097]   groups: 1 0
[  522.745876] r8169: eth0: link down
[  522.747432] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  533.492134] eth1: no IPv6 routers present

---

### Post by fleasbaby on 2009-05-14
PS: I apologize if I disappear for the next few days...buggering off for the weekend, but will be back Monday to rejoin the fray! :)

---

