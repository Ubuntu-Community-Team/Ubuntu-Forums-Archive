---
title: "Anyone having trouble in Natty with Intel cards?"
date: 2011-02-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ubuntu27 on 2011-02-22
I've been reading post of people who are having problems in Natty with nVidia video cards.

My question is "is there anyone having trouble with Intel or ATI?"

I would like to know that since one of my main laptops has Intel.

---

### Post by cariboo on 2011-02-22
ATI users are in the same boat as us Nvidia users when it comes to closed source drivers. My Intel powered netbook with 945 graphics chipset seems to be running quite well with very few problems.

Mind you I mostly am on IRC with the netbook, only occasionally opening firefox or chromium. I have the icons for my most used program in the panel, so I haven't had any problems with the menus so far.

---

### Post by pwzhangz on 2011-03-30
I have an Acer Aspire 5336-2460 with Intel GMA 4500MHD card.  Everything works great with 10.10.

With Natty, however, the screen was a total blank.  I. e., when I tried to boot with a Live Natty USB, the screen went into total dark after Natty booted into graphic moved (after the initial grub screen).

---

### Post by cariboo on 2011-03-30
Have you tried using the nomodeset option from the main Live CD menu? When booting from the Live CD, when you see the little man and keyboard, press the any key to bring up the menu, once you have selected your language, press F6 and select nomodeset, then press esc and enter.

---

### Post by tjeremiah on 2011-03-30
I have been testing since Alpha 1. My card is in my sig and everything has worked smoothly. No blank screen or screen tearing.

---

### Post by bzarnsy on 2011-03-31
dell dimension 4700
p4 3.2 gig
ati radeon x1300 pro
3 gigs ddr2

natty boots up ok but the screen goes blank for about 3 seconds
then on for about 30 seconds then blank and over and over again.
quite bothersome. what's up?

---

### Post by MacUntu on 2011-03-31
Core i5-560 on-die Intel HD Graphics - everything's fine.

---

### Post by jerrylamos on 2011-03-31
i845G seems to be running Natty 2D O.K.  Has had tons of problems and launchpad bugs ever since Intrepid but running now.  Classic "no effects" I ran briefly, just long enough to load Unity 2D from Synaptic.

This is intel "N10 family" whatever that is on a new netbook Acer Aspire one running Unity 3D. 

ati Xpress 200 runs Unity 3D.

ati mobility 7500 running Unity 2D O.K.

Now I'm not a Unity fan, it's just that this is Alpha/Beta time and that's what we're supposed to be testing.

Jerry

p.s.  OF COURSE, COMPIZ is still crashing at any time on Unity 3D usually manages to recover.  

Unity 2D doesn't use COMPIZ (I think?) avoiding tons and tons of problems and wasted processor cycles, and runs on all my intel and ati pc's.

Jerry

---

### Post by coffeecat on 2011-03-31
> **ubuntu27 said:**
> My question is "is there anyone having trouble with Intel or ATI?"

Laptop 1:

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```Unity/compiz fine.

Laptop 2: ATI Mobility Radeon HD4200 - Unity/compiz fine with open source driver.

Desktop: ATI Radeon HD4350 - Unity/compiz fine with open source driver.

---

### Post by KegHead on 2011-03-31
Hi!

No problems w/Intel.

KegHead

---

### Post by pwzhangz on 2011-03-31
> **cariboo907 said:**
> Have you tried using the nomodeset option from the main Live CD menu? When booting from the Live CD, when you see the little man and keyboard, press the any key to bring up the menu, once you have selected your language, press F6 and select nomodeset, then press esc and enter.

With the nomodeset option, I am able to boot into graphic mode, but only with 1024 x 768 resolution, and no Unity.

---

### Post by bzarnsy on 2011-03-31
just now installed beta 1
still have same screen goes off for 3 seconds on for 30 seconds
thing going on. no problem of this type with any previous releases.
again  what's up?
ati radeon x1300 pro 256meg
dell dimension 4700
p4 3.2 gig w/ hyperthreading

natty seems to be looking good but it's hard to check it out with
the screen going black all the time.
any suggestions or should i just be patient?

---

### Post by cariboo on 2011-03-31
What type of monitor do you have connected to your system? I have a noname crt connected to a system that sometimes has the same problem. If you open a terminal and type:

```
dmesg
```

you should see an EDID error of some sort. If you paste the error in your next post, we may be able to help you.

---

### Post by bzarnsy on 2011-04-01
here's dmesg

[    0.723607] pnp 00:09: [io  0x6400-0x64fe]
[    0.723612] pnp 00:09: [io  0x6500-0x65fe]
[    0.723616] pnp 00:09: [io  0x6600-0x66fe]
[    0.723621] pnp 00:09: [io  0x6700-0x67fe]
[    0.723627] pnp 00:09: [io  0x6800-0x68fe]
[    0.723632] pnp 00:09: [io  0x6900-0x69fe]
[    0.723638] pnp 00:09: [io  0x6a00-0x6afe]
[    0.723644] pnp 00:09: [io  0x6b00-0x6bfe]
[    0.723648] pnp 00:09: [io  0x6c00-0x6cfe]
[    0.723653] pnp 00:09: [io  0x6d00-0x6dfe]
[    0.723658] pnp 00:09: [io  0x6e00-0x6efe]
[    0.723663] pnp 00:09: [io  0x6f00-0x6ffe]
[    0.723668] pnp 00:09: [io  0xa000-0xa0fe]
[    0.723672] pnp 00:09: [io  0xa100-0xa1fe]
[    0.723676] pnp 00:09: [io  0xa200-0xa2fe]
[    0.723681] pnp 00:09: [io  0xa300-0xa3fe]
[    0.723685] pnp 00:09: [io  0xa400-0xa4fe]
[    0.723689] pnp 00:09: [io  0xa500-0xa5fe]
[    0.723694] pnp 00:09: [io  0xa600-0xa6fe]
[    0.723698] pnp 00:09: [io  0xa700-0xa7fe]
[    0.723702] pnp 00:09: [io  0xa800-0xa8fe]
[    0.723707] pnp 00:09: [io  0xa900-0xa9fe]
[    0.723711] pnp 00:09: [io  0xaa00-0xaafe]
[    0.723715] pnp 00:09: [io  0xab00-0xabfe]
[    0.723720] pnp 00:09: [io  0xac00-0xacfe]
[    0.723724] pnp 00:09: [io  0xad00-0xadfe]
[    0.723728] pnp 00:09: [io  0xae00-0xaefe]
[    0.723733] pnp 00:09: [io  0xaf00-0xaffe]
[    0.724330] system 00:09: [io  0x0100-0x01fe] could not be reserved
[    0.724336] system 00:09: [io  0x0200-0x0277] has been reserved
[    0.724342] system 00:09: [io  0x0280-0x02e7] has been reserved
[    0.724347] system 00:09: [io  0x02e8-0x02ef] has been reserved
[    0.724353] system 00:09: [io  0x02f0-0x02f7] has been reserved
[    0.724358] system 00:09: [io  0x02f8-0x02ff] has been reserved
[    0.724364] system 00:09: [io  0x0300-0x0377] could not be reserved
[    0.724370] system 00:09: [io  0x0380-0x03bb] has been reserved
[    0.724375] system 00:09: [io  0x03c0-0x03e7] has been reserved
[    0.724381] system 00:09: [io  0x03f6-0x03f7] could not be reserved
[    0.724387] system 00:09: [io  0x0400-0x04cf] has been reserved
[    0.724392] system 00:09: [io  0x04d2-0x057f] has been reserved
[    0.724398] system 00:09: [io  0x0580-0x0677] has been reserved
[    0.724403] system 00:09: [io  0x0680-0x0777] has been reserved
[    0.724409] system 00:09: [io  0x0780-0x07bb] has been reserved
[    0.724414] system 00:09: [io  0x07c0-0x07ff] has been reserved
[    0.724420] system 00:09: [io  0x08e0-0x08ff] has been reserved
[    0.724425] system 00:09: [io  0x0900-0x09fe] has been reserved
[    0.724431] system 00:09: [io  0x0a00-0x0afe] has been reserved
[    0.724437] system 00:09: [io  0x0b00-0x0bfe] has been reserved
[    0.724443] system 00:09: [io  0x0c80-0x0caf] has been reserved
[    0.724448] system 00:09: [io  0x0cb0-0x0cbf] has been reserved
[    0.724454] system 00:09: [io  0x0cc0-0x0cf7] has been reserved
[    0.724460] system 00:09: [io  0x0d00-0x0dfe] has been reserved
[    0.724465] system 00:09: [io  0x0e00-0x0efe] has been reserved
[    0.724471] system 00:09: [io  0x0f00-0x0ffe] has been reserved
[    0.724477] system 00:09: [io  0x2000-0x20fe] has been reserved
[    0.724483] system 00:09: [io  0x2100-0x21fe] has been reserved
[    0.724489] system 00:09: [io  0x2200-0x22fe] has been reserved
[    0.724494] system 00:09: [io  0x2300-0x23fe] has been reserved
[    0.724500] system 00:09: [io  0x2400-0x24fe] has been reserved
[    0.724506] system 00:09: [io  0x2500-0x25fe] has been reserved
[    0.724512] system 00:09: [io  0x2600-0x26fe] has been reserved
[    0.724517] system 00:09: [io  0x2700-0x27fe] has been reserved
[    0.724523] system 00:09: [io  0x2800-0x28fe] has been reserved
[    0.724529] system 00:09: [io  0x2900-0x29fe] has been reserved
[    0.724535] system 00:09: [io  0x2a00-0x2afe] has been reserved
[    0.724540] system 00:09: [io  0x2b00-0x2bfe] has been reserved
[    0.724546] system 00:09: [io  0x2c00-0x2cfe] has been reserved
[    0.724552] system 00:09: [io  0x2d00-0x2dfe] has been reserved
[    0.724558] system 00:09: [io  0x2e00-0x2efe] has been reserved
[    0.724565] system 00:09: [io  0x2f00-0x2ffe] has been reserved
[    0.724572] system 00:09: [io  0x5000-0x50fe] has been reserved
[    0.724580] system 00:09: [io  0x5100-0x51fe] has been reserved
[    0.724589] system 00:09: [io  0x5200-0x52fe] has been reserved
[    0.724596] system 00:09: [io  0x5300-0x53fe] has been reserved
[    0.724603] system 00:09: [io  0x5400-0x54fe] has been reserved
[    0.724610] system 00:09: [io  0x5500-0x55fe] has been reserved
[    0.724616] system 00:09: [io  0x5600-0x56fe] has been reserved
[    0.724622] system 00:09: [io  0x5700-0x57fe] has been reserved
[    0.724629] system 00:09: [io  0x5800-0x58fe] has been reserved
[    0.724635] system 00:09: [io  0x5900-0x59fe] has been reserved
[    0.724642] system 00:09: [io  0x5a00-0x5afe] has been reserved
[    0.724648] system 00:09: [io  0x5b00-0x5bfe] has been reserved
[    0.724655] system 00:09: [io  0x5c00-0x5cfe] has been reserved
[    0.724662] system 00:09: [io  0x5d00-0x5dfe] has been reserved
[    0.724672] system 00:09: [io  0x5e00-0x5efe] has been reserved
[    0.724679] system 00:09: [io  0x5f00-0x5ffe] has been reserved
[    0.724686] system 00:09: [io  0x6000-0x60fe] has been reserved
[    0.724692] system 00:09: [io  0x6100-0x61fe] has been reserved
[    0.724699] system 00:09: [io  0x6200-0x62fe] has been reserved
[    0.724707] system 00:09: [io  0x6300-0x63fe] has been reserved
[    0.724714] system 00:09: [io  0x6400-0x64fe] has been reserved
[    0.724721] system 00:09: [io  0x6500-0x65fe] has been reserved
[    0.724728] system 00:09: [io  0x6600-0x66fe] has been reserved
[    0.724736] system 00:09: [io  0x6700-0x67fe] has been reserved
[    0.724743] system 00:09: [io  0x6800-0x68fe] has been reserved
[    0.724749] system 00:09: [io  0x6900-0x69fe] has been reserved
[    0.724756] system 00:09: [io  0x6a00-0x6afe] has been reserved
[    0.724762] system 00:09: [io  0x6b00-0x6bfe] has been reserved
[    0.724769] system 00:09: [io  0x6c00-0x6cfe] has been reserved
[    0.724775] system 00:09: [io  0x6d00-0x6dfe] has been reserved
[    0.724782] system 00:09: [io  0x6e00-0x6efe] has been reserved
[    0.724789] system 00:09: [io  0x6f00-0x6ffe] has been reserved
[    0.724795] system 00:09: [io  0xa000-0xa0fe] has been reserved
[    0.724802] system 00:09: [io  0xa100-0xa1fe] has been reserved
[    0.724808] system 00:09: [io  0xa200-0xa2fe] has been reserved
[    0.724815] system 00:09: [io  0xa300-0xa3fe] has been reserved
[    0.724825] system 00:09: [io  0xa400-0xa4fe] has been reserved
[    0.724833] system 00:09: [io  0xa500-0xa5fe] has been reserved
[    0.724840] system 00:09: [io  0xa600-0xa6fe] has been reserved
[    0.724846] system 00:09: [io  0xa700-0xa7fe] has been reserved
[    0.724853] system 00:09: [io  0xa800-0xa8fe] has been reserved
[    0.724860] system 00:09: [io  0xa900-0xa9fe] has been reserved
[    0.724867] system 00:09: [io  0xaa00-0xaafe] has been reserved
[    0.724874] system 00:09: [io  0xab00-0xabfe] has been reserved
[    0.724881] system 00:09: [io  0xac00-0xacfe] has been reserved
[    0.724888] system 00:09: [io  0xad00-0xadfe] has been reserved
[    0.724895] system 00:09: [io  0xae00-0xaefe] has been reserved
[    0.724902] system 00:09: [io  0xaf00-0xaffe] has been reserved
[    0.724909] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.724915] system 00:09: [mem 0xfeda0000-0xfedacfff] has been reserved
[    0.724923] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.725042] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.725119] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.725133] pnp: PnP ACPI: found 11 devices
[    0.725136] ACPI: ACPI bus type pnp unregistered
[    0.725143] PnPBIOS: Disabled by ACPI PNP
[    0.763891] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.763903] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.763910] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.763916] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.763924] pci 0000:00:01.0:   bridge window [mem 0xdfd00000-0xdfefffff]
[    0.763931] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.763939] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.763945] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.763954] pci 0000:00:1c.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.763961] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.763971] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.763977] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.763986] pci 0000:00:1e.0:   bridge window [mem 0xdfb00000-0xdfbfffff]
[    0.764013] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.764053] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.764063] pci 0000:00:01.0: setting latency timer to 64
[    0.764076] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.764084] pci 0000:00:1c.0: setting latency timer to 64
[    0.764095] pci 0000:00:1e.0: setting latency timer to 64
[    0.764102] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.764108] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.764113] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.764118] pci_bus 0000:01: resource 1 [mem 0xdfd00000-0xdfefffff]
[    0.764123] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.764128] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.764133] pci_bus 0000:02: resource 1 [mem 0xdfc00000-0xdfcfffff]
[    0.764139] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.764144] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.764149] pci_bus 0000:03: resource 1 [mem 0xdfb00000-0xdfbfffff]
[    0.764154] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.764159] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.764225] NET: Registered protocol family 2
[    0.764394] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.764843] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.765479] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.765818] TCP: Hash tables configured (established 131072 bind 65536)
[    0.765822] TCP reno registered
[    0.765828] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.765842] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.766118] NET: Registered protocol family 1
[    0.766280] pci 0000:01:00.0: Boot video device
[    0.766304] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[    0.766315] PCI: CLS 64 bytes, default 64
[    0.766354] Simple Boot Flag at 0x7a set to 0x1
[    0.766686] cpufreq-nforce2: No nForce2 chipset.
[    0.766931] audit: initializing netlink socket (disabled)
[    0.766947] type=2000 audit(1301690305.760:1): initialized
[    0.780716] highmem bounce pool size: 64 pages
[    0.780730] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.784676] VFS: Disk quotas dquot_6.5.2
[    0.784809] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.786354] fuse init (API version 7.16)
[    0.786554] msgmni has been set to 1651
[    0.787041] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.787093] io scheduler noop registered
[    0.787097] io scheduler deadline registered
[    0.787131] io scheduler cfq registered (default)
[    0.787334] pcieport 0000:00:01.0: setting latency timer to 64
[    0.787389] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.787482] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.787540] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.787697] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.787750] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.788077] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.864044] ACPI: Power Button [VBTN]
[    0.864186] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.864195] ACPI: Power Button [PWRF]
[    0.864656] ACPI: acpi_idle registered with cpuidle
[    0.901750] ERST: Table is not found!
[    0.901895] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.922359] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.922374] Freeing initrd memory: 12512k freed
[    0.922830] isapnp: Scanning for PnP cards...
[    1.275937] isapnp: No Plug & Play device found
[    1.298977] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.299469] Linux agpgart interface v0.103
[    1.301603] brd: module loaded
[    1.302514] loop: module loaded
[    1.302655] i2c-core: driver [adp5520] using legacy suspend method
[    1.302658] i2c-core: driver [adp5520] using legacy resume method
[    1.302797] ata_piix 0000:00:1f.1: version 2.13
[    1.302813] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.302865] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.303381] scsi0 : ata_piix
[    1.303524] scsi1 : ata_piix
[    1.303597] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.303601] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.303665] ata_piix 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    1.303673] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.303773] ata2: port disabled. ignoring.
[    1.456044] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.456583] scsi2 : ata_piix
[    1.456695] scsi3 : ata_piix
[    1.456767] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    1.456771] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    1.457374] Fixed MDIO Bus: probed
[    1.457431] PPP generic driver version 2.4.2
[    1.457513] tun: Universal TUN/TAP device driver, 1.6
[    1.457516] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.457654] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.457687] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.457706] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.457711] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.457772] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.457919] ehci_hcd 0000:00:1d.7: debug port 1
[    1.461820] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.461843] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[    1.476018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.476218] hub 1-0:1.0: USB hub found
[    1.476225] hub 1-0:1.0: 8 ports detected
[    1.476344] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.476363] uhci_hcd: USB Universal Host Controller Interface driver
[    1.476403] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.476414] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.476419] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.476477] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.476534] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[    1.476725] hub 2-0:1.0: USB hub found
[    1.476732] hub 2-0:1.0: 2 ports detected
[    1.476839] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.476848] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.476852] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.476908] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.480314] ata1.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[    1.480320] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.480522] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    1.480723] hub 3-0:1.0: USB hub found
[    1.480729] hub 3-0:1.0: 2 ports detected
[    1.480833] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.480842] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.480846] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.480905] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.480973] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    1.481156] hub 4-0:1.0: USB hub found
[    1.481162] hub 4-0:1.0: 2 ports detected
[    1.481261] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.481270] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.481274] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.481348] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.481414] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    1.481604] hub 5-0:1.0: USB hub found
[    1.481610] hub 5-0:1.0: 2 ports detected
[    1.481790] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.484605] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.484615] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.484799] mousedev: PS/2 mouse device common for all mice
[    1.484996] rtc_cmos 00:05: RTC can wake from S4
[    1.488348] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.488377] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    1.488503] device-mapper: uevent: version 1.0.3
[    1.488623] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    1.488724] device-mapper: multipath: version 1.2.0 loaded
[    1.488731] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.488842] EISA: Probing bus 0 at eisa.0
[    1.488846] EISA: Cannot allocate resource for mainboard
[    1.488849] Cannot allocate resource for EISA slot 1
[    1.488852] Cannot allocate resource for EISA slot 2
[    1.488863] Cannot allocate resource for EISA slot 5
[    1.488867] Cannot allocate resource for EISA slot 6
[    1.488877] EISA: Detected 0 cards.
[    1.488968] cpuidle: using governor ladder
[    1.488973] cpuidle: using governor menu
[    1.489403] TCP cubic registered
[    1.489594] NET: Registered protocol family 10
[    1.490516] NET: Registered protocol family 17
[    1.490542] Registering the dns_resolver key type
[    1.490599] Using IPI No-Shortcut mode
[    1.490749] PM: Hibernation image not present or could not be loaded.
[    1.490766] registered taskstats version 1
[    1.491023]   Magic number: 7:763:648
[    1.491034] scsi_host host2: hash matches
[    1.491037] scsi host2: hash matches
[    1.491083] processor LNXCPU:01: hash matches
[    1.491120] rtc_cmos 00:05: setting system clock to 2011-04-01 20:38:27 UTC (1301690307)
[    1.491124] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.491126] EDD information not available.
[    1.512206] ata1.00: configured for UDMA/33
[    1.513981] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[    1.516735] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.516740] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.516897] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.517004] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.621073] ata3.00: ATA-8: WDC WD1600AAJB-00J3A0, 01.03E01, max UDMA/133
[    1.621077] ata3.00: 312581808 sectors, multi 8: LBA48 
[    1.637130] ata3.00: configured for UDMA/133
[    1.637266] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600AAJB-0 01.0 PQ: 0 ANSI: 5
[    1.637460] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.637533] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.637581] sd 2:0:0:0: [sda] Write Protect is off
[    1.637587] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.637643] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.696467]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.697098] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.764017] Refined TSC clocksource calibration: 3191.999 MHz.
[    1.764023] Switching to clocksource tsc
[    2.028016] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    2.552013] usb 4-2: new low speed USB device using uhci_hcd and address 3
[    5.644117] Freeing unused kernel memory: 700k freed
[    5.644592] Write protecting the kernel text: 5188k
[    5.644655] Write protecting the kernel read-only data: 2148k
[    5.682598] udev[71]: starting version 167
[    5.912115] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    5.912122] e100: Copyright(c) 1999-2006 Intel Corporation
[    5.912187] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.976384] e100 0000:03:08.0: PME# disabled
[    5.977579] e100 0000:03:08.0: eth0: addr 0xdfbff000, irq 20, MAC addr 00:13:20:6b:ce:4c
[    6.036166] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input2
[    6.036361] generic-usb 0003:06A3:8020.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1d.2-1/input0
[    6.140114] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input3
[    6.140416] generic-usb 0003:06A3:8020.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1d.2-1/input1
[    6.155659] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4
[    6.155889] generic-usb 0003:046D:C521.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-2/input0
[    6.185164] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input5
[    6.185426] generic-usb 0003:046D:C521.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-2/input1
[    6.185463] usbcore: registered new interface driver usbhid
[    6.185468] usbhid: USB HID core driver
[    6.455498] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    7.908152] Adding 3068408k swap on /dev/sda2.  Priority:-1 extents:1 across:3068408k 
[    8.407864] udev[264]: starting version 167
[    8.647662] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    9.644596] intel_rng: Firmware space is locked read-only. If you can't or
[    9.644600] intel_rng: don't want to disable this in firmware setup, and if
[    9.644603] intel_rng: you are certain that your system has a functional
[    9.644605] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    9.651702] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.729189] [drm] Initialized drm 1.1.0 20060810
[    9.862383] parport_pc 00:06: reported by Plug and Play ACPI
[    9.862445] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   10.066428] lp0: using parport0 (interrupt-driven).
[   10.198060] ppdev: user-space parallel port driver
[   10.442912] [drm] radeon defaulting to kernel modesetting.
[   10.442919] [drm] radeon kernel modesetting enabled.
[   10.443010] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.443021] radeon 0000:01:00.0: setting latency timer to 64
[   10.445557] [drm] initializing kernel modesetting (RV515 0x1002:0x7183).
[   10.445609] [drm] register mmio base: 0xDFDE0000
[   10.445613] [drm] register mmio size: 65536
[   10.445821] ATOM BIOS: 113
[   10.445848] [drm] Generation 2 PCI interface, using max accessible memory
[   10.445859] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
[   10.445866] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[   10.445914] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.445919] [drm] Driver supports precise vblank timestamp query.
[   10.445978] radeon 0000:01:00.0: irq 42 for MSI/MSI-X
[   10.445988] radeon 0000:01:00.0: radeon: using MSI.
[   10.446028] [drm] radeon: irq initialized.
[   10.446421] [drm] Detected VRAM RAM=256M, BAR=256M
[   10.446428] [drm] RAM width 128bits DDR
[   10.446577] [TTM] Zone  kernel: Available graphics memory: 429488 kiB.
[   10.446582] [TTM] Zone highmem: Available graphics memory: 1546948 kiB.
[   10.446586] [TTM] Initializing pool allocator.
[   10.446616] [drm] radeon: 256M of VRAM memory ready
[   10.446621] [drm] radeon: 512M of GTT memory ready.
[   10.446659] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.448757] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   10.450646] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   10.450677] radeon 0000:01:00.0: WB enabled
[   10.450780] [drm] Loading R500 Microcode
[   10.501530] [drm] radeon: ring at 0x0000000010001000
[   10.501565] [drm] ring test succeeded in 6 usecs
[   10.501875] [drm] radeon: ib pool ready.
[   10.502079] [drm] ib test succeeded in 0 usecs
[   10.502093] failed to evaluate ATIF got AE_BAD_PARAMETER
[   10.506515] [drm] Radeon Display Connectors
[   10.506522] [drm] Connector 0:
[   10.506526] [drm]   DVI-I
[   10.506529] [drm]   HPD1
[   10.506534] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   10.506538] [drm]   Encoders:
[   10.506541] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   10.506545] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[   10.506549] [drm] Connector 1:
[   10.506552] [drm]   S-video
[   10.506555] [drm]   Encoders:
[   10.506558] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   10.506562] [drm] Connector 2:
[   10.506565] [drm]   VGA
[   10.506569] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   10.506573] [drm]   Encoders:
[   10.506576] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   10.655418] [drm] fb mappable at 0xC00C0000
[   10.655422] [drm] vram apper at 0xC0000000
[   10.655424] [drm] size 8294400
[   10.655427] [drm] fb depth is 24
[   10.655429] [drm]    pitch is 7680
[   10.655884] Console: switching to colour frame buffer device 240x67
[   10.655978] fb0: radeondrmfb frame buffer device
[   10.655982] drm: registered panic notifier
[   10.656022] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
[   10.862535] type=1400 audit(1301690316.866:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=483 comm="apparmor_parser"
[   10.862557] type=1400 audit(1301690316.866:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=400 comm="apparmor_parser"
[   10.863610] type=1400 audit(1301690316.866:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=483 comm="apparmor_parser"
[   10.863630] type=1400 audit(1301690316.866:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=400 comm="apparmor_parser"
[   10.864316] type=1400 audit(1301690316.870:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=483 comm="apparmor_parser"
[   10.864344] type=1400 audit(1301690316.870:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=400 comm="apparmor_parser"
[   12.542300] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   12.542343] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   12.968031] intel8x0_measure_ac97_clock: measured 55827 usecs (2690 samples)
[   12.968036] intel8x0: clocking to 48000
[   13.592294] type=1400 audit(1301690319.598:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=704 comm="apparmor_parser"
[   13.593344] type=1400 audit(1301690319.598:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=704 comm="apparmor_parser"
[   13.593932] type=1400 audit(1301690319.598:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=704 comm="apparmor_parser"
[   13.713386] type=1400 audit(1301690319.718:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=703 comm="apparmor_parser"
[   16.577125] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.580145] e100 0000:03:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   16.592347] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   18.885057] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   24.527305] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   27.040010] eth0: no IPv6 routers present
[  336.278650] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  336.285901] SGI XFS Quota Management subsystem
[  336.314143] JFS: nTxBlock = 8192, nTxLock = 65536
[  336.377417] NTFS driver 2.1.30 [Flags: R/O MODULE].
[  336.416192] QNX4 filesystem 0.2.3 registered.
[  336.506576] Btrfs loaded
[  336.851137] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  337.312781] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[  337.749699] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[  338.109484] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  340.729588] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[  342.341869] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
bzarnsy@bzarnsy-Dimension-4700:~$

---

### Post by executorvs on 2011-04-15
I know it's a little late, but on my laptop which uses an intel GMA 4500mhd compiz has problems with handling certain commands. the easiest one to run into is the brightness setting which freezes the interface. it's not a new problem and may be restricted to Acer Timelines, otherwise apart from a little choppiness with certain video files all seems ok. I haven't tested the 2D desktop yet to see if it will still fix the brightness issue.

---

