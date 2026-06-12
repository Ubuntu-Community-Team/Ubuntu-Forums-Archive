---
title: "Help with LIRC"
date: 2008-06-22
forum: Mythbuntu
---

### Post by mark467 on 2008-06-22
I think I have my remote set up right based on all the help from the forums, but I dont think LIRC is working right.
Can someone walk me through getting the right info to post to show if it is lirc or something else wrong. I am new to linux so be specific on commands....

thanks

---

### Post by vanhoja on 2008-06-22
Mark467...  I've been playing around with MythTV and Ubuntu Linux for a little bit now (2+ yrs), but haven't really felt qualified to offer advice... As of late, I've been wrangling with LIRC quite a bit in Mythbuntu 8.04, so I wouldn't mind helping out with what I've been able to figure out.:cool:

To get started, what we'll need to know is:
[LIST=1]
[*]What make/model of remote are you trying to use?
[*]Which version of Ubuntu or Mythbuntu are you running?
[*]If you've tried using the Mythbuntu Control Centre's LIRC generator, what's in your hardware.conf and lircd.conf files? You can find these in /etc/lirc; just double-click the icon if you're in a File Manager window or type *nano /etc/lirc/hardware.conf* and copy/paste the output into your reply (Control-X gets you out of *nano*).
[*]If you type *irw *in a terminal and press a few buttons on the remote, do you see any code pop up in a new line? (Use Control-C to get out of *irw* and back to a command prompt.)
[/LIST]

What we're looking for is to see if the remote's drivers are setup (hardware.conf) and if it's looking for the right codes coming in from the remote receiver (lircd.conf and the output from irw).  This information should get the ball rolling.

>>vanhoja

---

### Post by nasha on 2008-06-22
If your new to forums, i suggest you take a look here and develop some forum etiquette. You haven't given anybody any information about your problem, so you cant expect them to help you.

[HTML]http://ubuntuforums.org/showthread.php?t=736528[/HTML]

---

### Post by mark467 on 2008-06-23
Ok here is what I have:

[http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Vista+Companion/Pinnacle+Remote+Kit+for+Windows+Media+Center.htm](http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Vista+Companion/Pinnacle+Remote+Kit+for+Windows+Media+Center.htm)

Also I followed these instructions

 Re: Lirc with mceusb2 driving me insane :(
I was able to get my remote working with these instructions. I actually use an older MCE remote with the Pinnacle receiver. The remote included with the Pinnacle receiver also works. Here is what I did:

Step 1) Verify the receiver you now have. Run "lsusb" and look for a line like this:
Code:

Bus 002 Device 002: ID 2304:0225 Pinnacle Systems, Inc. [hex]

Important part is 2304:0225
The ID needs to be 2304:0225. Other receivers may work, but I don't know about them.

Step 2) Down load lirc. Go to the [www.lirc.org](www.lirc.org) website and download a CVS snapshot. (As of 03-13-2008 0.8.3pre1 is the newest.)

Step 3) Extract the snapshot (tar -jxvf lirc-0.8.3pre1.tar.bz2) This should create a new directory called lirc-0.8.3pre1.

Step 4) Patch the file with the new info. I used vi from the command line, but any text editor will work. i.e. gedit, kate, etc. Here is exactly what I did:
Change to directory and patch file. cd lirc-0.8.3pre1/drivers/lirc_mceusb2. Run 'ls' and make sure the lirc_mceusb2.c file is in the current directory. Run 'vi lirc_mceusb2.c'. Search for a line that says vendor section. It will look like this:
Code:

#define VENDOR_MITSUMI          0x03ee
#define VENDOR_TOPSEED          0x1784
#define VENDOR_RICAVISION       0x179d
#define VENDOR_ITRON            0x195d
#define VENDOR_FIC              0x1509
#define VENDOR_LG               0x043e
#define VENDOR_MICROSOFT        0x045e
#define VENDOR_FORMOSA          0x147a
#define VENDOR_FINTEK           0x1934
#define VENDOR_PINNACLE         0x2304

The last line is the new one I added.
The next section of the file looks like this:
Code:

        /* Microsoft MCE Infrared Transceiver */
        { USB_DEVICE(VENDOR_MICROSOFT, 0x00a0) },
        /* Formosa eHome Infrared Transceiver */
        { USB_DEVICE(VENDOR_FORMOSA, 0xe015) },
        /* Fintek eHome Infrared Transceiver */
        { USB_DEVICE(VENDOR_FINTEK, 0x1934) },
        /* Pinnacle Windows Vista Transceiver */
        { USB_DEVICE(VENDOR_PINNACLE, 0x0225) },
        /* Terminating entry */
        { }

I added the two lines with the word Pinnacle in them.

Search through the file for this section:
Code:

                       switch (ir->buf_in[i]) {
                        /* data headers */
                        case 0x90:
                        case 0x8F:
                        case 0x8E:
                        case 0x8D:
                        case 0x8C:
                        case 0x8B:
                        case 0x8A:
                        case 0x89:
                        case 0x88:
                        case 0x87:

I added the "case 0x90" line.

Save and exit. In vi use ":wq".

Step 5) Recompile lirc. I had to add build-essential and linux-headers-2.6.22-14-generic.
"sudo apt-get install build-essential linux-headers-2.6.22-14-generic" I am on amd64 so i386 may be different. Once you have the needed packages run ./configure from the lirc-0.8.3pre1 directory. For option 1 choose USB Devices->Windows Media Center Remote new version (older version). Then "save and run configure"

Step 6) Once configure finishes it will say to run make and make install. Run make with "make". Once that finishes run make install. "sudo make install" This will install the new kernel modules and the new lirc daemon under /usr/local/bin/

Step 7) You can reboot or just stop Lirc, remove the kernel modules, and start lirc back up.
sudo /etc/init.d/lirc stop
sudo rmmod lirc_mceusb2
sudo rmmod lirc_dev
sudo /etc/init.d/lirc start


below are current logs and confs

Mythbuntu 8.04

mythtv-common:
  Installed: 0.21.0+fixes16838-0ubuntu3
  Candidate: 0.21.0+fixes16838-0ubuntu3.1
  Version table:
     0.21.0+fixes16838-0ubuntu3.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
 *** 0.21.0+fixes16838-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
        100 /var/lib/dpkg/status

[COLOR="Red"]FORNTENDLOG[/COLOR]

2008-06-23 06:30:52.929 Starting update of NDFD-6_day
2008-06-23 06:30:56.104 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.$
2008-06-23 06:45:51.689 Starting update of BBC-Current-XML
2008-06-23 06:45:52.547 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbccu$
2008-06-23 06:45:52.945 Starting update of NDFD-6_day
2008-06-23 06:45:55.772 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.$
2008-06-23 07:00:52.961 Starting update of NDFD-6_day
2008-06-23 07:00:56.882 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.$

(gksudo:8534): Gtk-WARNING **: Unable to locate theme engine in module_path: "p$

(gksudo:8534): Gtk-WARNING **: Unable to locate theme engine in module_path: "p$

(gksudo:8534): Gtk-WARNING **: Unable to locate theme engine in module_path: "p$
^MReading package lists... 0%^M^MReading package lists... 100%^M^MReading packa$
^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 0%^M^MBuilding $
^MReading state information... 0%^M^MReading state information... 0%^M^MReading$
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:205: GtkWarning$
  gtk.main()

[COLOR="Red"]DMESG[/COLOR]

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4d80
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6DC0 checksum 0
[    0.000000] ACPI: RSDP 000F6DC0, 0014 (r0 P4M800)
[    0.000000] ACPI: RSDT 3FFF3040, 002C (r1 P4M800 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF30C0, 0074 (r1 P4M800 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF3180, 53AC (r1 P4M800 AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF8580, 0068 (r1 P4M800 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=5f287288-9b68-416b-9bbb-be6bb0c24388 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2533.448 MHz processor.
[   22.389760] Console: colour VGA+ 80x25
[   22.389765] console [tty0] enabled
[   22.390446] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.391122] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.429015] Memory: 1026880k/1048512k available (2157k kernel code, 20916k reserved, 998k data, 364k init, 131008k highmem)
[   22.429025] virtual kernel memory layout:
[   22.429026]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.429027]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.429028]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.429029]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.429031]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   22.429032]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   22.429033]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   22.429037] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.429096] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   22.509094] Calibrating delay using timer specific routine.. 5073.61 BogoMIPS (lpj=10147232)
[   22.509130] Security Framework initialized
[   22.509141] SELinux:  Disabled at boot.
[   22.509160] AppArmor: AppArmor initialized
[   22.509165] Failure registering capabilities with primary security module.
[   22.509175] Mount-cache hash table entries: 512
[   22.509357] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   22.509372] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   22.509375] CPU: L2 cache: 512K
[   22.509379] CPU: Hyper-Threading is disabled
[   22.509381] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   22.509396] Compat vDSO mapped to ffffe000.
[   22.509414] Checking 'hlt' instruction... OK.
[   22.525542] SMP alternatives: switching to UP code
[   22.527321] Freeing SMP alternatives: 11k freed
[   22.527468] Early unpacking initramfs... done
[   22.883071] ACPI: Core revision 20070126
[   22.883142] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.887140] CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 07
[   22.887188] Total of 1 processors activated (5073.61 BogoMIPS).
[   22.887942] ENABLING IO-APIC IRQs
[   22.888272] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.032935] Brought up 1 CPUs
[   23.032996] CPU0 attaching sched-domain:
[   23.033000]  domain 0: span 01
[   23.033002]   groups: 01
[   23.033219] net_namespace: 64 bytes
[   23.033233] Booting paravirtualized kernel on bare hardware
[   23.033902] Time: 18:44:59  Date: 06/22/08
[   23.033934] NET: Registered protocol family 16
[   23.034185] EISA bus registered
[   23.034222] ACPI: bus type pci registered
[   23.041748] PCI: PCI BIOS revision 2.10 entry at 0xfb3d0, last bus=1
[   23.041751] PCI: Using configuration type 1
[   23.041752] Setting up standard PCI resources
[   23.050647] ACPI: EC: Look up EC in DSDT
[   23.056839] ACPI: Interpreter enabled
[   23.056843] ACPI: (supports S0 S1 S4 S5)
[   23.056860] ACPI: Using IOAPIC for interrupt routing
[   23.064329] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.065574] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.111066] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   23.111255] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   23.111444] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[   23.111615] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.111782] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.111941] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.112100] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.112260] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.112462] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   23.112643] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   23.112823] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   23.113042] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[   23.113184] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.113226] pnp: PnP ACPI init
[   23.113236] ACPI: bus type pnp registered
[   23.117737] pnp: PnP ACPI: found 13 devices
[   23.117740] ACPI: ACPI bus type pnp unregistered
[   23.117746] PnPBIOS: Disabled by ACPI PNP
[   23.118036] PCI: Using ACPI for IRQ routing
[   23.118041] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.140848] NET: Registered protocol family 8
[   23.140850] NET: Registered protocol family 20
[   23.140934] AppArmor: AppArmor Filesystem Enabled
[   23.144836] Time: tsc clocksource has been installed.
[   23.152880] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   23.152884] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   23.152887] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   23.152890] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   23.152893] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   23.152896] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   23.152899] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   23.152901] system 00:00: iomem range 0x100000-0x3ffeffff could not be reserved
[   23.152904] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   23.152907] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   23.152910] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
[   23.152918] system 00:02: ioport range 0x400-0x47f has been reserved
[   23.152921] system 00:02: ioport range 0x500-0x50f has been reserved
[   23.152928] system 00:03: ioport range 0xb78-0xb7b has been reserved
[   23.152931] system 00:03: ioport range 0xf78-0xf7b has been reserved
[   23.152933] system 00:03: ioport range 0xa78-0xa7b has been reserved
[   23.152936] system 00:03: ioport range 0xe78-0xe7b has been reserved
[   23.152938] system 00:03: ioport range 0xbbc-0xbbf has been reserved
[   23.152941] system 00:03: ioport range 0xfbc-0xfbf has been reserved
[   23.152944] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   23.152946] system 00:03: ioport range 0x290-0x297 has been reserved
[   23.183446] PCI: Bridge: 0000:00:01.0
[   23.183449]   IO window: disabled.
[   23.183454]   MEM window: f8000000-f9ffffff
[   23.183458]   PREFETCH window: f0000000-f7ffffff
[   23.183478] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.183492] NET: Registered protocol family 2
[   23.220900] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.221315] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.222385] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.223028] TCP: Hash tables configured (established 131072 bind 65536)
[   23.223033] TCP reno registered
[   23.233001] checking if image is initramfs... it is
[   23.684616] Switched to high resolution mode on CPU 0
[   23.927002] Freeing initrd memory: 7815k freed
[   23.927670] audit: initializing netlink socket (disabled)
[   23.927689] audit(1214160299.392:1): initialized
[   23.927904] highmem bounce pool size: 64 pages
[   23.930099] VFS: Disk quotas dquot_6.5.1
[   23.930192] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.930353] io scheduler noop registered
[   23.930356] io scheduler anticipatory registered
[   23.930358] io scheduler deadline registered
[   23.930372] io scheduler cfq registered (default)
[   23.930388] PCI: VIA PCI bridge detected. Disabling DAC.
[   23.930458] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   23.930467] Boot video device is 0000:01:00.0
[   23.930808] isapnp: Scanning for PnP cards...
[   24.285046] isapnp: No Plug & Play device found
[   24.319251] Real Time Clock Driver v1.12ac
[   24.319373] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.319500] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.319653] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.320425] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.320814] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.321798] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.321884] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   24.322009] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.322410] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.322416] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.328405] mice: PS/2 mouse device common for all mice
[   24.328557] EISA: Probing bus 0 at eisa.0
[   24.328596] EISA: Detected 0 cards.
[   24.328601] cpuidle: using governor ladder
[   24.328603] cpuidle: using governor menu
[   24.328711] NET: Registered protocol family 1
[   24.328746] Using IPI No-Shortcut mode
[   24.328785] registered taskstats version 1
[   24.328902]   Magic number: 12:247:747
[   24.329051] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   24.329054] EDD information not available.
[   24.329458] Freeing unused kernel memory: 364k freed
[   24.360230] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   25.583099] fuse init (API version 7.9)
[   25.600861] ACPI: Fan [FAN] (on)
[   25.607665] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.609584] ACPI: Thermal Zone [THRM] (29 C)
[   26.332074] SCSI subsystem initialized
[   26.415892] libata version 3.00 loaded.
[   26.435104] usbcore: registered new interface driver usbfs
[   26.435134] usbcore: registered new interface driver hub
[   26.438123] sata_via 0000:00:0f.0: version 2.3
[   26.438417] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   26.438426] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   26.438479] sata_via 0000:00:0f.0: routed to hard irq line 11
[   26.447940] usbcore: registered new device driver usb
[   26.471365] scsi0 : sata_via
[   26.478514] USB Universal Host Controller Interface driver v3.0
[   26.491070] scsi1 : sata_via
[   26.492622] ata1: SATA max UDMA/133 cmd 0xe000 ctl 0xe100 bmdma 0xe400 irq 16
[   26.492626] ata2: SATA max UDMA/133 cmd 0xe200 ctl 0xe300 bmdma 0xe408 irq 16
[   26.511104] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   26.511113] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   26.695003] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   26.906853] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   26.917737] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   26.917804] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   26.920512] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   26.920523] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   26.920536] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   26.920942] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   26.920980] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000e700
[   26.921152] usb usb1: configuration #1 chosen from 1 choice
[   26.921183] hub 1-0:1.0: USB hub found
[   26.921191] hub 1-0:1.0: 2 ports detected
[   27.022970] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   27.022987] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   27.023015] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   27.023040] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000e800
[   27.023177] usb usb2: configuration #1 chosen from 1 choice
[   27.023211] hub 2-0:1.0: USB hub found
[   27.023218] hub 2-0:1.0: 2 ports detected
[   27.126891] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   27.126909] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   27.126938] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   27.126963] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000e900
[   27.127096] usb usb3: configuration #1 chosen from 1 choice
[   27.127124] hub 3-0:1.0: USB hub found
[   27.127132] hub 3-0:1.0: 2 ports detected
[   27.230827] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   27.230845] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   27.230884] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   27.230910] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000ea00
[   27.231042] usb usb4: configuration #1 chosen from 1 choice
[   27.231071] hub 4-0:1.0: USB hub found
[   27.231078] hub 4-0:1.0: 2 ports detected
[   27.334880] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   27.334901] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   27.334936] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   27.334985] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfb000000
[   27.346659] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.346825] usb usb5: configuration #1 chosen from 1 choice
[   27.346855] hub 5-0:1.0: USB hub found
[   27.346864] hub 5-0:1.0: 8 ports detected
[   27.451093] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   27.451104] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
[   27.451417] eth0: VIA Rhine II at 0xfb001000, 00:16:17:11:db:95, IRQ 18.
[   27.452129] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[   27.452254] pata_via 0000:00:0f.1: version 0.3.3
[   27.452276] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   27.453760] scsi2 : pata_via
[   27.454667] scsi3 : pata_via
[   27.456312] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe600 irq 14
[   27.456315] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe608 irq 15
[   27.657078] ata3.00: ATA-7: MAXTOR STM3500630A, 3.AAE, max UDMA/100
[   27.657083] ata3.00: 976773168 sectors, multi 16: LBA48 
[   27.723687] ata3.00: configured for UDMA/100
[   28.058566] ata4.00: ATAPI: SONY    DVD RW DRU-190A, 1.64, max UDMA/66
[   28.246345] ata4.00: configured for UDMA/66
[   28.246495] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM350063 3.AA PQ: 0 ANSI: 5
[   28.248042] scsi 3:0:0:0: CD-ROM            SONY     DVD RW DRU-190A  1.64 PQ: 0 ANSI: 5
[   28.263938] Driver 'sd' needs updating - please use bus_type methods
[   28.264048] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   28.264065] sd 2:0:0:0: [sda] Write Protect is off
[   28.264068] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.264091] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.264152] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   28.264165] sd 2:0:0:0: [sda] Write Protect is off
[   28.264168] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.264189] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.264194]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   28.279403]  sda1 sda2 <<6>usb 5-7: new high speed USB device using ehci_hcd and address 2
[   28.299927]  sda5 >
[   28.300052] sd 2:0:0:0: [sda] Attached SCSI disk
[   28.308247] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   28.308274] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   28.314151] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[   28.314158] Uniform CD-ROM driver Revision: 3.20
[   28.314231] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   28.581721] Attempting manual resume
[   28.581727] swsusp: Resume From Partition 8:5
[   28.581729] PM: Checking swsusp image.
[   28.581968] PM: Resume from disk failed.
[   28.608296] usb 5-7: configuration #1 chosen from 1 choice
[   28.622336] kjournald starting.  Commit interval 5 seconds
[   28.622354] EXT3-fs: mounted filesystem with ordered data mode.
[   29.121663] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   29.312716] usb 4-2: configuration #1 chosen from 1 choice
[   34.125891] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   34.392902] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.501441] Linux agpgart interface v0.102
[   34.541758] agpgart: Detected VIA P4M800 chipset
[   34.552068] agpgart: AGP aperture is 128M @ 0xe8000000
[   34.563539] input: PS2++ Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   34.597953] parport_pc 00:0a: reported by Plug and Play ACPI
[   34.598057] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   34.714801] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.929918] Linux video capture interface: v2.00
[   34.966715] input: Power Button (FF) as /devices/virtual/input/input4
[   34.994579] ACPI: Power Button (FF) [PWRF]
[   34.994662] input: Power Button (CM) as /devices/virtual/input/input5
[   35.026583] ACPI: Power Button (CM) [PWRB]
[   35.026659] input: Sleep Button (CM) as /devices/virtual/input/input6
[   35.058565] ACPI: Sleep Button (CM) [SLPB]
[   35.470339] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   35.470423] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 19
[   35.470495] cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected]
[   35.470498] cx88[0]: TV tuner type 44, Radio tuner type -1
[   35.627999] cx88[0]/0: found at 0000:00:06.0, rev: 5, irq: 19, latency: 32, mmio: 0xfa000000
[   36.077303] tuner 1-0043: chip found @ 0x86 (cx88[0])
[   36.077342] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   36.077345] tuner 1-0043: type set to tda9887
[   36.084223] All bytes are equal. It is not a TEA5767
[   36.084227] tuner 1-0060: chip found @ 0xc0 (cx88[0])
[   36.084247] tuner-simple 1-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[   36.084250] tuner 1-0060: type set to Philips 4 in 1 (ATI
[   36.084253] tuner-simple 1-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[   36.084255] tuner 1-0060: type set to Philips 4 in 1 (ATI
[   36.134775] cx88[0]/0: registered device video0 [v4l2]
[   36.134799] cx88[0]/0: registered device vbi0
[   36.772786] nvidia: module license 'NVIDIA' taints kernel.
[   37.500732] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   37.501046] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   37.605002] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   37.605014] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 21
[   37.605187] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   37.798884] phy0: Selected rate control algorithm 'simple'
[   37.892264] usbcore: registered new interface driver rt73usb
[   40.058298] lp0: using parport0 (interrupt-driven).
[   40.248001] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   40.341249] wlan0: Initial auth_alg=0
[   40.341257] wlan0: authenticate with AP 00:30:bd:f8:92:07
[   40.345388] wlan0: RX authentication from 00:30:bd:f8:92:07 (alg=0 transaction=2 status=0)
[   40.345392] wlan0: authenticated
[   40.345395] wlan0: associate with AP 00:30:bd:f8:92:07
[   40.360148] wlan0: RX AssocResp from 00:30:bd:f8:92:07 (capab=0x1 status=0 aid=4)
[   40.360153] wlan0: associated
[   40.892655] EXT3 FS on sda1, internal journal
[   41.058171] NET: Registered protocol family 17
[   42.369015] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.416589] No dock devices found.
[   45.929548] NET: Registered protocol family 10
[   45.930004] lo: Disabled Privacy Extensions
[   47.830272] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   47.830279] apm: overridden by ACPI.
[   55.335468] eth0: link down
[   55.338166] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.899332] wlan0: no IPv6 routers present
[   57.289905] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   57.289927] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   57.290009] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   57.921975] lirc_dev: IR Remote Control driver registered, major 61 
[   57.945468] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[   57.949326] 
[   57.949333] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
[   57.949336] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   57.968310] usbcore: registered new interface driver lirc_mceusb2
[16770.858623] wlan0: RX deauthentication from 00:30:bd:f8:92:07 (reason=7)
[16770.858630] wlan0: deauthenticated
[16771.858024] wlan0: authenticate with AP 00:30:bd:f8:92:07
[16771.859716] wlan0: RX authentication from 00:30:bd:f8:92:07 (alg=0 transaction=2 status=0)
[16771.859720] wlan0: authenticated
[16771.859724] wlan0: associate with AP 00:30:bd:f8:92:07
[16772.057919] wlan0: associate with AP 00:30:bd:f8:92:07
[16772.060006] wlan0: RX ReassocResp from 00:30:bd:f8:92:07 (capab=0x1 status=0 aid=4)
[16772.060011] wlan0: associated
[16973.490158] UDF-fs: No VRS found
[16973.554857] ISO 9660 Extensions: Microsoft Joliet Level 3
[16973.556603] ISOFS: changing to secondary root
[20502.848100] wlan0: RX deauthentication from 00:30:bd:f8:92:07 (reason=7)
[20502.848107] wlan0: deauthenticated
[20503.847461] wlan0: authenticate with AP 00:30:bd:f8:92:07
[20503.849091] wlan0: RX authentication from 00:30:bd:f8:92:07 (alg=0 transaction=2 status=0)
[20503.849097] wlan0: authenticated
[20503.849100] wlan0: associate with AP 00:30:bd:f8:92:07
[20503.851474] wlan0: RX ReassocResp from 00:30:bd:f8:92:07 (capab=0x1 status=0 aid=4)
[20503.851480] wlan0: associated

[COLOR="Red"]hardware.conf[/COLOR]

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc/0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""


[COLOR="Red"]lircd.conf[/COLOR]

#
# RC-6 config file
#
# source: [http://home.hccnet.nl/m.majoor/projects__remote_control.htm](http://home.hccnet.nl/m.majoor/projects__remote_control.htm)
#         [http://home.hccnet.nl/m.majoor/pronto.pdf](http://home.hccnet.nl/m.majoor/pronto.pdf)
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

        Blue    0x00007ba1
        Yellow  0x00007ba2
        Green   0x00007ba3
        Red     0x00007ba4
        Teletext        0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
	RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

	Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
	Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote



IRW

 irw
connect: Connection refused

---

### Post by mark467 on 2008-06-23
Also in /dev   I have /dev/lircd only no /dev/lirc/0

---

### Post by axelsvag on 2008-06-23
Do you really use mythbuntu? A lot of your work is automated in mythbuntu.

---

### Post by nasha on 2008-06-23
Mark, seems your using exactly the same remote kit that i failed miserably attempting to get going. 
[HTML]http://ubuntuforums.org/showthread.php?t=713682&highlight=pinnacle[/HTML]
I came across a lot of strange occurrences with this remote kit, and eventually gave up. It appears i never actually got the USB device to a point where lirc would recognise it. It should be at /dev/lirc0 not /dev/lirc/0 if you can manage to get it to that state. I'll have another play around and see if i can come up with anything.

EDIT:
[http://ubuntuforums.org/showthread.php?t=388728&highlight=lirc&page=4](http://ubuntuforums.org/showthread.php?t=388728&highlight=lirc&page=4)
After following crowbars post in that thread, i now have a lirc0 but im exhibitng the same problem as you when i run IRW: Connection Refused...
irrecord returns the following:
> Press RETURN now to start recording.
................................................................................
Found const length: 105141
Please keep on pressing buttons like described above.
................................................................................
RC-5 remote control found.
Found possible header: 2719 815
Found lead pulse: 490
No repeat code found.
Unknown encoding found.

Strange that it seems to think the remote is RC5... Can anyone confirm or deny this output is correct?

So close yet so far... I pick up this problem about once a month to try and get it going, this is the closest ive come yet. 
If anyone could offer some advice to either of us, it would be greatly appreciated!

---

### Post by mark467 on 2008-06-24
I would love some help on this any more info I need to post let me know. I would love to get the ir blaster on it to work also but that is not my primary concern.

---

### Post by mark467 on 2008-07-09
Anyone have any luck with this yet. I am ready to dump it and buy one. I have a harmony remote, is there a way to put an ir reciver on the mythbox to work with this. If not does anyone know of a remote I can be and it work right out of the box?

---

