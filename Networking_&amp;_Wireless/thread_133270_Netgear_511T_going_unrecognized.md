---
title: "Netgear 511T going unrecognized?"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by Skye on 2006-02-19
Hey everyone.

I've reached a point where I don't think I can go any further, and I need some help.

I've needed wireless capabilities for some time, and today I went out and got a Netgear WG511T cardbus adapter for my laptop.  This was not an uninformed decision- I looked the card up on the site reccomended in the wireless card wiki page ([http://linux-wless.passys.nl]("http://linux-wless.passys.nl"),) which lists the  card as supposed, using the madwifi chipset.  I also checked the Ubuntu forums, which also lists the card as supported, but notes that some users have had problems.

So, I bring the card home, and install it on my windows partition- everything goes fine, so I know that the card works, and that the card slot works, which makes my problem even odder.

After confirming that it works in windows, I booted into linux, to see if it worked, and it just plain doesn't.  The problem seems to be that the card itself isn't recognized, neither in **lspci** nor in **cardctl ident**, nor in [B]lshw
[/B]

These are the steps I've taken to try and fix this:

-Installed the restricted-modules package for my kernel (at that point, it was the k7 flavor)  That didn't work.
-Installed the madwifi-ng source off their site, per the instructions on their site, and also per the instructions on the madwifi wiki here on the ubuntu wiki.
-Re-installed ubuntu entirely, with the card in the slot, and it was STILL not recognized.  Afterwards, I tried installing the restricted modules and the madwifi-ng source again, but had similar results.
-Tried all the things in the [wireless troubleshooting guide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide?") in the wiki related to hardware recognition.


lspci output:

```
spitfire@cerberus:/usr/src/madwifi-ng$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:05:09.0 CardBus bridge: Texas Instruments: Unknown device 8031

```

cardctl ident output:
```
spitfire@cerberus:/usr/src/madwifi-ng$ sudo cardctl ident
Socket 0:
  no product info available

```

The lshw output is far too long to post, but there is nothing in there pertaining to the carbus slot or the network card.

If this were a software problem, I'd be able to deal with it, but as it is, I can't get the computer to see the card.  I know the card works, and I know the slot works, but linux can't "see" it.  

So, does anyone have any suggestions?  I'd really appreciate any help anyone could offer, as this problem has stumped me.  Has anyone else had success getting this card recognized?

Thanks!

---

### Post by Lambert on 2006-02-19
What is the output of this command?

```
lsmod | grep pcm
```

---

### Post by Skye on 2006-02-19
Thanks for the reply!

```

spitfire@cerberus:~$ lsmod | grep pcm
pcmcia                 24584  2
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10120  2 snd_atiixp,snd_pcm

```

---

### Post by Lambert on 2006-02-19
It was just a quick thought but didn't see anything.

I don't know what's happening but it is not recognizing your card at all. So either the memory can't be read or something is not triggering the memory to be read.

Do you know anybody else that has a card you could try? This is just to check that the memory can be read on another card.

You can also look in to something called cis_speed setting for the pcmcia_core module. Do a google search and do some reading and also look at this post.

[http://ubuntuforums.org/showpost.php?p=687075&postcount=16](http://ubuntuforums.org/showpost.php?p=687075&postcount=16)

I'm also wondering if there is a problem with the bridge just before the socket (not a physical problem with it, but something that is just causing a problem between the socket and the bridge running linux).


 I would suggest looking into what cardbus bridge is in that path and do some searching on that and pcmcia or linux to see if there is something there. You can find the cardbus bridges with this command

lspci -v | grep -A 5 CardBus

There can be other things I'm not aware of, you have an uncommon problem from what I've seen here on this forum.

---

### Post by Skye on 2006-02-19
Thank you, thank you, thank you!

I googled the "cis_speed" term you mentioned, and found someone on the mandriva forums that had a similar issue- apparently, the cardbus socket on my laptop, (a Compaq Presario v2000) is built in such a way that you need to pass **pci=assign-busses** to the kernel at boot in order to get 32 bit cardbus cards recognized automatically.

I added that to my grub parameters, and the madwifi drivers I installed earlier kicked in automatically.  Thank you SO MUCH for pointing me in the right direction!

---

### Post by dickohead on 2006-02-26
I'm having the exact same problem on a different machine. Mine is an Arima, so the popularity of Linux on one of these will be much less than a compaq! I did try adding pci=assign-busses to grub, but it has had no affect.

The madwifi/atheros drivers are installed with my kernel.

I have tried searching for cis_speed but have come across nothing useful for my laptop. Is there anything else I can do to test if mine is even recognised?

---

### Post by Lambert on 2006-02-26
Run this command as it lists all recognized hardware for you pc.

sudo lshw

You can try limiting output by modifying command like this.

sudo lshw -C network

---

### Post by Skye on 2006-02-26
I've also found that the card itself will give you an indication if it's being recognized- while in linux, what are the two little lights on the card doing?  I *think* they work in the following way-

**Right light blinking-** Card is unrecognized by system- this is what I got before I passed pci=assign-busses to the kernel

**Right light solid-**  Card is recognized, but inacative in terms of network activity

**Lights alternate right/left/right/left-** Card is active and searching for/trying to connect to a network

**Both lights blink simultaneously-** network link established, and the card is sending/recieveing data.

**Both lights are dark-** you may have a defective card or a defective card slot.

Also, you could trying running ```
lspci |grep Atheros
``` in a terminal to see if the card is recognized... this command is similar to the command Lambert reccomended, though.

---

### Post by dickohead on 2006-02-26
I know my card works, but the lights never come in Linux. How wouyld I find out if the slot is unrecognised, and install a driver for it?

---

### Post by Skye on 2006-02-26
We need some more info, first.  What is the exact model name/number of your laptop?  

What does ```
lspci
``` give you in a terminal?

Also, please run the command Lambert suggested: ```
sudo lshw -C network
```

---

### Post by dickohead on 2006-02-27
Okay, sitting at my laptop now.

lspci gives me:
```

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03 )
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media I O] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev  a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa st Ethernet (rev 91)
0000:00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 0 1)
0000:00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 80)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M 661FX/M661MX/741/M741/760/M760 PCI/AGP

```

and

sudo lshw -C network gives me:
```

  *-network
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:25:1d:22:17
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.08 Jan. 22 2005 duplex=full ip=192.168.1.102 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:dfffc000-dfffcfff irq:10

```

Which I know tells me my card isn't there!

My laptop is an Arima W720-K8M good luck searching for any useful information on that model number! It's an Athlon 64 2800 with 512mb RAM, running 32bit Ubuntu Breezy.

---

### Post by Lambert on 2006-02-27
Let's check to see if all the correct modules are loaded for the slot. run this command and post output.

lsmod | grep core

---

### Post by dickohead on 2006-02-27
Alrighty! Booting between Windows and Linux here, Linux is so much faster!!! Lol. 

Okay lsmod | grep core gives me:
[code]
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               9184  1 snd
i2c_core               19728  2 i2c_acpi_ec,i2c_sis96x
usbcore               104316  4 usb_storage,ehci_hcd,ohci_hcd
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,sis5513
[/core]

And when I reboot/shutdown my computer it gives me an error stating that (this is a new error by the way) "[bunch of numbers] pcmcia_core unable to supply power" so I'm guessing that's my problem... hope it helps someone!

---

### Post by Skye on 2006-02-27
Could you post the output of

```
dmesg
```

---

### Post by dickohead on 2006-02-28
The output of dmesg is:
```

PI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 1e000000 (gap: 1e000000:e1 780000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro vga=771 quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1796.130 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour dummy device 80x25
[4294670.588000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.588000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.596000] Memory: 478596k/491328k available (1416k kernel code, 12100k re served, 762k data, 224k init, 0k highmem)
[4294670.596000] Checking if this processor honours the WP bit even in superviso r mode... Ok.
[4294670.596000] Calibrating delay loop... 3571.71 BogoMIPS (lpj=1785856)
[4294670.618000] Security Framework v1.0.0 initialized
[4294670.618000] SELinux:  Disabled at boot.
[4294670.618000] Mount-cache hash table entries: 512
[4294670.618000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 0 0000000 00000000 00000000 00000001
[4294670.618000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00 000000 00000000 00000000 00000001
[4294670.618000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/lin e)
[4294670.618000] CPU: L2 Cache: 512K (64 bytes/line)
[4294670.618000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000010  00000000 00000000 00000001
[4294670.618000] CPU: AMD Mobile AMD Athlon(tm) 64 Processor 2800+ stepping 00
[4294670.618000] Enabling fast FPU save and restore... done.
[4294670.618000] Enabling unmasked SIMD FPU exception support... done.
[4294670.618000] Checking 'hlt' instruction... OK.
[4294670.622000] Checking for popad bug... OK.
[4294670.622000] checking if image is initramfs... it is
[4294671.052000] Freeing initrd memory: 5172k freed
[4294671.053000] ACPI: Looking for DSDT in initrd... not found!
[4294671.100000]  not found!
[4294671.105000] ENABLING IO-APIC IRQs
[4294671.105000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294671.216000] NET: Registered protocol family 16
[4294671.216000] EISA bus registered
[4294671.216000] ACPI: bus type pci registered
[4294671.216000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[4294671.216000] PCI: Using configuration type 1
[4294671.216000] mtrr: v2.0 (20020519)
[4294671.216000] ACPI: Subsystem revision 20050729
[4294671.220000] ACPI: Interpreter enabled
[4294671.220000] ACPI: Using IOAPIC for interrupt routing
[4294671.221000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.221000] PCI: Probing PCI hardware (bus 00)
[4294671.221000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.221000] Uncovering SIS963 that hid as a SIS503 (compatible=0)
[4294671.221000] Enabling SiS 96x SMBus.
[4294671.222000] Boot video device is 0000:01:00.0
[4294671.232000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.233000] burst-mode-ec-10-Aug
[4294671.233000] ACPI: Embedded Controller [EC0] (gpe 25)
[4294671.235000] ACPI: PCI Interrupt Link [LNKA] (IRQs 7 *10 11 12 14 15)
[4294671.235000] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *10 11 12 14 15)
[4294671.235000] ACPI: PCI Interrupt Link [LNKC] (IRQs 7 10 *11 12 14 15)
[4294671.236000] ACPI: PCI Interrupt Link [LNKD] (IRQs 7 *10 11 12 14 15)
[4294671.236000] ACPI: PCI Interrupt Link [LNKE] (IRQs *7 10 11 12 14 15)
[4294671.236000] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 *10 11 12 14 15)
[4294671.236000] ACPI: PCI Interrupt Link [LNKG] (IRQs 7 10 11 12 14 15) *0, dis abled.
[4294671.236000] ACPI: PCI Interrupt Link [LNKH] (IRQs 7 *10 11 12 14 15)
[4294671.236000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.236000] pnp: PnP ACPI init
[4294671.238000] pnp: PnP ACPI: found 10 devices
[4294671.238000] PnPBIOS: Disabled by ACPI PNP
[4294671.238000] PCI: Using ACPI for IRQ routing
[4294671.238000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps , post a report
[4294671.241000] audit: initializing netlink socket (disabled)
[4294671.241000] audit: initialized
[4294671.241000] VFS: Disk quotas dquot_6.5.1
[4294671.241000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.241000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.241000] devfs: boot_options: 0x0
[4294671.241000] Initializing Cryptographic API
[4294671.241000] isapnp: Scanning for PnP cards...
[4294671.595000] isapnp: No Plug & Play device found
[4294671.609000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 i rq 1,12
[4294671.611000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.611000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.611000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ shari ng enabled
[4294671.613000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> I RQ 18
[4294671.613000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[4294671.613000] io scheduler noop registered
[4294671.613000] io scheduler anticipatory registered
[4294671.613000] io scheduler deadline registered
[4294671.613000] io scheduler cfq registered
[4294671.613000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294671.613000] EISA: Probing bus 0 at eisa.0
[4294671.613000] EISA: Detected 0 cards.
[4294671.613000] NET: Registered protocol family 2
[4294671.623000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294671.623000] TCP established hash table entries: 16384 (order: 5, 131072 byt es)
[4294671.623000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.623000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.623000] NET: Registered protocol family 8
[4294671.623000] NET: Registered protocol family 20
[4294671.623000] ACPI wakeup devices:
[4294671.623000] PCI0  MAC MC97 LID0
[4294671.623000] ACPI: (supports S0 S1 S3 S4 S5)
[4294671.623000] Freeing unused kernel memory: 224k freed
[4294671.634000] vesafb: framebuffer at 0xd0000000, mapped to 0xde880000, using 937k, total 16384k
[4294671.634000] vesafb: mode is 800x600x8, linelength=800, pages=15
[4294671.634000] vesafb: protected mode interface info at cbdd:0004
[4294671.634000] vesafb: scrolling: redraw
[4294671.634000] vesafb: Pseudocolor: size=6:6:6:6, shift=0:0:0:0
[4294671.637000] Console: switching to colour frame buffer device 100x37
[4294671.637000] fb0: VESA VGA frame buffer device
[4294671.646000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.673000] Capability LSM initialized
[4294672.681000] NET: Registered protocol family 1
[4294672.691000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.691000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294672.691000] ACPI: bus type ide registered
[4294672.697000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294672.697000] SIS5513: chipset revision 0
[4294672.697000] SIS5513: not 100% native mode: will probe irqs later
[4294672.697000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[4294672.697000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb: DMA
[4294672.697000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd: DMA
[4294672.697000] Probing IDE interface ide0...
[4294672.961000] hda: TOSHIBA MK6025GAS, ATA DISK drive
[4294673.573000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.573000] Probing IDE interface ide1...
[4294674.296000] hdc: TOSHIBA ODD-DVD SD-R6372, ATAPI CD/DVD-ROM drive
[4294674.908000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.908000] Probing IDE interface ide2...
[4294675.421000] Probing IDE interface ide3...
[4294675.933000] Probing IDE interface ide4...
[4294676.445000] Probing IDE interface ide5...
[4294676.959000] hda: max request size: 128KiB
[4294677.008000] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
[4294677.008000] hda: cache flushes supported
[4294677.008000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
[4294677.068000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294677.068000] Uniform CD-ROM driver Revision: 3.20
[4294677.277000] Attempting manual resume
[4294677.299000] swsusp: Suspend partition has wrong signature?
[4294677.350000] usbcore: registered new driver usbfs
[4294677.350000] usbcore: registered new driver hub
[4294677.351000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Dri ver (PCI)
[4294677.351000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> I RQ 20
[4294677.351000] ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS] USB 1.0  Controller
[4294677.351000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus num ber 1
[4294677.351000] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdffff000
[4294677.404000] hub 1-0:1.0: USB hub found
[4294677.404000] hub 1-0:1.0: 3 ports detected
[4294677.407000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> I RQ 21
[4294677.407000] ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS] USB 1.0  Controller (#2)
[4294677.407000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus num ber 2
[4294677.407000] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdfffe000
[4294677.460000] hub 2-0:1.0: USB hub found
[4294677.460000] hub 2-0:1.0: 3 ports detected
[4294677.476000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> I RQ 23
[4294677.476000] ehci_hcd 0000:00:03.3: Silicon Integrated Systems [SiS] USB 2.0  Controller
[4294677.476000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus num ber 3
[4294677.476000] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdfffd000
[4294677.476000] PCI: cache line size of 64 is not supported by device 0000:00:0 3.3
[4294677.476000] ehci_hcd 0000:00:03.3: USB 2.0 initialized, EHCI 1.00, driver 1 0 Dec 2004
[4294677.476000] hub 3-0:1.0: USB hub found
[4294677.476000] hub 3-0:1.0: 6 ports detected
[4294677.504000] sis900.c: v1.08.08 Jan. 22 2005
[4294677.504000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> I RQ 19
[4294677.505000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[4294677.514000] 0000:00:04.0: Using transceiver found at address 1 as default
[4294677.515000] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 19, 00:03:25:1d: 22:17.
[4294679.804000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294679.805000] ACPI: Thermal Zone [THRM] (33 C)
[4294679.943000] Attempting manual resume
[4294679.952000] swsusp: Suspend partition has wrong signature?
[4294679.979000] kjournald starting.  Commit interval 5 seconds
[4294679.979000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.426000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294684.342000] Adding 2642684k swap on /dev/hda3.  Priority:-1 extents:1
[4294684.543000] EXT3 FS on hda2, internal journal
[4294692.205000] lp: driver loaded but no devices found
[4294692.224000] mice: PS/2 mouse device common for all mice
[4294692.257000] ieee1394: Initialized config rom entry `ip1394'
[4294692.263000] SCSI subsystem initialized
[4294692.267000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294692.857000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x90 4713/0x10008
[4294692.859000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294693.082000] ts: Compaq touchscreen protocol output
[4294694.707000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294695.549000] cdrom: open failed.
[4294695.995000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294696.053000] NTFS volume version 3.1.
[4294697.392000] Linux agpgart interface v0.101 (c) Dave Jones
[4294697.399000] agpgart: Detected SiS 760 chipset
[4294697.412000] agpgart: AGP aperture is 4M @ 0xe0000000
[4294697.476000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294697.484000] shpchp: shpc_init : shpc_cap_offset == 0
[4294697.484000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294697.595000] i2c-sis96x version 1.0.0
[4294697.598000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[4294697.832000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> I RQ 18
[4294698.390000] intel8x0_measure_ac97_clock: measured 49540 usecs
[4294698.390000] intel8x0: clocking to 48000
[4294699.262000] Linux Kernel Card Services
[4294699.262000]   options:  [pci] [cardbus] [pm]
[4294699.273000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> I RQ 17
[4294699.273000] Yenta: CardBus bridge found at 0000:00:0a.0 [161f:2038]
[4294699.273000] Yenta: adjusting diagnostic: 40 -> 60
[4294699.273000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294699.273000] Yenta: Routing CardBus interrupts to PCI
[4294699.273000] Yenta TI: socket 0000:00:0a.0, mfunc 0x01001002, devctl 0x44
[4294699.374000] Yenta TI: socket 0000:00:0a.0 probing PCI interrupt failed, try ing to fix
[4294699.475000] Yenta TI: socket 0000:00:0a.0 no PCI interrupts. Fish. Please r eport.
[4294699.595000] Yenta: ISA IRQ mask 0x0000, PCI irq 0
[4294699.595000] Socket status: 00000000
[4294699.684000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294699.684000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 18 (level, low) -> I RQ 18
[4294699.684000] PCI: Via IRQ fixup for 0000:00:0c.0, from 11 to 2
[4294699.741000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfff98 00-dfff9fff]  Max Packet=[2048]
[4294701.008000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00032521380067cc]
[4294701.819000] Real Time Clock Driver v1.12
[4294701.979000] input: PC Speaker
[4294703.617000] NET: Registered protocol family 17
[4294705.608000] eth0: Media Link On 100mbps full-duplex
[4294715.805000] NET: Registered protocol family 10
[4294715.805000] Disabled Privacy Extensions on device c02eb280(lo)
[4294715.806000] IPv6 over IPv4 tunneling driver
[4294717.886000] ACPI: AC Adapter [AC] (on-line)
[4294717.924000] ACPI: Battery Slot [BAT1] (battery present)
[4294717.940000] ACPI: Power Button (FF) [PWRF]
[4294717.941000] ACPI: Lid Switch [LID0]
[4294717.941000] ACPI: Sleep Button (CM) [SLPB]
[4294717.941000] ACPI: Power Button (CM) [PWRB]
[4294718.025000] ibm_acpi: ec object not found
[4294725.965000] eth0: no IPv6 routers present
[4294726.269000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294726.269000] apm: overridden by ACPI.
[4294726.854000] cs: IO port probe 0x100-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d 7
[4294726.856000] cs: IO port probe 0xc00-0xcf7: clean.
[4294726.856000] cs: IO port probe 0xa00-0xaff: clean.
[4294727.215000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (versio n 1.40.4)
[4294727.223000] powernow-k8:    0 : fid 0x0 (800 MHz), vid 0x13 (1075 mV)
[4294727.223000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x8 (1350 mV)
[4294727.223000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x4 (1450 mV)
[4294727.224000] cpu_init done, current fid 0xa, vid 0x4
[4294728.042000] Bluetooth: Core ver 2.7
[4294728.042000] NET: Registered protocol family 31
[4294728.042000] Bluetooth: HCI device and connection manager initialized
[4294728.042000] Bluetooth: HCI socket layer initialized
[4294728.149000] Bluetooth: L2CAP ver 2.7
[4294728.149000] Bluetooth: L2CAP socket layer initialized
[4294728.178000] Bluetooth: RFCOMM ver 1.5
[4294728.178000] Bluetooth: RFCOMM socket layer initialized
[4294728.178000] Bluetooth: RFCOMM TTY layer initialized

```

Yeah, it's huge!

---

### Post by K.Mandla on 2006-02-28
Just as a side note, there are situations where PCMCIA cards are not recognized by Linux, as a consequence of the kernel (2.6.x). ...

[http://ubuntuforums.org/showthread.php?t=125334](http://ubuntuforums.org/showthread.php?t=125334)
[http://damnsmalllinux.org/wiki/index.php/Frequently_Asked_Questions](http://damnsmalllinux.org/wiki/index.php/Frequently_Asked_Questions)

(Check the question about DSL using the 2.6 kernel.)

As I understand it, it happens mostly in older machines, in conjunction with newer cards.

If you're willing to drop way, way back in the Ubuntu line, or if you're willing to try Slackware with the 2.4.31 kernel, you might be able to at least identify the problem.

Just an idea.

---

### Post by dickohead on 2006-02-28
The machine is an Athlon 64 - not 64Mhz, but 64BIT - as in new as shit!!! :)

But thank you for your links!!!

---

### Post by Skye on 2006-02-28
AH HA!

I think this will help:
[http://www.archivum.info/ubuntu-devel@lists.ubuntu.com/2005-09/msg00136.html]("http://www.archivum.info/ubuntu-devel@lists.ubuntu.com/2005-09/msg00136.html")

Specifically, 
> 
> * My CardBus does not function. I have an "ENE CD1410" CardBus 
> controller, and it does not recieve an IRQ and thus spams "unable to 
> apply power" messages all over the place. This particular CardBus is 
> used in many laptops (eg eMachines, Total Periperhals, Arima, many 
> others). It's a Kernel ACPI issue and has actually been fixed already in
> the 2.6.13 kernel (among numerous other things). 2.6.13 has been stable
> for a number of weeks now, so will Breezy use kernel 2.6.13 to resolve
> these show-stoppers? Please.


This seems to be at least similar to your issue.  If you upgrade to 2.6.13 (or even 2.6.14, there's a howto on how to do that [here)]("http://www.ubuntuforums.org/showthread.php?t=84174") your problems *may* be fixed.

Good Luck!

---

### Post by dickohead on 2006-02-28
Thank you very much! I'll keep you posted on how it goes!

---

### Post by dickohead on 2006-03-01
Alrighty then!!! We have progress!!! The light blinks now!! Woohoo!!! Now to get ndiswrapper working! Thanks so much guys!!!

---

### Post by dickohead on 2006-03-01
And it works!!!

After installing the 2.6.14 kernel and manually installing ndiswrapper as per the wiki - it all works and now i'm windows free on my laptop!!! THANK YOU!!!!!!!!

---

