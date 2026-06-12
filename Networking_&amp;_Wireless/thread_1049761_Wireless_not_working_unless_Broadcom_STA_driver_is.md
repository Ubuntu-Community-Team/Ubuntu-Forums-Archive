---
title: "Wireless not working unless Broadcom STA driver is deactivated reactivated"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by Detcader on 2009-01-24
I'm on a Dell Inspiron 1525 laptop, Linux Kernel 2.6.27-11-generic. on -10-generic, wireless worked normally. Now, after much effort, Ubuntu only recognizes the wireless card when I boot after I deactive the Broadcom STA driver under Hardware Drivers, and then reactivate it.

--Some information--

Here is the results of 

```
ifconfig ;  iwconfig;  route -n;  cat /etc/resolv.conf  and cat /etc/network/interfaces
```:

```

eth0      Link encap:Ethernet  HWaddr 00:21:9b:e2:a5:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:22:69:32:05:f9  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6655 errors:0 dropped:0 overruns:0 frame:8464
          TX packets:7908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2167344 (2.1 MB)  TX bytes:6648853 (6.6 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10538 (10.5 KB)  TX bytes:10538 (10.5 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
domain home
search home
nameserver 192.168.1.1
cat: and: No such file or directory
cat: cat: No such file or directory
auto lo
iface lo inet loopback

```

I'm using wicd as a network manager, because I don't want to type a password in every time I boot with nm-applet

---

### Post by pytheas22 on 2009-01-24
If you run this command once:
```

echo wl | sudo tee -a /etc/modules
```

Now reboot.  Does that solve the problem?

If not, try this:

1. type:

```
sudo gedit /etc/init.d/modprobe-wl.sh
```

A blank file will open.  Add these lines to it:
```

#!/bin/bash

modprobe wl
rmmod wl
modprobe wl
ifconfig eth1 up
```

Then save and close the file, and run these commands:
```

cd /etc/init.d
sudo chmod +x modprobe-wl.sh
sudo update-rc.d modprobe-wl.sh start 99 2 3 4 5
```

Now reboot.  If you still have to reload the driver manually, please post the output of:
```

dmesg
```

(There will be quite a bit of output; please post it all.)

---

### Post by kevdog on 2009-01-25
pytheas -- again a great solution by making this a runlevel script, however I believe you should again add it in run level 99 rather than the default run level 20.  This would allow every service to be started and the last thing to run -- the wireless configuration.  I think this would be the preferred method.

Also whatever just happened to placing these commands within rc.local?  I know there are multiple ways to skin a cat, however I'm just trying to keep things straight forward and easy!!

---

### Post by pytheas22 on 2009-01-25
kevdog: I didn't think it would make a difference when the script was run--basically I'm assuming that simply reloading the wl module after its initial insertion is what it takes to solve the problem--but I guess it can't hurt to run it as late as possible.  I changed the original post to reflect that (please let me know if the syntax looks wrong; I'm rusty on the update-rc.d arguments).  Thanks for the suggestion.

---

### Post by kevdog on 2009-01-25
Looks good to me -- You might be right about your assumption -- I just don't know.  If I don't know I usually error for things to be loaded later in the boot sequence.  Of course the beauty of using update-rc.d is that the parameter can quickly be changed.

---

### Post by seoci on 2009-02-13
I have a different laptop, a Dell Inspiron 1318, but ran into the same issue.  Adding wl to /etc/modules didn't solve the problem, but adding the stuff you put in modprobe-wl.sh to rc.local did solve the problem.

Just wanted to let you know that you got it (as well as anyone else who ends up looking here for a solution).

---

### Post by gamerguy76 on 2009-05-25
Thank you! I spent three days trying to figure this out. I have dell xps 1330 with 1505n wireless. After installing the script you suggested everything works perfectly when I reboot.

---

### Post by htpw16 on 2009-10-25
Hello all,

Came across this thread when I was looking how to get more information from my iwconfig. I have the Broadcom STA driver and my wireless connection is working flawlessly. However, when I iwconfig all I get is
 
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated  
```

I want to also set/ play with the rate and txpower which I am currently unable to do. Any ideas or suggestions?

Thanks.

---

### Post by pytheas22 on 2009-10-26
htpw16: the only suggestion I have is to try installing the STA driver using the version from [Broadcom's website]("http://www.broadcom.com/support/802.11/linux_sta.php"), which will probably be more up-to-date than the Ubuntu one and might work better.

That said, I doubt it actually will.  The driver may simply not be designed to support all the iwconfig calls on your hardware, and since it's closed-source and proprietary, there's not much that can be done about it besides complain to Broadcom and hope they fix it.

If your card is supported by the open-source and standards-compliant b43 driver, you could try that instead, but there are a few Broadcom chips (in particular, the 11n ones) that don't yet work with b43.

---

### Post by Torgas Prim on 2009-11-01
I have been following this thread's suggestions and am at the dmesg command:
I mistakenly hit No I think when enabling the driver during a fresh install of ubuntu, to allow the firmware to install also. How can I fix this?

[    9.408274] Brought up 1 CPUs
[    9.408344] CPU0 attaching sched-domain:
[    9.408347]  domain 0: span 01
[    9.408348]   groups: 01
[    9.408491] net_namespace: 64 bytes
[    9.408497] Booting paravirtualized kernel on bare hardware
[    9.408911] Time: 13:07:52  Date: 11/01/09
[    9.408931] NET: Registered protocol family 16
[    9.409080] EISA bus registered
[    9.409106] ACPI: bus type pci registered
[    9.415198] PCI: PCI BIOS revision 2.10 entry at 0xfd8cc, last bus=1
[    9.415200] PCI: Using configuration type 1
[    9.415205] Setting up standard PCI resources
[    9.416721] ACPI: EC: Look up EC in DSDT
[    9.418879] ACPI: Interpreter enabled
[    9.418881] ACPI: (supports S0 S3 S4 S5)
[    9.418890] ACPI: Using IOAPIC for interrupt routing
[    9.420854] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.424091] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[    9.424093] ACPI: EC: driver started in interrupt mode
[    9.424121] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.424476] PCI quirk: region 4000-407f claimed by vt8235 PM
[    9.424479] PCI quirk: region 8100-810f claimed by vt8235 SMB
[    9.424831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.429505] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
[    9.429566] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11, disabled.
[    9.429623] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *10, disabled.
[    9.429679] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *10, disabled.
[    9.429758] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 12 14 15)
[    9.429834] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    9.429911] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 11 12 14 15) *10
[    9.429989] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    9.430072] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.430094] pnp: PnP ACPI init
[    9.430100] ACPI: bus type pnp registered
[    9.431744] pnp: PnP ACPI: found 9 devices
[    9.431746] ACPI: ACPI bus type pnp unregistered
[    9.431749] PnPBIOS: Disabled by ACPI PNP
[    9.431911] PCI: Using ACPI for IRQ routing
[    9.431913] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.440208] NET: Registered protocol family 8
[    9.440210] NET: Registered protocol family 20
[    9.440263] AppArmor: AppArmor Filesystem Enabled
[    9.444179] Time: tsc clocksource has been installed.
[    9.452194] system 00:05: iomem range 0x0-0x9ffff could not be reserved
[    9.452197] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
[    9.452200] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
[    9.452202] system 00:05: iomem range 0xffee0000-0xffefffff has been reserved
[    9.452205] system 00:05: iomem range 0xfee00400-0xfee013ff has been reserved
[    9.452209] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    9.452212] system 00:06: ioport range 0xf510-0xf511 has been reserved
[    9.452214] system 00:06: ioport range 0xf500-0xf500 has been reserved
[    9.452217] system 00:06: ioport range 0x4000-0x407f has been reserved
[    9.452219] system 00:06: ioport range 0x8100-0x811f could not be reserved
[    9.452222] system 00:06: ioport range 0x300-0x301 has been reserved
[    9.482489] PCI: Bridge: 0000:00:01.0
[    9.482491]   IO window: 2000-2fff
[    9.482495]   MEM window: d0100000-d01fffff
[    9.482498]   PREFETCH window: d8000000-dfffffff
[    9.482501] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[    9.482503]   IO window: 00003000-000030ff
[    9.482506]   IO window: 00003400-000034ff
[    9.482509]   PREFETCH window: 60000000-63ffffff
[    9.482513]   MEM window: 64000000-67ffffff
[    9.482526] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    9.482564] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 16
[    9.482578] NET: Registered protocol family 2
[    9.520129] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.520405] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.521568] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.522231] TCP: Hash tables configured (established 131072 bind 65536)
[    9.522234] TCP reno registered
[    9.532191] checking if image is initramfs... it is
[    9.983332] Switched to high resolution mode on CPU 0
[   10.125480] Freeing initrd memory: 7310k freed
[   10.126042] audit: initializing netlink socket (disabled)
[   10.126056] audit(1257080872.088:1): initialized
[   10.126203] highmem bounce pool size: 64 pages
[   10.127704] VFS: Disk quotas dquot_6.5.1
[   10.127763] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.127889] io scheduler noop registered
[   10.127891] io scheduler anticipatory registered
[   10.127893] io scheduler deadline registered
[   10.127902] io scheduler cfq registered (default)
[   10.127909] PCI: VIA PCI bridge detected. Disabling DAC.
[   10.127965] Boot video device is 0000:01:00.0
[   10.128171] isapnp: Scanning for PnP cards...
[   10.481255] isapnp: No Plug & Play device found
[   10.506159] Real Time Clock Driver v1.12ac
[   10.506238] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.507165] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.507222] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.507291] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.510302] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.510306] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.510585] mice: PS/2 mouse device common for all mice
[   10.510673] EISA: Probing bus 0 at eisa.0
[   10.510680] Cannot allocate resource for EISA slot 1
[   10.510682] Cannot allocate resource for EISA slot 2
[   10.510684] Cannot allocate resource for EISA slot 3
[   10.510686] Cannot allocate resource for EISA slot 4
[   10.510703] EISA: Detected 0 cards.
[   10.510705] cpuidle: using governor ladder
[   10.510707] cpuidle: using governor menu
[   10.510788] NET: Registered protocol family 1
[   10.510810] Using IPI No-Shortcut mode
[   10.510841] registered taskstats version 1
[   10.510933]   Magic number: 1:547:128
[   10.511069]   hash matches device device:03
[   10.511071]   hash matches device PNP0C02:00
[   10.511077] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.511079] EDD information not available.
[   10.511514] Freeing unused kernel memory: 368k freed
[   10.511538] Write protecting the kernel read-only data: 803k
[   10.538373] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.718516] fuse init (API version 7.9)
[   11.734652] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   12.176772] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 18 (level, low) -> IRQ 17
[   12.176801] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[   12.176806] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[   12.176811] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[   12.176816] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[   12.176820] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[   12.180106] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0c.0
[   12.204392] usbcore: registered new interface driver usbfs
[   12.204422] usbcore: registered new interface driver hub
[   12.215611] usbcore: registered new device driver usb
[   12.227587] USB Universal Host Controller Interface driver v3.0
[   12.227751] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug
[   12.227797] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
[   12.227800] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
[   12.227808] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 18
[   12.227818] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   12.228067] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   12.228099] uhci_hcd 0000:00:10.0: irq 18, io base 0x00001c80
[   12.228224] usb usb1: configuration #1 chosen from 1 choice
[   12.228248] hub 1-0:1.0: USB hub found
[   12.228252] hub 1-0:1.0: 2 ports detected
[   12.271232] SCSI subsystem initialized
[   12.319408] libata version 3.00 loaded.
[   12.331500] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 18
[   12.331513] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   12.331544] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   12.331566] uhci_hcd 0000:00:10.1: irq 18, io base 0x00001ca0
[   12.331666] usb usb2: configuration #1 chosen from 1 choice
[   12.331687] hub 2-0:1.0: USB hub found
[   12.331692] hub 2-0:1.0: 2 ports detected
[   12.331733] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   12.435324] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 18
[   12.435337] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   12.435358] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   12.435380] uhci_hcd 0000:00:10.2: irq 18, io base 0x00001cc0
[   12.435479] usb usb3: configuration #1 chosen from 1 choice
[   12.435499] hub 3-0:1.0: USB hub found
[   12.435504] hub 3-0:1.0: 2 ports detected
[   12.539239] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 18
[   12.539255] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   12.539278] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   12.539317] ehci_hcd 0000:00:10.3: irq 18, io mem 0xd0002800
[   12.551016] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.551114] usb usb4: configuration #1 chosen from 1 choice
[   12.551134] hub 4-0:1.0: USB hub found
[   12.551141] hub 4-0:1.0: 6 ports detected
[   12.655598] ACPI: PCI Interrupt Link [ALKB] disabled and referenced, BIOS bug
[   12.655645] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 23
[   12.655647] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[   12.655656] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKB] -> GSI 23 (level, low) -> IRQ 19
[   12.659768] eth0: VIA Rhine II at 0xd0002c00, 00:03:25:13:26:68, IRQ 19.
[   12.660475] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   12.660777] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[   12.660811] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 22
[   12.660813] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 22
[   12.660817] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 22 (level, low) -> IRQ 20
[   12.660871] ACPI: PCI interrupt for device 0000:00:11.1 disabled
[   12.662989] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 21
[   12.715627] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[d0002000-d00027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.728945] pata_via 0000:00:11.1: version 0.3.3
[   12.728968] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 22 (level, low) -> IRQ 20
[   12.729802] scsi0 : pata_via
[   12.730314] scsi1 : pata_via
[   12.730817] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1ce0 irq 14
[   12.730819] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1ce8 irq 15
[   12.894882] ata1.00: ATA-5: HITACHI_DK23FA-60, 00M4A0A0, max UDMA/100
[   12.894887] ata1.00: 117210240 sectors, multi 16: LBA 
[   12.902765] ata1.00: configured for UDMA/100
[   13.134061] hub 4-0:1.0: over-current change on port 1
[   13.222231] ata2.00: ATAPI: Slimtype COMBO LSC-24082K, JK0N, max UDMA/33
[   13.237881] hub 4-0:1.0: over-current change on port 2
[   13.393822] ata2.00: configured for UDMA/33
[   13.393926] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23FA-6 00M4 PQ: 0 ANSI: 5
[   13.394699] scsi 1:0:0:0: CD-ROM            Slimtype COMBO LSC-24082K JK0N PQ: 0 ANSI: 5
[   13.402031] Driver 'sd' needs updating - please use bus_type methods
[   13.402118] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.402129] sd 0:0:0:0: [sda] Write Protect is off
[   13.402132] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.402146] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.402185] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.402192] sd 0:0:0:0: [sda] Write Protect is off
[   13.402194] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.402205] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.402208]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   13.438126]  sda1 sda2 < sda5 >
[   13.466214] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.471810] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.471829] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.474544] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[   13.474549] Uniform CD-ROM driver Revision: 3.20
[   13.474589] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   13.764001] Attempting manual resume
[   13.764006] swsusp: Resume From Partition 8:5
[   13.764007] PM: Checking swsusp image.
[   13.764164] PM: Resume from disk failed.
[   13.808869] kjournald starting.  Commit interval 5 seconds
[   13.808881] EXT3-fs: mounted filesystem with ordered data mode.
[   13.884803] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   13.992725] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000325212900abce]
[   14.059535] usb 2-2: configuration #1 chosen from 1 choice
[   14.065482] hub 2-2:1.0: USB hub found
[   14.066459] hub 2-2:1.0: 3 ports detected
[   14.377897] usb 2-2.1: new full speed USB device using uhci_hcd and address 3
[   14.512726] usb 2-2.1: configuration #1 chosen from 1 choice
[   14.725270] usb 2-2.2: new low speed USB device using uhci_hcd and address 4
[   14.870088] usb 2-2.2: configuration #1 chosen from 1 choice
[   25.832958] Yenta: CardBus bridge found at 0000:00:0a.0 [161f:2032]
[   25.832977] Yenta: Using CSCINT to route CSC interrupts to PCI
[   25.832979] Yenta: Routing CardBus interrupts to PCI
[   25.832982] Yenta TI: socket 0000:00:0a.0, mfunc 0x01001002, devctl 0x44
[   25.980749] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.020609] Linux agpgart interface v0.102
[   26.065315] Yenta: ISA IRQ mask 0x0808, PCI irq 16
[   26.065319] Socket status: 30000006
[   26.085693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.120498] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.213107] irda_init()
[   26.213128] NET: Registered protocol family 23
[   26.370628] input: Power Button (FF) as /devices/virtual/input/input3
[   26.379993] ACPI: Power Button (FF) [PWRF]
[   26.380068] input: Power Button (CM) as /devices/virtual/input/input4
[   26.395953] ACPI: Power Button (CM) [PWRB]
[   26.396033] input: Sleep Button (CM) as /devices/virtual/input/input5
[   26.411922] ACPI: Sleep Button (CM) [SLPB]
[   26.411964] input: Lid Switch as /devices/virtual/input/input6
[   26.412322] ACPI: Lid Switch [LID]
[   26.438658] agpgart: Detected AGP bridge 0
[   26.455305] agpgart: AGP aperture is 256M @ 0xe0000000
[   26.780850] ACPI: AC Adapter [AC] (on-line)
[   26.880587] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   26.916314] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   27.102240] ACPI: Battery Slot [BAT0] (battery present)
[   27.415180] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/LNXVIDEO:00/input/input8
[   27.442251] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   27.760670] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   27.852650] [fglrx] Maximum main memory to use for locked dma buffers: 1171 MBytes.
[   27.852683] [fglrx] ASYNCIO init succeed!
[   27.852916] [fglrx] PAT is enabled successfully!
[   27.876098] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   27.903249] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[   27.903294] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   27.903296] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   27.903300] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   27.920045] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   28.041428] usbcore: registered new interface driver hiddev
[   28.045355] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.1/2-2.1:1.0/input/input9
[   28.055747] b43-phy0: Broadcom 4306 WLAN found
[   28.061251] input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:10.1-2.1
[   28.067236] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.1/2-2.1:1.1/input/input10
[   28.077162] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2
[   28.077183] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   28.081216] input,hidraw1: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:10.1-2.1
[   28.096272] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.2/2-2.2:1.0/input/input11
[   28.102537] phy0: Selected rate control algorithm 'simple'
[   28.117113] input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2.2
[   28.117132] usbcore: registered new interface driver usbhid
[   28.117136] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.524500] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 1 converters and GPIO not ready (0xff00)
[   28.525400] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   28.525529] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   28.989028] cs: IO port probe 0x100-0x3af: clean.
[   28.990939] cs: IO port probe 0x3e0-0x4ff: clean.
[   28.991752] cs: IO port probe 0x820-0x8ff: clean.
[   28.992420] cs: IO port probe 0xc00-0xcf7: clean.
[   28.993230] cs: IO port probe 0xa00-0xaff: clean.
[   30.368121] lp: driver loaded but no devices found
[   30.439882] ieee80211_crypt: registered algorithm 'NULL'
[   30.550659] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k
[   31.092266] EXT3 FS on sda1, internal journal
[   32.353029] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.863958] No dock devices found.
[   33.170133] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[   33.170171] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6
[   33.170173] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xe
[   33.170175] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x18
[   33.975984] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.975990] apm: overridden by ACPI.
[   34.330024] ppdev: user-space parallel port driver
[   34.488787] audit(1257080897.302:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4963 profile="/usr/sbin/cupsd" namespace="default"
[   35.409157] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   35.456149] input: b43-phy0 as /devices/virtual/input/input12
[   35.536136] Bluetooth: Core ver 2.11
[   35.539098] NET: Registered protocol family 31
[   35.539102] Bluetooth: HCI device and connection manager initialized
[   35.539107] Bluetooth: HCI socket layer initialized
[   35.564912] Bluetooth: L2CAP ver 2.9
[   35.564918] Bluetooth: L2CAP socket layer initialized
[   35.654599] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   35.654607] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   35.686296] Bluetooth: RFCOMM socket layer initialized
[   35.686312] Bluetooth: RFCOMM TTY layer initialized
[   35.686313] Bluetooth: RFCOMM ver 1.8
[   93.061767] Marking TSC unstable due to: cpufreq changes.
[   93.070745] Time: acpi_pm clocksource has been installed.
[   93.334810] Clocksource tsc unstable (delta = -163967774 ns)
[   94.145526] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 22
[   94.204036] input: b43-phy0 as /devices/virtual/input/input13
[   94.250143] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   94.250156] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   39.837772] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   39.837779] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   39.837784] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
[   39.838639] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   39.838889] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   39.839172] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   39.839413] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[   39.843245] [fglrx] GART Table is not in FRAME_BUFFER range 
[   39.843252] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   39.843255] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   39.977036] [fglrx] interrupt source 20008000 successfully enabled
[   39.977044] [fglrx] enable ID = 0x00000004
[   39.977532] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   39.977814] [fglrx] interrupt source 10000000 successfully enabled
[   39.977817] [fglrx] enable ID = 0x00000005
[   39.978125] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   40.338588] NET: Registered protocol family 17
[  105.510821] NET: Registered protocol family 10
[  105.511846] lo: Disabled Privacy Extensions
[  115.954831] eth0: no IPv6 routers present
[  116.285683] input: b43-phy0 as /devices/virtual/input/input14
[  116.326507] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  116.326520] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   56.398300] input: b43-phy0 as /devices/virtual/input/input15
[   56.440041] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   56.440048] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  168.510305] input: b43-phy0 as /devices/virtual/input/input16
[  168.552324] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  168.552337] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  174.528929] ACPI: EC: missing write data confirmation, don't expect it any longer.
[  195.588844] input: b43-phy0 as /devices/virtual/input/input17
[  195.632287] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  195.632300] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  203.331498] b43-phy1: Broadcom 4306 WLAN found
[  203.352850] b43-phy1 debug: Found PHY: Analog 2, Type 2, Revision 2
[  203.352879] b43-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[  203.383669] phy1: Selected rate control algorithm 'simple'
[  203.389302] BUG: unable to handle kernel NULL pointer dereference at virtual address 0000000d
[  203.389313] printing eip: c031c5db *pde = 00000000 
[  203.389322] Oops: 0002 [#1] SMP 
[  203.389328] Modules linked in: ipv6 af_packet binfmt_misc rfcomm l2cap bluetooth rfkill_input ppdev powernow_k8 cpufreq_userspace cpufreq_conservative cpufreq_ondemand cpufreq_stats freq_table cpufreq_powersave container sbs sbshc dock iptable_filter ip_tables x_tables wl(P) ieee80211_crypt sbp2 parport_pc lp parport joydev pcmcia arc4 ecb blkcipher b43 snd_via82xx usbhid rfkill hid gameport mac80211 snd_via82xx_modem snd_ac97_codec fglrx(P) ac97_bus snd_mpu401_uart cfg80211 snd_pcm_oss snd_mixer_oss snd_pcm led_class video output input_polldev snd_seq_dummy snd_seq_oss snd_seq_midi battery snd_rawmidi snd_seq_midi_event i2c_viapro i2c_core serio_raw ac snd_seq snd_timer snd_seq_device via_ircc evdev amd64_agp button snd psmouse irda k8temp shpchp pci_hotplug agpgart pcspkr soundcore crc_ccitt yenta_socket rsrc_nonstatic pcmcia_core snd_page_alloc ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_via ata_generic ohci1394 pata_acpi ieee1394 via_rhine mii libata scsi_mod ehci_hcd uhci_hcd usbcore ssb thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  203.389443] 
[  203.389449] Pid: 5196, comm: ipolldevd Tainted: P        (2.6.24-25-generic #1)
[  203.389456] EIP: 0060:[<c031c5db>] EFLAGS: 00010246 CPU: 0
[  203.389468] EIP is at mutex_lock+0xb/0x20
[  203.389473] EAX: 0000000d EBX: 0000000d ECX: f44850d8 EDX: f7632000
[  203.389479] ESI: 0000000d EDI: f44850c0 EBP: 00000001 ESP: f7633f54
[  203.389484]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  203.389490] Process ipolldevd (pid: 5196, ti=f7632000 task=f772b700 task.ti=f7632000)
[  203.389495] Stack: dfa83800 f8b87d94 c031bc1a df9c5374 000000fa f44850c0 f44850d4 dfa16080 
[  203.389507]        f8ad00d0 f8ad00e4 f44850d4 dfa16080 c013ceff 00000000 000000ff 00000000 
[  203.389518]        00000000 dfa16084 dfa1608c dfa16080 c013d9a0 dfa16084 c013da24 00000000 
[  203.389529] Call Trace:
[  203.389540]  [<f8b87d94>] b43_rfkill_poll+0x24/0xf0 [b43]
[  203.389573]  [<c031bc1a>] schedule+0x20a/0x600
[  203.389606]  [<f8ad00d0>] input_polled_device_work+0x0/0x40 [input_polldev]
[  203.389620]  [<f8ad00e4>] input_polled_device_work+0x14/0x40 [input_polldev]
[  203.389640]  [<c013ceff>] run_workqueue+0xbf/0x160
[  203.389682]  [<c013d9a0>] worker_thread+0x0/0xe0
[  203.389695]  [<c013da24>] worker_thread+0x84/0xe0
[  203.389713]  [<c0140cb0>] autoremove_wake_function+0x0/0x40
[  203.389740]  [<c013d9a0>] worker_thread+0x0/0xe0
[  203.389753]  [<c01409f2>] kthread+0x42/0x70
[  203.389760]  [<c01409b0>] kthread+0x0/0x70
[  203.389775]  [<c0105667>] kernel_thread_helper+0x7/0x10
[  203.389812]  =======================
[  203.389815] Code: 53 89 c3 e8 a8 fa ff ff b8 ff ff ff ff 90 0f c1 03 83 e8 01 78 04 5b 31 c0 c3 89 d8 5b eb 21 90 53 89 c3 e8 88 fa ff ff 89 d8 90 <ff> 08 79 05 e8 fc 00 00 00 5b c3 8d 76 00 8d bc 27 00 00 00 00 
[  203.389862] EIP: [<c031c5db>] mutex_lock+0xb/0x20 SS:ESP 0068:f7633f54
[  203.389879] ---[ end trace 2b075207c47a1dda ]---
[  207.472936] input: b43-phy1 as /devices/virtual/input/input18
[  207.538926] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  207.538937] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  212.075573] input: b43-phy1 as /devices/virtual/input/input19
[  212.117987] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  212.117998] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  119.251352] input: b43-phy1 as /devices/virtual/input/input20
[  119.300746] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  119.300753] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  269.812226] input: b43-phy1 as /devices/virtual/input/input21
[  269.854413] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  269.854424] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).

---

### Post by pytheas22 on 2009-11-01
Torgas Prim: please try running these commands; these will grab the firmware for you and install it in the correct location manually:
```

wget http://burnthesorbonne.com/files/b43_firmware.tar.gz
tar -xzvf b43_firmware.tar.gz 
rm b43_firmware.tar.gz 
sudo mv b43* /lib/firmware
```

After that, reboot and you should be good to go.  If it still doesn't work, please let me know the output of:
```

dmesg | grep -e b43 -ie firmware
ls /lib/firmware
lspci -nn
```

---

### Post by Torgas Prim on 2009-11-02
Bah, it worked...I hate you...lol
;)

Thanks a bunch!

---

### Post by jcolsen on 2009-11-02
I've tried your solution and this is my dmesg output:
[    0.229626] pci 0000:00:1f.2: reg 10 io port: [0x1f0-0x1f7]
[    0.229635] pci 0000:00:1f.2: reg 14 io port: [0x3f4-0x3f7]
[    0.229643] pci 0000:00:1f.2: reg 18 io port: [0x170-0x177]
[    0.229652] pci 0000:00:1f.2: reg 1c io port: [0x374-0x377]
[    0.229661] pci 0000:00:1f.2: reg 20 io port: [0xbfa0-0xbfaf]
[    0.229697] pci 0000:00:1f.2: PME# supported from D3hot
[    0.229702] pci 0000:00:1f.2: PME# disabled
[    0.229763] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.229961] pci 0000:0b:00.0: reg 10 32bit mmio: [0xdfdfc000-0xdfdfffff]
[    0.230235] pci 0000:0b:00.0: supports D1 D2
[    0.230362] pci 0000:00:1c.0: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]
[    0.230428] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.230434] pci 0000:00:1c.3: bridge 32bit mmio: [0xdfa00000-0xdfcfffff]
[    0.230443] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xd0000000-0xd01fffff]
[    0.230493] pci 0000:03:00.0: reg 10 32bit mmio: [0xdf9fe000-0xdf9fffff]
[    0.230559] pci 0000:03:00.0: supports D1 D2
[    0.230562] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.230568] pci 0000:03:00.0: PME# disabled
[    0.230616] pci 0000:03:01.0: reg 10 32bit mmio: [0xdf9fd800-0xdf9fdfff]
[    0.230684] pci 0000:03:01.0: supports D1 D2
[    0.230687] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.230694] pci 0000:03:01.0: PME# disabled
[    0.230742] pci 0000:03:01.1: reg 10 32bit mmio: [0xdf9fd500-0xdf9fd5ff]
[    0.230809] pci 0000:03:01.1: supports D1 D2
[    0.230811] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.230818] pci 0000:03:01.1: PME# disabled
[    0.230866] pci 0000:03:01.2: reg 10 32bit mmio: [0xdf9fd600-0xdf9fd6ff]
[    0.230931] pci 0000:03:01.2: supports D1 D2
[    0.230934] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.230940] pci 0000:03:01.2: PME# disabled
[    0.230987] pci 0000:03:01.3: reg 10 32bit mmio: [0xdf9fd700-0xdf9fd7ff]
[    0.231055] pci 0000:03:01.3: supports D1 D2
[    0.231058] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.231064] pci 0000:03:01.3: PME# disabled
[    0.231137] pci 0000:00:1e.0: transparent bridge
[    0.231145] pci 0000:00:1e.0: bridge 32bit mmio: [0xdf900000-0xdf9fffff]
[    0.231172] pci_bus 0000:00: on NUMA node 0
[    0.231178] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.231515] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.231614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.231709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.241906] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.242046] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
[    0.242184] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.242321] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.242458] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.242601] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.242746] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.242888] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.243117] SCSI subsystem initialized
[    0.243142] libata version 3.00 loaded.
[    0.243142] usbcore: registered new interface driver usbfs
[    0.243142] usbcore: registered new interface driver hub
[    0.243142] usbcore: registered new device driver usb
[    0.243142] ACPI: WMI: Mapper loaded
[    0.243142] PCI: Using ACPI for IRQ routing
[    0.252010] Bluetooth: Core ver 2.15
[    0.252027] NET: Registered protocol family 31
[    0.252027] Bluetooth: HCI device and connection manager initialized
[    0.252027] Bluetooth: HCI socket layer initialized
[    0.252027] NetLabel: Initializing
[    0.252027] NetLabel:  domain hash size = 128
[    0.252029] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.252046] NetLabel:  unlabeled traffic allowed by default
[    0.252219] hpet clockevent registered
[    0.252223] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.252231] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.252237] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.260017] Switched to high resolution mode on CPU 0
[    0.260599] Switched to high resolution mode on CPU 1
[    0.268019] pnp: PnP ACPI init
[    0.268034] ACPI: bus type pnp registered
[    0.301415] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.301420] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.301515] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.301520] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.301525] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.301529] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.302568] pnp: PnP ACPI: found 11 devices
[    0.302571] ACPI: ACPI bus type pnp unregistered
[    0.302575] PnPBIOS: Disabled by ACPI PNP
[    0.302587] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.302592] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.302596] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.302600] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.302605] system 00:00: iomem range 0x100000-0x5f6d33ff could not be reserved
[    0.302609] system 00:00: iomem range 0x5f6d3400-0x5f6fffff has been reserved
[    0.302613] system 00:00: iomem range 0x5f700000-0x5f7fffff has been reserved
[    0.302617] system 00:00: iomem range 0x5f700000-0x5fefffff could not be reserved
[    0.302621] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.302626] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.302630] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.302634] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.302638] system 00:00: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.302642] system 00:00: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.302646] system 00:00: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.302650] system 00:00: iomem range 0xf0006000-0xf0006fff has been reserved
[    0.302654] system 00:00: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.302659] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.302667] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.302675] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.302679] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.302683] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.302687] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.302697] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.302700] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.302704] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.302708] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.302712] system 00:08: ioport range 0x940-0x97f has been reserved
[    0.337419] AppArmor: AppArmor Filesystem Enabled
[    0.337472] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.337475] pci 0000:00:1c.0:   IO window: disabled
[    0.337482] pci 0000:00:1c.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.337488] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.337494] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0c
[    0.337498] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.337505] pci 0000:00:1c.3:   MEM window: 0xdfa00000-0xdfcfffff
[    0.337511] pci 0000:00:1c.3:   PREFETCH window: 0x000000d0000000-0x000000d01fffff
[    0.337521] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.337524] pci 0000:00:1e.0:   IO window: disabled
[    0.337531] pci 0000:00:1e.0:   MEM window: 0xdf900000-0xdf9fffff
[    0.337536] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.337554]   alloc irq_desc for 16 on node -1
[    0.337557]   alloc kstat_irqs on node -1
[    0.337564] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.337571] pci 0000:00:1c.0: setting latency timer to 64
[    0.337580]   alloc irq_desc for 19 on node -1
[    0.337583]   alloc kstat_irqs on node -1
[    0.337587] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.337593] pci 0000:00:1c.3: setting latency timer to 64
[    0.337602] pci 0000:00:1e.0: setting latency timer to 64
[    0.337608] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.337612] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.337616] pci_bus 0000:0b: resource 1 mem: [0xdfd00000-0xdfdfffff]
[    0.337619] pci_bus 0000:0c: resource 0 io:  [0xd000-0xdfff]
[    0.337623] pci_bus 0000:0c: resource 1 mem: [0xdfa00000-0xdfcfffff]
[    0.337627] pci_bus 0000:0c: resource 2 pref mem [0xd0000000-0xd01fffff]
[    0.337630] pci_bus 0000:03: resource 1 mem: [0xdf900000-0xdf9fffff]
[    0.337634] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.337637] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.337678] NET: Registered protocol family 2
[    0.337792] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.338168] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.338952] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.339344] TCP: Hash tables configured (established 131072 bind 65536)
[    0.339348] TCP reno registered
[    0.339457] NET: Registered protocol family 1
[    0.339538] Trying to unpack rootfs image as initramfs...
[    0.584298] Freeing initrd memory: 7464k freed
[    0.589108] Simple Boot Flag value 0x3 read from CMOS RAM was invalid
[    0.589113] Simple Boot Flag at 0x79 set to 0x1
[    0.589345] cpufreq-nforce2: No nForce2 chipset.
[    0.589386] Scanning for low memory corruption every 60 seconds
[    0.589523] audit: initializing netlink socket (disabled)
[    0.589543] type=2000 audit(1257211337.588:1): initialized
[    0.600138] highmem bounce pool size: 64 pages
[    0.600145] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.602105] VFS: Disk quotas dquot_6.5.2
[    0.602190] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.602917] fuse init (API version 7.12)
[    0.603027] msgmni has been set to 1719
[    0.603320] alg: No test for stdrng (krng)
[    0.603337] io scheduler noop registered
[    0.603340] io scheduler anticipatory registered
[    0.603342] io scheduler deadline registered
[    0.603395] io scheduler cfq registered (default)
[    0.603410] pci 0000:00:02.0: Boot video device
[    0.603688]   alloc irq_desc for 24 on node -1
[    0.603691]   alloc kstat_irqs on node -1
[    0.603706] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.603719] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.603891]   alloc irq_desc for 25 on node -1
[    0.603893]   alloc kstat_irqs on node -1
[    0.603903] pcieport-driver 0000:00:1c.3: irq 25 for MSI/MSI-X
[    0.603915] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.604049] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.604143] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.604662] ACPI: AC Adapter [AC] (on-line)
[    0.604765] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.605141] ACPI: Lid Switch [LID]
[    0.605205] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.605213] ACPI: Power Button [PBTN]
[    0.605270] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.605273] ACPI: Sleep Button [SBTN]
[    0.606009] ACPI: SSDT 5f6d41f5 001AF (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.606390] ACPI: SSDT 5f6d4018 00158 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.606721] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.606753] processor LNXCPU:00: registered as cooling_device0
[    0.606758] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.607171] ACPI: SSDT 5f6d43a4 00090 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.607503] ACPI: SSDT 5f6d4170 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.607900] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.607930] processor LNXCPU:01: registered as cooling_device1
[    0.607935] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.612878] thermal LNXTHERM:01: registered as thermal_zone0
[    0.612888] ACPI: Thermal Zone [THM] (49 C)
[    0.612959] isapnp: Scanning for PnP cards...
[    0.651894] ACPI: Battery Slot [BAT0] (battery present)
[    0.969861] isapnp: No Plug & Play device found
[    0.971242] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.972879] brd: module loaded
[    0.973464] loop: module loaded
[    0.973555] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.973686] ata_piix 0000:00:1f.2: version 2.13
[    0.973705]   alloc irq_desc for 17 on node -1
[    0.973708]   alloc kstat_irqs on node -1
[    0.973716] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.973723] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.973771] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.973868] scsi0 : ata_piix
[    0.973970] scsi1 : ata_piix
[    0.974876] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.974880] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.976007] Fixed MDIO Bus: probed
[    0.976052] PPP generic driver version 2.4.2
[    0.976160] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.976182]   alloc irq_desc for 20 on node -1
[    0.976184]   alloc kstat_irqs on node -1
[    0.976190] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.976203] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.976208] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.976263] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.980178] ehci_hcd 0000:00:1d.7: debug port 1
[    0.980186] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.980203] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.996021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.996116] usb usb1: configuration #1 chosen from 1 choice
[    0.996155] hub 1-0:1.0: USB hub found
[    0.996164] hub 1-0:1.0: 8 ports detected
[    0.996246] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.996265] uhci_hcd: USB Universal Host Controller Interface driver
[    0.996294] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.996302] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.996306] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.996345] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.996374] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.996468] usb usb2: configuration #1 chosen from 1 choice
[    0.996501] hub 2-0:1.0: USB hub found
[    0.996510] hub 2-0:1.0: 2 ports detected
[    0.996567]   alloc irq_desc for 21 on node -1
[    0.996570]   alloc kstat_irqs on node -1
[    0.996576] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.996583] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.996587] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.996632] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.996670] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.996766] usb usb3: configuration #1 chosen from 1 choice
[    0.996798] hub 3-0:1.0: USB hub found
[    0.996806] hub 3-0:1.0: 2 ports detected
[    0.996868]   alloc irq_desc for 22 on node -1
[    0.996871]   alloc kstat_irqs on node -1
[    0.996876] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.996883] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.996887] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.996925] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.996962] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.997067] usb usb4: configuration #1 chosen from 1 choice
[    0.997100] hub 4-0:1.0: USB hub found
[    0.997108] hub 4-0:1.0: 2 ports detected
[    0.997166]   alloc irq_desc for 23 on node -1
[    0.997169]   alloc kstat_irqs on node -1
[    0.997174] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.997182] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.997186] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.997222] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.997260] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.997355] usb usb5: configuration #1 chosen from 1 choice
[    0.997388] hub 5-0:1.0: USB hub found
[    0.997396] hub 5-0:1.0: 2 ports detected
[    0.997514] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.000229] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.000237] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.000326] mice: PS/2 mouse device common for all mice
[    1.000464] rtc_cmos 00:06: RTC can wake from S4
[    1.000503] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.000537] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.000676] device-mapper: uevent: version 1.0.3
[    1.000774] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.000854] device-mapper: multipath: version 1.1.0 loaded
[    1.000857] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.000997] EISA: Probing bus 0 at eisa.0
[    1.001070] EISA: Mainboard RG_FFFF detected.
[    1.001089] Cannot allocate resource for EISA slot 1
[    1.001121] EISA: Detected 0 cards.
[    1.001358] cpuidle: using governor ladder
[    1.001524] cpuidle: using governor menu
[    1.002133] TCP cubic registered
[    1.002337] NET: Registered protocol family 10
[    1.002921] lo: Disabled Privacy Extensions
[    1.003349] NET: Registered protocol family 17
[    1.003366] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.003373] Bluetooth: L2CAP ver 2.13
[    1.003375] Bluetooth: L2CAP socket layer initialized
[    1.003381] Bluetooth: SCO (Voice Link) ver 0.6
[    1.003383] Bluetooth: SCO socket layer initialized
[    1.003415] Bluetooth: RFCOMM TTY layer initialized
[    1.003418] Bluetooth: RFCOMM socket layer initialized
[    1.003421] Bluetooth: RFCOMM ver 1.11
[    1.003826] Using IPI No-Shortcut mode
[    1.003898] PM: Resume from disk failed.
[    1.003915] registered taskstats version 1
[    1.004059]   Magic number: 1:181:356
[    1.004064] input event2: hash matches
[    1.004166] rtc_cmos 00:06: setting system clock to 2009-11-03 01:22:18 UTC (1257211338)
[    1.004170] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.004173] EDD information not available.
[    1.136940] ata1.00: failed to set max address (err_mask=0x1)
[    1.136944] ata1.00: device aborted resize (75200265 -> 78140160), skipping HPA handling
[    1.136951] ata1.00: ATA-7: FUJITSU MHV2040BH, 00850028, max UDMA/100
[    1.136955] ata1.00: 75200265 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.144622] ata2.00: ATAPI: TSSTcorp CDDVDW SN-S082H, SB01, max UDMA/33
[    1.152579] ata1.00: configured for UDMA/100
[    1.152718] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2040B 0085 PQ: 0 ANSI: 5
[    1.152859] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.152907] sd 0:0:0:0: [sda] 75200265 512-byte logical blocks: (38.5 GB/35.8 GiB)
[    1.152967] sd 0:0:0:0: [sda] Write Protect is off
[    1.152971] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.153003] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.153158]  sda:
[    1.176341] ata2.00: configured for UDMA/33
[    1.185324] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-S082H  SB01 PQ: 0 ANSI: 5
[    1.190313]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.201800] Uniform CD-ROM driver Revision: 3.20
[    1.201895] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.201946] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.223344]  sda5 >
[    1.223647] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.223674] Freeing unused kernel memory: 540k freed
[    1.224074] Write protecting the kernel text: 4568k
[    1.224141] Write protecting the kernel read-only data: 1836k
[    1.253016] Clocksource tsc unstable (delta = 1650601279 ns)
[    1.363678] Linux agpgart interface v0.103
[    1.380753] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    1.381512] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.384521] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.387607] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:26/input/input5
[    1.387644] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    1.387695] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    1.387779] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/input/input6
[    1.387809] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    1.471101] [drm] Initialized drm 1.1.0 20060810
[    1.488078] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.488086] i915 0000:00:02.0: setting latency timer to 64
[    1.548978] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.607057] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[df9fd800-df9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.991746] [drm] TV-14: set mode NTSC 480i 0
[    2.117487] [drm] fb0: inteldrmfb frame buffer device
[    2.117500] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.185441] [drm] LVDS-8: set mode 1280x800 17
[    2.411551] Console: switching to colour frame buffer device 160x50
[    2.621865] PM: Starting manual resume from disk
[    2.621871] PM: Resume from partition 8:5
[    2.621873] PM: Checking hibernation image.
[    2.622097] PM: Resume from disk failed.
[    2.694538] kjournald starting.  Commit interval 5 seconds
[    2.694561] EXT3-fs: mounted filesystem with writeback data mode.
[    2.880491] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc00005030941]
[    4.335329] type=1505 audit(1257211341.827:2): operation="profile_load" pid=404 name=/usr/share/gdm/guest-session/Xsession
[    4.352914] type=1505 audit(1257211341.847:3): operation="profile_load" pid=405 name=/sbin/dhclient3
[    4.353700] type=1505 audit(1257211341.847:4): operation="profile_load" pid=405 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.354130] type=1505 audit(1257211341.847:5): operation="profile_load" pid=405 name=/usr/lib/connman/scripts/dhclient-script
[    4.402611] type=1505 audit(1257211341.897:6): operation="profile_load" pid=406 name=/usr/bin/evince
[    4.414794] type=1505 audit(1257211341.907:7): operation="profile_load" pid=406 name=/usr/bin/evince-previewer
[    4.421982] type=1505 audit(1257211341.915:8): operation="profile_load" pid=406 name=/usr/bin/evince-thumbnailer
[    4.465007] type=1505 audit(1257211341.959:9): operation="profile_load" pid=408 name=/usr/lib/cups/backend/cups-pdf
[    4.465930] type=1505 audit(1257211341.959:10): operation="profile_load" pid=408 name=/usr/sbin/cupsd
[    6.272206] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k 
[    7.168603] EXT3 FS on sda1, internal journal
[   13.784510] __ratelimit: 3 callbacks suppressed
[   13.784515] type=1505 audit(1257211351.279:12): operation="profile_replace" pid=576 name=/usr/share/gdm/guest-session/Xsession
[   13.786453] type=1505 audit(1257211351.279:13): operation="profile_replace" pid=577 name=/sbin/dhclient3
[   13.787238] type=1505 audit(1257211351.279:14): operation="profile_replace" pid=577 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   13.787669] type=1505 audit(1257211351.279:15): operation="profile_replace" pid=577 name=/usr/lib/connman/scripts/dhclient-script
[   13.792131] type=1505 audit(1257211351.287:16): operation="profile_replace" pid=578 name=/usr/bin/evince
[   13.806085] type=1505 audit(1257211351.299:17): operation="profile_replace" pid=578 name=/usr/bin/evince-previewer
[   13.813827] type=1505 audit(1257211351.307:18): operation="profile_replace" pid=578 name=/usr/bin/evince-thumbnailer
[   13.823954] type=1505 audit(1257211351.315:19): operation="profile_replace" pid=580 name=/usr/lib/cups/backend/cups-pdf
[   13.824879] type=1505 audit(1257211351.319:20): operation="profile_replace" pid=580 name=/usr/sbin/cupsd
[   13.827636] type=1505 audit(1257211351.319:21): operation="profile_replace" pid=581 name=/usr/sbin/tcpdump
[   22.496912] udev: starting version 147
[   23.691529] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   24.241979] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   24.277974] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   24.371365] dell-wmi: No known WMI GUID found
[   24.405799] intel_rng: FWH not detected
[   24.764057] lp: driver loaded but no devices found
[   24.821527] lib80211: common routines for IEEE802.11 drivers
[   24.821531] lib80211_crypt: registered algorithm 'NULL'
[   24.910586] sdhci: Secure Digital Host Controller Interface driver
[   24.910590] sdhci: Copyright(c) Pierre Ossman
[   24.917708] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[   24.917730]   alloc irq_desc for 18 on node -1
[   24.917733]   alloc kstat_irqs on node -1
[   24.917742] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   24.919807] Registered led device: mmc0::
[   24.920854] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   25.107716] wl: module license 'MIXED/Proprietary' taints kernel.
[   25.107723] Disabling lock debugging due to kernel taint
[   25.110785] wl 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.110803] wl 0000:0b:00.0: setting latency timer to 64
[   25.555206] lib80211_crypt: registered algorithm 'TKIP'
[   25.555524] eth0: Broadcom BCM4311 802.11 Wireless Controller 5.10.91.9
[   25.774403] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.832100] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   25.832130] b44.c:v2.0
[   25.853034] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:1a:53:24
[   25.951251] udev: renamed network interface eth0 to eth1
[   26.138389] udev: renamed network interface eth1_rename to eth0
[   26.279116] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.286905] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   26.286939] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.465581] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   26.465680] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   29.754931] ip_tables: (C) 2000-2006 Netfilter Core Team
[   29.816203] b44: eth0: Link is up at 100 Mbps, full duplex.
[   29.816207] b44: eth0: Flow control is off for TX and off for RX.
[   29.816514] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.935773] ppdev: user-space parallel port driver
[   37.040048] eth1: no IPv6 routers present
[   40.224041] eth0: no IPv6 routers present
[   45.748511] device lo entered promiscuous mode
[   45.749463] device eth0 entered promiscuous mode
[   53.810417] [drm] TV-14: set mode NTSC 480i 0
[   53.953079] [drm] TV-14: set mode NTSC 480i 0
[   54.350127] [drm] TV-14: set mode NTSC 480i 0
[   54.490328] [drm] TV-14: set mode NTSC 480i 0
[   60.496138] [drm] TV-14: set mode NTSC 480i 0
[   60.636591] [drm] TV-14: set mode NTSC 480i 0
[   60.912539] [drm] TV-14: set mode NTSC 480i 0
[   61.053284] [drm] TV-14: set mode NTSC 480i 0
[   61.356470] [drm] TV-14: set mode NTSC 480i 0
[   61.496911] [drm] TV-14: set mode NTSC 480i 0
[  256.213695] [drm] TV-14: set mode NTSC 480i 0
[  256.355925] [drm] TV-14: set mode NTSC 480i 0
[  256.641662] [drm] TV-14: set mode NTSC 480i 0
[  256.783527] [drm] TV-14: set mode NTSC 480i 0
[  257.061245] [drm] TV-14: set mode NTSC 480i 0
[  257.201383] [drm] TV-14: set mode NTSC 480i 0
[  260.552509] [drm] TV-14: set mode NTSC 480i 0
[  260.693568] [drm] TV-14: set mode NTSC 480i 0
jon@HQ:~$


my wireless has been great in ibex and jaunty but with koala I'm not finding any wireless networks!

---

### Post by pytheas22 on 2009-11-02
jcolsen: please post the output of these commands:
```

sudo iwlist scan
lshw -C Network
```

Also, what are you using to try to connect?  NetworkManager or a different program?

---

### Post by jiapei100 on 2009-11-02
Hi, I'm using wicd rather than network-manager.

here is my
iwlist scan  and
lshw -C Network


```
jiapei@jiapei-laptop:/etc/init.d$ sudo iwlist scan                     
lo        Interface doesn't support scanning.                          

eth0      Interface doesn't support scanning.

wlan0     No scan results

jiapei@jiapei-laptop:/etc/init.d$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:7c:1b:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:aa100000-aa100fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:09:08.0
       logical name: eth0
       version: 02
       serial: 00:40:d0:a9:19:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.4 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:a4000000-a4000fff ioport:1200(size=64)

```


What's more:
my dmesg

```
jiapei@jiapei-laptop:/sys/bus/pci/devices$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu   
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)                                                                                  
[    0.000000] KERNEL supported cpus:                                                   
[    0.000000]   Intel GenuineIntel                                                     
[    0.000000]   AMD AuthenticAMD                                                       
[    0.000000]   NSC Geode by NSC                                                       
[    0.000000]   Cyrix CyrixInstead                                                     
[    0.000000]   Centaur CentaurHauls                                                   
[    0.000000]   Transmeta GenuineTMx86                                                 
[    0.000000]   Transmeta TransmetaCPU                                                 
[    0.000000]   UMC UMC UMC UMC                                                        
[    0.000000] BIOS-provided physical RAM map:                                          
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)                 
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)               
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)               
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fcf7000 (usable)                 
[    0.000000]  BIOS-e820: 000000007fcf7000 - 000000007fcff000 (reserved)               
[    0.000000]  BIOS-e820: 000000007fcff000 - 000000007fdbd000 (usable)                 
[    0.000000]  BIOS-e820: 000000007fdbd000 - 000000007fdbf000 (reserved)               
[    0.000000]  BIOS-e820: 000000007fdbf000 - 000000007fe8a000 (usable)                 
[    0.000000]  BIOS-e820: 000000007fe8a000 - 000000007febf000 (ACPI NVS)               
[    0.000000]  BIOS-e820: 000000007febf000 - 000000007ff00000 (ACPI data)              
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)               
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)               
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)               
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)               
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)               
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)               
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)               
[    0.000000] DMI 2.3 present.                                                         
[    0.000000] last_pfn = 0x7fe8a max_arch_pfn = 0x100000                               
[    0.000000] MTRR default type: uncachable                                            
[    0.000000] MTRR fixed ranges enabled:                                               
[    0.000000]   00000-9FFFF write-back                                                 
[    0.000000]   A0000-BFFFF uncachable                                                 
[    0.000000]   C0000-CFFFF write-protect                                              
[    0.000000]   D0000-EFFFF uncachable                                                 
[    0.000000]   F0000-FFFFF write-protect                                              
[    0.000000] MTRR variable ranges enabled:                                            
[    0.000000]   0 disabled                                                             
[    0.000000]   1 base 000000000 mask F80000000 write-back                             
[    0.000000]   2 base 07FF00000 mask FFFF00000 uncachable                             
[    0.000000]   3 disabled                                                             
[    0.000000]   4 disabled                                                             
[    0.000000]   5 disabled                                                             
[    0.000000]   6 disabled                                                             
[    0.000000]   7 disabled                                                             
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106         
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)                                                                                   
[    0.000000] Scanning 1 areas for low memory corruption                               
[    0.000000] modified physical RAM map:                                               
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)                  
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)                
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)                  
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)                
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)                
[    0.000000]  modified: 0000000000100000 - 000000007fcf7000 (usable)                  
[    0.000000]  modified: 000000007fcf7000 - 000000007fcff000 (reserved)                
[    0.000000]  modified: 000000007fcff000 - 000000007fdbd000 (usable)                  
[    0.000000]  modified: 000000007fdbd000 - 000000007fdbf000 (reserved)                
[    0.000000]  modified: 000000007fdbf000 - 000000007fe8a000 (usable)                  
[    0.000000]  modified: 000000007fe8a000 - 000000007febf000 (ACPI NVS)                
[    0.000000]  modified: 000000007febf000 - 000000007ff00000 (ACPI data)               
[    0.000000]  modified: 000000007ff00000 - 0000000080000000 (reserved)                
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)                
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)                
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)                
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)                
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)                
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)                
[    0.000000] initial memory mapped : 0 - 00c00000                                     
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000                   
[    0.000000] Using x86 segment limits to approximate NX protection                    
[    0.000000]  0000000000 - 0000400000 page 4k                                         
[    0.000000]  0000400000 - 0037400000 page 2M                                         
[    0.000000]  0037400000 - 00377fe000 page 4k                                         
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000                  
[    0.000000] RAMDISK: 378a4000 - 37fefc99                                             
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff8c99                               
[    0.000000] Move RAMDISK from 00000000378a4000 - 0000000037fefc98 to 008ad000 - 00ff8c98                                                                                     
[    0.000000] ACPI: RSDP 000fe020 00014 (v00 NEC   )                                   
[    0.000000] ACPI: RSDT 7fefe038 00034 (v01 NEC    H2O      00000001      01000013)   
[    0.000000] ACPI: FACP 7fefd000 00074 (v01 NEC    H2O      00000001 MSFT 01000013)   
[    0.000000] ACPI: DSDT 7fef8000 04CDB (v01 NEC    H2O      00000001 MSFT 01000013)   
[    0.000000] ACPI: FACS 7fe8a000 00040                                                
[    0.000000] ACPI: SSDT 7fef7000 00210 (v01 NEC    H2O      00000001 MSFT 01000013)   
[    0.000000] ACPI: APIC 7fef6000 00068 (v01 NEC    H2O      00000001 MSFT 01000013)   
[    0.000000] ACPI: MCFG 7fef4000 0003C (v01 NEC    H2O      00000001 MSFT 01000013)   
[    0.000000] ACPI: Local APIC address 0xfee00000                                      
[    0.000000] 1158MB HIGHMEM available.                                                
[    0.000000] 887MB LOWMEM available.                                                  
[    0.000000]   mapped low ram: 0 - 377fe000                                           
[    0.000000]   low ram: 0 - 377fe000                                                  
[    0.000000]   node 0 low ram: 00000000 - 377fe000                                    
[    0.000000]   node 0 bootmap 00008000 - 0000ef00                                     
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]             
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                                                    
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                                                                    
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                                                                    
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]                                                                                    
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]                                                                                    
[    0.000000]   #5 [00008a9000 - 00008ac25c]              BRK ==> [00008a9000 - 00008ac25c]                                                                                    
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]                                                                                    
[    0.000000]   #7 [00008ad000 - 0000ff8c99]      NEW RAMDISK ==> [00008ad000 - 0000ff8c99]                                                                                    
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]                                                                                    
[    0.000000] found SMP MP-table at [c00fe060] fe060                                   
[    0.000000] Zone PFN ranges:                                                         
[    0.000000]   DMA      0x00000000 -> 0x00001000                                      
[    0.000000]   Normal   0x00001000 -> 0x000377fe                                      
[    0.000000]   HighMem  0x000377fe -> 0x0007fe8a                                      
[    0.000000] Movable zone start PFN for each node                                     
[    0.000000] early_node_map[5] active PFN ranges                                      
[    0.000000]     0: 0x00000000 -> 0x00000002                                          
[    0.000000]     0: 0x00000006 -> 0x0000009f                                          
[    0.000000]     0: 0x00000100 -> 0x0007fcf7                                          
[    0.000000]     0: 0x0007fcff -> 0x0007fdbd                                          
[    0.000000]     0: 0x0007fdbf -> 0x0007fe8a                                          
[    0.000000] On node 0 totalpages: 523803                                             
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000       
[    0.000000]   DMA zone: 32 pages used for memmap                                     
[    0.000000]   DMA zone: 0 pages reserved                                             
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0                                     
[    0.000000]   Normal zone: 1744 pages used for memmap                                
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31                               
[    0.000000]   HighMem zone: 2318 pages used for memmap                               
[    0.000000]   HighMem zone: 294260 pages, LIFO batch:31                              
[    0.000000] Using APIC driver default                                                
[    0.000000] ACPI: PM-Timer IO Port: 0x408                                            
[    0.000000] ACPI: Local APIC address 0xfee00000                                      
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)                       
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)                       
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                      
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])                      
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])                  
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23           
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)              
[    0.000000] ACPI: IRQ0 used by override.                                             
[    0.000000] ACPI: IRQ2 used by override.                                             
[    0.000000] ACPI: IRQ9 used by override.                                             
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                            
[    0.000000] Using ACPI (MADT) for SMP configuration information                      
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs                                     
[    0.000000] nr_irqs_gsi: 24                                                          
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000        
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000        
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000        
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000        
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)   
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1                   
[    0.000000] PERCPU: Embedded 14 pages at c200a000, static data 35612 bytes           
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519709                                                                                      
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=5b598001-debf-4cfe-9bf1-4eb263148eed ro quiet splash                                   
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)                    
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)         
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)           
[    0.000000] Enabling fast FPU save and restore... done.                              
[    0.000000] Enabling unmasked SIMD FPU exception support... done.                    
[    0.000000] Initializing CPU#0                                                       
[    0.000000] allocated 10478280 bytes of page_cgroup                                  
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups                                                                                       
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fe8a)                      
[    0.000000] Memory: 2051452k/2095656k available (4565k kernel code, 42924k reserved, 2143k data, 540k init, 1186312k highmem)                                                
[    0.000000] virtual kernel memory layout:                                            
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)                        
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)                        
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)                        
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)                        
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)                        
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)                        
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)                        
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                                                      
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1  
[    0.000000] NR_IRQS:2304 nr_irqs:424                                                 
[    0.000000] Fast TSC calibration using PIT                                           
[    0.000000] Detected 1994.861 MHz processor.                                         
[    0.001076] Console: colour VGA+ 80x25                                               
[    0.001080] console [tty0] enabled                                                   
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.72 BogoMIPS (lpj=7979444)                                                        
[    0.004033] Security Framework initialized                                           
[    0.004054] AppArmor: AppArmor initialized                                           
[    0.004061] Mount-cache hash table entries: 512                                      
[    0.004200] Initializing cgroup subsys ns                                            
[    0.004205] Initializing cgroup subsys cpuacct                                       
[    0.004209] Initializing cgroup subsys memory                                        
[    0.004216] Initializing cgroup subsys freezer                                       
[    0.004218] Initializing cgroup subsys net_cls                                       
[    0.004234] CPU: L1 I cache: 32K, L1 D cache: 32K                                    
[    0.004237] CPU: L2 cache: 4096K                                                     
[    0.004240] CPU: Physical Processor ID: 0                                            
[    0.004241] CPU: Processor Core ID: 0                                                
[    0.004246] mce: CPU supports 6 MCE banks                                            
[    0.004255] CPU0: Thermal monitoring enabled (TM2)                                   
[    0.004259] using mwait in idle threads.                                             
[    0.004265] Performance Counters: Core2 events, Intel PMU driver.                    
[    0.004274] ... version:                 2                                           
[    0.004276] ... bit width:               40                                          
[    0.004278] ... generic counters:        2                                           
[    0.004279] ... value mask:              000000ffffffffff                            
[    0.004281] ... max period:              000000007fffffff                            
[    0.004283] ... fixed-purpose counters:  3                                           
[    0.004285] ... counter mask:            0000000700000003                            
[    0.004289] Checking 'hlt' instruction... OK.                                        
[    0.022710] ACPI: Core revision 20090521                                             
[    0.032431] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                     
[    0.074579] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06        
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000                                   
[    0.004000] Initializing CPU#1                                                       
[    0.004000] Calibrating delay using timer specific routine.. 3990.20 BogoMIPS (lpj=7980411)                                                                                  
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K                                    
[    0.004000] CPU: L2 cache: 4096K                                                     
[    0.004000] CPU: Physical Processor ID: 0                                            
[    0.004000] CPU: Processor Core ID: 1                                                
[    0.004000] mce: CPU supports 6 MCE banks                                            
[    0.004000] CPU1: Thermal monitoring enabled (TM2)                                   
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106         
[    0.161838] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06        
[    0.161853] checking TSC synchronization [CPU#0 -> CPU#1]: passed.                   
[    0.164024] Brought up 2 CPUs                                                        
[    0.164026] Total of 2 processors activated (7979.92 BogoMIPS).                      
[    0.164080] CPU0 attaching sched-domain:                                             
[    0.164083]  domain 0: span 0-1 level MC                                             
[    0.164086]   groups: 0 1                                                            
[    0.164091] CPU1 attaching sched-domain:                                             
[    0.164093]  domain 0: span 0-1 level MC                                             
[    0.164096]   groups: 1 0                                                            
[    0.164176] Booting paravirtualized kernel on bare hardware                          
[    0.164224] regulator: core version 0.5                                              
[    0.164224] Time:  4:39:18  Date: 11/03/09                                           
[    0.164224] NET: Registered protocol family 16                                       
[    0.164224] EISA bus registered                                                      
[    0.164234] ACPI: bus type pci registered                                            
[    0.164306] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255         
[    0.164309] PCI: MCFG area at e0000000 reserved in E820                              
[    0.164311] PCI: Using MMCONFIG for extended config space                            
[    0.164313] PCI: Using configuration type 1 for base access                          
[    0.165378] bio: create slab <bio-0> at 0                                            
[    0.168720] ACPI: EC: Look up EC in DSDT                                             
[    0.172038] ACPI: Interpreter enabled                                                
[    0.172049] ACPI: (supports S0 S1 S3 S4 S5)                                          
[    0.172075] ACPI: Using IOAPIC for interrupt routing                                 
[    0.172396] ACPI: EC: non-query interrupt received, switching to interrupt mode      
[    0.186606] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62            
[    0.186609] ACPI: EC: driver started in interrupt mode                               
[    0.186799] ACPI: No dock devices found.                                             
[    0.187408] ACPI Warning: \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 20090521 nspredef-328                                                  
[    0.187417] ACPI: PCI Root Bridge [PCI0] (0000:00)                                   
[    0.187533] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold                    
[    0.187537] pci 0000:00:01.0: PME# disabled                                          
[    0.187633] pci 0000:00:1b.0: reg 10 64bit mmio: [0xac300000-0xac303fff]             
[    0.187697] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold                    
[    0.187702] pci 0000:00:1b.0: PME# disabled                                          
[    0.187792] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold                    
[    0.187797] pci 0000:00:1c.0: PME# disabled                                          
[    0.187891] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold                    
[    0.187896] pci 0000:00:1c.1: PME# disabled                                          
[    0.187989] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold                    
[    0.187994] pci 0000:00:1c.2: PME# disabled                                          
[    0.188093] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold                    
[    0.188098] pci 0000:00:1c.3: PME# disabled                                          
[    0.188168] pci 0000:00:1d.0: reg 20 io port: [0x7080-0x709f]                        
[    0.188236] pci 0000:00:1d.1: reg 20 io port: [0x7060-0x707f]                        
[    0.188303] pci 0000:00:1d.2: reg 20 io port: [0x7040-0x705f]                        
[    0.188371] pci 0000:00:1d.3: reg 20 io port: [0x7020-0x703f]                        
[    0.188443] pci 0000:00:1d.7: reg 10 32bit mmio: [0xac304400-0xac3047ff]             
[    0.188510] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                    
[    0.188516] pci 0000:00:1d.7: PME# disabled                                          
[    0.188697] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000                       
[    0.188704] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO  
[    0.188709] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO           
[    0.188786] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]                            
[    0.188795] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]                            
[    0.188803] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]                            
[    0.188812] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]                            
[    0.188820] pci 0000:00:1f.2: reg 20 io port: [0x70a0-0x70af]                        
[    0.188857] pci 0000:00:1f.2: PME# supported from D3hot                              
[    0.188862] pci 0000:00:1f.2: PME# disabled                                          
[    0.188927] pci 0000:00:1f.3: reg 20 io port: [0x7000-0x701f]                        
[    0.188991] pci 0000:01:00.0: reg 10 32bit mmio: [0x90000000-0x9fffffff]             
[    0.188997] pci 0000:01:00.0: reg 14 io port: [0x6000-0x60ff]                        
[    0.189004] pci 0000:01:00.0: reg 18 32bit mmio: [0xac200000-0xac20ffff]             
[    0.189022] pci 0000:01:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]             
[    0.189042] pci 0000:01:00.0: supports D1 D2                                         
[    0.189105] pci 0000:00:01.0: bridge io port: [0x6000-0x6fff]                        
[    0.189109] pci 0000:00:01.0: bridge 32bit mmio: [0xac200000-0xac2fffff]             
[    0.189114] pci 0000:00:01.0: bridge 64bit mmio pref: [0x90000000-0x9fffffff]        
[    0.189178] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]                        
[    0.189183] pci 0000:00:1c.0: bridge 32bit mmio: [0xab200000-0xac1fffff]             
[    0.189192] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xa4100000-0xa50fffff]        
[    0.189340] pci 0000:03:00.0: reg 10 32bit mmio: [0xaa100000-0xaa100fff]             
[    0.189588] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold                    
[    0.189601] pci 0000:03:00.0: PME# disabled                                          
[    0.189719] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]                        
[    0.189725] pci 0000:00:1c.1: bridge 32bit mmio: [0xaa100000-0xab1fffff]             
[    0.189734] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xa5100000-0xa60fffff]        
[    0.189798] pci 0000:00:1c.2: bridge io port: [0x3000-0x3fff]                        
[    0.189803] pci 0000:00:1c.2: bridge 32bit mmio: [0xa9100000-0xaa0fffff]             
[    0.189812] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xa6100000-0xa70fffff]        
[    0.189876] pci 0000:00:1c.3: bridge io port: [0x2000-0x2fff]                        
[    0.189881] pci 0000:00:1c.3: bridge 32bit mmio: [0xa8100000-0xa90fffff]             
[    0.189890] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xa7100000-0xa80fffff]        
[    0.189937] pci 0000:09:02.0: reg 10 32bit mmio: [0xa4003000-0xa4003fff]             
[    0.189946] pci 0000:09:02.0: reg 14 32bit mmio: [0xa4004000-0xa40047ff]             
[    0.190000] pci 0000:09:02.0: supports D1 D2                                         
[    0.190002] pci 0000:09:02.0: PME# supported from D0 D1 D2 D3hot D3cold              
[    0.190007] pci 0000:09:02.0: PME# disabled                                          
[    0.190060] pci 0000:09:02.2: reg 10 32bit mmio: [0xa4004800-0xa40048ff]             
[    0.190133] pci 0000:09:02.2: supports D1 D2                                         
[    0.190135] pci 0000:09:02.2: PME# supported from D0 D1 D2 D3hot D3cold              
[    0.190141] pci 0000:09:02.2: PME# disabled                                          
[    0.190192] pci 0000:09:02.3: reg 10 32bit mmio: [0xa4001000-0xa4001fff]             
[    0.190265] pci 0000:09:02.3: supports D1 D2                                         
[    0.190267] pci 0000:09:02.3: PME# supported from D0 D1 D2 D3hot D3cold              
[    0.190273] pci 0000:09:02.3: PME# disabled                                          
[    0.190335] pci 0000:09:08.0: reg 10 32bit mmio: [0xa4000000-0xa4000fff]             
[    0.190344] pci 0000:09:08.0: reg 14 io port: [0x1200-0x123f]                        
[    0.190397] pci 0000:09:08.0: supports D1 D2                                         
[    0.190400] pci 0000:09:08.0: PME# supported from D0 D1 D2 D3hot D3cold              
[    0.190405] pci 0000:09:08.0: PME# disabled                                          
[    0.190457] pci 0000:00:1e.0: transparent bridge                                     
[    0.190462] pci 0000:00:1e.0: bridge io port: [0x1000-0x1fff]                        
[    0.190468] pci 0000:00:1e.0: bridge 32bit mmio: [0xa2000000-0xa40fffff]             
[    0.190476] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xa0000000-0xa1ffffff]        
[    0.190513] pci_bus 0000:00: on NUMA node 0                                          
[    0.190518] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                      
[    0.190716] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]                 
[    0.190773] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]                 
[    0.190879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]                 
[    0.190963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]                 
[    0.191047] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]                 
[    0.191130] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]                 
[    0.194163] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)               
[    0.194274] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)               
[    0.194384] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)               
[    0.194492] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)               
[    0.194600] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)               
[    0.194708] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.  
[    0.194816] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.  
[    0.194925] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)               
[    0.195108] SCSI subsystem initialized                                               
[    0.195127] libata version 3.00 loaded.                                              
[    0.195127] usbcore: registered new interface driver usbfs                           
[    0.195127] usbcore: registered new interface driver hub                             
[    0.195127] usbcore: registered new device driver usb                                
[    0.195127] ACPI: WMI: Mapper loaded                                                 
[    0.195127] PCI: Using ACPI for IRQ routing                                          
[    0.204014] Bluetooth: Core ver 2.15                                                 
[    0.204040] NET: Registered protocol family 31                                       
[    0.204040] Bluetooth: HCI device and connection manager initialized                 
[    0.204040] Bluetooth: HCI socket layer initialized                                  
[    0.204040] NetLabel: Initializing                                                   
[    0.204040] NetLabel:  domain hash size = 128                                        
[    0.204041] NetLabel:  protocols = UNLABELED CIPSOv4                                 
[    0.204063] NetLabel:  unlabeled traffic allowed by default                          
[    0.204242] hpet clockevent registered                                               
[    0.204245] HPET: 3 timers in total, 0 timers will be used for per-cpu timer         
[    0.204252] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                                  
[    0.204258] hpet0: 3 comparators, 64-bit 14.318180 MHz counter                       
[    0.220097] pnp: PnP ACPI init                                                       
[    0.220114] ACPI: bus type pnp registered                                            
[    0.223154] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1e.0 BAR 13 (0x1000-0x1fff), disabling                                                                   
[    0.223638] pnp: PnP ACPI: found 8 devices                                           
[    0.223641] ACPI: ACPI bus type pnp unregistered                                     
[    0.223645] PnPBIOS: Disabled by ACPI PNP                                            
[    0.223655] system 00:01: ioport range 0x600-0x60f has been reserved                 
[    0.223658] system 00:01: ioport range 0x610-0x610 has been reserved                 
[    0.223661] system 00:01: ioport range 0x800-0x80f has been reserved                 
[    0.223664] system 00:01: ioport range 0x400-0x47f has been reserved                 
[    0.223666] system 00:01: ioport range 0x500-0x53f has been reserved                 
[    0.223669] system 00:01: ioport range 0x378-0x37f has been reserved                 
[    0.223672] system 00:01: ioport range 0x778-0x77f has been reserved                 
[    0.223676] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved        
[    0.223679] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved        
[    0.223682] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved        
[    0.223685] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved        
[    0.223689] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved        
[    0.223692] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved    
[    0.223695] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved        
[    0.258370] AppArmor: AppArmor Filesystem Enabled                                    
[    0.258386] pci 0000:01:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]                                                                                   
[    0.258447] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01                      
[    0.258450] pci 0000:00:01.0:   IO window: 0x6000-0x6fff                             
[    0.258455] pci 0000:00:01.0:   MEM window: 0xac200000-0xac2fffff                    
[    0.258459] pci 0000:00:01.0:   PREFETCH window: 0x00000090000000-0x0000009fffffff   
[    0.258464] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02                      
[    0.258468] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff                             
[    0.258474] pci 0000:00:1c.0:   MEM window: 0xab200000-0xac1fffff                    
[    0.258480] pci 0000:00:1c.0:   PREFETCH window: 0x000000a4100000-0x000000a50fffff   
[    0.258488] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03                      
[    0.258492] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff                             
[    0.258498] pci 0000:00:1c.1:   MEM window: 0xaa100000-0xab1fffff                    
[    0.258503] pci 0000:00:1c.1:   PREFETCH window: 0x000000a5100000-0x000000a60fffff   
[    0.258512] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05                      
[    0.258515] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff                             
[    0.258522] pci 0000:00:1c.2:   MEM window: 0xa9100000-0xaa0fffff                    
[    0.258527] pci 0000:00:1c.2:   PREFETCH window: 0x000000a6100000-0x000000a70fffff   
[    0.258535] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:07                      
[    0.258539] pci 0000:00:1c.3:   IO window: 0x2000-0x2fff                             
[    0.258545] pci 0000:00:1c.3:   MEM window: 0xa8100000-0xa90fffff                    
[    0.258550] pci 0000:00:1c.3:   PREFETCH window: 0x000000a7100000-0x000000a80fffff   
[    0.258559] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09                      
[    0.258563] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff                             
[    0.258569] pci 0000:00:1e.0:   MEM window: 0xa2000000-0xa40fffff                    
[    0.258574] pci 0000:00:1e.0:   PREFETCH window: 0x000000a0000000-0x000000a1ffffff   
[    0.258588]   alloc irq_desc for 16 on node -1                                       
[    0.258590]   alloc kstat_irqs on node -1                                            
[    0.258596] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16             
[    0.258600] pci 0000:00:01.0: setting latency timer to 64                            
[    0.258609] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16             
[    0.258614] pci 0000:00:1c.0: setting latency timer to 64                            
[    0.258623]   alloc irq_desc for 17 on node -1                                       
[    0.258624]   alloc kstat_irqs on node -1                                            
[    0.258628] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17             
[    0.258633] pci 0000:00:1c.1: setting latency timer to 64                            
[    0.258642]   alloc irq_desc for 18 on node -1                                       
[    0.258643]   alloc kstat_irqs on node -1                                            
[    0.258647] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18             
[    0.258652] pci 0000:00:1c.2: setting latency timer to 64                            
[    0.258661]   alloc irq_desc for 19 on node -1                                       
[    0.258662]   alloc kstat_irqs on node -1                                            
[    0.258666] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19             
[    0.258671] pci 0000:00:1c.3: setting latency timer to 64                            
[    0.258680] pci 0000:00:1e.0: setting latency timer to 64                            
[    0.258684] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]                           
[    0.258687] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]                   
[    0.258689] pci_bus 0000:01: resource 0 io:  [0x6000-0x6fff]                         
[    0.258692] pci_bus 0000:01: resource 1 mem: [0xac200000-0xac2fffff]                 
[    0.258694] pci_bus 0000:01: resource 2 pref mem [0x90000000-0x9fffffff]             
[    0.258697] pci_bus 0000:02: resource 0 io:  [0x5000-0x5fff]                         
[    0.258699] pci_bus 0000:02: resource 1 mem: [0xab200000-0xac1fffff]                 
[    0.258702] pci_bus 0000:02: resource 2 pref mem [0xa4100000-0xa50fffff]             
[    0.258705] pci_bus 0000:03: resource 0 io:  [0x4000-0x4fff]                         
[    0.258707] pci_bus 0000:03: resource 1 mem: [0xaa100000-0xab1fffff]                 
[    0.258710] pci_bus 0000:03: resource 2 pref mem [0xa5100000-0xa60fffff]             
[    0.258712] pci_bus 0000:05: resource 0 io:  [0x3000-0x3fff]                         
[    0.258715] pci_bus 0000:05: resource 1 mem: [0xa9100000-0xaa0fffff]                 
[    0.258718] pci_bus 0000:05: resource 2 pref mem [0xa6100000-0xa70fffff]             
[    0.258720] pci_bus 0000:07: resource 0 io:  [0x2000-0x2fff]                         
[    0.258723] pci_bus 0000:07: resource 1 mem: [0xa8100000-0xa90fffff]                 
[    0.258725] pci_bus 0000:07: resource 2 pref mem [0xa7100000-0xa80fffff]             
[    0.258728] pci_bus 0000:09: resource 0 io:  [0x1000-0x1fff]                         
[    0.258731] pci_bus 0000:09: resource 1 mem: [0xa2000000-0xa40fffff]                 
[    0.258733] pci_bus 0000:09: resource 2 pref mem [0xa0000000-0xa1ffffff]             
[    0.258736] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]                           
[    0.258738] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]                   
[    0.258770] NET: Registered protocol family 2                                        
[    0.258861] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)        
[    0.259167] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)     
[    0.259598] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)              
[    0.259818] TCP: Hash tables configured (established 131072 bind 65536)              
[    0.259820] TCP reno registered                                                      
[    0.259885] NET: Registered protocol family 1                                        
[    0.259940] Trying to unpack rootfs image as initramfs...                            
[    0.448115] Freeing initrd memory: 7471k freed                                       
[    0.452396] cpufreq-nforce2: No nForce2 chipset.                                     
[    0.452431] Scanning for low memory corruption every 60 seconds                      
[    0.452543] audit: initializing netlink socket (disabled)                            
[    0.452563] type=2000 audit(1257223158.452:1): initialized                           
[    0.461150] highmem bounce pool size: 64 pages                                       
[    0.461155] HugeTLB registered 4 MB page size, pre-allocated 0 pages                 
[    0.462668] VFS: Disk quotas dquot_6.5.2                                             
[    0.462729] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)               
[    0.463298] fuse init (API version 7.12)                                             
[    0.463383] msgmni has been set to 1705                                              
[    0.463608] alg: No test for stdrng (krng)                                           
[    0.463623] io scheduler noop registered                                             
[    0.463625] io scheduler anticipatory registered                                     
[    0.463627] io scheduler deadline registered                                         
[    0.463668] io scheduler cfq registered (default)                                    
[    0.463886] pci 0000:01:00.0: Boot video device                                      
[    0.463905] pci 0000:09:08.0: Firmware left e100 interrupts enabled; disabling       
[    0.464028]   alloc irq_desc for 24 on node -1                                       
[    0.464030]   alloc kstat_irqs on node -1                                            
[    0.464040] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X                       
[    0.464048] pcieport-driver 0000:00:01.0: setting latency timer to 64                
[    0.464172]   alloc irq_desc for 25 on node -1                                       
[    0.464174]   alloc kstat_irqs on node -1                                            
[    0.464188] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X                       
[    0.464199] pcieport-driver 0000:00:1c.0: setting latency timer to 64                
[    0.464357]   alloc irq_desc for 26 on node -1                                       
[    0.464359]   alloc kstat_irqs on node -1                                            
[    0.464369] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X                       
[    0.464380] pcieport-driver 0000:00:1c.1: setting latency timer to 64                
[    0.464542]   alloc irq_desc for 27 on node -1                                       
[    0.464544]   alloc kstat_irqs on node -1                                            
[    0.464553] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X                       
[    0.464565] pcieport-driver 0000:00:1c.2: setting latency timer to 64                
[    0.464724]   alloc irq_desc for 28 on node -1                                       
[    0.464726]   alloc kstat_irqs on node -1                                            
[    0.464735] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X                       
[    0.464746] pcieport-driver 0000:00:1c.3: setting latency timer to 64                
[    0.464857] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                          
[    0.464875] Firmware did not grant requested _OSC control                            
[    0.464897] Firmware did not grant requested _OSC control                            
[    0.464911] Firmware did not grant requested _OSC control                            
[    0.464925] Firmware did not grant requested _OSC control                            
[    0.465015] Firmware did not grant requested _OSC control                            
[    0.465030] Firmware did not grant requested _OSC control                            
[    0.465044] Firmware did not grant requested _OSC control                            
[    0.465058] Firmware did not grant requested _OSC control                            
[    0.465118] pciehp 0000:00:1c.3:pcie04: HPC vendor_id 8086 device_id 27d6 ss_vid 0 ss_did 0                                                                                  
[    0.465166] pciehp 0000:00:1c.3:pcie04: service driver pciehp loaded                 
[    0.465174] pciehp: PCI Express Hot Plug Controller Driver version: 0.4              
[    0.467304] ACPI: AC Adapter [AC] (on-line)                                          
[    0.467446] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0     
[    0.467453] ACPI: Power Button [PWRF]                                                
[    0.467545] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                                                                    
[    0.467555] ACPI: Power Button [PWRB]                                                
[    0.467647] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2                                                                                      
[    0.470120] ACPI: Lid Switch [LID]                                                   
[    0.470214] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3                                                                                    
[    0.470220] ACPI: Sleep Button [SLPB]                                                
[    0.470635] Marking TSC unstable due to TSC halts in idle                            
[    0.470662] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])                          
[    0.470687] processor LNXCPU:00: registered as cooling_device0                       
[    0.470691] ACPI: Processor [CPU0] (supports 8 throttling states)                    
[    0.470879] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])                          
[    0.470905] processor LNXCPU:01: registered as cooling_device1                       
[    0.470909] ACPI: Processor [CPU1] (supports 8 throttling states)                    
[    0.473594] isapnp: Scanning for PnP cards...                                        
[    0.474683] Switched to high resolution mode on CPU 1                                
[    0.474689] Switched to high resolution mode on CPU 0                                
[    0.556682] ACPI: Battery Slot [BAT0] (battery present)                              
[    0.827640] isapnp: No Plug & Play device found                                      
[    0.828730] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled                  
[    0.830026] brd: module loaded                                                       
[    0.830486] loop: module loaded                                                      
[    0.830556] input: Macintosh mouse button emulation as /devices/virtual/input/input4 
[    0.830665] ata_piix 0000:00:1f.2: version 2.13                                      
[    0.830682] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17        
[    0.830688] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]                             
[    0.830730] ata_piix 0000:00:1f.2: setting latency timer to 64                       
[    0.830808] scsi0 : ata_piix                                                         
[    0.830891] scsi1 : ata_piix                                                         
[    0.831850] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x70a0 irq 14          
[    0.831853] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x70a8 irq 15          
[    0.832780] Fixed MDIO Bus: probed                                                   
[    0.832814] PPP generic driver version 2.4.2                                         
[    0.832899] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver               
[    0.832921] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16        
[    0.832930] ehci_hcd 0000:00:1d.7: setting latency timer to 64                       
[    0.832934] ehci_hcd 0000:00:1d.7: EHCI Host Controller                              
[    0.832982] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1     
[    0.836911] ehci_hcd 0000:00:1d.7: debug port 1                                      
[    0.836918] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported            
[    0.836931] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xac304400                         
[    0.852062] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                        
[    0.852213] usb usb1: configuration #1 chosen from 1 choice                          
[    0.852269] hub 1-0:1.0: USB hub found                                               
[    0.852283] hub 1-0:1.0: 8 ports detected                                            
[    0.852377] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                   
[    0.852393] uhci_hcd: USB Universal Host Controller Interface driver                 
[    0.852414] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16        
[    0.852421] uhci_hcd 0000:00:1d.0: setting latency timer to 64                       
[    0.852424] uhci_hcd 0000:00:1d.0: UHCI Host Controller                              
[    0.852458] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2     
[    0.852486] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00007080                        
[    0.852566] usb usb2: configuration #1 chosen from 1 choice                          
[    0.852594] hub 2-0:1.0: USB hub found                                               
[    0.852601] hub 2-0:1.0: 2 ports detected                                            
[    0.852648] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17        
[    0.852655] uhci_hcd 0000:00:1d.1: setting latency timer to 64                       
[    0.852658] uhci_hcd 0000:00:1d.1: UHCI Host Controller                              
[    0.852687] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3     
[    0.852722] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00007060                        
[    0.852800] usb usb3: configuration #1 chosen from 1 choice                          
[    0.852826] hub 3-0:1.0: USB hub found                                               
[    0.852833] hub 3-0:1.0: 2 ports detected                                            
[    0.852881] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18        
[    0.852887] uhci_hcd 0000:00:1d.2: setting latency timer to 64                       
[    0.852891] uhci_hcd 0000:00:1d.2: UHCI Host Controller                              
[    0.852920] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4     
[    0.852954] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00007040                        
[    0.853033] usb usb4: configuration #1 chosen from 1 choice                          
[    0.853059] hub 4-0:1.0: USB hub found                                               
[    0.853066] hub 4-0:1.0: 2 ports detected                                            
[    0.853112] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19        
[    0.853119] uhci_hcd 0000:00:1d.3: setting latency timer to 64                       
[    0.853122] uhci_hcd 0000:00:1d.3: UHCI Host Controller                              
[    0.853151] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5     
[    0.853186] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00007020                        
[    0.853267] usb usb5: configuration #1 chosen from 1 choice                          
[    0.853294] hub 5-0:1.0: USB hub found                                               
[    0.853300] hub 5-0:1.0: 2 ports detected                                            
[    0.853394] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12    
[    0.860598] i8042.c: Detected active multiplexing controller, rev 1.1.               
[    0.863879] serio: i8042 KBD port at 0x60,0x64 irq 1                                 
[    0.863885] serio: i8042 AUX0 port at 0x60,0x64 irq 12                               
[    0.863888] serio: i8042 AUX1 port at 0x60,0x64 irq 12                               
[    0.863891] serio: i8042 AUX2 port at 0x60,0x64 irq 12                               
[    0.863894] serio: i8042 AUX3 port at 0x60,0x64 irq 12                               
[    0.863949] mice: PS/2 mouse device common for all mice                              
[    0.864145] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0                    
[    0.864179] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs                 
[    0.864273] device-mapper: uevent: version 1.0.3                                     
[    0.864351] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com                                                                                 
[    0.864455] device-mapper: multipath: version 1.1.0 loaded                           
[    0.864458] device-mapper: multipath round-robin: version 1.0.0 loaded               
[    0.864577] EISA: Probing bus 0 at eisa.0                                            
[    0.864583] Cannot allocate resource for EISA slot 1                                 
[    0.864585] Cannot allocate resource for EISA slot 2                                 
[    0.864587] Cannot allocate resource for EISA slot 3                                 
[    0.864589] Cannot allocate resource for EISA slot 4                                 
[    0.864591] Cannot allocate resource for EISA slot 5                                 
[    0.864593] Cannot allocate resource for EISA slot 6                                 
[    0.864595] Cannot allocate resource for EISA slot 7                                 
[    0.864601] EISA: Detected 0 cards.                                                  
[    0.864795] cpuidle: using governor ladder                                           
[    0.864931] cpuidle: using governor menu                                             
[    0.865423] TCP cubic registered                                                     
[    0.865591] NET: Registered protocol family 10                                       
[    0.866050] lo: Disabled Privacy Extensions                                          
[    0.866395] NET: Registered protocol family 17                                       
[    0.866412] Bluetooth: L2CAP ver 2.13                                                
[    0.866414] Bluetooth: L2CAP socket layer initialized                                
[    0.866417] Bluetooth: SCO (Voice Link) ver 0.6                                      
[    0.866418] Bluetooth: SCO socket layer initialized                                  
[    0.866460] Bluetooth: RFCOMM TTY layer initialized                                  
[    0.866463] Bluetooth: RFCOMM socket layer initialized                               
[    0.866465] Bluetooth: RFCOMM ver 1.11                                               
[    0.866807] Using IPI No-Shortcut mode                                               
[    0.866871] PM: Resume from disk failed.                                             
[    0.866883] registered taskstats version 1                                           
[    0.866986]   Magic number: 1:808:665                                                
[    0.867065] rtc_cmos 00:03: setting system clock to 2009-11-03 04:39:19 UTC (1257223159)                                                                                     
[    0.867068] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                     
[    0.867070] EDD information not available.                                           
[    0.869717] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5                                                                               
[    0.992667] ata1.00: ATA-7: Hitachi HTS541212H9SA00, HP4OC20F, max UDMA/100          
[    0.992674] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)             
[    1.004586] ata2.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.20, max UDMA/33               
[    1.008701] ata1.00: configured for UDMA/100                                         
[    1.008916] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54121 HP4O PQ: 0 ANSI: 5                                                                                     
[    1.009084] sd 0:0:0:0: Attached scsi generic sg0 type 0                             
[    1.009121] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)    
[    1.009168] sd 0:0:0:0: [sda] Write Protect is off                                   
[    1.009171] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                
[    1.009195] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                          
[    1.009319]  sda:                                                                    
[    1.020522] ata2.00: configured for UDMA/33                                          
[    1.022920] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.20 PQ: 0 ANSI: 5                                                                                     
[    1.027423] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray    
[    1.027429] Uniform CD-ROM driver Revision: 3.20                                     
[    1.027565] sr 1:0:0:0: Attached scsi CD-ROM sr0                                     
[    1.027645] sr 1:0:0:0: Attached scsi generic sg1 type 5                             
[    1.032347]  sda1 sda2 < sda5 >                                                      
[    1.059748] sd 0:0:0:0: [sda] Attached SCSI disk                                     
[    1.059770] Freeing unused kernel memory: 540k freed                                 
[    1.060125] Write protecting the kernel text: 4568k                                  
[    1.060176] Write protecting the kernel read-only data: 1836k                        
[    1.168489] Linux agpgart interface v0.103                                           
[    1.258545] [drm] Initialized drm 1.1.0 20060810                                     
[    1.273838] [drm] radeon default to kernel modesetting DISABLED.                     
[    1.274485] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16             
[    1.274490] pci 0000:01:00.0: setting latency timer to 64                            
[    1.274618] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0     
[    1.287527] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6                                                                   
[    1.287561] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)           
[    1.290280] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI                    
[    1.290283] e100: Copyright(c) 1999-2006 Intel Corporation                           
[    1.290326]   alloc irq_desc for 20 on node -1                                       
[    1.290329]   alloc kstat_irqs on node -1                                            
[    1.290337] e100 0000:09:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20            
[    1.290405] e100 0000:09:08.0: setting latency timer to 64                           
[    1.317650] e100 0000:09:08.0: PME# disabled                                         
[    1.318483] e100: eth0: e100_probe: addr 0xa4000000, irq 20, MAC addr 00:40:d0:a9:19:ff                                                                                      
[    1.318508] ohci1394 0000:09:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16        
[    1.318515] ohci1394 0000:09:02.0: setting latency timer to 64                       
[    1.373038] usb 2-1: new low speed USB device using uhci_hcd and address 2           
[    1.377302] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[a4003000-a40037ff]  Max Packet=[2048]  IR/IT contexts=[8/8]                                             
[    1.554575] usb 2-1: configuration #1 chosen from 1 choice                           
[    1.565054] usbcore: registered new interface driver hiddev                          
[    1.579737] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input7                                  
[    1.579814] generic-usb 0003:045E:0039.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1/input0        
[    1.579827] usbcore: registered new interface driver usbhid                          
[    1.579830] usbhid: v2.6:USB HID core driver                                         
[    2.112949] PM: Starting manual resume from disk                                     
[    2.112953] PM: Resume from partition 8:5                                            
[    2.112955] PM: Checking hibernation image.                                          
[    2.113179] PM: Resume from disk failed.                                             
[    2.133756] EXT4-fs (sda1): barriers enabled                                         
[    2.152148] kjournald2 starting: pid 415, dev sda1:8, commit interval 5 seconds      
[    2.152175] EXT4-fs (sda1): delayed allocation enabled                               
[    2.152183] EXT4-fs: file extents enabled                                            
[    2.161390] EXT4-fs: mballoc enabled                                                 
[    2.161403] EXT4-fs (sda1): mounted filesystem with ordered data mode                
[    2.648535] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[7856341278563412]          
[    2.932053] type=1505 audit(1257223161.564:2): operation="profile_load" pid=438 name=/usr/share/gdm/guest-session/Xsession                                                   
[    2.935418] type=1505 audit(1257223161.564:3): operation="profile_load" pid=439 name=/sbin/dhclient3                                                                         
[    2.936243] type=1505 audit(1257223161.568:4): operation="profile_load" pid=439 name=/usr/lib/NetworkManager/nm-dhcp-client.action                                           
[    2.936641] type=1505 audit(1257223161.568:5): operation="profile_load" pid=439 name=/usr/lib/connman/scripts/dhclient-script                                                
[    2.985866] type=1505 audit(1257223161.616:6): operation="profile_load" pid=440 name=/usr/bin/evince                                                                         
[    2.997160] type=1505 audit(1257223161.628:7): operation="profile_load" pid=440 name=/usr/bin/evince-previewer                                                               
[    3.003840] type=1505 audit(1257223161.632:8): operation="profile_load" pid=440 name=/usr/bin/evince-thumbnailer                                                             
[    3.035018] type=1505 audit(1257223161.664:9): operation="profile_load" pid=442 name=/usr/lib/cups/backend/cups-pdf                                                          
[    4.254662] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k                                                                                        
[    4.283965] udev: starting version 147                                               
[    4.494030] EXT4-fs (sda1): internal journal on sda1:8                               
[    7.394781] __ratelimit: 6 callbacks suppressed                                      
[    7.394785] type=1505 audit(1257223166.024:12): operation="profile_replace" pid=789 name=/usr/share/gdm/guest-session/Xsession                                               
[    7.396506] type=1505 audit(1257223166.028:13): operation="profile_replace" pid=790 name=/sbin/dhclient3                                                                     
[    7.397255] type=1505 audit(1257223166.028:14): operation="profile_replace" pid=790 name=/usr/lib/NetworkManager/nm-dhcp-client.action                                       
[    7.397656] type=1505 audit(1257223166.028:15): operation="profile_replace" pid=790 name=/usr/lib/connman/scripts/dhclient-script                                            
[    7.401385] type=1505 audit(1257223166.032:16): operation="profile_replace" pid=791 name=/usr/bin/evince                                                                     
[    7.412743] type=1505 audit(1257223166.044:17): operation="profile_replace" pid=791 name=/usr/bin/evince-previewer                                                           
[    7.420623] type=1505 audit(1257223166.052:18): operation="profile_replace" pid=791 name=/usr/bin/evince-thumbnailer                                                         
[    7.430097] type=1505 audit(1257223166.060:19): operation="profile_replace" pid=793 name=/usr/lib/cups/backend/cups-pdf                                                      
[    7.430953] type=1505 audit(1257223166.060:20): operation="profile_replace" pid=793 name=/usr/sbin/cupsd                                                                     
[    7.433460] type=1505 audit(1257223166.064:21): operation="profile_replace" pid=794 name=/usr/sbin/tcpdump                                                                   
[    7.551242] ip_tables: (C) 2000-2006 Netfilter Core Team                             
[    7.856112] cfg80211: Calling CRDA to update world regulatory domain                 
[    8.078904] intel_rng: FWH not detected                                              
[    8.633061] cfg80211: World regulatory domain updated:                               
[    8.633065]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)       
[    8.633068]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)            
[    8.633071]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)            
[    8.633073]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)            
[    8.633076]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)            
[    8.633079]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)            
[    8.764041] lp: driver loaded but no devices found                                   
[    9.462832] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0  
[    9.507735] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks                                                                          
[    9.507738] iwl3945: Copyright(c) 2003-2009 Intel Corporation                        
[    9.507807] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17         
[    9.507822] iwl3945 0000:03:00.0: setting latency timer to 64                        
[    9.578072] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels 
[    9.578075] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG          
[    9.578190]   alloc irq_desc for 29 on node -1                                       
[    9.578192]   alloc kstat_irqs on node -1                                            
[    9.578226] iwl3945 0000:03:00.0: irq 29 for MSI/MSI-X                               
[    9.583848] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input8                                                                                 
[   10.186301] sdhci: Secure Digital Host Controller Interface driver                   
[   10.186305] sdhci: Copyright(c) Pierre Ossman                                        
[   10.187587] sdhci-pci 0000:09:02.2: SDHCI controller found [1217:7120] (rev 1)       
[   10.187606] sdhci-pci 0000:09:02.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16       
[   10.187630] mmc0: Unknown controller version (16). You may experience problems.      
[   10.187671] Registered led device: mmc0::                                            
[   10.187707] mmc0: SDHCI controller on PCI [0000:09:02.2] using PIO
[   10.263025] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   10.448088] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   10.448107]   alloc irq_desc for 23 on node -1
[   10.448112]   alloc kstat_irqs on node -1
[   10.448123] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   10.448206]   alloc irq_desc for 30 on node -1
[   10.448210]   alloc kstat_irqs on node -1
[   10.448227] HDA Intel 0000:00:1b.0: irq 30 for MSI/MSI-X
[   10.448289] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.422071] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   17.418897] iwl3945 0000:03:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[   17.486973] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   17.556591] Registered led device: iwl-phy0::radio
[   17.556669] Registered led device: iwl-phy0::assoc
[   17.556703] Registered led device: iwl-phy0::RX
[   17.556736] Registered led device: iwl-phy0::TX
[   17.570046] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.756258] ppdev: user-space parallel port driver
[   20.428320] [drm] Setting GART location based on new memory map
[   20.430476] [drm] Loading R500 Microcode
[   20.430527] [drm] Num pipes: 1
[   20.430536] [drm] writeback test succeeded in 2 usecs
[   23.498908] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.804192] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   25.804464] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.628329] Registered led device: iwl-phy0::radio
[   28.628407] Registered led device: iwl-phy0::assoc
[   28.628440] Registered led device: iwl-phy0::RX
[   28.628473] Registered led device: iwl-phy0::TX
[   28.646001] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.902925] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.804200] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   30.804468] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   40.865055] eth0: no IPv6 routers present
[   52.704030] Clocksource tsc unstable (delta = -69977429 ns)

```


> **pytheas22 said:**
> jcolsen: please post the output of these commands:
```

sudo iwlist scan
lshw -C Network
```

Also, what are you using to try to connect?  NetworkManager or a different program?

---

### Post by pytheas22 on 2009-11-03
jiapei100: I'm wondering if your network is on channel 12 or 13, which the iwl3945 driver can't see by default (because those channels are only used in Europe and Asia; for more details, read [this thread]("http://ubuntuforums.org/showthread.php?t=1068032")).  To fix it, please try running this command:
```

echo options cfg80211 ieee80211_regdom="EU" | sudo tee -a /etc/modprobe.d/options
```

Then reboot.  Do you still have the problem?

---

### Post by jiapei100 on 2009-11-03
Hi, thank you so much for your prompt reply. Problem continues:
All attached as follows:

```
jiapei@jiapei-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=15 dBm                                              
          Retry  long limit:7   RTS thr:off   Fragment thr:off         
          Power Management:on                                          
                                                                       
jiapei@jiapei-laptop:~$ ifconfig                                       
eth0      Link encap:Ethernet  HWaddr 00:40:d0:a9:19:ff                
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fea9:19ff/64 Scope:Link            
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1            
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0          
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0        
          collisions:0 txqueuelen:1000                                  
          RX bytes:162890 (162.8 KB)  TX bytes:62628 (62.6 KB)          

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                           
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)      

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:7c:1b:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1     
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                        
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)              

jiapei@jiapei-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network                                        
       description: Wireless interface             
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation                               
       physical id: 0                                          
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:7c:1b:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:aa100000-aa100fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:09:08.0
       logical name: eth0
       version: 02
       serial: 00:40:d0:a9:19:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.4 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:a4000000-a4000fff ioport:1200(size=64)
jiapei@jiapei-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

jiapei@jiapei-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```



What's more, since I'm using wicd, in the Preferences->Advance Settings, how to setup the options for
WPA supplicant
and
Backend ??

Now, I'm using wext and external. I tried all the compositions as well, but all failed.

Can you please help? It's seriously depressing on this point for Ubuntu 9.10 ...


Finally, thanks again.

Best Regards
JIA






> **pytheas22 said:**
> jiapei100: I'm wondering if your network is on channel 12 or 13, which the iwl3945 driver can't see by default (because those channels are only used in Europe and Asia; for more details, read [this thread]("http://ubuntuforums.org/showthread.php?t=1068032")).  To fix it, please try running this command:
```

echo options cfg80211 ieee80211_regdom="EU" | sudo tee -a /etc/modprobe.d/options
```

Then reboot.  Do you still have the problem?

---

### Post by pytheas22 on 2009-11-03
jiapei100: for now, don't worry about the WPA stuff (which shouldn't actually be a problem; wicd should be able to handle it all automatically).  The problem to deal with first is your inability to detect wireless networks.  I'm not sure what's wrong here because everything looks like it should be working.

What are the settings for the network you're trying to connect to?  In other words, which mode is it in (11a, 11b, 11g or 11n, or mixed) and which channel is it on (1-13).  Does it have a hidden ESSID?  If you don't know how to find this information, let me know and I'll tell you where to look.

Also, are there normally many networks visible from your location, or just one?

And do you have a button that you can use to turn your wireless card on and off, or is it always on?

---

### Post by kevdog on 2009-11-03
phytheas22

I like your channel changing option.  Bought I thought the iw application was supposed to do this! [http://linuxwireless.org/en/users/Documentation/iw](http://linuxwireless.org/en/users/Documentation/iw)

I guess of course this wouldn't work with intel devices but rather broadcom and some atheros based chipsets.

I guess I'll just go away now!!

---

### Post by pytheas22 on 2009-11-03
kevdog: I'm interested in knowing which channel jiapei100's network operates on because there is a known issue with the iwl3945 driver where by default it can only detect channels 1-11, since these are the only valid channels in most of the world.  In Europe and parts of Asia, however, channels 12 and 13 are also used.  iwl3945 can't see these channels by default, but if you load the module with special options, it can.

So I don't want jiapei100 to change the router's channel; I just want to know which one it's on so that we can know whether the issue with iwl3945 not seeing channels 12 and 13 could be the problem.

As far as I know, the channel issue is specific to iwl3945 (and maybe other iwl* drivers, although I've only seen it with iwl3945 specifically), not Broadcom or anything else.

If you have other thoughts, feel free to chime in.  If the channel issue isn't at fault here, I don't know what's wrong for jiapei100, because everything else looks like it should be working (wireless radio does not appear to be turned off).  The only other possible thing I can think of is that his network is in 802.11n mode, but his card doesn't support 11n.

---

### Post by jiapei100 on 2009-11-03
Hi, Dear Pytheas:

Thanks for your kind reply !! Thank you..



> **pytheas22 said:**
> jiapei100: for now, don't worry about the WPA stuff (which shouldn't actually be a problem; wicd should be able to handle it all automatically).  The problem to deal with first is your inability to detect wireless networks.  I'm not sure what's wrong here because everything looks like it should be working.

What are the settings for the network you're trying to connect to?  In other words, which mode is it in (11a, 11b, 11g or 11n, or mixed) and which channel is it on (1-13).  Does it have a hidden ESSID?  If you don't know how to find this information, let me know and I'll tell you where to look.

Sorry, I've got no idea which mode I'm in. Please let me know how to detect all these information. 
Please have a look at my post at
[http://ubuntuforums.org/showthread.php?p=8235728](http://ubuntuforums.org/showthread.php?p=8235728)
for more details. Hope that can help a little bit.

> **pytheas22 said:**
> 
Also, are there normally many networks visible from your location, or just one?

Yes, there was several wireless networks detected, but now none .


> **pytheas22 said:**
> 
And do you have a button that you can use to turn your wireless card on and off, or is it always on?

Yes, there is such a button. I tried to turn it on and off, but it seems nothing happened.


I just wonder that my problem is "wl" has not been successfully loaded as my test

```

jiapei@jiapei-laptop:~$ sudo modprobe wl
[sudo] password for jiapei:
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting wl (/lib/modules/2.6.31-14-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```



What's more, now, I reinstall network-manager and remove wicd, I'm still not able to activate my wireless internet.
```

in Network Connections, 
Wireless tab
SSID: mySSID
Model: Infrastructure ( I don't think it's Ad hoc)
BSSID: empty
MAC address: empty
MTU: automatic bytes

IPv4 Settings tab
Method: Automatic (DHCP) addresses only
DNS servers: 192.168.1.1
Search domains: empty
DHCP client ID: empty

IPv6 Settings tab
Method: Automatic
DNS Servers: disactivated to change (in gray)
Search domains: disactivated to change (in gray)

Wireless Security tab  // this tab should be ok
Security: WPA & WPA2 Personal
Password: my password

```

Anyway, please do let me know how to detect my wireless mode first. 


Thank you very much.

Best Regards
JIA

---

### Post by pytheas22 on 2009-11-03
jiapei100: to find the settings of you network, you will need to go to a computer connected to it (i.e., a computer that you are able to access wireless with), open a web browser, and put 192.168.1.1 in the address bar (if you receive an error saying the page was not found, try 10.0.0.1, 10.0.1.1 or 192.168.0.1 instead).  This will bring you to an interface where you can see the settings of your wireless network.  The interface is different on different routers so I can't tell you exactly where to look, but somewhere there you should be able to find information regarding the wireless channel and mode.

It's curious that you say there's a button to turn your wireless on and off, but it doesn't seem to be working.  It may be the case that a setting in BIOS is overriding the switch.  Could you go into your computer's BIOS and see if there are any settings related to wireless, and if so, try playing with them to see if that will allow you to see networks?

> 
I just wonder that my problem is "wl" has not been successfully loaded as my test

Don't worry about this.  'wl' is for Broadcom-based wireless cards.  Yours is Intel so wl doesn't matter.

---

### Post by jiapei100 on 2009-11-04
checked already.

BIOS wireless is turned on.


:S
so depressed..
Thanks anyway...

cheers
JIA

---

### Post by jiapei100 on 2009-11-04
Hi, pytheas:

I found that on the router, the wireless channel has been set to 12 !!!!
Now, I changed it manually to 10. But, I worry that next time when I reboot the router, will it automatically change the wireless channel to 12 again? Anyway, let me move ahead first.

Thank you !!
Rgds
JIA

> **pytheas22 said:**
> jiapei100: I'm wondering if your network is on channel 12 or 13, which the iwl3945 driver can't see by default (because those channels are only used in Europe and Asia; for more details, read [this thread]("http://ubuntuforums.org/showthread.php?t=1068032")).  To fix it, please try running this command:
```

echo options cfg80211 ieee80211_regdom="EU" | sudo tee -a /etc/modprobe.d/options
```

Then reboot.  Do you still have the problem?

---

### Post by jiapei100 on 2009-11-04
Yes !!
Hahahaha, after I change the channel to 10, my network is working fine !!!

Thank you so much !!!

Best Regards
JIA Pei

---

### Post by pytheas22 on 2009-11-04
jiapei100: glad it finally worked.  It sounds like it was the issue with channels 12 and 13 not being visible, after all.  I'm not sure why adding the special option to your /etc/modprobe.d/options file, as I asked you to do earlier, didn't help; maybe that command doesn't work anymore in modern versions of Ubuntu.  In any case, good to hear it's working now.

---

### Post by jiapei100 on 2009-11-05
thank you very much pythreas !! Thanks !!!

Yup, the command seems not to work, but following your suggestion to change router settings from website [http://192.168.1.1](http://192.168.1.1)  I managed to change the wireless channel.  Perfect. Now, it's working. 

Ubuntu 9.10 is not as bad as I imagined. It's ok !!!
^_^
Cheers
JIA

> **pytheas22 said:**
> jiapei100: glad it finally worked.  It sounds like it was the issue with channels 12 and 13 not being visible, after all.  I'm not sure why adding the special option to your /etc/modprobe.d/options file, as I asked you to do earlier, didn't help; maybe that command doesn't work anymore in modern versions of Ubuntu.  In any case, good to hear it's working now.

---

### Post by quinnten83 on 2009-11-05
```
> **Torgas Prim said:**
> I have been following this thread's suggestions and am at the dmesg command:
I mistakenly hit No I think when enabling the driver during a fresh install of ubuntu, to allow the firmware to install also. How can I fix this?

[    9.408274] Brought up 1 CPUs
[    9.408344] CPU0 attaching sched-domain:
[    9.408347]  domain 0: span 01
[    9.408348]   groups: 01
[    9.408491] net_namespace: 64 bytes
[    9.408497] Booting paravirtualized kernel on bare hardware
[    9.408911] Time: 13:07:52  Date: 11/01/09
[    9.408931] NET: Registered protocol family 16
[    9.409080] EISA bus registered
[    9.409106] ACPI: bus type pci registered
[    9.415198] PCI: PCI BIOS revision 2.10 entry at 0xfd8cc, last bus=1
[    9.415200] PCI: Using configuration type 1
[    9.415205] Setting up standard PCI resources
[    9.416721] ACPI: EC: Look up EC in DSDT
[    9.418879] ACPI: Interpreter enabled
[    9.418881] ACPI: (supports S0 S3 S4 S5)
[    9.418890] ACPI: Using IOAPIC for interrupt routing
[    9.420854] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.424091] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[    9.424093] ACPI: EC: driver started in interrupt mode
[    9.424121] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.424476] PCI quirk: region 4000-407f claimed by vt8235 PM
[    9.424479] PCI quirk: region 8100-810f claimed by vt8235 SMB
[    9.424831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.429505] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
[    9.429566] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11, disabled.
[    9.429623] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *10, disabled.
[    9.429679] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *10, disabled.
[    9.429758] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 12 14 15)
[    9.429834] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    9.429911] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 11 12 14 15) *10
[    9.429989] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    9.430072] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.430094] pnp: PnP ACPI init
[    9.430100] ACPI: bus type pnp registered
[    9.431744] pnp: PnP ACPI: found 9 devices
[    9.431746] ACPI: ACPI bus type pnp unregistered
[    9.431749] PnPBIOS: Disabled by ACPI PNP
[    9.431911] PCI: Using ACPI for IRQ routing
[    9.431913] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.440208] NET: Registered protocol family 8
[    9.440210] NET: Registered protocol family 20
[    9.440263] AppArmor: AppArmor Filesystem Enabled
[    9.444179] Time: tsc clocksource has been installed.
[    9.452194] system 00:05: iomem range 0x0-0x9ffff could not be reserved
[    9.452197] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
[    9.452200] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
[    9.452202] system 00:05: iomem range 0xffee0000-0xffefffff has been reserved
[    9.452205] system 00:05: iomem range 0xfee00400-0xfee013ff has been reserved
[    9.452209] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    9.452212] system 00:06: ioport range 0xf510-0xf511 has been reserved
[    9.452214] system 00:06: ioport range 0xf500-0xf500 has been reserved
[    9.452217] system 00:06: ioport range 0x4000-0x407f has been reserved
[    9.452219] system 00:06: ioport range 0x8100-0x811f could not be reserved
[    9.452222] system 00:06: ioport range 0x300-0x301 has been reserved
[    9.482489] PCI: Bridge: 0000:00:01.0
[    9.482491]   IO window: 2000-2fff
[    9.482495]   MEM window: d0100000-d01fffff
[    9.482498]   PREFETCH window: d8000000-dfffffff
[    9.482501] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[    9.482503]   IO window: 00003000-000030ff
[    9.482506]   IO window: 00003400-000034ff
[    9.482509]   PREFETCH window: 60000000-63ffffff
[    9.482513]   MEM window: 64000000-67ffffff
[    9.482526] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    9.482564] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 16
[    9.482578] NET: Registered protocol family 2
[    9.520129] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.520405] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.521568] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.522231] TCP: Hash tables configured (established 131072 bind 65536)
[    9.522234] TCP reno registered
[    9.532191] checking if image is initramfs... it is
[    9.983332] Switched to high resolution mode on CPU 0
[   10.125480] Freeing initrd memory: 7310k freed
[   10.126042] audit: initializing netlink socket (disabled)
[   10.126056] audit(1257080872.088:1): initialized
[   10.126203] highmem bounce pool size: 64 pages
[   10.127704] VFS: Disk quotas dquot_6.5.1
[   10.127763] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.127889] io scheduler noop registered
[   10.127891] io scheduler anticipatory registered
[   10.127893] io scheduler deadline registered
[   10.127902] io scheduler cfq registered (default)
[   10.127909] PCI: VIA PCI bridge detected. Disabling DAC.
[   10.127965] Boot video device is 0000:01:00.0
[   10.128171] isapnp: Scanning for PnP cards...
[   10.481255] isapnp: No Plug & Play device found
[   10.506159] Real Time Clock Driver v1.12ac
[   10.506238] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.507165] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.507222] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.507291] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.510302] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.510306] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.510585] mice: PS/2 mouse device common for all mice
[   10.510673] EISA: Probing bus 0 at eisa.0
[   10.510680] Cannot allocate resource for EISA slot 1
[   10.510682] Cannot allocate resource for EISA slot 2
[   10.510684] Cannot allocate resource for EISA slot 3
[   10.510686] Cannot allocate resource for EISA slot 4
[   10.510703] EISA: Detected 0 cards.
[   10.510705] cpuidle: using governor ladder
[   10.510707] cpuidle: using governor menu
[   10.510788] NET: Registered protocol family 1
[   10.510810] Using IPI No-Shortcut mode
[   10.510841] registered taskstats version 1
[   10.510933]   Magic number: 1:547:128
[   10.511069]   hash matches device device:03
[   10.511071]   hash matches device PNP0C02:00
[   10.511077] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.511079] EDD information not available.
[   10.511514] Freeing unused kernel memory: 368k freed
[   10.511538] Write protecting the kernel read-only data: 803k
[   10.538373] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.718516] fuse init (API version 7.9)
[   11.734652] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   12.176772] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 18 (level, low) -> IRQ 17
[   12.176801] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[   12.176806] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[   12.176811] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[   12.176816] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[   12.176820] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[   12.180106] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0c.0
[   12.204392] usbcore: registered new interface driver usbfs
[   12.204422] usbcore: registered new interface driver hub
[   12.215611] usbcore: registered new device driver usb
[   12.227587] USB Universal Host Controller Interface driver v3.0
[   12.227751] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug
[   12.227797] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
[   12.227800] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
[   12.227808] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 18
[   12.227818] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   12.228067] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   12.228099] uhci_hcd 0000:00:10.0: irq 18, io base 0x00001c80
[   12.228224] usb usb1: configuration #1 chosen from 1 choice
[   12.228248] hub 1-0:1.0: USB hub found
[   12.228252] hub 1-0:1.0: 2 ports detected
[   12.271232] SCSI subsystem initialized
[   12.319408] libata version 3.00 loaded.
[   12.331500] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 18
[   12.331513] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   12.331544] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   12.331566] uhci_hcd 0000:00:10.1: irq 18, io base 0x00001ca0
[   12.331666] usb usb2: configuration #1 chosen from 1 choice
[   12.331687] hub 2-0:1.0: USB hub found
[   12.331692] hub 2-0:1.0: 2 ports detected
[   12.331733] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   12.435324] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 18
[   12.435337] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   12.435358] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   12.435380] uhci_hcd 0000:00:10.2: irq 18, io base 0x00001cc0
[   12.435479] usb usb3: configuration #1 chosen from 1 choice
[   12.435499] hub 3-0:1.0: USB hub found
[   12.435504] hub 3-0:1.0: 2 ports detected
[   12.539239] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKD] -> GSI 21 (level, low) -> IRQ 18
[   12.539255] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   12.539278] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   12.539317] ehci_hcd 0000:00:10.3: irq 18, io mem 0xd0002800
[   12.551016] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.551114] usb usb4: configuration #1 chosen from 1 choice
[   12.551134] hub 4-0:1.0: USB hub found
[   12.551141] hub 4-0:1.0: 6 ports detected
[   12.655598] ACPI: PCI Interrupt Link [ALKB] disabled and referenced, BIOS bug
[   12.655645] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 23
[   12.655647] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[   12.655656] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKB] -> GSI 23 (level, low) -> IRQ 19
[   12.659768] eth0: VIA Rhine II at 0xd0002c00, 00:03:25:13:26:68, IRQ 19.
[   12.660475] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   12.660777] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[   12.660811] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 22
[   12.660813] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 22
[   12.660817] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 22 (level, low) -> IRQ 20
[   12.660871] ACPI: PCI interrupt for device 0000:00:11.1 disabled
[   12.662989] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 21
[   12.715627] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[d0002000-d00027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.728945] pata_via 0000:00:11.1: version 0.3.3
[   12.728968] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 22 (level, low) -> IRQ 20
[   12.729802] scsi0 : pata_via
[   12.730314] scsi1 : pata_via
[   12.730817] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1ce0 irq 14
[   12.730819] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1ce8 irq 15
[   12.894882] ata1.00: ATA-5: HITACHI_DK23FA-60, 00M4A0A0, max UDMA/100
[   12.894887] ata1.00: 117210240 sectors, multi 16: LBA 
[   12.902765] ata1.00: configured for UDMA/100
[   13.134061] hub 4-0:1.0: over-current change on port 1
[   13.222231] ata2.00: ATAPI: Slimtype COMBO LSC-24082K, JK0N, max UDMA/33
[   13.237881] hub 4-0:1.0: over-current change on port 2
[   13.393822] ata2.00: configured for UDMA/33
[   13.393926] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23FA-6 00M4 PQ: 0 ANSI: 5
[   13.394699] scsi 1:0:0:0: CD-ROM            Slimtype COMBO LSC-24082K JK0N PQ: 0 ANSI: 5
[   13.402031] Driver 'sd' needs updating - please use bus_type methods
[   13.402118] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.402129] sd 0:0:0:0: [sda] Write Protect is off
[   13.402132] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.402146] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.402185] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.402192] sd 0:0:0:0: [sda] Write Protect is off
[   13.402194] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.402205] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.402208]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   13.438126]  sda1 sda2 < sda5 >
[   13.466214] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.471810] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.471829] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.474544] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[   13.474549] Uniform CD-ROM driver Revision: 3.20
[   13.474589] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   13.764001] Attempting manual resume
[   13.764006] swsusp: Resume From Partition 8:5
[   13.764007] PM: Checking swsusp image.
[   13.764164] PM: Resume from disk failed.
[   13.808869] kjournald starting.  Commit interval 5 seconds
[   13.808881] EXT3-fs: mounted filesystem with ordered data mode.
[   13.884803] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   13.992725] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000325212900abce]
[   14.059535] usb 2-2: configuration #1 chosen from 1 choice
[   14.065482] hub 2-2:1.0: USB hub found
[   14.066459] hub 2-2:1.0: 3 ports detected
[   14.377897] usb 2-2.1: new full speed USB device using uhci_hcd and address 3
[   14.512726] usb 2-2.1: configuration #1 chosen from 1 choice
[   14.725270] usb 2-2.2: new low speed USB device using uhci_hcd and address 4
[   14.870088] usb 2-2.2: configuration #1 chosen from 1 choice
[   25.832958] Yenta: CardBus bridge found at 0000:00:0a.0 [161f:2032]
[   25.832977] Yenta: Using CSCINT to route CSC interrupts to PCI
[   25.832979] Yenta: Routing CardBus interrupts to PCI
[   25.832982] Yenta TI: socket 0000:00:0a.0, mfunc 0x01001002, devctl 0x44
[   25.980749] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.020609] Linux agpgart interface v0.102
[   26.065315] Yenta: ISA IRQ mask 0x0808, PCI irq 16
[   26.065319] Socket status: 30000006
[   26.085693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.120498] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.213107] irda_init()
[   26.213128] NET: Registered protocol family 23
[   26.370628] input: Power Button (FF) as /devices/virtual/input/input3
[   26.379993] ACPI: Power Button (FF) [PWRF]
[   26.380068] input: Power Button (CM) as /devices/virtual/input/input4
[   26.395953] ACPI: Power Button (CM) [PWRB]
[   26.396033] input: Sleep Button (CM) as /devices/virtual/input/input5
[   26.411922] ACPI: Sleep Button (CM) [SLPB]
[   26.411964] input: Lid Switch as /devices/virtual/input/input6
[   26.412322] ACPI: Lid Switch [LID]
[   26.438658] agpgart: Detected AGP bridge 0
[   26.455305] agpgart: AGP aperture is 256M @ 0xe0000000
[   26.780850] ACPI: AC Adapter [AC] (on-line)
[   26.880587] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   26.916314] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   27.102240] ACPI: Battery Slot [BAT0] (battery present)
[   27.415180] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/LNXVIDEO:00/input/input8
[   27.442251] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   27.760670] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   27.852650] [fglrx] Maximum main memory to use for locked dma buffers: 1171 MBytes.
[   27.852683] [fglrx] ASYNCIO init succeed!
[   27.852916] [fglrx] PAT is enabled successfully!
[   27.876098] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   27.903249] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[   27.903294] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   27.903296] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   27.903300] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   27.920045] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   28.041428] usbcore: registered new interface driver hiddev
[   28.045355] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.1/2-2.1:1.0/input/input9
[   28.055747] b43-phy0: Broadcom 4306 WLAN found
[   28.061251] input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:10.1-2.1
[   28.067236] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.1/2-2.1:1.1/input/input10
[   28.077162] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2
[   28.077183] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   28.081216] input,hidraw1: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:10.1-2.1
[   28.096272] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.2/2-2.2:1.0/input/input11
[   28.102537] phy0: Selected rate control algorithm 'simple'
[   28.117113] input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2.2
[   28.117132] usbcore: registered new interface driver usbhid
[   28.117136] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.524500] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 1 converters and GPIO not ready (0xff00)
[   28.525400] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   28.525529] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   28.989028] cs: IO port probe 0x100-0x3af: clean.
[   28.990939] cs: IO port probe 0x3e0-0x4ff: clean.
[   28.991752] cs: IO port probe 0x820-0x8ff: clean.
[   28.992420] cs: IO port probe 0xc00-0xcf7: clean.
[   28.993230] cs: IO port probe 0xa00-0xaff: clean.
[   30.368121] lp: driver loaded but no devices found
[   30.439882] ieee80211_crypt: registered algorithm 'NULL'
[   30.550659] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k
[   31.092266] EXT3 FS on sda1, internal journal
[   32.353029] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.863958] No dock devices found.
[   33.170133] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[   33.170171] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6
[   33.170173] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xe
[   33.170175] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x18
[   33.975984] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.975990] apm: overridden by ACPI.
[   34.330024] ppdev: user-space parallel port driver
[   34.488787] audit(1257080897.302:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4963 profile="/usr/sbin/cupsd" namespace="default"
[   35.409157] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   35.456149] input: b43-phy0 as /devices/virtual/input/input12
[   35.536136] Bluetooth: Core ver 2.11
[   35.539098] NET: Registered protocol family 31
[   35.539102] Bluetooth: HCI device and connection manager initialized
[   35.539107] Bluetooth: HCI socket layer initialized
[   35.564912] Bluetooth: L2CAP ver 2.9
[   35.564918] Bluetooth: L2CAP socket layer initialized
[   35.654599] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   35.654607] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   35.686296] Bluetooth: RFCOMM socket layer initialized
[   35.686312] Bluetooth: RFCOMM TTY layer initialized
[   35.686313] Bluetooth: RFCOMM ver 1.8
[   93.061767] Marking TSC unstable due to: cpufreq changes.
[   93.070745] Time: acpi_pm clocksource has been installed.
[   93.334810] Clocksource tsc unstable (delta = -163967774 ns)
[   94.145526] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 22
[   94.204036] input: b43-phy0 as /devices/virtual/input/input13
[   94.250143] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   94.250156] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   39.837772] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   39.837779] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   39.837784] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
[   39.838639] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   39.838889] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   39.839172] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   39.839413] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[   39.843245] [fglrx] GART Table is not in FRAME_BUFFER range 
[   39.843252] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   39.843255] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   39.977036] [fglrx] interrupt source 20008000 successfully enabled
[   39.977044] [fglrx] enable ID = 0x00000004
[   39.977532] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   39.977814] [fglrx] interrupt source 10000000 successfully enabled
[   39.977817] [fglrx] enable ID = 0x00000005
[   39.978125] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   40.338588] NET: Registered protocol family 17
[  105.510821] NET: Registered protocol family 10
[  105.511846] lo: Disabled Privacy Extensions
[  115.954831] eth0: no IPv6 routers present
[  116.285683] input: b43-phy0 as /devices/virtual/input/input14
[  116.326507] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  116.326520] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   56.398300] input: b43-phy0 as /devices/virtual/input/input15
[   56.440041] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   56.440048] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  168.510305] input: b43-phy0 as /devices/virtual/input/input16
[  168.552324] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  168.552337] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  174.528929] ACPI: EC: missing write data confirmation, don't expect it any longer.
[  195.588844] input: b43-phy0 as /devices/virtual/input/input17
[  195.632287] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  195.632300] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  203.331498] b43-phy1: Broadcom 4306 WLAN found
[  203.352850] b43-phy1 debug: Found PHY: Analog 2, Type 2, Revision 2
[  203.352879] b43-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[  203.383669] phy1: Selected rate control algorithm 'simple'
[  203.389302] BUG: unable to handle kernel NULL pointer dereference at virtual address 0000000d
[  203.389313] printing eip: c031c5db *pde = 00000000 
[  203.389322] Oops: 0002 [#1] SMP 
[  203.389328] Modules linked in: ipv6 af_packet binfmt_misc rfcomm l2cap bluetooth rfkill_input ppdev powernow_k8 cpufreq_userspace cpufreq_conservative cpufreq_ondemand cpufreq_stats freq_table cpufreq_powersave container sbs sbshc dock iptable_filter ip_tables x_tables wl(P) ieee80211_crypt sbp2 parport_pc lp parport joydev pcmcia arc4 ecb blkcipher b43 snd_via82xx usbhid rfkill hid gameport mac80211 snd_via82xx_modem snd_ac97_codec fglrx(P) ac97_bus snd_mpu401_uart cfg80211 snd_pcm_oss snd_mixer_oss snd_pcm led_class video output input_polldev snd_seq_dummy snd_seq_oss snd_seq_midi battery snd_rawmidi snd_seq_midi_event i2c_viapro i2c_core serio_raw ac snd_seq snd_timer snd_seq_device via_ircc evdev amd64_agp button snd psmouse irda k8temp shpchp pci_hotplug agpgart pcspkr soundcore crc_ccitt yenta_socket rsrc_nonstatic pcmcia_core snd_page_alloc ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_via ata_generic ohci1394 pata_acpi ieee1394 via_rhine mii libata scsi_mod ehci_hcd uhci_hcd usbcore ssb thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  203.389443] 
[  203.389449] Pid: 5196, comm: ipolldevd Tainted: P        (2.6.24-25-generic #1)
[  203.389456] EIP: 0060:[<c031c5db>] EFLAGS: 00010246 CPU: 0
[  203.389468] EIP is at mutex_lock+0xb/0x20
[  203.389473] EAX: 0000000d EBX: 0000000d ECX: f44850d8 EDX: f7632000
[  203.389479] ESI: 0000000d EDI: f44850c0 EBP: 00000001 ESP: f7633f54
[  203.389484]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  203.389490] Process ipolldevd (pid: 5196, ti=f7632000 task=f772b700 task.ti=f7632000)
[  203.389495] Stack: dfa83800 f8b87d94 c031bc1a df9c5374 000000fa f44850c0 f44850d4 dfa16080 
[  203.389507]        f8ad00d0 f8ad00e4 f44850d4 dfa16080 c013ceff 00000000 000000ff 00000000 
[  203.389518]        00000000 dfa16084 dfa1608c dfa16080 c013d9a0 dfa16084 c013da24 00000000 
[  203.389529] Call Trace:
[  203.389540]  [<f8b87d94>] b43_rfkill_poll+0x24/0xf0 [b43]
[  203.389573]  [<c031bc1a>] schedule+0x20a/0x600
[  203.389606]  [<f8ad00d0>] input_polled_device_work+0x0/0x40 [input_polldev]
[  203.389620]  [<f8ad00e4>] input_polled_device_work+0x14/0x40 [input_polldev]
[  203.389640]  [<c013ceff>] run_workqueue+0xbf/0x160
[  203.389682]  [<c013d9a0>] worker_thread+0x0/0xe0
[  203.389695]  [<c013da24>] worker_thread+0x84/0xe0
[  203.389713]  [<c0140cb0>] autoremove_wake_function+0x0/0x40
[  203.389740]  [<c013d9a0>] worker_thread+0x0/0xe0
[  203.389753]  [<c01409f2>] kthread+0x42/0x70
[  203.389760]  [<c01409b0>] kthread+0x0/0x70
[  203.389775]  [<c0105667>] kernel_thread_helper+0x7/0x10
[  203.389812]  =======================
[  203.389815] Code: 53 89 c3 e8 a8 fa ff ff b8 ff ff ff ff 90 0f c1 03 83 e8 01 78 04 5b 31 c0 c3 89 d8 5b eb 21 90 53 89 c3 e8 88 fa ff ff 89 d8 90 <ff> 08 79 05 e8 fc 00 00 00 5b c3 8d 76 00 8d bc 27 00 00 00 00 
[  203.389862] EIP: [<c031c5db>] mutex_lock+0xb/0x20 SS:ESP 0068:f7633f54
[  203.389879] ---[ end trace 2b075207c47a1dda ]---
[  207.472936] input: b43-phy1 as /devices/virtual/input/input18
[  207.538926] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  207.538937] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  212.075573] input: b43-phy1 as /devices/virtual/input/input19
[  212.117987] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  212.117998] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  119.251352] input: b43-phy1 as /devices/virtual/input/input20
[  119.300746] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  119.300753] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  269.812226] input: b43-phy1 as /devices/virtual/input/input21
[  269.854413] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  269.854424] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).

```

AAAAAARGH, dude!!
Use the code tags...
:P

---

### Post by doi65535 on 2009-11-14
now thing is I googled around and found this thread that is quite close to what happens to me.

in short, after booting my dell studio 15 with ubuntu 9.10 and broadcom 4315 wireless I have to start synaptic, start the hardware drivers manager, try to deactivate the driver, get an error, close synaptic, deactivate and reactivate the driver so that my wifi would work.

now, as interesting as this sounds, it's not so fun.

oh, and I'm running all from a usb stick to make it work properly first and then install everything for good

somehow I think the output of dmesg would help some of you help me so here it comes

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe5c800 (usable)
[    0.000000]  BIOS-e820: 000000007fe5c800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7fe5c max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fe5c800 (usable)
[    0.000000]  modified: 000000007fe5c800 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 7f8d2000 - 7fe4f098
[    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
[    0.000000] Move RAMDISK from 000000007f8d2000 - 000000007fe4f097 to 008ad000 - 00e2a097
[    0.000000] ACPI: RSDP 000fbaf0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 7fe5e200 00064 (v01 DELL    M09     27D80702 ASL  00000061)
[    0.000000] ACPI: FACP 7fe5e09c 000F4 (v04 DELL    M09     27D80702 ASL  00000061)
[    0.000000] ACPI: DSDT 7fe5e800 0521C (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 7fe6d000 00040
[    0.000000] ACPI: HPET 7fe5e300 00038 (v01 DELL    M09     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 7fe5e400 00068 (v01 DELL    M09     27D80702 ASL  00000047)
[    0.000000] ACPI: MCFG 7fe5e3c0 0003E (v16 DELL    M09     27D80702 ASL  00000061)
[    0.000000] ACPI: SLIC 7fe5e49c 00024 (v01 DELL    M09     27D80702 ASL  00000061)
[    0.000000] ACPI: OSFR 7fe5da00 00086 (v01 DELL    M09     27D80702 ASL  00000061)
[    0.000000] ACPI: BOOT 7fe5dfc0 00028 (v01 DELL    M09     27D80702 ASL  00000061)
[    0.000000] ACPI: SSDT 7fe5c9fa 004D4 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac184]              BRK ==> [00008a9000 - 00008ac184]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fe5c
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fe5c
[    0.000000] On node 0 totalpages: 523767
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2317 pages used for memmap
[    0.000000]   HighMem zone: 294225 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c200a000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519674
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10477360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fe5c)
[    0.000000] Memory: 2053052k/2095472k available (4565k kernel code, 41072k reserved, 2143k data, 540k init, 1186168k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1995.212 MHz processor.
[    0.001985] Console: colour VGA+ 80x25
[    0.001989] console [tty0] enabled
[    0.002156] hpet clockevent registered
[    0.002160] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002166] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.42 BogoMIPS (lpj=7980848)
[    0.002185] Security Framework initialized
[    0.002206] AppArmor: AppArmor initialized
[    0.002213] Mount-cache hash table entries: 512
[    0.002348] Initializing cgroup subsys ns
[    0.002353] Initializing cgroup subsys cpuacct
[    0.002357] Initializing cgroup subsys memory
[    0.002364] Initializing cgroup subsys freezer
[    0.002366] Initializing cgroup subsys net_cls
[    0.002381] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.002384] CPU: L2 cache: 2048K
[    0.002387] CPU: Physical Processor ID: 0
[    0.002389] CPU: Processor Core ID: 0
[    0.002393] mce: CPU supports 6 MCE banks
[    0.002401] CPU0: Thermal monitoring enabled (TM2)
[    0.002405] using mwait in idle threads.
[    0.002412] Performance Counters: Core2 events, Intel PMU driver.
[    0.002421] ... version:                 2
[    0.002423] ... bit width:               40
[    0.002424] ... generic counters:        2
[    0.002426] ... value mask:              000000ffffffffff
[    0.002428] ... max period:              000000007fffffff
[    0.002430] ... fixed-purpose counters:  3
[    0.002431] ... counter mask:            0000000700000003
[    0.002436] Checking 'hlt' instruction... OK.
[    0.018565] ACPI: Core revision 20090521
[    0.028438] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070150] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.38 BogoMIPS (lpj=7980771)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.157443] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[    0.157459] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.160023] Brought up 2 CPUs
[    0.160025] Total of 2 processors activated (7980.80 BogoMIPS).
[    0.160079] CPU0 attaching sched-domain:
[    0.160082]  domain 0: span 0-1 level MC
[    0.160085]   groups: 0 1
[    0.160090] CPU1 attaching sched-domain:
[    0.160092]  domain 0: span 0-1 level MC
[    0.160095]   groups: 1 0
[    0.160172] Booting paravirtualized kernel on bare hardware
[    0.160214] regulator: core version 0.5
[    0.160214] Time: 21:05:39  Date: 11/14/09
[    0.160214] NET: Registered protocol family 16
[    0.160217] EISA bus registered
[    0.160227] ACPI: bus type pci registered
[    0.160296] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.160299] PCI: MCFG area at f8000000 reserved in E820
[    0.160301] PCI: Using MMCONFIG for extended config space
[    0.160303] PCI: Using configuration type 1 for base access
[    0.161335] bio: create slab <bio-0> at 0
[    0.164287] ACPI: EC: Look up EC in DSDT
[    0.184183] ACPI: SSDT 7fe6d080 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.199513] ACPI: Interpreter enabled
[    0.199519] ACPI: (supports S0 S3 S4 S5)
[    0.199539] ACPI: Using IOAPIC for interrupt routing
[    0.280891] ACPI: No dock devices found.
[    0.298545] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.298669] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.298673] pci 0000:00:01.0: PME# disabled
[    0.298772] pci 0000:00:1a.0: reg 20 io port: [0x6f60-0x6f7f]
[    0.298845] pci 0000:00:1a.1: reg 20 io port: [0x6f80-0x6f9f]
[    0.298925] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
[    0.298995] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.299001] pci 0000:00:1a.7: PME# disabled
[    0.299061] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6ffc000-0xf6ffffff]
[    0.299130] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.299135] pci 0000:00:1b.0: PME# disabled
[    0.299232] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.299238] pci 0000:00:1c.0: PME# disabled
[    0.299338] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.299343] pci 0000:00:1c.1: PME# disabled
[    0.299445] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.299450] pci 0000:00:1c.3: PME# disabled
[    0.299552] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.299557] pci 0000:00:1c.5: PME# disabled
[    0.299628] pci 0000:00:1d.0: reg 20 io port: [0x6f00-0x6f1f]
[    0.299700] pci 0000:00:1d.1: reg 20 io port: [0x6f20-0x6f3f]
[    0.299775] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
[    0.299853] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
[    0.299924] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.299930] pci 0000:00:1d.7: PME# disabled
[    0.300120] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.300124] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.300129] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.300136] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.300140] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0300 (mask 003f)
[    0.300233] pci 0000:00:1f.2: reg 10 io port: [0x6e70-0x6e77]
[    0.300242] pci 0000:00:1f.2: reg 14 io port: [0x6e78-0x6e7b]
[    0.300251] pci 0000:00:1f.2: reg 18 io port: [0x6e80-0x6e87]
[    0.300259] pci 0000:00:1f.2: reg 1c io port: [0x6e88-0x6e8b]
[    0.300268] pci 0000:00:1f.2: reg 20 io port: [0x6ea0-0x6ebf]
[    0.300277] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf6ffb800-0xf6ffbfff]
[    0.300325] pci 0000:00:1f.2: PME# supported from D3hot
[    0.300330] pci 0000:00:1f.2: PME# disabled
[    0.300366] pci 0000:00:1f.3: reg 10 32bit mmio: [0xf6ffb700-0xf6ffb7ff]
[    0.300395] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.300467] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[    0.300475] pci 0000:01:00.0: reg 14 io port: [0xee00-0xeeff]
[    0.300484] pci 0000:01:00.0: reg 18 32bit mmio: [0xf6df0000-0xf6dfffff]
[    0.300511] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.300543] pci 0000:01:00.0: supports D1 D2
[    0.300595] pci 0000:01:00.1: reg 10 32bit mmio: [0xf6dec000-0xf6deffff]
[    0.300664] pci 0000:01:00.1: supports D1 D2
[    0.300743] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.300747] pci 0000:00:01.0: bridge 32bit mmio: [0xf6d00000-0xf6efffff]
[    0.300752] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.301039] pci 0000:0c:00.0: reg 10 64bit mmio: [0xf6cfc000-0xf6cfffff]
[    0.301266] pci 0000:0c:00.0: supports D1 D2
[    0.301268] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.301280] pci 0000:0c:00.0: PME# disabled
[    0.301428] pci 0000:00:1c.1: bridge 32bit mmio: [0xf6c00000-0xf6cfffff]
[    0.301502] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.301508] pci 0000:00:1c.3: bridge 32bit mmio: [0xf6a00000-0xf6bfffff]
[    0.301517] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf0000000-0xf01fffff]
[    0.301657] pci 0000:09:00.0: reg 10 64bit mmio: [0xf69f0000-0xf69fffff]
[    0.301827] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.301836] pci 0000:09:00.0: PME# disabled
[    0.301931] pci 0000:00:1c.5: bridge 32bit mmio: [0xf6900000-0xf69fffff]
[    0.301987] pci 0000:03:01.0: reg 10 32bit mmio: [0xf68ff800-0xf68fffff]
[    0.302054] pci 0000:03:01.0: supports D1 D2
[    0.302056] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.302061] pci 0000:03:01.0: PME# disabled
[    0.302109] pci 0000:03:01.1: reg 10 32bit mmio: [0xf68ff500-0xf68ff5ff]
[    0.302176] pci 0000:03:01.1: supports D1 D2
[    0.302178] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.302183] pci 0000:03:01.1: PME# disabled
[    0.302230] pci 0000:03:01.2: reg 10 32bit mmio: [0xf68ff600-0xf68ff6ff]
[    0.302298] pci 0000:03:01.2: supports D1 D2
[    0.302300] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.302305] pci 0000:03:01.2: PME# disabled
[    0.302354] pci 0000:03:01.3: reg 10 32bit mmio: [0xf68ff700-0xf68ff7ff]
[    0.302420] pci 0000:03:01.3: supports D1 D2
[    0.302422] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.302428] pci 0000:03:01.3: PME# disabled
[    0.302504] pci 0000:00:1e.0: transparent bridge
[    0.302512] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6800000-0xf68fffff]
[    0.302558] pci_bus 0000:00: on NUMA node 0
[    0.302563] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.302820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.302936] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.303010] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.303083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.303158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.303233] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.314143] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *4
[    0.314264] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.314382] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *3
[    0.314485] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11) *0, disabled.
[    0.314605] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.314727] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.314848] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.314955] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.315143] SCSI subsystem initialized
[    0.315163] libata version 3.00 loaded.
[    0.315163] usbcore: registered new interface driver usbfs
[    0.315163] usbcore: registered new interface driver hub
[    0.315163] usbcore: registered new device driver usb
[    0.315163] ACPI: WMI: Mapper loaded
[    0.315163] PCI: Using ACPI for IRQ routing
[    0.324009] Bluetooth: Core ver 2.15
[    0.324023] NET: Registered protocol family 31
[    0.324023] Bluetooth: HCI device and connection manager initialized
[    0.324023] Bluetooth: HCI socket layer initialized
[    0.324023] NetLabel: Initializing
[    0.324023] NetLabel:  domain hash size = 128
[    0.324023] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.324034] NetLabel:  unlabeled traffic allowed by default
[    0.324064] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.324070] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.340008] pnp: PnP ACPI init
[    0.340017] ACPI: bus type pnp registered
[    0.358573] pnp 00:0a: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.358578] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.358671] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.358674] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.358677] pnp 00:0b: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.358681] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.379328] pnp: PnP ACPI: found 13 devices
[    0.379330] ACPI: ACPI bus type pnp unregistered
[    0.379334] PnPBIOS: Disabled by ACPI PNP
[    0.379346] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    0.379353] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.379359] system 00:0a: ioport range 0x900-0x97f has been reserved
[    0.379362] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.379369] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.379372] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.379374] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    0.379377] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.379384] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.379387] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.379390] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.379393] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.379396] system 00:0c: iomem range 0x100000-0x7fe5c7ff could not be reserved
[    0.379399] system 00:0c: iomem range 0x7fe5c800-0x7fefffff has been reserved
[    0.379402] system 00:0c: iomem range 0x7ff00000-0x7fffffff has been reserved
[    0.379405] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved
[    0.379408] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.379412] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.379415] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.379418] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.379421] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.379424] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.379427] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.379430] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.379433] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.379436] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.414110] AppArmor: AppArmor Filesystem Enabled
[    0.414192] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.414195] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.414200] pci 0000:00:01.0:   MEM window: 0xf6d00000-0xf6efffff
[    0.414204] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.414209] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.414211] pci 0000:00:1c.0:   IO window: disabled
[    0.414218] pci 0000:00:1c.0:   MEM window: disabled
[    0.414223] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.414228] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.414230] pci 0000:00:1c.1:   IO window: disabled
[    0.414237] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff
[    0.414242] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.414247] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.414251] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.414258] pci 0000:00:1c.3:   MEM window: 0xf6a00000-0xf6bfffff
[    0.414264] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.414272] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.414274] pci 0000:00:1c.5:   IO window: disabled
[    0.414281] pci 0000:00:1c.5:   MEM window: 0xf6900000-0xf69fffff
[    0.414286] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.414292] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.414294] pci 0000:00:1e.0:   IO window: disabled
[    0.414300] pci 0000:00:1e.0:   MEM window: 0xf6800000-0xf68fffff
[    0.414305] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.414317]   alloc irq_desc for 16 on node -1
[    0.414319]   alloc kstat_irqs on node -1
[    0.414324] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.414329] pci 0000:00:01.0: setting latency timer to 64
[    0.414338] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.414343] pci 0000:00:1c.0: setting latency timer to 64
[    0.414352]   alloc irq_desc for 17 on node -1
[    0.414354]   alloc kstat_irqs on node -1
[    0.414358] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.414363] pci 0000:00:1c.1: setting latency timer to 64
[    0.414372]   alloc irq_desc for 19 on node -1
[    0.414374]   alloc kstat_irqs on node -1
[    0.414377] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.414383] pci 0000:00:1c.3: setting latency timer to 64
[    0.414392] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.414398] pci 0000:00:1c.5: setting latency timer to 64
[    0.414407] pci 0000:00:1e.0: setting latency timer to 64
[    0.414412] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.414414] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.414417] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.414420] pci_bus 0000:01: resource 1 mem: [0xf6d00000-0xf6efffff]
[    0.414422] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.414425] pci_bus 0000:0c: resource 1 mem: [0xf6c00000-0xf6cfffff]
[    0.414428] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff]
[    0.414430] pci_bus 0000:0d: resource 1 mem: [0xf6a00000-0xf6bfffff]
[    0.414433] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.414436] pci_bus 0000:09: resource 1 mem: [0xf6900000-0xf69fffff]
[    0.414438] pci_bus 0000:03: resource 1 mem: [0xf6800000-0xf68fffff]
[    0.414441] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.414443] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.414477] NET: Registered protocol family 2
[    0.414575] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.414897] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.415387] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.415631] TCP: Hash tables configured (established 131072 bind 65536)
[    0.415634] TCP reno registered
[    0.415702] NET: Registered protocol family 1
[    0.415760] Trying to unpack rootfs image as initramfs...
[    0.505488] Switched to high resolution mode on CPU 1
[    0.508001] Switched to high resolution mode on CPU 0
[    1.828337] Freeing initrd memory: 5620k freed
[    1.831418] Simple Boot Flag at 0x79 set to 0x1
[    1.831604] cpufreq-nforce2: No nForce2 chipset.
[    1.831634] Scanning for low memory corruption every 60 seconds
[    1.831742] audit: initializing netlink socket (disabled)
[    1.831764] type=2000 audit(1258232740.828:1): initialized
[    1.840339] highmem bounce pool size: 64 pages
[    1.840344] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.841849] VFS: Disk quotas dquot_6.5.2
[    1.841912] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.842456] fuse init (API version 7.12)
[    1.842545] msgmni has been set to 1705
[    1.842756] alg: No test for stdrng (krng)
[    1.842769] io scheduler noop registered
[    1.842771] io scheduler anticipatory registered
[    1.842773] io scheduler deadline registered
[    1.842816] io scheduler cfq registered (default)
[    1.842971] pci 0000:01:00.0: Boot video device
[    1.843112]   alloc irq_desc for 24 on node -1
[    1.843114]   alloc kstat_irqs on node -1
[    1.843124] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    1.843131] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.843272]   alloc irq_desc for 25 on node -1
[    1.843274]   alloc kstat_irqs on node -1
[    1.843284] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    1.843296] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.843464]   alloc irq_desc for 26 on node -1
[    1.843466]   alloc kstat_irqs on node -1
[    1.843475] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    1.843487] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.843652]   alloc irq_desc for 27 on node -1
[    1.843654]   alloc kstat_irqs on node -1
[    1.843663] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    1.843675] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.843845]   alloc irq_desc for 28 on node -1
[    1.843846]   alloc kstat_irqs on node -1
[    1.843856] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    1.843868] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.843983] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.844134] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.844294] ACPI: AC Adapter [AC] (on-line)
[    1.844371] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.849211] ACPI: Lid Switch [LID]
[    1.849257] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.849263] ACPI: Power Button [PBTN]
[    1.849306] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.849308] ACPI: Sleep Button [SBTN]
[    1.849959] ACPI: SSDT 7fe5d538 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    1.850451] ACPI: SSDT 7fe5cece 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    1.850804] Monitor-Mwait will be used to enter C-1 state
[    1.850829] Monitor-Mwait will be used to enter C-2 state
[    1.850851] Monitor-Mwait will be used to enter C-3 state
[    1.850859] Marking TSC unstable due to TSC halts in idle
[    1.850878] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.850903] processor LNXCPU:00: registered as cooling_device0
[    1.850907] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.851240] ACPI: SSDT 7fe5d77c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    1.851552] ACPI: SSDT 7fe5d4b3 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    1.852014] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.852039] processor LNXCPU:01: registered as cooling_device1
[    1.852043] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.866294] thermal LNXTHERM:01: registered as thermal_zone0
[    1.866303] ACPI: Thermal Zone [THM] (52 C)
[    1.866368] isapnp: Scanning for PnP cards...
[    1.926169] ACPI: Battery Slot [BAT0] (battery present)
[    2.221589] isapnp: No Plug & Play device found
[    2.222703] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.224062] brd: module loaded
[    2.224517] loop: module loaded
[    2.224586] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.224659] ahci 0000:00:1f.2: version 3.0
[    2.224673] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.224707]   alloc irq_desc for 29 on node -1
[    2.224709]   alloc kstat_irqs on node -1
[    2.224720] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    2.224798] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    2.224802] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    2.224808] ahci 0000:00:1f.2: setting latency timer to 64
[    2.241063] scsi0 : ahci
[    2.241148] scsi1 : ahci
[    2.241207] scsi2 : ahci
[    2.241425] ata1: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffb900 irq 29
[    2.241429] ata2: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffb980 irq 29
[    2.241433] ata3: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffba00 irq 29
[    2.242384] Fixed MDIO Bus: probed
[    2.242420] PPP generic driver version 2.4.2
[    2.242509] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.242530]   alloc irq_desc for 22 on node -1
[    2.242533]   alloc kstat_irqs on node -1
[    2.242538] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.242549] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.242552] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.242598] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.246509] ehci_hcd 0000:00:1a.7: debug port 1
[    2.246516] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.246530] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.261013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.261084] usb usb1: configuration #1 chosen from 1 choice
[    2.261113] hub 1-0:1.0: USB hub found
[    2.261121] hub 1-0:1.0: 4 ports detected
[    2.261183]   alloc irq_desc for 20 on node -1
[    2.261185]   alloc kstat_irqs on node -1
[    2.261190] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.261199] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.261203] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.261232] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.265155] ehci_hcd 0000:00:1d.7: debug port 1
[    2.265163] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.265178] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    2.280018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.280089] usb usb2: configuration #1 chosen from 1 choice
[    2.280115] hub 2-0:1.0: USB hub found
[    2.280122] hub 2-0:1.0: 6 ports detected
[    2.280187] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.280204] uhci_hcd: USB Universal Host Controller Interface driver
[    2.280224] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.280232] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.280235] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.280272] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.280301] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[    2.280379] usb usb3: configuration #1 chosen from 1 choice
[    2.280408] hub 3-0:1.0: USB hub found
[    2.280414] hub 3-0:1.0: 2 ports detected
[    2.280463]   alloc irq_desc for 21 on node -1
[    2.280465]   alloc kstat_irqs on node -1
[    2.280470] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.280476] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.280480] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.280509] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.280544] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[    2.280624] usb usb4: configuration #1 chosen from 1 choice
[    2.280650] hub 4-0:1.0: USB hub found
[    2.280657] hub 4-0:1.0: 2 ports detected
[    2.280706] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.280713] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.280717] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.280745] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.280774] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[    2.280854] usb usb5: configuration #1 chosen from 1 choice
[    2.280879] hub 5-0:1.0: USB hub found
[    2.280885] hub 5-0:1.0: 2 ports detected
[    2.280933] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.280940] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.280944] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.280973] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.281012] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[    2.281092] usb usb6: configuration #1 chosen from 1 choice
[    2.281118] hub 6-0:1.0: USB hub found
[    2.281125] hub 6-0:1.0: 2 ports detected
[    2.281178] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.281185] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.281189] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.281223] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.281251] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    2.281329] usb usb7: configuration #1 chosen from 1 choice
[    2.281355] hub 7-0:1.0: USB hub found
[    2.281362] hub 7-0:1.0: 2 ports detected
[    2.281469] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.288609] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.288614] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.288664] mice: PS/2 mouse device common for all mice
[    2.288772] rtc_cmos 00:04: RTC can wake from S4
[    2.288803] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.288836] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.288933] device-mapper: uevent: version 1.0.3
[    2.289035] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.289124] device-mapper: multipath: version 1.1.0 loaded
[    2.289127] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.289249] EISA: Probing bus 0 at eisa.0
[    2.289257] Cannot allocate resource for EISA slot 1
[    2.289287] EISA: Detected 0 cards.
[    2.289473] cpuidle: using governor ladder
[    2.289595] cpuidle: using governor menu
[    2.290100] TCP cubic registered
[    2.290250] NET: Registered protocol family 10
[    2.290713] lo: Disabled Privacy Extensions
[    2.291057] NET: Registered protocol family 17
[    2.291074] Bluetooth: L2CAP ver 2.13
[    2.291075] Bluetooth: L2CAP socket layer initialized
[    2.291078] Bluetooth: SCO (Voice Link) ver 0.6
[    2.291080] Bluetooth: SCO socket layer initialized
[    2.291125] Bluetooth: RFCOMM TTY layer initialized
[    2.291127] Bluetooth: RFCOMM socket layer initialized
[    2.291129] Bluetooth: RFCOMM ver 1.11
[    2.291568] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.291641] Using IPI No-Shortcut mode
[    2.291698] PM: Resume from disk failed.
[    2.291710] registered taskstats version 1
[    2.291833]   Magic number: 1:823:95
[    2.291930] rtc_cmos 00:04: setting system clock to 2009-11-14 21:05:41 UTC (1258232741)
[    2.291933] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.291935] EDD information not available.
[    2.500062] Clocksource tsc unstable (delta = -197618065 ns)
[    2.564072] ata3: SATA link down (SStatus 0 SControl 300)
[    2.564108] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.568430] ata1.00: ATA-8: SAMSUNG HM160HI, HH100-11, max UDMA7
[    2.568437] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    2.568522] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.574509] ata1.00: configured for UDMA/133
[    2.581539] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7640S, HD14, max UDMA/100
[    2.588245] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HI  HH10 PQ: 0 ANSI: 5
[    2.588374] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.588413] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.588458] sd 0:0:0:0: [sda] Write Protect is off
[    2.588461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.588484] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.588605]  sda:
[    2.595047] ata2.00: configured for UDMA/100
[    2.608082] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
[    2.608087] ata2: irq_stat 0x40000001
[    2.608096] ata2: hard resetting link
[    2.684060] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    2.818465] usb 2-3: configuration #1 chosen from 1 choice
[    2.928074] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    3.067841] usb 2-5: configuration #1 chosen from 1 choice
[    3.224044]  sda1 sda2 < sda5 >
[    3.255977] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.308057] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    3.332090] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.358545] ata2.00: configured for UDMA/100
[    3.359033] ata2: EH complete
[    3.360218] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7640S HD14 PQ: 0 ANSI: 5
[    3.365990] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    3.365996] Uniform CD-ROM driver Revision: 3.20
[    3.366132] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.366211] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.366265] Freeing unused kernel memory: 540k freed
[    3.366623] Write protecting the kernel text: 4568k
[    3.366681] Write protecting the kernel read-only data: 1836k
[    3.490903] usb 3-1: configuration #1 chosen from 1 choice
[    3.494605] hub 3-1:1.0: USB hub found
[    3.497420] hub 3-1:1.0: 3 ports detected
[    3.503365] Linux agpgart interface v0.103
[    3.506866] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.506884] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    3.528137] tg3.c:v3.99 (April 20, 2009)
[    3.528163] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.528176] tg3 0000:09:00.0: setting latency timer to 64
[    3.536556] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/device:2c/input/input5
[    3.536595] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    3.546243] tg3 0000:09:00.0: PME# disabled
[    3.575848] ohci1394 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.589769] Initializing USB Mass Storage driver...
[    3.589868] scsi3 : SCSI emulation for USB Mass Storage devices
[    3.589967] usbcore: registered new interface driver usb-storage
[    3.589970] USB Mass Storage support registered.
[    3.599923] usb-storage: device found at 2
[    3.599926] usb-storage: waiting for device to settle before scanning
[    3.621436] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    3.629620] [drm] Initialized drm 1.1.0 20060810
[    3.634065] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f68ff800-f68fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.646026] [drm] radeon default to kernel modesetting DISABLED.
[    3.647258] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.647264] pci 0000:01:00.0: setting latency timer to 64
[    3.647408] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    3.802376] usb 3-1.1: new full speed USB device using uhci_hcd and address 3
[    3.924482] usb 3-1.1: configuration #1 chosen from 1 choice
[    3.931673] usbcore: registered new interface driver hiddev
[    3.934709] input: HID 413c:8157 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input6
[    3.934772] generic-usb 0003:413C:8157.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8157] on usb-0000:00:1a.0-1.1/input0
[    3.934785] usbcore: registered new interface driver usbhid
[    3.934788] usbhid: v2.6:USB HID core driver
[    4.001381] usb 3-1.2: new full speed USB device using uhci_hcd and address 4
[    4.123485] usb 3-1.2: configuration #1 chosen from 1 choice
[    4.126740] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:21:70:74:7f:ae
[    4.126744] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    4.126747] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    4.126749] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.130779] input: HID 413c:8158 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input7
[    4.130854] generic-usb 0003:413C:8158.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:1a.0-1.2/input0
[    4.720588] xor: automatically using best checksumming function: pIII_sse
[    4.737009]    pIII_sse  :  7320.000 MB/sec
[    4.737011] xor: using function: pIII_sse (7320.000 MB/sec)
[    4.739496] device-mapper: dm-raid45: initialized v0.2594b
[    4.885283] kjournald starting.  Commit interval 5 seconds
[    4.885303] EXT3-fs: mounted filesystem with writeback data mode.
[    4.909402] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc0000d406870]
[    8.596466] usb-storage: device scan complete
[    8.597284] scsi 3:0:0:0: Direct-Access     UDISK    PDU01_4G 84I2.0  0.00 PQ: 0 ANSI: 2
[    8.597681] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    8.598492] sd 3:0:0:0: [sdb] 7897088 512-byte logical blocks: (4.04 GB/3.76 GiB)
[    8.599254] sd 3:0:0:0: [sdb] Write Protect is off
[    8.599260] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[    8.599264] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[    8.602405] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[    8.602410]  sdb: sdb1
[    8.661567] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[    8.661571] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[    9.424888] aufs 2-standalone.tree-30-20090727
[    9.439718] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   13.131907] kjournald starting.  Commit interval 5 seconds
[   13.131967] EXT3 FS on loop1, internal journal
[   13.131974] ext3_orphan_cleanup: deleting unreferenced inode 4053
[   13.132163] ext3_orphan_cleanup: deleting unreferenced inode 16
[   13.132227] ext3_orphan_cleanup: deleting unreferenced inode 15
[   13.132236] EXT3-fs: loop1: 3 orphan inodes deleted
[   13.132238] EXT3-fs: recovery complete.
[   13.132553] EXT3-fs: mounted filesystem with writeback data mode.
[   13.198831] aufs test_add:242:exe[955]: uid/gid/perm //filesystem.squashfs 0/0/0755, 1000/1000/0755
[   48.957638] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k 
[   49.204662] udev: starting version 147
[   49.814973] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   49.843089] Linux video capture interface: v2.00
[   49.878382] ip_tables: (C) 2000-2006 Netfilter Core Team
[   49.887166] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:18a0)
[   49.890784] input: Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input8
[   49.905268] usbcore: registered new interface driver uvcvideo
[   49.905273] USB Video Class driver (v0.1.0)
[   50.010240] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   50.010245] Disabling lock debugging due to kernel taint
[   50.032557] [fglrx] Maximum main memory to use for locked dma buffers: 1884 MBytes.
[   50.032929] [fglrx]   vendor: 1002 device: 95c4 count: 1
[   50.034514] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
[   50.034525] pci 0000:01:00.0: setting latency timer to 64
[   50.034754] [fglrx] Kernel PAT support is enabled
[   50.034781] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[   50.050800] sdhci: Secure Digital Host Controller Interface driver
[   50.050803] sdhci: Copyright(c) Pierre Ossman
[   50.147890] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   50.147909]   alloc irq_desc for 18 on node -1
[   50.147911]   alloc kstat_irqs on node -1
[   50.147918] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   50.155989] Registered led device: mmc0::
[   50.156029] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   50.187635] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   50.209366] usb 3-1.3: new full speed USB device using uhci_hcd and address 5
[   50.302706] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[   50.322532] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   50.352508] usb 3-1.3: configuration #1 chosen from 1 choice
[   51.158037] tg3 0000:09:00.0: PME# disabled
[   51.158413]   alloc irq_desc for 30 on node -1
[   51.158416]   alloc kstat_irqs on node -1
[   51.158441] tg3 0000:09:00.0: irq 30 for MSI/MSI-X
[   51.308409] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.942913] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   55.943034] usbcore: registered new interface driver btusb
[   55.975417] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   55.975445] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   56.921480] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[   57.105111] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   57.105115] Bluetooth: BNEP filters: protocol multicast
[   57.152585] Bridge firewalling registered
[   57.933011] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x00bf0700
[   57.933494] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   57.933585] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   57.933652] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   57.934259] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   57.934308] HDA Intel 0000:01:00.1: setting latency timer to 64
[   72.562104] lp: driver loaded but no devices found
[   72.575149] ppdev: user-space parallel port driver
[  106.202705]   alloc irq_desc for 31 on node -1
[  106.202709]   alloc kstat_irqs on node -1
[  106.202723] fglrx_pci 0000:01:00.0: irq 31 for MSI/MSI-X
[  106.203396] [fglrx] Firegl kernel thread PID: 4472
[  106.798405] [fglrx] Gart USWC size:627 M.
[  106.798409] [fglrx] Gart cacheable size:247 M.
[  106.798415] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  106.798418] [fglrx] Reserved FB block: Unshared offset:fe03000, size:1f9000 
[  106.798420] [fglrx] Reserved FB block: Unshared offset:fffc000, size:4000 
[  111.277321] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[  114.645112] CE: hpet increasing min_delta_ns to 15000 nsec
[  132.969126] CE: hpet increasing min_delta_ns to 22500 nsec
[  134.033156] CE: hpet increasing min_delta_ns to 33750 nsec
[  137.500138] CE: hpet increasing min_delta_ns to 50624 nsec
[  234.334845] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[  258.298432] lib80211: common routines for IEEE802.11 drivers
[  258.298436] lib80211_crypt: registered algorithm 'NULL'
[  258.303681] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  258.303701] wl 0000:0c:00.0: setting latency timer to 64
[  258.326715] lib80211_crypt: registered algorithm 'TKIP'
[  258.326877] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[  258.364404] wl 0000:0c:00.0: PCI INT A disabled
[  258.364718] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  258.364742] wl 0000:0c:00.0: setting latency timer to 64
[  258.384735] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[  268.913020] eth1: no IPv6 routers present
```

---

### Post by pytheas22 on 2009-11-14
doi65535: if you type these commands in a terminal, does it have the same effect as the stuff you're doing deactivating and reactivating the driver through the graphical interface:
```

sudo rmmod wl
sudo modprobe wl
sudo ifconfig eth1 up
```

If that works, you can just write a script to do this automatically at boot.

Also, what is the error message you get when you try to deactivate the driver?

---

### Post by doi65535 on 2009-11-15
now, things have changed a little overnight

as such, I had to reinstall ubuntu on the usb stick and I apparently no longer need to have synaptic running in order to be able to disable/enable the sta driver

however, when I run in terminal the above mentioned commands the response is
ERROR: Module does not exist in /proc/modules

then nothing

and then
eth1: ERROR while getting interface flags: No such device

and wireless no longer works, even if I disable/enable the driver by hand

on a subsequent reboot it begins to work if I enable/disable the driver by hand and then turn wireless off and back on from the button on the laptop

i'll try again the fixes from post #2, since the situation has changed, and keep you informed. oh one difference from before: this time I did not enable fglrx, left it for later since it apparently works out of the box.



the error I got before when synaptic had to be open first was something about install files archive() if I remember correctly, sorry for the imprecision


edit: echo wl | sudo tee -a /etc/modules did not do any good
and the disable/enable of the driver no longer works, I get a crash report could not be able to tell what it was about. removed the entry from /etc/modules and starts to work again if disabled/enabled by hand

might any of these have to do with the fact that I am running from a usb stick as a livecd instead of it being installed on the stick itsef?

SOLVED: well, it appears this was the case. I installed ubuntu on the stick, as opposed to running live from it, tried installing bcwl-kernel-source package and afterwards it started working as advertised. thanks for your input!

---

