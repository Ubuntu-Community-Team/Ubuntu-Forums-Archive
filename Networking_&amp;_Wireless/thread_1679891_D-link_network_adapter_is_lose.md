---
title: "D-link network adapter is lose"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by SergeyTsaplin on 2011-02-01
Hi.
First of all, I would like to apologize for my bad english.
I have a problem.
On my desktop with Ubuntu 10.10 integrated network adapter was broke. I've put new adapter D-Link DFE-520TX.LED on the adapter and on the router are glowing, but OS don't display this device. It looks like this:
```
$ifconfig -a
lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:20 errors:0 dropped:0 overruns:0 frame:0
         TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0 
         RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)
```
And this:
```
#lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
```
Logs from /var/log/kern.log
```
Jan 28 18:31:27 nikki-desktop kernel: [    0.668362] cpuidle: using governor ladder
Jan 28 18:31:27 nikki-desktop kernel: [    0.668367] cpuidle: using governor menu
Jan 28 18:31:27 nikki-desktop kernel: [    0.669037] TCP cubic registered
Jan 28 18:31:27 nikki-desktop kernel: [    0.669321] NET: Registered protocol family 10
Jan 28 18:31:27 nikki-desktop kernel: [    0.670035] lo: Disabled Privacy Extensions
Jan 28 18:31:27 nikki-desktop kernel: [    0.670536] NET: Registered protocol family 17
Jan 28 18:31:27 nikki-desktop kernel: [    0.670626] Using IPI No-Shortcut mode
Jan 28 18:31:27 nikki-desktop kernel: [    0.670791] PM: Resume from disk failed.
Jan 28 18:31:27 nikki-desktop kernel: [    0.670811] registered taskstats version 1
Jan 28 18:31:27 nikki-desktop kernel: [    0.671087]   Magic number: 11:460:545
Jan 28 18:31:27 nikki-desktop kernel: [    0.671202] rtc_cmos 00:03: setting system clock to 2011-01-28 18:31:12 UTC (1296239472)
Jan 28 18:31:27 nikki-desktop kernel: [    0.671207] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 28 18:31:27 nikki-desktop kernel: [    0.671211] EDD information not available.
Jan 28 18:31:27 nikki-desktop kernel: [    0.673895] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.23 PQ: 0 ANSI: 5
Jan 28 18:31:27 nikki-desktop kernel: [    0.693314] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jan 28 18:31:27 nikki-desktop kernel: [    0.693322] Uniform CD-ROM driver Revision: 3.20
Jan 28 18:31:27 nikki-desktop kernel: [    0.693528] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan 28 18:31:27 nikki-desktop kernel: [    0.693644] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan 28 18:31:27 nikki-desktop kernel: [    0.693839] scsi 1:0:1:0: Direct-Access     ATA      WDC WD1200BB-00R 20.0 PQ: 0 ANSI: 5
Jan 28 18:31:27 nikki-desktop kernel: [    0.694065] sd 1:0:1:0: Attached scsi generic sg2 type 0
Jan 28 18:31:27 nikki-desktop kernel: [    0.694193] sd 1:0:1:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Jan 28 18:31:27 nikki-desktop kernel: [    0.694303] sd 1:0:1:0: [sdb] Write Protect is off
Jan 28 18:31:27 nikki-desktop kernel: [    0.694309] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jan 28 18:31:27 nikki-desktop kernel: [    0.694356] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 28 18:31:27 nikki-desktop kernel: [    0.694613]  sdb: sda1 sda2 < unknown partition table
Jan 28 18:31:27 nikki-desktop kernel: [    0.702794] sd 1:0:1:0: [sdb] Attached SCSI disk
Jan 28 18:31:27 nikki-desktop kernel: [    0.728525]  sda5 >
Jan 28 18:31:27 nikki-desktop kernel: [    0.729128] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 28 18:31:27 nikki-desktop kernel: [    0.853242] [COLOR="Red"]irq 23: nobody cared (try booting with the "irqpoll" option)
Jan 28 18:31:27 nikki-desktop kernel: [    0.853250] Pid: 16, comm: async/0 Not tainted 2.6.35-24-generic #42-Ubuntu
Jan 28 18:31:27 nikki-desktop kernel: [    0.853253] Call Trace:
Jan 28 18:31:27 nikki-desktop kernel: [    0.853266]  [<c05c707f>] ? printk+0x2d/0x36
Jan 28 18:31:27 nikki-desktop kernel: [    0.853274]  [<c01a9a7c>] __report_bad_irq+0x2c/0x90
Jan 28 18:31:27 nikki-desktop kernel: [    0.853279]  [<c01a7f94>] ? handle_IRQ_event+0x44/0x150
Jan 28 18:31:27 nikki-desktop kernel: [    0.853284]  [<c01a9c3d>] note_interrupt+0x15d/0x1a0
Jan 28 18:31:27 nikki-desktop kernel: [    0.853289]  [<c01aa31c>] handle_fasteoi_irq+0xac/0xe0
Jan 28 18:31:27 nikki-desktop kernel: [    0.853295]  [<c01050ad>] handle_irq+0x1d/0x30
Jan 28 18:31:27 nikki-desktop kernel: [    0.853300]  [<c05d027c>] do_IRQ+0x4c/0xc0
Jan 28 18:31:27 nikki-desktop kernel: [    0.853305]  [<c0103630>] common_interrupt+0x30/0x38
Jan 28 18:31:27 nikki-desktop kernel: [    0.853312]  [<c022e899>] ? notify_change+0x1e9/0x2f0
Jan 28 18:31:27 nikki-desktop kernel: [    0.853317]  [<c022232b>] ? putname+0x2b/0x40
Jan 28 18:31:27 nikki-desktop kernel: [    0.853322]  [<c02253aa>] ? user_path_at+0x4a/0x80
Jan 28 18:31:27 nikki-desktop kernel: [    0.853329]  [<c023b4fa>] utimes_common+0xba/0x170
Jan 28 18:31:27 nikki-desktop kernel: [    0.853334]  [<c023b63f>] do_utimes+0x8f/0xe0
Jan 28 18:31:27 nikki-desktop kernel: [    0.853341]  [<c081b7f8>] do_utime+0x30/0x32
Jan 28 18:31:27 nikki-desktop kernel: [    0.853345]  [<c081b8dc>] do_copy+0x4f/0xca
Jan 28 18:31:27 nikki-desktop kernel: [    0.853350]  [<c081b542>] flush_buffer+0x75/0x9a
Jan 28 18:31:27 nikki-desktop kernel: [    0.853356]  [<c083db20>] gunzip+0x270/0x30c
Jan 28 18:31:27 nikki-desktop kernel: [    0.853361]  [<c0350b70>] ? nofill+0x0/0x10
Jan 28 18:31:27 nikki-desktop kernel: [    0.853366]  [<c083d8b0>] ? gunzip+0x0/0x30c
Jan 28 18:31:27 nikki-desktop kernel: [    0.853371]  [<c081c25e>] unpack_to_rootfs+0x1d8/0x2ff
Jan 28 18:31:27 nikki-desktop kernel: [    0.853375]  [<c081b4cd>] ? flush_buffer+0x0/0x9a
Jan 28 18:31:27 nikki-desktop kernel: [    0.853379]  [<c081b300>] ? error+0x0/0x13
Jan 28 18:31:27 nikki-desktop kernel: [    0.853384]  [<c081c3db>] async_populate_rootfs+0x56/0xd0
Jan 28 18:31:27 nikki-desktop kernel: [    0.853389]  [<c05c97bf>] ? _raw_spin_lock_irqsave+0x2f/0x50
Jan 28 18:31:27 nikki-desktop kernel: [    0.853395]  [<c016cfca>] run_one_entry+0x6a/0x190
Jan 28 18:31:27 nikki-desktop kernel: [    0.853402]  [<c012cef8>] ? default_spin_lock_flags+0x8/0x10
Jan 28 18:31:27 nikki-desktop kernel: [    0.853407]  [<c05c97bf>] ? _raw_spin_lock_irqsave+0x2f/0x50
Jan 28 18:31:27 nikki-desktop kernel: [    0.853413]  [<c0166220>] ? add_wait_queue+0x40/0x50
Jan 28 18:31:27 nikki-desktop kernel: [    0.853417]  [<c016d0f0>] ? async_thread+0x0/0xd0
Jan 28 18:31:27 nikki-desktop kernel: [    0.853422]  [<c016d13d>] async_thread+0x4d/0xd0
Jan 28 18:31:27 nikki-desktop kernel: [    0.853427]  [<c0142dd0>] ? default_wake_function+0x0/0x20
Jan 28 18:31:27 nikki-desktop kernel: [    0.853432]  [<c0165a94>] kthread+0x74/0x80
Jan 28 18:31:27 nikki-desktop kernel: [    0.853436]  [<c0165a20>] ? kthread+0x0/0x80
Jan 28 18:31:27 nikki-desktop kernel: [    0.853441]  [<c010363e>] kernel_thread_helper+0x6/0x10
Jan 28 18:31:27 nikki-desktop kernel: [    0.853444] handlers:
Jan 28 18:31:27 nikki-desktop kernel: [    0.853446] [<c0470160>] (usb_hcd_irq+0x0/0x80)
Jan 28 18:31:27 nikki-desktop kernel: [    0.853453] [<c0470160>] (usb_hcd_irq+0x0/0x80)
Jan 28 18:31:27 nikki-desktop kernel: [    0.853458] Disabling IRQ #23[/COLOR]
Jan 28 18:31:27 nikki-desktop kernel: [    0.895236] Freeing initrd memory: 10512k freed
Jan 28 18:31:27 nikki-desktop kernel: [    0.902617] Freeing unused kernel memory: 688k freed
Jan 28 18:31:27 nikki-desktop kernel: [    0.903277] Write protecting the kernel text: 4932k
Jan 28 18:31:27 nikki-desktop kernel: [    0.903335] Write protecting the kernel read-only data: 1980k
Jan 28 18:31:27 nikki-desktop kernel: [    0.929310] udev[79]: starting version 163
Jan 28 18:31:27 nikki-desktop kernel: [    0.947654] usb 5-1: new low speed USB device using uhci_hcd and address 2
```
And this is /proc/interrupts:
```
           CPU0       CPU1       
  0:         48          0   IO-APIC-edge      timer
  1:       3010          0   IO-APIC-edge      i8042
  6:          3          0   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
14:      17008          0   IO-APIC-edge      ata_piix
15:       6087          0   IO-APIC-edge      ata_piix
16:         44      30793   IO-APIC-fasteoi   uhci_hcd:usb5, nvidia
18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
23:     107865          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
41:       1407          0   PCI-MSI-edge      hda_intel
NMI:          0          0   Non-maskable interrupts
LOC:      65601      70238   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       2244       2011   Rescheduling interrupts
CAL:        189        163   Function call interrupts
TLB:       1044        930   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          5          5   Machine check polls
ERR:          1
MIS:          0
```

Help me, please!!!

---

