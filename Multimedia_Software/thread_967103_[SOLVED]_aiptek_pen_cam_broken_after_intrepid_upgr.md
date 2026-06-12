---
title: "[SOLVED] aiptek pen cam broken after intrepid upgrade doesn't register /dev/video* de"
date: 2008-11-01
forum: Multimedia Software
---

### Post by josephdaniel on 2008-11-01
I posted this as a bug here : [https://bugs.launchpad.net/ubuntu/+bug/292379](https://bugs.launchpad.net/ubuntu/+bug/292379)

I am posting it here to see if there is an available work around.

Details:

Aiptek pencam broken after upgrade to intrepid final release.
The appropriate module is loaded (stv680) and it reports registering the device video0 but it's not there in /dev

The same webcam was working fine with hardy since I first tested it. Following is the output from the commands I thought to be relevant.

dmesg output:
[ 300.636049] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 300.924873] usb 2-1: configuration #1 chosen from 1 choice
[ 301.298679] Linux video capture interface: v2.00
[ 301.320476] stv680: [stv680_probe:1430] STV(i): STV0680 camera found.
[ 301.323115] stv680: [stv680_probe:1470] STV(i): registered new video device: video0
[ 301.326214] usbcore: registered new interface driver stv680
[ 301.327731] stv680: [usb_stv680_init:1551] STV(i): usb camera driver version v0.25 registering
[ 301.327742] stv680: STV0680 USB Camera Driver v0.25
[ 301.411957] stv680: [stv_init:380] STV(i): QVGA is supported
[ 301.423923] stv680: [stv_init:396] STV(i): Camera has 0 pictures.
[ 301.564770] stv680: [usb_stv680_remove_disconnected:1507] STV(i): STV0680 disconnected

lsusb output:
Bus 002 Device 002: ID 0553:0202 STMicroelectronics Imaging Division (VLSI Vision) Aiptek PenCam 1
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ls /dev | grep video
gives nothing. There are no video devices under /dev

This camera has built in memory to store about 25 VGA photos. When it's connected F-spot offers to download the stored photos but it always fails with an I/O error. This was also working on hardy before upgrading.

What do you think might cause this? The same behavior occurs on my desktop machine that has also been upgraded from hardy to intrepid today.

Thanks,
Joseph

---

### Post by dougfractal on 2008-11-06
I had the same problem, it affected my STV0680 USB Camera and my  SAA7130 tv card, both were detected but no /dev/video*.

Just had kernel update. now 2.6.27-7-generic. All seems fine (I haven't got my STV0680 with me right now, but the tv card works so i'm feeling it was a v4l issue.)

---

### Post by dougfractal on 2008-11-06
repeat entry

---

### Post by pierrehenri on 2008-11-11
I was able to get it to work.
After you plug the webcam, you need to unmount the desktop camera icon, then unload the stv680 module and then reload it. My guess is there's some kind of conflict between the pictures mode and the webcam mode but I'm no expert.

---

### Post by josephdaniel on 2008-11-11
thanks a lot pierre for this excellent hint. I really appreciate it. 

I don't care about having to reload the module each time. I just want the camera to work.

I see that you have also added this workaround to the bug report at launchpad. Lets hope this gets fixed in the future kernel versions.

You're an expert to me, Thanks again.

EDIT: It is working, but I just noticed that the colors are wrong. It seems that the red and blue are exchanged. Do you have the same problem?

EDIT EDIT: Colors were fixed by setting the module parametes: "modprobe stv680 swapRGB_on=-1"

Joe

---

### Post by gcvisel on 2008-12-19
> **pierrehenri said:**
> I was able to get it to work.
After you plug the webcam, you need to unmount the desktop camera icon, then unload the stv680 module and then reload it. My guess is there's some kind of conflict between the pictures mode and the webcam mode but I'm no expert.

Any specifics on how to "unload", unmount, and reload modules?  I have a similar issue with a Clique Hue camera.  The audio is recognized but not the video.
ls /dev/video* gives:
ls: cannot access /dev/video*: No such file or directory

Thanks,
Gerry

---

### Post by go_beep_yourself on 2009-01-02
How did you get the audio working on a Clique Hue Webcam? By audio, do you mean the builtin microphone? What did you mean?

To load modules use modprobe. To remove modules, use rmmod or modprobe -r. You can also load modules with insmod.

---

### Post by josephdaniel on 2009-01-02
Actually my aiptek pencam doesn't have a builtin microphone. The problem described here was only about the video.

---

### Post by go_beep_yourself on 2009-01-02
I was asking gcvisel. He has the Clique Hue camera.

---

### Post by tonyuk123 on 2009-01-20
How did you get your pencam working on Ubuntu 8.04?
I can't seem to get mine working
Tony

---

### Post by josephdaniel on 2009-01-20
Well, for me it worked out-of-the-box on 8.04. I would just plug it and the /dev/video* device is registed. 

But here's what I do on 8.10 to get it to work, you can try it on 8.04 but I have no idea whether this would work or not.

After plugging the pencam, I unload the module and reload it as advised by pierre.

```
sudo rmmod stv680
```
then
```
sudo modprobe stv680
```
or the following if you have the same color issue I described
```
sudo modprobe stv680 swapRGB_on=-1
```

If this doesn't work, I suggest you paste your dmesg output after plugging the camera. I am not an expert but maybe I can help.

Joe

---

### Post by tonyuk123 on 2009-01-22
Hi thanks for trying to help.
Unfortunately it made no difference.

lsusb 

tried the command got this 'lsusb'

here are the results 

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 03f0:b802 Hewlett-Packard Photosmart 7400 Series
Bus 003 Device 005: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0553:0202 STMicroelectronics Imaging Division (VLSI Vision) Aiptek PenCam 1
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

seems it thinks it is an Aiptek PenCam, good start i guess.
When you use the /dev/video*
where * is a number (i think it is 0 (zero)on mine) 
how does that relate to the info above.
I notice the webcam is on Bus001 device 002
should the software be set to look for /dev/video2 ?
maybe this is my problem?

I am new to Ubuntu (linux) but i am fairly savvy on most subjects and willing to learn if i can ;)

---

### Post by josephdaniel on 2009-01-27
Well it should be /dev/video0 no matter what the BusID is. As far as I understand the number only increases when you have more than one video device connected.

To list all the available video devices on your system you can try the following.It will list all the available /dev/video entries whatever the number is.

```
ls /dev | grep video
```

Also try the command dmesg. Run it before and after connecting the camera and paste the changes here. Maybe this gives any more information that can help.

Joseph

---

### Post by tonyuk123 on 2009-02-08
ok well i did dmesg with cam unplugged
here is results
```

[    0.000000] Kernel command line: root=UUID=a3e31542-543e-40e1-81bd-068b7e348d48 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1700.049 MHz processor.
[   15.559379] Console: colour VGA+ 80x25
[   15.559386] console [tty0] enabled
[   15.560032] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.560999] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.587946] Memory: 506724k/524224k available (2179k kernel code, 15968k reserved, 1008k data, 368k init, 0k highmem)
[   15.587960] virtual kernel memory layout:
[   15.587961]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   15.587963]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.587965]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   15.587966]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   15.587968]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   15.587970]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   15.587971]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   15.587977] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.588044] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.668034] Calibrating delay using timer specific routine.. 3404.08 BogoMIPS (lpj=6808171)
[   15.668083] Security Framework initialized
[   15.668097] SELinux:  Disabled at boot.
[   15.668124] AppArmor: AppArmor initialized
[   15.668132] Failure registering capabilities with primary security module.
[   15.668148] Mount-cache hash table entries: 512
[   15.668436] Initializing cgroup subsys ns
[   15.668451] Initializing cgroup subsys cpuacct
[   15.668479] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   15.668501] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   15.668505] CPU: L2 cache: 128K
[   15.668510] CPU: Hyper-Threading is disabled
[   15.668513] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00043080 00000000 00000000 00000000 00000000
[   15.668537] Compat vDSO mapped to ffffe000.
[   15.668565] Checking 'hlt' instruction... OK.
[   15.684702] SMP alternatives: switching to UP code
[   15.687474] Freeing SMP alternatives: 11k freed
[   15.687746] Early unpacking initramfs... done
[   16.261828] ACPI: Core revision 20070126
[   16.261937] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.264465] ACPI: setting ELCR to 0200 (from 0a20)
[   16.335084] CPU0: Intel(R) Celeron(R) CPU 1.70GHz stepping 03
[   16.335100] SMP motherboard not detected.
[   16.335105] Local APIC not detected. Using dummy APIC emulation.
[   16.335211] Brought up 1 CPUs
[   16.335249] CPU0 attaching sched-domain:
[   16.335257]  domain 0: span 01
[   16.335261]   groups: 01
[   16.335915] net_namespace: 64 bytes
[   16.335931] Booting paravirtualized kernel on bare hardware
[   16.337051] Time: 14:02:55  Date: 02/08/09
[   16.337134] NET: Registered protocol family 16
[   16.338062] EISA bus registered
[   16.338104] ACPI: bus type pci registered
[   16.364113] PCI: PCI BIOS revision 2.10 entry at 0xfb0b0, last bus=2
[   16.364120] PCI: Using configuration type 1
[   16.364130] Setting up standard PCI resources
[   16.369780] ACPI: EC: Look up EC in DSDT
[   16.374895] ACPI: Interpreter enabled
[   16.374907] ACPI: (supports S0 S3 S4 S5)
[   16.374942] ACPI: Using PIC for interrupt routing
[   16.390310] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.390754] PCI quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[   16.390763] PCI quirk: region 4080-40bf claimed by ICH4 GPIO
[   16.391905] PCI: Transparent bridge - 0000:00:1e.0
[   16.391969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.392213] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   16.414729] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   16.414943] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   16.415147] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.415351] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.415555] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.415853] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.416062] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.416285] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.416807] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.416955] pnp: PnP ACPI init
[   16.416981] ACPI: bus type pnp registered
[   16.426679] pnp: PnP ACPI: found 16 devices
[   16.426689] ACPI: ACPI bus type pnp unregistered
[   16.426700] PnPBIOS: Disabled by ACPI PNP
[   16.427889] PCI: Using ACPI for IRQ routing
[   16.427900] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.459661] NET: Registered protocol family 8
[   16.459668] NET: Registered protocol family 20
[   16.459945] AppArmor: AppArmor Filesystem Enabled
[   16.463631] Time: tsc clocksource has been installed.
[   16.471842] system 00:00: iomem range 0xcfc00-0xcffff has been reserved
[   16.471851] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   16.471856] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   16.471862] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   16.471868] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
[   16.471874] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   16.471879] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[   16.471886] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[   16.471892] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[   16.471897] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[   16.471903] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[   16.471918] system 00:02: ioport range 0x4000-0x40bf could not be reserved
[   16.471931] system 00:03: ioport range 0xb78-0xb7b has been reserved
[   16.471936] system 00:03: ioport range 0xf78-0xf7b has been reserved
[   16.471942] system 00:03: ioport range 0xa78-0xa7b has been reserved
[   16.471947] system 00:03: ioport range 0xe78-0xe7b has been reserved
[   16.471952] system 00:03: ioport range 0xbbc-0xbbf has been reserved
[   16.471957] system 00:03: ioport range 0xfbc-0xfbf has been reserved
[   16.471962] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   16.471968] system 00:03: ioport range 0x294-0x297 has been reserved
[   16.503938] PCI: Bridge: 0000:00:01.0
[   16.503946]   IO window: disabled.
[   16.503954]   MEM window: e4000000-e5ffffff
[   16.503960]   PREFETCH window: d0000000-dfffffff
[   16.503969] PCI: Bridge: 0000:00:1e.0
[   16.503975]   IO window: c000-cfff
[   16.503983]   MEM window: e6000000-e60fffff
[   16.503989]   PREFETCH window: disabled.
[   16.504015] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.504047] NET: Registered protocol family 2
[   16.543771] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.544282] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   16.544515] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   16.544860] TCP: Hash tables configured (established 16384 bind 16384)
[   16.544875] TCP reno registered
[   16.555920] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   17.046240]  it is
[   17.637553] Freeing initrd memory: 7319k freed
[   17.639371] audit: initializing netlink socket (disabled)
[   17.639404] audit(1234101775.992:1): initialized
[   17.646532] VFS: Disk quotas dquot_6.5.1
[   17.646822] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.647368] io scheduler noop registered
[   17.647376] io scheduler anticipatory registered
[   17.647381] io scheduler deadline registered
[   17.647434] io scheduler cfq registered (default)
[   17.647515] Boot video device is 0000:01:00.0
[   17.648732] isapnp: Scanning for PnP cards...
[   18.003056] isapnp: No Plug & Play device found
[   18.217816] Real Time Clock Driver v1.12ac
[   18.218205] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.218513] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.219072] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.221581] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.222878] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.226335] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.226632] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.227073] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.230358] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.230372] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.239004] mice: PS/2 mouse device common for all mice
[   18.239551] EISA: Probing bus 0 at eisa.0
[   18.239581] Cannot allocate resource for EISA slot 4
[   18.239602] EISA: Detected 0 cards.
[   18.239611] cpuidle: using governor ladder
[   18.239616] cpuidle: using governor menu
[   18.239827] NET: Registered protocol family 1
[   18.239913] Using IPI No-Shortcut mode
[   18.239997] registered taskstats version 1
[   18.240164]   Magic number: 13:21:30
[   18.240183]   hash matches device ttydd
[   18.240359] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.240364] EDD information not available.
[   18.241300] Freeing unused kernel memory: 368k freed
[   18.241368] Write protecting the kernel read-only data: 806k
[   18.268237] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.858642] fuse init (API version 7.9)
[   19.901504] ACPI: Fan [FAN] (on)
[   19.916937] ACPI: Processor [CPU0] (supports 2 throttling states)
[   19.920771] ACPI: Thermal Zone [THRM] (58 C)
[   21.276932] SCSI subsystem initialized
[   21.316846] usbcore: registered new interface driver usbfs
[   21.316906] usbcore: registered new interface driver hub
[   21.351734] usbcore: registered new device driver usb
[   21.369524] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   21.369619] 8139cp 0000:02:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   21.369627] 8139cp 0000:02:0c.0: Try the "8139too" driver instead.
[   21.388743] 8139too Fast Ethernet driver 0.9.28
[   21.405895] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   21.405906] PCI: setting IRQ 11 as level-triggered
[   21.405912] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   21.406872] eth0: RealTek RTL8139 at 0xc800, 00:40:f4:74:72:c4, IRQ 11
[   21.406879] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   21.440693] USB Universal Host Controller Interface driver v3.0
[   21.441146] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   21.441156] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   21.441182] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.441190] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   21.441973] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   21.442026] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000d000
[   21.442358] usb usb1: configuration #1 chosen from 1 choice
[   21.442418] hub 1-0:1.0: USB hub found
[   21.442435] hub 1-0:1.0: 2 ports detected
[   21.494185] libata version 3.00 loaded.
[   21.545163] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   21.545174] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   21.545200] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   21.545207] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   21.545307] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   21.545350] uhci_hcd 0000:00:1f.4: irq 11, io base 0x0000d800
[   21.545637] usb usb2: configuration #1 chosen from 1 choice
[   21.545699] hub 2-0:1.0: USB hub found
[   21.545718] hub 2-0:1.0: 2 ports detected
[   21.649099] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   21.649110] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   21.649136] uhci_hcd 0000:02:06.0: UHCI Host Controller
[   21.649241] uhci_hcd 0000:02:06.0: new USB bus registered, assigned bus number 3
[   21.649283] uhci_hcd 0000:02:06.0: irq 11, io base 0x0000c000
[   21.649559] usb usb3: configuration #1 chosen from 1 choice
[   21.649621] hub 3-0:1.0: USB hub found
[   21.649638] hub 3-0:1.0: 2 ports detected
[   21.650589] Floppy drive(s): fd0 is 1.44M
[   21.668381] FDC 0 is a post-1991 82077
[   21.752714] ACPI: PCI Interrupt 0000:02:06.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   21.752746] uhci_hcd 0000:02:06.1: UHCI Host Controller
[   21.752823] uhci_hcd 0000:02:06.1: new USB bus registered, assigned bus number 4
[   21.752864] uhci_hcd 0000:02:06.1: irq 11, io base 0x0000c400
[   21.753136] usb usb4: configuration #1 chosen from 1 choice
[   21.753200] hub 4-0:1.0: USB hub found
[   21.753217] hub 4-0:1.0: 2 ports detected
[   21.784479] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   21.857286] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[   21.857297] PCI: setting IRQ 5 as level-triggered
[   21.857303] ACPI: PCI Interrupt 0000:02:06.2[C] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   21.857336] ehci_hcd 0000:02:06.2: EHCI Host Controller
[   21.857443] ehci_hcd 0000:02:06.2: new USB bus registered, assigned bus number 5
[   21.857536] ehci_hcd 0000:02:06.2: irq 5, io mem 0xe6000000
[   21.912393] ehci_hcd 0000:02:06.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.912686] usb usb5: configuration #1 chosen from 1 choice
[   21.912748] hub 5-0:1.0: USB hub found
[   21.912768] hub 5-0:1.0: 4 ports detected
[   22.016825] ata_piix 0000:00:1f.1: version 2.12
[   22.016948] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.021068] scsi0 : ata_piix
[   22.023495] scsi1 : ata_piix
[   22.024751] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   22.024761] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   22.029934] usb 1-1: configuration #1 chosen from 1 choice
[   22.360660] ata1.00: ATA-7: HDS728080PLAT20, PF2OA2AA, max UDMA/133
[   22.360670] ata1.00: 160836480 sectors, multi 16: LBA48 
[   22.360713] ata1.01: ATAPI: ATAPI   DVD DD 2X16X4X16, G7H9, max UDMA/33
[   22.384590] ata1.00: configured for UDMA/100
[   22.556499] ata1.01: configured for UDMA/33
[   22.720420] ata2.00: ATA-7: Maxtor 2F020J0, VAM51JJ0, max UDMA/133
[   22.720430] ata2.00: 40718160 sectors, multi 16: LBA 
[   22.720455] ata2.00: limited to UDMA/33 due to 40-wire cable
[   22.729085] ata2.00: configured for UDMA/33
[   22.729384] scsi 0:0:0:0: Direct-Access     ATA      HDS728080PLAT20  PF2O PQ: 0 ANSI: 5
[   22.732510] scsi 0:0:1:0: CD-ROM            ATAPI    DVD DD 2X16X4X16 G7H9 PQ: 0 ANSI: 5
[   22.732982] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 2F020J0   VAM5 PQ: 0 ANSI: 5
[   23.259535] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   23.449636] usb 3-1: configuration #1 chosen from 1 choice
[   23.543208] Driver 'sd' needs updating - please use bus_type methods
[   23.543478] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[   23.543517] sd 0:0:0:0: [sda] Write Protect is off
[   23.543522] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.543575] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.543734] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[   23.543769] sd 0:0:0:0: [sda] Write Protect is off
[   23.543774] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.543828] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.543840]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   23.570963]  sda5 sda6 >
[   23.571541] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.572111] sd 1:0:0:0: [sdb] 40718160 512-byte hardware sectors (20848 MB)
[   23.572147] sd 1:0:0:0: [sdb] Write Protect is off
[   23.572153] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   23.572202] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.572355] sd 1:0:0:0: [sdb] 40718160 512-byte hardware sectors (20848 MB)
[   23.572389] sd 1:0:0:0: [sdb] Write Protect is off
[   23.572395] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   23.572443] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.572454]  sdb:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   23.576564] Uniform CD-ROM driver Revision: 3.20
[   23.576684] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   23.691237] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   23.869428] usb 3-2: configuration #1 chosen from 1 choice
[   23.874637] usbcore: registered new interface driver libusual
[   23.889601] Initializing USB Mass Storage driver...
[   23.899172] scsi2 : SCSI emulation for USB Mass Storage devices
[   23.901868] usbcore: registered new interface driver usb-storage
[   23.901879] USB Mass Storage support registered.
[   23.902178] usb-storage: device found at 2
[   23.902185] usb-storage: waiting for device to settle before scanning
[   25.161713]  sdb1
[   25.161893] sd 1:0:0:0: [sdb] Attached SCSI disk
[   25.192229] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.192276] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   25.192329] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   25.794160] Attempting manual resume
[   25.794173] swsusp: Resume From Partition 8:5
[   25.794176] PM: Checking swsusp image.
[   25.794485] PM: Resume from disk failed.
[   25.854974] kjournald starting.  Commit interval 5 seconds
[   25.855016] EXT3-fs: mounted filesystem with ordered data mode.
[   28.897541] usb-storage: device scan complete
[   28.905500] scsi 2:0:0:0: Direct-Access     HP       Photosmart 7400  1.00 PQ: 0 ANSI: 2
[   28.921566] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   28.921676] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   34.424789] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.475241] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.540679] Linux agpgart interface v0.102
[   34.629997] agpgart: Detected an Intel 845G Chipset.
[   34.634319] agpgart: AGP aperture is 64M @ 0xe0000000
[   34.913709] input: Power Button (FF) as /devices/virtual/input/input2
[   34.932495] ACPI: Power Button (FF) [PWRF]
[   34.932772] input: Power Button (CM) as /devices/virtual/input/input3
[   34.944334] ACPI: Power Button (CM) [PWRB]
[   34.944636] input: Sleep Button (CM) as /devices/virtual/input/input4
[   34.960426] ACPI: Sleep Button (CM) [SLPB]
[   35.029379] intel_rng: FWH not detected
[   35.197707] iTCO_vendor_support: vendor-support=0
[   35.260218] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   35.260579] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   35.260597] iTCO_wdt: No card detected
[   36.484393] nvidia: module license 'NVIDIA' taints kernel.
[   37.293831] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   39.265188] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input6
[   39.918071] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   39.918874] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   39.938377] parport_pc 00:0b: reported by Plug and Play ACPI
[   39.938442] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.005723] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0xB802
[   40.005772] usbcore: registered new interface driver usblp
[   40.229092] Linux video capture interface: v2.00
[   40.341718] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1425] STV(i): STV0680 camera found.
[   40.341806] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1465] STV(i): registered new video device: video0
[   40.341857] usbcore: registered new interface driver stv680
[   40.341867] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [usb_stv680_init:1546] STV(i): usb camera driver version v0.25 registering
[   40.341872] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: STV0680 USB Camera Driver v0.25
[   40.606264] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   40.606274] PCI: setting IRQ 9 as level-triggered
[   40.606279] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   40.606320] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   41.200494] intel8x0_measure_ac97_clock: measured 55406 usecs
[   41.200502] intel8x0: clocking to 48000
[   44.949035] lp0: using parport0 (interrupt-driven).
[   45.083631] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   45.713007] EXT3 FS on sda6, internal journal
[   47.412269] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.255525] No dock devices found.
[   50.336949] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   50.336961] apm: overridden by ACPI.
[   50.525588] ppdev: user-space parallel port driver
[   50.711455] audit(1234101809.981:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5068 profile="/usr/sbin/cupsd" namespace="default"
[   52.155370] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:374] STV(i): CIF is supported
[   52.172324] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:392] STV(i): Camera has 0 pictures.
[   52.246267] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:419] STV(i): Video Mode set to CIF
[   54.276253] eth0: link down
[   54.509150] Bluetooth: Core ver 2.11
[   54.516549] NET: Registered protocol family 31
[   54.516563] Bluetooth: HCI device and connection manager initialized
[   54.516574] Bluetooth: HCI socket layer initialized
[   54.564436] Bluetooth: L2CAP ver 2.9
[   54.564447] Bluetooth: L2CAP socket layer initialized
[   54.636658] Bluetooth: RFCOMM socket layer initialized
[   54.637236] Bluetooth: RFCOMM TTY layer initialized
[   54.637254] Bluetooth: RFCOMM ver 1.8
[   57.572351] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   57.572953] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   57.573509] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  768.809874] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  770.975424] NET: Registered protocol family 17
[  775.642029] eth0: link down
[  777.403152] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  780.730558] NET: Registered protocol family 10
[  780.731878] lo: Disabled Privacy Extensions
[  795.560822] eth0: no IPv6 routers present
[  798.914737] UDF-fs: No VRS found
[  799.034681] ISO 9660 Extensions: Microsoft Joliet Level 1
[  799.242758] ISOFS: changing to secondary root
[ 1080.410553] usblp0: removed
[ 1081.551899] audit(1234102841.453:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6272 profile="/usr/sbin/cupsd" namespace="default"
[ 2806.924125] audit(1234104567.885:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6864 profile="/usr/sbin/cupsd" namespace="default"
[ 2840.128124] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 2855.230845] usb 3-1: device descriptor read/64, error -110
[ 2870.437613] usb 3-1: device descriptor read/64, error -110
[ 2870.653358] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 2885.756081] usb 3-1: device descriptor read/64, error -110
[ 2900.962734] usb 3-1: device descriptor read/64, error -110
[ 2901.178598] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 2906.197124] usb 3-1: device descriptor read/8, error -110
[ 2911.314318] usb 3-1: device descriptor read/8, error -110
[ 2911.528242] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 2916.546509] usb 3-1: device descriptor read/8, error -110
[ 2921.663682] usb 3-1: device descriptor read/8, error -110
[ 2921.766201] usb 3-1: USB disconnect, address 2
[ 2921.767465] scsi 2:0:0:0: Device offlined - not ready after error recovery
[ 2921.774333] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774370] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774380] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774389] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774396] scsi 2:0:0:0: [sdc] READ CAPACITY failed
[ 2921.774400] scsi 2:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2921.774408] scsi 2:0:0:0: [sdc] Sense not available.
[ 2921.774418] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774426] scsi 2:0:0:0: [sdc] Write Protect is off
[ 2921.774431] scsi 2:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 2921.774435] scsi 2:0:0:0: [sdc] Assuming drive cache: write through
[ 2921.774464] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774476] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774485] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774494] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774500] scsi 2:0:0:0: [sdc] READ CAPACITY failed
[ 2921.774504] scsi 2:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2921.774512] scsi 2:0:0:0: [sdc] Sense not available.
[ 2921.774519] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774526] scsi 2:0:0:0: [sdc] Write Protect is off
[ 2921.774530] scsi 2:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 2921.774534] scsi 2:0:0:0: [sdc] Assuming drive cache: write through
[ 2921.877874] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 2921.997804] usb 3-1: device descriptor read/64, error -71
[ 2922.221821] usb 3-1: device descriptor read/64, error -71
[ 2922.437672] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 2922.559688] usb 3-1: device descriptor read/64, error -71
[ 2922.781324] usb 3-1: device descriptor read/64, error -71
[ 2922.997197] usb 3-1: new full speed USB device using uhci_hcd and address 6
[ 2923.408923] usb 3-1: device not accepting address 6, error -71
[ 2923.520861] usb 3-1: new full speed USB device using uhci_hcd and address 7
[ 2923.932586] usb 3-1: device not accepting address 7, error -71
[ 8425.810868] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 8425.997081] usb 4-1: configuration #1 chosen from 1 choice
[ 8821.347923] usb 4-1: USB disconnect, address 2
[13929.983776] usb 1-1: USB disconnect, address 2
[13929.983937] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [usb_stv680_remove_disconnected:1502] STV(i): STV0680 disconnected
```

and here is with it plugged in
```

[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1700.049 MHz processor.
[   15.559379] Console: colour VGA+ 80x25
[   15.559386] console [tty0] enabled
[   15.560032] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.560999] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.587946] Memory: 506724k/524224k available (2179k kernel code, 15968k reserved, 1008k data, 368k init, 0k highmem)
[   15.587960] virtual kernel memory layout:
[   15.587961]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   15.587963]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.587965]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   15.587966]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   15.587968]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   15.587970]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   15.587971]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   15.587977] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.588044] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.668034] Calibrating delay using timer specific routine.. 3404.08 BogoMIPS (lpj=6808171)
[   15.668083] Security Framework initialized
[   15.668097] SELinux:  Disabled at boot.
[   15.668124] AppArmor: AppArmor initialized
[   15.668132] Failure registering capabilities with primary security module.
[   15.668148] Mount-cache hash table entries: 512
[   15.668436] Initializing cgroup subsys ns
[   15.668451] Initializing cgroup subsys cpuacct
[   15.668479] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   15.668501] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   15.668505] CPU: L2 cache: 128K
[   15.668510] CPU: Hyper-Threading is disabled
[   15.668513] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00043080 00000000 00000000 00000000 00000000
[   15.668537] Compat vDSO mapped to ffffe000.
[   15.668565] Checking 'hlt' instruction... OK.
[   15.684702] SMP alternatives: switching to UP code
[   15.687474] Freeing SMP alternatives: 11k freed
[   15.687746] Early unpacking initramfs... done
[   16.261828] ACPI: Core revision 20070126
[   16.261937] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.264465] ACPI: setting ELCR to 0200 (from 0a20)
[   16.335084] CPU0: Intel(R) Celeron(R) CPU 1.70GHz stepping 03
[   16.335100] SMP motherboard not detected.
[   16.335105] Local APIC not detected. Using dummy APIC emulation.
[   16.335211] Brought up 1 CPUs
[   16.335249] CPU0 attaching sched-domain:
[   16.335257]  domain 0: span 01
[   16.335261]   groups: 01
[   16.335915] net_namespace: 64 bytes
[   16.335931] Booting paravirtualized kernel on bare hardware
[   16.337051] Time: 14:02:55  Date: 02/08/09
[   16.337134] NET: Registered protocol family 16
[   16.338062] EISA bus registered
[   16.338104] ACPI: bus type pci registered
[   16.364113] PCI: PCI BIOS revision 2.10 entry at 0xfb0b0, last bus=2
[   16.364120] PCI: Using configuration type 1
[   16.364130] Setting up standard PCI resources
[   16.369780] ACPI: EC: Look up EC in DSDT
[   16.374895] ACPI: Interpreter enabled
[   16.374907] ACPI: (supports S0 S3 S4 S5)
[   16.374942] ACPI: Using PIC for interrupt routing
[   16.390310] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.390754] PCI quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[   16.390763] PCI quirk: region 4080-40bf claimed by ICH4 GPIO
[   16.391905] PCI: Transparent bridge - 0000:00:1e.0
[   16.391969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.392213] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   16.414729] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   16.414943] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   16.415147] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.415351] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.415555] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.415853] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.416062] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.416285] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.416807] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.416955] pnp: PnP ACPI init
[   16.416981] ACPI: bus type pnp registered
[   16.426679] pnp: PnP ACPI: found 16 devices
[   16.426689] ACPI: ACPI bus type pnp unregistered
[   16.426700] PnPBIOS: Disabled by ACPI PNP
[   16.427889] PCI: Using ACPI for IRQ routing
[   16.427900] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.459661] NET: Registered protocol family 8
[   16.459668] NET: Registered protocol family 20
[   16.459945] AppArmor: AppArmor Filesystem Enabled
[   16.463631] Time: tsc clocksource has been installed.
[   16.471842] system 00:00: iomem range 0xcfc00-0xcffff has been reserved
[   16.471851] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   16.471856] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   16.471862] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   16.471868] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
[   16.471874] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   16.471879] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[   16.471886] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[   16.471892] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[   16.471897] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[   16.471903] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[   16.471918] system 00:02: ioport range 0x4000-0x40bf could not be reserved
[   16.471931] system 00:03: ioport range 0xb78-0xb7b has been reserved
[   16.471936] system 00:03: ioport range 0xf78-0xf7b has been reserved
[   16.471942] system 00:03: ioport range 0xa78-0xa7b has been reserved
[   16.471947] system 00:03: ioport range 0xe78-0xe7b has been reserved
[   16.471952] system 00:03: ioport range 0xbbc-0xbbf has been reserved
[   16.471957] system 00:03: ioport range 0xfbc-0xfbf has been reserved
[   16.471962] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   16.471968] system 00:03: ioport range 0x294-0x297 has been reserved
[   16.503938] PCI: Bridge: 0000:00:01.0
[   16.503946]   IO window: disabled.
[   16.503954]   MEM window: e4000000-e5ffffff
[   16.503960]   PREFETCH window: d0000000-dfffffff
[   16.503969] PCI: Bridge: 0000:00:1e.0
[   16.503975]   IO window: c000-cfff
[   16.503983]   MEM window: e6000000-e60fffff
[   16.503989]   PREFETCH window: disabled.
[   16.504015] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.504047] NET: Registered protocol family 2
[   16.543771] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.544282] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   16.544515] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   16.544860] TCP: Hash tables configured (established 16384 bind 16384)
[   16.544875] TCP reno registered
[   16.555920] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   17.046240]  it is
[   17.637553] Freeing initrd memory: 7319k freed
[   17.639371] audit: initializing netlink socket (disabled)
[   17.639404] audit(1234101775.992:1): initialized
[   17.646532] VFS: Disk quotas dquot_6.5.1
[   17.646822] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.647368] io scheduler noop registered
[   17.647376] io scheduler anticipatory registered
[   17.647381] io scheduler deadline registered
[   17.647434] io scheduler cfq registered (default)
[   17.647515] Boot video device is 0000:01:00.0
[   17.648732] isapnp: Scanning for PnP cards...
[   18.003056] isapnp: No Plug & Play device found
[   18.217816] Real Time Clock Driver v1.12ac
[   18.218205] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.218513] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.219072] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.221581] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.222878] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.226335] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.226632] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.227073] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.230358] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.230372] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.239004] mice: PS/2 mouse device common for all mice
[   18.239551] EISA: Probing bus 0 at eisa.0
[   18.239581] Cannot allocate resource for EISA slot 4
[   18.239602] EISA: Detected 0 cards.
[   18.239611] cpuidle: using governor ladder
[   18.239616] cpuidle: using governor menu
[   18.239827] NET: Registered protocol family 1
[   18.239913] Using IPI No-Shortcut mode
[   18.239997] registered taskstats version 1
[   18.240164]   Magic number: 13:21:30
[   18.240183]   hash matches device ttydd
[   18.240359] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.240364] EDD information not available.
[   18.241300] Freeing unused kernel memory: 368k freed
[   18.241368] Write protecting the kernel read-only data: 806k
[   18.268237] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.858642] fuse init (API version 7.9)
[   19.901504] ACPI: Fan [FAN] (on)
[   19.916937] ACPI: Processor [CPU0] (supports 2 throttling states)
[   19.920771] ACPI: Thermal Zone [THRM] (58 C)
[   21.276932] SCSI subsystem initialized
[   21.316846] usbcore: registered new interface driver usbfs
[   21.316906] usbcore: registered new interface driver hub
[   21.351734] usbcore: registered new device driver usb
[   21.369524] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   21.369619] 8139cp 0000:02:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   21.369627] 8139cp 0000:02:0c.0: Try the "8139too" driver instead.
[   21.388743] 8139too Fast Ethernet driver 0.9.28
[   21.405895] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   21.405906] PCI: setting IRQ 11 as level-triggered
[   21.405912] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   21.406872] eth0: RealTek RTL8139 at 0xc800, 00:40:f4:74:72:c4, IRQ 11
[   21.406879] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   21.440693] USB Universal Host Controller Interface driver v3.0
[   21.441146] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   21.441156] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   21.441182] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.441190] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   21.441973] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   21.442026] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000d000
[   21.442358] usb usb1: configuration #1 chosen from 1 choice
[   21.442418] hub 1-0:1.0: USB hub found
[   21.442435] hub 1-0:1.0: 2 ports detected
[   21.494185] libata version 3.00 loaded.
[   21.545163] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   21.545174] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   21.545200] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   21.545207] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   21.545307] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   21.545350] uhci_hcd 0000:00:1f.4: irq 11, io base 0x0000d800
[   21.545637] usb usb2: configuration #1 chosen from 1 choice
[   21.545699] hub 2-0:1.0: USB hub found
[   21.545718] hub 2-0:1.0: 2 ports detected
[   21.649099] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   21.649110] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   21.649136] uhci_hcd 0000:02:06.0: UHCI Host Controller
[   21.649241] uhci_hcd 0000:02:06.0: new USB bus registered, assigned bus number 3
[   21.649283] uhci_hcd 0000:02:06.0: irq 11, io base 0x0000c000
[   21.649559] usb usb3: configuration #1 chosen from 1 choice
[   21.649621] hub 3-0:1.0: USB hub found
[   21.649638] hub 3-0:1.0: 2 ports detected
[   21.650589] Floppy drive(s): fd0 is 1.44M
[   21.668381] FDC 0 is a post-1991 82077
[   21.752714] ACPI: PCI Interrupt 0000:02:06.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   21.752746] uhci_hcd 0000:02:06.1: UHCI Host Controller
[   21.752823] uhci_hcd 0000:02:06.1: new USB bus registered, assigned bus number 4
[   21.752864] uhci_hcd 0000:02:06.1: irq 11, io base 0x0000c400
[   21.753136] usb usb4: configuration #1 chosen from 1 choice
[   21.753200] hub 4-0:1.0: USB hub found
[   21.753217] hub 4-0:1.0: 2 ports detected
[   21.784479] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   21.857286] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[   21.857297] PCI: setting IRQ 5 as level-triggered
[   21.857303] ACPI: PCI Interrupt 0000:02:06.2[C] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   21.857336] ehci_hcd 0000:02:06.2: EHCI Host Controller
[   21.857443] ehci_hcd 0000:02:06.2: new USB bus registered, assigned bus number 5
[   21.857536] ehci_hcd 0000:02:06.2: irq 5, io mem 0xe6000000
[   21.912393] ehci_hcd 0000:02:06.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.912686] usb usb5: configuration #1 chosen from 1 choice
[   21.912748] hub 5-0:1.0: USB hub found
[   21.912768] hub 5-0:1.0: 4 ports detected
[   22.016825] ata_piix 0000:00:1f.1: version 2.12
[   22.016948] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.021068] scsi0 : ata_piix
[   22.023495] scsi1 : ata_piix
[   22.024751] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   22.024761] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   22.029934] usb 1-1: configuration #1 chosen from 1 choice
[   22.360660] ata1.00: ATA-7: HDS728080PLAT20, PF2OA2AA, max UDMA/133
[   22.360670] ata1.00: 160836480 sectors, multi 16: LBA48 
[   22.360713] ata1.01: ATAPI: ATAPI   DVD DD 2X16X4X16, G7H9, max UDMA/33
[   22.384590] ata1.00: configured for UDMA/100
[   22.556499] ata1.01: configured for UDMA/33
[   22.720420] ata2.00: ATA-7: Maxtor 2F020J0, VAM51JJ0, max UDMA/133
[   22.720430] ata2.00: 40718160 sectors, multi 16: LBA 
[   22.720455] ata2.00: limited to UDMA/33 due to 40-wire cable
[   22.729085] ata2.00: configured for UDMA/33
[   22.729384] scsi 0:0:0:0: Direct-Access     ATA      HDS728080PLAT20  PF2O PQ: 0 ANSI: 5
[   22.732510] scsi 0:0:1:0: CD-ROM            ATAPI    DVD DD 2X16X4X16 G7H9 PQ: 0 ANSI: 5
[   22.732982] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 2F020J0   VAM5 PQ: 0 ANSI: 5
[   23.259535] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   23.449636] usb 3-1: configuration #1 chosen from 1 choice
[   23.543208] Driver 'sd' needs updating - please use bus_type methods
[   23.543478] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[   23.543517] sd 0:0:0:0: [sda] Write Protect is off
[   23.543522] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.543575] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.543734] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[   23.543769] sd 0:0:0:0: [sda] Write Protect is off
[   23.543774] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.543828] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.543840]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   23.570963]  sda5 sda6 >
[   23.571541] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.572111] sd 1:0:0:0: [sdb] 40718160 512-byte hardware sectors (20848 MB)
[   23.572147] sd 1:0:0:0: [sdb] Write Protect is off
[   23.572153] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   23.572202] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.572355] sd 1:0:0:0: [sdb] 40718160 512-byte hardware sectors (20848 MB)
[   23.572389] sd 1:0:0:0: [sdb] Write Protect is off
[   23.572395] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   23.572443] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.572454]  sdb:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   23.576564] Uniform CD-ROM driver Revision: 3.20
[   23.576684] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   23.691237] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   23.869428] usb 3-2: configuration #1 chosen from 1 choice
[   23.874637] usbcore: registered new interface driver libusual
[   23.889601] Initializing USB Mass Storage driver...
[   23.899172] scsi2 : SCSI emulation for USB Mass Storage devices
[   23.901868] usbcore: registered new interface driver usb-storage
[   23.901879] USB Mass Storage support registered.
[   23.902178] usb-storage: device found at 2
[   23.902185] usb-storage: waiting for device to settle before scanning
[   25.161713]  sdb1
[   25.161893] sd 1:0:0:0: [sdb] Attached SCSI disk
[   25.192229] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.192276] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   25.192329] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   25.794160] Attempting manual resume
[   25.794173] swsusp: Resume From Partition 8:5
[   25.794176] PM: Checking swsusp image.
[   25.794485] PM: Resume from disk failed.
[   25.854974] kjournald starting.  Commit interval 5 seconds
[   25.855016] EXT3-fs: mounted filesystem with ordered data mode.
[   28.897541] usb-storage: device scan complete
[   28.905500] scsi 2:0:0:0: Direct-Access     HP       Photosmart 7400  1.00 PQ: 0 ANSI: 2
[   28.921566] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   28.921676] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   34.424789] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.475241] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.540679] Linux agpgart interface v0.102
[   34.629997] agpgart: Detected an Intel 845G Chipset.
[   34.634319] agpgart: AGP aperture is 64M @ 0xe0000000
[   34.913709] input: Power Button (FF) as /devices/virtual/input/input2
[   34.932495] ACPI: Power Button (FF) [PWRF]
[   34.932772] input: Power Button (CM) as /devices/virtual/input/input3
[   34.944334] ACPI: Power Button (CM) [PWRB]
[   34.944636] input: Sleep Button (CM) as /devices/virtual/input/input4
[   34.960426] ACPI: Sleep Button (CM) [SLPB]
[   35.029379] intel_rng: FWH not detected
[   35.197707] iTCO_vendor_support: vendor-support=0
[   35.260218] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   35.260579] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   35.260597] iTCO_wdt: No card detected
[   36.484393] nvidia: module license 'NVIDIA' taints kernel.
[   37.293831] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   39.265188] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input6
[   39.918071] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   39.918874] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   39.938377] parport_pc 00:0b: reported by Plug and Play ACPI
[   39.938442] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.005723] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0xB802
[   40.005772] usbcore: registered new interface driver usblp
[   40.229092] Linux video capture interface: v2.00
[   40.341718] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1425] STV(i): STV0680 camera found.
[   40.341806] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1465] STV(i): registered new video device: video0
[   40.341857] usbcore: registered new interface driver stv680
[   40.341867] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [usb_stv680_init:1546] STV(i): usb camera driver version v0.25 registering
[   40.341872] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: STV0680 USB Camera Driver v0.25
[   40.606264] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   40.606274] PCI: setting IRQ 9 as level-triggered
[   40.606279] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   40.606320] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   41.200494] intel8x0_measure_ac97_clock: measured 55406 usecs
[   41.200502] intel8x0: clocking to 48000
[   44.949035] lp0: using parport0 (interrupt-driven).
[   45.083631] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   45.713007] EXT3 FS on sda6, internal journal
[   47.412269] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.255525] No dock devices found.
[   50.336949] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   50.336961] apm: overridden by ACPI.
[   50.525588] ppdev: user-space parallel port driver
[   50.711455] audit(1234101809.981:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5068 profile="/usr/sbin/cupsd" namespace="default"
[   52.155370] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:374] STV(i): CIF is supported
[   52.172324] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:392] STV(i): Camera has 0 pictures.
[   52.246267] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv_init:419] STV(i): Video Mode set to CIF
[   54.276253] eth0: link down
[   54.509150] Bluetooth: Core ver 2.11
[   54.516549] NET: Registered protocol family 31
[   54.516563] Bluetooth: HCI device and connection manager initialized
[   54.516574] Bluetooth: HCI socket layer initialized
[   54.564436] Bluetooth: L2CAP ver 2.9
[   54.564447] Bluetooth: L2CAP socket layer initialized
[   54.636658] Bluetooth: RFCOMM socket layer initialized
[   54.637236] Bluetooth: RFCOMM TTY layer initialized
[   54.637254] Bluetooth: RFCOMM ver 1.8
[   57.572351] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   57.572953] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   57.573509] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  768.809874] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  770.975424] NET: Registered protocol family 17
[  775.642029] eth0: link down
[  777.403152] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  780.730558] NET: Registered protocol family 10
[  780.731878] lo: Disabled Privacy Extensions
[  795.560822] eth0: no IPv6 routers present
[  798.914737] UDF-fs: No VRS found
[  799.034681] ISO 9660 Extensions: Microsoft Joliet Level 1
[  799.242758] ISOFS: changing to secondary root
[ 1080.410553] usblp0: removed
[ 1081.551899] audit(1234102841.453:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6272 profile="/usr/sbin/cupsd" namespace="default"
[ 2806.924125] audit(1234104567.885:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6864 profile="/usr/sbin/cupsd" namespace="default"
[ 2840.128124] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 2855.230845] usb 3-1: device descriptor read/64, error -110
[ 2870.437613] usb 3-1: device descriptor read/64, error -110
[ 2870.653358] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 2885.756081] usb 3-1: device descriptor read/64, error -110
[ 2900.962734] usb 3-1: device descriptor read/64, error -110
[ 2901.178598] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 2906.197124] usb 3-1: device descriptor read/8, error -110
[ 2911.314318] usb 3-1: device descriptor read/8, error -110
[ 2911.528242] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 2916.546509] usb 3-1: device descriptor read/8, error -110
[ 2921.663682] usb 3-1: device descriptor read/8, error -110
[ 2921.766201] usb 3-1: USB disconnect, address 2
[ 2921.767465] scsi 2:0:0:0: Device offlined - not ready after error recovery
[ 2921.774333] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774370] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774380] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774389] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774396] scsi 2:0:0:0: [sdc] READ CAPACITY failed
[ 2921.774400] scsi 2:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2921.774408] scsi 2:0:0:0: [sdc] Sense not available.
[ 2921.774418] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774426] scsi 2:0:0:0: [sdc] Write Protect is off
[ 2921.774431] scsi 2:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 2921.774435] scsi 2:0:0:0: [sdc] Assuming drive cache: write through
[ 2921.774464] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774476] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774485] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774494] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774500] scsi 2:0:0:0: [sdc] READ CAPACITY failed
[ 2921.774504] scsi 2:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2921.774512] scsi 2:0:0:0: [sdc] Sense not available.
[ 2921.774519] scsi 2:0:0:0: rejecting I/O to dead device
[ 2921.774526] scsi 2:0:0:0: [sdc] Write Protect is off
[ 2921.774530] scsi 2:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 2921.774534] scsi 2:0:0:0: [sdc] Assuming drive cache: write through
[ 2921.877874] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 2921.997804] usb 3-1: device descriptor read/64, error -71
[ 2922.221821] usb 3-1: device descriptor read/64, error -71
[ 2922.437672] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 2922.559688] usb 3-1: device descriptor read/64, error -71
[ 2922.781324] usb 3-1: device descriptor read/64, error -71
[ 2922.997197] usb 3-1: new full speed USB device using uhci_hcd and address 6
[ 2923.408923] usb 3-1: device not accepting address 6, error -71
[ 2923.520861] usb 3-1: new full speed USB device using uhci_hcd and address 7
[ 2923.932586] usb 3-1: device not accepting address 7, error -71
[ 8425.810868] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 8425.997081] usb 4-1: configuration #1 chosen from 1 choice
[ 8821.347923] usb 4-1: USB disconnect, address 2
[13929.983776] usb 1-1: USB disconnect, address 2
[13929.983937] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [usb_stv680_remove_disconnected:1502] STV(i): STV0680 disconnected
[14164.279698] usb 1-1: new full speed USB device using uhci_hcd and address 3
[14164.598926] usb 1-1: configuration #1 chosen from 1 choice
[14164.604653] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1425] STV(i): STV0680 camera found.
[14164.604732] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1465] STV(i): registered new video device: video0
```

does it give any clues?
i have seen a driver for my cam which is completely different, but i have no clue how to compile it or use it!

---

### Post by josephdaniel on 2009-02-08
Hi,

Apparently the driver is working properly. There is no need to recompile or anything. The following two lines show that the driver is working and it should be present at /dev/video0

```
[14164.604653] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1425] STV(i): STV0680 camera found.
[14164.604732] /build/buildd/linux-2.6.24/drivers/media/video/stv680.c: [stv680_probe:1465] STV(i): registered new video device: video0
```

With the camera plugged, try this command to make sure the /dev/video0 entry is available:

```
ls /dev/video*
```

When you first said the camera was not working? What's the application you were using? I suggest you try camorama. I have tested my aiptek camera with this program and it's working.

Install camorama via the following
```
sudo apt-get install camorama
```

then run it from the console (camorama).

Please check these two steps and post back the results.

Joe

---

### Post by tonyuk123 on 2009-02-09
Hi,
When i try lsusb the cam is present and working.
I am at work so cant try the camorama just yet (windows here!)
The cam does work in cheese, but thats about it, I wanted to use it on a mesenger, but so far no luck, amsn,gyachi,kopete all dont work, the nearest is kopete, but it has picture(of sorts) but it is screwed, as if the vertical hold has gone.
I have seen another driver for an aiptek pencam but it needs compiling and installing, which so far i don't know how to do.
I have the files but no idea what exactly i should do with them.
Tony

btw
the driver i have found is spca5xx which is for the aiptek pencam.
although it seems to default to stv680
should i let it use the dfault as it only seems to work in cheese!
or should i try to compile/user the new driver?

---

### Post by Jyraya on 2010-06-08
> **pierrehenri said:**
> I was able to get it to work.
After you plug the webcam, you need to unmount the desktop camera icon, then unload the stv680 module and then reload it. My guess is there's some kind of conflict between the pictures mode and the webcam mode but I'm no expert.
Hello, i have the same pb but can't reload the modules, if anyone could gives me de good commands it will be very helpfull.

When i plug :

Jun  8 16:15:51 Ubunvince kernel: [141336.944040] usb 4-1: new full speed USB device using uhci_hcd and address 9
Jun  8 16:15:52 Ubunvince kernel: [141337.228232] usb 4-1: configuration #1 chosen from 1 choice
Jun  8 16:15:52 Ubunvince kernel: [141337.231161] stv680 [stv680_probe:1430] 
Jun  8 16:15:52 Ubunvince kernel: [141337.231163] STV(i): STV0680 camera found.
Jun  8 16:15:52 Ubunvince kernel: [141337.231217] stv680 [stv680_probe:1471] 
Jun  8 16:15:52 Ubunvince kernel: [141337.231218] STV(i): registered new video device: video0
Jun  8 16:15:52 Ubunvince kernel: [141337.273114] stv680 [stv_init:382] 
Jun  8 16:15:52 Ubunvince kernel: [141337.273116] STV(i): QVGA is supported
Jun  8 16:15:52 Ubunvince kernel: [141337.283112] stv680 [stv_init:398] 
Jun  8 16:15:52 Ubunvince kernel: [141337.283114] STV(i): Camera has 0 pictures.
Jun  8 16:15:52 Ubunvince kernel: [141337.325120] stv680 [stv_init:382] 
Jun  8 16:15:52 Ubunvince kernel: [141337.325122] STV(i): QVGA is supported
Jun  8 16:15:52 Ubunvince kernel: [141337.336120] stv680 [stv_init:398] 
Jun  8 16:15:52 Ubunvince kernel: [141337.336122] STV(i): Camera has 0 pictures.
Jun  8 16:15:52 Ubunvince kernel: [141337.441647] stv680 [usb_stv680_remove_disconnected:1508] 


lsusb :

Bus 004 Device 009: ID 0553:0202 STMicroelectronics Imaging Division (VLSI Vision) Aiptek PenCam 1

Then i unmount the desktop camera icon but i cant reload it properly...i dont know if im using it properly...

This gives me nothing :
vince@Ubunvince:~$ modprobe stv680
vince@Ubunvince:~$ 

Im still stuck.

Thanks if any one could help ! :)

---

### Post by guilloip on 2011-01-13
I have the same problem.
My Aiptek pencam 1 is not recognized as a webcam, only as a still photo device.

It used to be recognized by debian years ago, but now I am trying to use it under Ubuntu 10.04 as a webcam but programs can't see it.

FIRST:
I tried coding: "modprob stv680" and mod loaded and recognized the device, but non /dev/video* was created.
 
THEN:
I coded: "MAKEDEV video"
/dev/video0 and more were created, and looking at dmseg I foud my Aiptek cam was recognized and connected to /de/video0, but video programs still can not open it, as it there were no device at all.  Even though when I run them as root.

HELP!

---

### Post by guilloip on 2011-01-13
OK, Solved! Partially at least.

I followed the instructions to: Unmount USB device that GNOME mountted.
Unload STV680 driver and load it again.

I only can see it with camorama as root, but it works!

It is clear that there is a conflict between gnome and common scense.  Gnome, always gnome.  It is going too Window$.

THANKS!

---

