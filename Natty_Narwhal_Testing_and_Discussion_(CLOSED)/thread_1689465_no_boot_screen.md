---
title: "no boot screen"
date: 2011-02-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-02-16
just installed 15/2 daily build when trying to boot goes through bios boot screen then it goes to a black screen with a blinking cursor on the left side of the screen. I have an ati 6950 card installed on an asus dual core system I am writing this from yesterdays live cd I have no idea why I cant get a screen by the way sda is windows 7 sdb is ubuntu 
regards ron

---

### Post by cariboo on 2011-02-16
Could you please clarify what your problem is, I read it as not seeing a grub boot menu. or is the system booting, but not displaying the desktop.

---

### Post by rbrick49 on 2011-02-17
****cariboo I just installed from yesterdays build ubuntu natty after installing new graphics card ati 6950 when I use the live cd it works ok but in low graphics but when I try to install from live boot disc or other option direct install ,I get a black screen with blinking cursor at top left side of screen,also I noticed when rebooting from install a big water  mark on left side of screen.ubuntu as I see it should at least give me low graphics as did the live disc but no it doesnt I had to reinstall windows as it shot it out the window i am at a loss here or is my repoitiry not up to date i am an Aussie living in Thailand so maybe repos not uptodate mate ubuntu has allways worked for me this has me at a loss, even with new graphics card I should get low resolution, your thoughts mate
regards Ronnie

---

### Post by ronacc on 2011-02-17
from the grub menu hit e and remove quiet splash and vthandoff=7 from the bootline and then hit whatever key combination its says to use to boot and see what happens , that should give some text output during boot to give you some info as to where its hanging .

---

### Post by rbrick49 on 2011-02-17
ronacc i dont get any boot screen it just goes through the asus bios setup then goes to a black screen there is something relly wrong and I am stumped
regards ronnie

---

### Post by ronacc on 2011-02-17
boot your live cd and take a look at your install , in /boot look to make sure your kernel stuff is there ( vmlinuz , initrd etc ) and in /boot/grub have a look at grub.cfg to see if it makes sense ( correct uuid , drive# etc ) . if you are not even getting a grub menu grub may have gotten installed to the wrong place , try d/l'ing boot-info-script [http://ubuntuforums.org/showthread.php?t=1676235 ](http://ubuntuforums.org/showthread.php?t=1676235 ) and see what that tells you ( you can run it from the live cd ) .

---

### Post by rbrick49 on 2011-02-17
ok ronacc checking now get back to you shortly

---

### Post by cariboo on 2011-02-17
If Ubuntu is the only os on your system, you won't see a grub menu, to see it hold down the shift key during post.

---

### Post by Harry33 on 2011-02-17
> **rbrick49 said:**
> ****cariboo I just installed from yesterdays build ubuntu natty after installing new graphics card ati 6950 when
...
regards Ronnie

So you do have quite a new graphics card: ATI Radeon HD6950.
Those 6*** series ATI cards (Northern Islands) need the newest open source drivers.
ATM there is not recent enough in Natty repos.
It should be v. 6.14.
You can find one from the xorg-edgers PPA. Download it from there.
To install that you need at least to get to the console or failsafe graphics mode (with vesa driver).

Read this too:
[http://www.phoronix.com/scan.php?page=news_item&px=OTA3Nw](http://www.phoronix.com/scan.php?page=news_item&px=OTA3Nw)

---

### Post by rbrick49 on 2011-02-17
this is what I dont understand when I run live cd it works fine but in low graphics mode because of my card but when i do a full install to my hard drive it goes through ok but when I reboot after install no grub menu just a black screen it should run in low graphics

---

### Post by rbrick49 on 2011-02-17
heres dmeg

```

[    3.307354] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    3.307356] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    3.307415] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.307460] pnp 00:02: [dma 4]
[    3.307462] pnp 00:02: [io  0x0000-0x000f]
[    3.307464] pnp 00:02: [io  0x0081-0x0083]
[    3.307465] pnp 00:02: [io  0x0087]
[    3.307467] pnp 00:02: [io  0x0089-0x008b]
[    3.307469] pnp 00:02: [io  0x008f]
[    3.307471] pnp 00:02: [io  0x00c0-0x00df]
[    3.307501] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    3.307512] pnp 00:03: [io  0x0070-0x0071]
[    3.307522] pnp 00:03: [irq 8]
[    3.307558] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    3.307567] pnp 00:04: [io  0x0061]
[    3.307600] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    3.307609] pnp 00:05: [io  0x00f0-0x00ff]
[    3.307618] pnp 00:05: [irq 13]
[    3.307648] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    3.308812] pnp 00:06: [io  0x0378-0x037f]
[    3.308817] pnp 00:06: [irq 7]
[    3.308819] pnp 00:06: [dma 0 disabled]
[    3.309138] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    3.309175] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    3.309212] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    3.309848] pnp 00:08: [io  0x03f8-0x03ff]
[    3.309853] pnp 00:08: [irq 4]
[    3.309855] pnp 00:08: [dma 0 disabled]
[    3.309949] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    3.310075] pnp 00:09: [io  0x0060]
[    3.310077] pnp 00:09: [io  0x0064]
[    3.310079] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    3.310081] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    3.310141] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    3.310143] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    3.310146] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.310230] pnp 00:0a: [io  0x0010-0x001f]
[    3.310232] pnp 00:0a: [io  0x0022-0x003f]
[    3.310234] pnp 00:0a: [io  0x0062-0x0063]
[    3.310236] pnp 00:0a: [io  0x0065-0x006f]
[    3.310238] pnp 00:0a: [io  0x0072-0x007f]
[    3.310240] pnp 00:0a: [io  0x0080]
[    3.310241] pnp 00:0a: [io  0x0084-0x0086]
[    3.310243] pnp 00:0a: [io  0x0088]
[    3.310245] pnp 00:0a: [io  0x008c-0x008e]
[    3.310247] pnp 00:0a: [io  0x0090-0x009f]
[    3.310249] pnp 00:0a: [io  0x00a2-0x00bf]
[    3.310250] pnp 00:0a: [io  0x00b1]
[    3.310252] pnp 00:0a: [io  0x00e0-0x00ef]
[    3.310254] pnp 00:0a: [io  0x04d0-0x04d1]
[    3.310256] pnp 00:0a: [io  0x040b]
[    3.310257] pnp 00:0a: [io  0x04d6]
[    3.310259] pnp 00:0a: [io  0x0c00-0x0c01]
[    3.310261] pnp 00:0a: [io  0x0c14]
[    3.310263] pnp 00:0a: [io  0x0c50-0x0c51]
[    3.310265] pnp 00:0a: [io  0x0c52]
[    3.310267] pnp 00:0a: [io  0x0c6c]
[    3.310268] pnp 00:0a: [io  0x0c6f]
[    3.310270] pnp 00:0a: [io  0x0cd0-0x0cd1]
[    3.310272] pnp 00:0a: [io  0x0cd2-0x0cd3]
[    3.310274] pnp 00:0a: [io  0x0cd4-0x0cd5]
[    3.310276] pnp 00:0a: [io  0x0cd6-0x0cd7]
[    3.310277] pnp 00:0a: [io  0x0cd8-0x0cdf]
[    3.310279] pnp 00:0a: [io  0x0b00-0x0b3f]
[    3.310281] pnp 00:0a: [io  0x0800-0x089f]
[    3.310283] pnp 00:0a: [io  0x0b20-0x0b2f]
[    3.310285] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    3.310287] pnp 00:0a: [io  0x0900-0x090f]
[    3.310289] pnp 00:0a: [io  0x0910-0x091f]
[    3.310294] pnp 00:0a: [io  0xfe00-0xfefe]
[    3.310296] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    3.310298] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
[    3.310300] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    3.310393] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    3.310396] system 00:0a: [io  0x040b] has been reserved
[    3.310398] system 00:0a: [io  0x04d6] has been reserved
[    3.310401] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    3.310403] system 00:0a: [io  0x0c14] has been reserved
[    3.310409] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    3.310411] system 00:0a: [io  0x0c52] has been reserved
[    3.310414] system 00:0a: [io  0x0c6c] has been reserved
[    3.310416] system 00:0a: [io  0x0c6f] has been reserved
[    3.310419] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    3.310421] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    3.310424] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    3.310426] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    3.310429] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    3.310431] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    3.310434] system 00:0a: [io  0x0800-0x089f] has been reserved
[    3.310436] system 00:0a: [io  0x0b20-0x0b2f] has been reserved
[    3.310439] system 00:0a: [io  0x0900-0x090f] has been reserved
[    3.310442] system 00:0a: [io  0x0910-0x091f] has been reserved
[    3.310445] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    3.310448] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    3.310451] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    3.310453] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    3.310457] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.310618] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
[    3.310620] pnp 00:0b: [io  0x0230-0x023f]
[    3.310622] pnp 00:0b: [io  0x0290-0x029f]
[    3.310624] pnp 00:0b: [io  0x0300-0x030f]
[    3.310625] pnp 00:0b: [io  0x0a30-0x0a3f]
[    3.310681] system 00:0b: [io  0x0230-0x023f] has been reserved
[    3.310684] system 00:0b: [io  0x0290-0x029f] has been reserved
[    3.310686] system 00:0b: [io  0x0300-0x030f] has been reserved
[    3.310688] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    3.310691] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.310740] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    3.310800] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    3.310803] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.311269] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    3.311271] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    3.311273] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    3.311275] pnp 00:0d: [mem 0x00100000-0xcfffffff]
[    3.311277] pnp 00:0d: [mem 0xfed45000-0xffffffff]
[    3.311344] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    3.311347] system 00:0d: [mem 0x000c0000-0x000cffff] has been reserved
[    3.311349] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    3.311352] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
[    3.311355] system 00:0d: [mem 0xfed45000-0xffffffff] could not be reserved
[    3.311358] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    3.311463] pnp: PnP ACPI: found 14 devices
[    3.311465] ACPI: ACPI bus type pnp unregistered
[    3.317782] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    3.317786] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    3.317790] pci 0000:00:02.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    3.317793] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.317797] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    3.317800] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    3.317803] pci 0000:00:06.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    3.317806] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    3.317810] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    3.317812] pci 0000:00:14.4:   bridge window [io  disabled]
[    3.317817] pci 0000:00:14.4:   bridge window [mem disabled]
[    3.317821] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    3.317843] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.317847] pci 0000:00:02.0: setting latency timer to 64
[    3.317852] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.317855] pci 0000:00:06.0: setting latency timer to 64
[    3.317864] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    3.317866] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    3.317868] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    3.317870] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    3.317874] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    3.317877] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff]
[    3.317879] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    3.317881] pci_bus 0000:01: resource 1 [mem 0xfbe00000-0xfbefffff]
[    3.317884] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.317887] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    3.317889] pci_bus 0000:02: resource 1 [mem 0xfbf00000-0xfbffffff]
[    3.317891] pci_bus 0000:02: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    3.317894] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    3.317896] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
```

---

### Post by rbrick49 on 2011-02-17
full dmeg

```

[    3.306259] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    3.306259] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
[    3.306259] NetLabel: Initializing
[    3.306259] NetLabel:  domain hash size = 128
[    3.306259] NetLabel:  protocols = UNLABELED CIPSOv4
[    3.306259] NetLabel:  unlabeled traffic allowed by default
[    3.306259] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    3.306259] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    3.306259] Switching to clocksource hpet
[    3.306259] Switched to NOHz mode on CPU #0
[    3.306259] Switched to NOHz mode on CPU #1
[    3.307002] AppArmor: AppArmor Filesystem Enabled
[    3.307034] pnp: PnP ACPI init
[    3.307055] ACPI: bus type pnp registered
[    3.307181] pnp 00:00: [bus 00-ff]
[    3.307184] pnp 00:00: [io  0x0cf8-0x0cff]
[    3.307187] pnp 00:00: [io  0x0000-0x0cf7 window]
[    3.307189] pnp 00:00: [io  0x0d00-0xffff window]
[    3.307191] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    3.307193] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    3.307195] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
[    3.307198] pnp 00:00: [mem 0xf0000000-0xfed44fff window]
[    3.307264] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    3.307354] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    3.307356] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    3.307415] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.307460] pnp 00:02: [dma 4]
[    3.307462] pnp 00:02: [io  0x0000-0x000f]
[    3.307464] pnp 00:02: [io  0x0081-0x0083]
[    3.307465] pnp 00:02: [io  0x0087]
[    3.307467] pnp 00:02: [io  0x0089-0x008b]
[    3.307469] pnp 00:02: [io  0x008f]
[    3.307471] pnp 00:02: [io  0x00c0-0x00df]
[    3.307501] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    3.307512] pnp 00:03: [io  0x0070-0x0071]
[    3.307522] pnp 00:03: [irq 8]
[    3.307558] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    3.307567] pnp 00:04: [io  0x0061]
[    3.307600] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    3.307609] pnp 00:05: [io  0x00f0-0x00ff]
[    3.307618] pnp 00:05: [irq 13]
[    3.307648] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    3.308812] pnp 00:06: [io  0x0378-0x037f]
[    3.308817] pnp 00:06: [irq 7]
[    3.308819] pnp 00:06: [dma 0 disabled]
[    3.309138] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    3.309175] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    3.309212] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    3.309848] pnp 00:08: [io  0x03f8-0x03ff]
[    3.309853] pnp 00:08: [irq 4]
[    3.309855] pnp 00:08: [dma 0 disabled]
[    3.309949] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    3.310075] pnp 00:09: [io  0x0060]
[    3.310077] pnp 00:09: [io  0x0064]
[    3.310079] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    3.310081] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    3.310141] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    3.310143] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    3.310146] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.310230] pnp 00:0a: [io  0x0010-0x001f]
[    3.310232] pnp 00:0a: [io  0x0022-0x003f]
[    3.310234] pnp 00:0a: [io  0x0062-0x0063]
[    3.310236] pnp 00:0a: [io  0x0065-0x006f]
[    3.310238] pnp 00:0a: [io  0x0072-0x007f]
[    3.310240] pnp 00:0a: [io  0x0080]
[    3.310241] pnp 00:0a: [io  0x0084-0x0086]
[    3.310243] pnp 00:0a: [io  0x0088]
[    3.310245] pnp 00:0a: [io  0x008c-0x008e]
[    3.310247] pnp 00:0a: [io  0x0090-0x009f]
[    3.310249] pnp 00:0a: [io  0x00a2-0x00bf]
[    3.310250] pnp 00:0a: [io  0x00b1]
[    3.310252] pnp 00:0a: [io  0x00e0-0x00ef]
[    3.310254] pnp 00:0a: [io  0x04d0-0x04d1]
[    3.310256] pnp 00:0a: [io  0x040b]
[    3.310257] pnp 00:0a: [io  0x04d6]
[    3.310259] pnp 00:0a: [io  0x0c00-0x0c01]
[    3.310261] pnp 00:0a: [io  0x0c14]
[    3.310263] pnp 00:0a: [io  0x0c50-0x0c51]
[    3.310265] pnp 00:0a: [io  0x0c52]
[    3.310267] pnp 00:0a: [io  0x0c6c]
[    3.310268] pnp 00:0a: [io  0x0c6f]
[    3.310270] pnp 00:0a: [io  0x0cd0-0x0cd1]
[    3.310272] pnp 00:0a: [io  0x0cd2-0x0cd3]
[    3.310274] pnp 00:0a: [io  0x0cd4-0x0cd5]
[    3.310276] pnp 00:0a: [io  0x0cd6-0x0cd7]
[    3.310277] pnp 00:0a: [io  0x0cd8-0x0cdf]
[    3.310279] pnp 00:0a: [io  0x0b00-0x0b3f]
[    3.310281] pnp 00:0a: [io  0x0800-0x089f]
[    3.310283] pnp 00:0a: [io  0x0b20-0x0b2f]
[    3.310285] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    3.310287] pnp 00:0a: [io  0x0900-0x090f]
[    3.310289] pnp 00:0a: [io  0x0910-0x091f]
[    3.310294] pnp 00:0a: [io  0xfe00-0xfefe]
[    3.310296] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    3.310298] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
[    3.310300] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    3.310393] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    3.310396] system 00:0a: [io  0x040b] has been reserved
[    3.310398] system 00:0a: [io  0x04d6] has been reserved
[    3.310401] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    3.310403] system 00:0a: [io  0x0c14] has been reserved
[    3.310409] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    3.310411] system 00:0a: [io  0x0c52] has been reserved
[    3.310414] system 00:0a: [io  0x0c6c] has been reserved
[    3.310416] system 00:0a: [io  0x0c6f] has been reserved
[    3.310419] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    3.310421] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    3.310424] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    3.310426] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    3.310429] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    3.310431] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    3.310434] system 00:0a: [io  0x0800-0x089f] has been reserved
[    3.310436] system 00:0a: [io  0x0b20-0x0b2f] has been reserved
[    3.310439] system 00:0a: [io  0x0900-0x090f] has been reserved
[    3.310442] system 00:0a: [io  0x0910-0x091f] has been reserved
[    3.310445] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    3.310448] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    3.310451] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    3.310453] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    3.310457] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.310618] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
[    3.310620] pnp 00:0b: [io  0x0230-0x023f]
[    3.310622] pnp 00:0b: [io  0x0290-0x029f]
[    3.310624] pnp 00:0b: [io  0x0300-0x030f]
[    3.310625] pnp 00:0b: [io  0x0a30-0x0a3f]
[    3.310681] system 00:0b: [io  0x0230-0x023f] has been reserved
[    3.310684] system 00:0b: [io  0x0290-0x029f] has been reserved
[    3.310686] system 00:0b: [io  0x0300-0x030f] has been reserved
[    3.310688] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    3.310691] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.310740] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    3.310800] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    3.310803] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.311269] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    3.311271] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    3.311273] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    3.311275] pnp 00:0d: [mem 0x00100000-0xcfffffff]
[    3.311277] pnp 00:0d: [mem 0xfed45000-0xffffffff]
[    3.311344] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    3.311347] system 00:0d: [mem 0x000c0000-0x000cffff] has been reserved
[    3.311349] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    3.311352] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
[    3.311355] system 00:0d: [mem 0xfed45000-0xffffffff] could not be reserved
[    3.311358] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    3.311463] pnp: PnP ACPI: found 14 devices
[    3.311465] ACPI: ACPI bus type pnp unregistered
[    3.317782] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    3.317786] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    3.317790] pci 0000:00:02.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    3.317793] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.317797] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    3.317800] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    3.317803] pci 0000:00:06.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    3.317806] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    3.317810] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    3.317812] pci 0000:00:14.4:   bridge window [io  disabled]
[    3.317817] pci 0000:00:14.4:   bridge window [mem disabled]
[    3.317821] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    3.317843] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.317847] pci 0000:00:02.0: setting latency timer to 64
[    3.317852] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.317855] pci 0000:00:06.0: setting latency timer to 64
[    3.317864] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    3.317866] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    3.317868] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    3.317870] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    3.317874] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    3.317877] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff]
[    3.317879] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    3.317881] pci_bus 0000:01: resource 1 [mem 0xfbe00000-0xfbefffff]
[    3.317884] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.317887] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    3.317889] pci_bus 0000:02: resource 1 [mem 0xfbf00000-0xfbffffff]
[    3.317891] pci_bus 0000:02: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    3.317894] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    3.317896] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    3.317898] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    3.317901] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    3.317903] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xdfffffff]
[    3.317905] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed44fff]
[    3.317940] NET: Registered protocol family 2
[    3.318190] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    3.320209] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    3.323841] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.324326] TCP: Hash tables configured (established 524288 bind 65536)
[    3.324329] TCP reno registered
[    3.324355] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    3.324440] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    3.324612] NET: Registered protocol family 1
[    3.490033] pci 0000:01:00.0: Boot video device
[    3.490041] PCI: CLS 64 bytes, default 64
[    3.491146] PCI-DMA: Disabling AGP.
[    3.491235] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    3.491237] PCI-DMA: using GART IOMMU.
[    3.491240] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    3.494216] Scanning for low memory corruption every 60 seconds
[    3.494334] audit: initializing netlink socket (disabled)
[    3.494345] type=2000 audit(1298014542.490:1): initialized
[    3.507329] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.509336] VFS: Disk quotas dquot_6.5.2
[    3.509400] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.510101] fuse init (API version 7.16)
[    3.510205] msgmni has been set to 15998
[    3.510496] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.510499] io scheduler noop registered
[    3.510501] io scheduler deadline registered
[    3.510540] io scheduler cfq registered (default)
[    3.510685] pcieport 0000:00:02.0: setting latency timer to 64
[    3.510719] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    3.510815] pcieport 0000:00:06.0: setting latency timer to 64
[    3.510840] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    3.510926] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.510949] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.511132] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    3.511137] ACPI: Power Button [PWRB]
[    3.511189] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    3.511192] ACPI: Power Button [PWRF]
[    3.511361] ACPI: acpi_idle registered with cpuidle
[    3.630461] ERST: Table is not found!
[    3.630552] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.651224] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.980768] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.990335] Linux agpgart interface v0.103
[    3.991636] brd: module loaded
[    3.992221] loop: module loaded
[    3.992336] i2c-core: driver [adp5520] using legacy suspend method
[    3.992338] i2c-core: driver [adp5520] using legacy resume method
[    3.992541] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.992574] pata_acpi 0000:00:14.1: setting latency timer to 64
[    3.992973] Fixed MDIO Bus: probed
[    3.993005] PPP generic driver version 2.4.2
[    3.993061] tun: Universal TUN/TAP device driver, 1.6
[    3.993062] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.993157] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.993212] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.993239] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    3.993291] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    4.020036] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    4.020055] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    4.020069] ehci_hcd 0000:00:12.2: debug port 1
[    4.020092] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbdff000
[    4.040027] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    4.040138] hub 1-0:1.0: USB hub found
[    4.040142] hub 1-0:1.0: 6 ports detected
[    4.040275] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.040286] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.040327] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    4.070044] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    4.070057] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    4.070070] ehci_hcd 0000:00:13.2: debug port 1
[    4.070090] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbdfa800
[    4.090021] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    4.090115] hub 2-0:1.0: USB hub found
[    4.090118] hub 2-0:1.0: 6 ports detected
[    4.090218] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.090264] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.090277] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    4.090328] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    4.090373] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbdfe000
[    4.154114] hub 3-0:1.0: USB hub found
[    4.154124] hub 3-0:1.0: 3 ports detected
[    4.154245] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.154257] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    4.154296] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    4.154337] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbdfd000
[    4.214115] hub 4-0:1.0: USB hub found
[    4.214124] hub 4-0:1.0: 3 ports detected
[    4.214245] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.214256] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.214295] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    4.214343] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbdfc000
[    4.274114] hub 5-0:1.0: USB hub found
[    4.274124] hub 5-0:1.0: 3 ports detected
[    4.274245] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.274258] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.274297] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    4.274338] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbdfb000
[    4.334121] hub 6-0:1.0: USB hub found
[    4.334131] hub 6-0:1.0: 3 ports detected
[    4.334250] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.334262] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    4.334301] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    4.334343] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbdf9000
[    4.360025] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    4.394123] hub 7-0:1.0: USB hub found
[    4.394133] hub 7-0:1.0: 2 ports detected
[    4.394219] uhci_hcd: USB Universal Host Controller Interface driver
[    4.394330] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    4.394707] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.394713] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.394838] mousedev: PS/2 mouse device common for all mice
[    4.394962] rtc_cmos 00:03: RTC can wake from S4
[    4.430073] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.430099] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.430191] device-mapper: uevent: version 1.0.3
[    4.430264] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    4.430357] device-mapper: multipath: version 1.2.0 loaded
[    4.430359] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.430498] cpuidle: using governor ladder
[    4.430500] cpuidle: using governor menu
[    4.430758] TCP cubic registered
[    4.430890] NET: Registered protocol family 10
[    4.431365] NET: Registered protocol family 17
[    4.431385] Registering the dns_resolver key type
[    4.431411] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ (2 cpu cores) (version 2.20.00)
[    4.431470] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0xc
[    4.431472] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xe
[    4.431474] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x10
[    4.431475] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x10
[    4.431477] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x10
[    4.431479] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
[    4.431621] PM: Hibernation image not present or could not be loaded.
[    4.431633] registered taskstats version 1
[    4.431889]   Magic number: 15:97:572
[    4.431981] rtc_cmos 00:03: setting system clock to 2011-02-18 07:35:44 UTC (1298014544)
[    4.431984] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.431985] EDD information not available.
[    4.433523] Freeing unused kernel memory: 952k freed
[    4.433914] Write protecting the kernel read-only data: 10240k
[    4.434758] Freeing unused kernel memory: 216k freed
[    4.439640] Freeing unused kernel memory: 1452k freed
[    4.465287] udev[102]: starting version 167
[    4.530068] scsi0 : pata_atiixp
[    4.538559] scsi1 : pata_atiixp
[    4.539274] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    4.539277] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    4.545250] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.545278] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.545319] r8169 0000:02:00.0: setting latency timer to 64
[    4.545366] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    4.545806] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xffffc9000178e000, 00:24:8c:d6:ab:ef, XID 1c4000c0 IRQ 42
[    4.545815] ahci 0000:00:11.0: version 3.0
[    4.545828] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.545939] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    4.545943] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    4.547288] scsi2 : ahci
[    4.548432] scsi3 : ahci
[    4.549382] scsi4 : ahci
[    4.550669] scsi5 : ahci
[    4.550818] ata3: SATA max UDMA/133 abar m1024@0xfbdff800 port 0xfbdff900 irq 22
[    4.550822] ata4: SATA max UDMA/133 abar m1024@0xfbdff800 port 0xfbdff980 irq 22
[    4.550826] ata5: SATA max UDMA/133 abar m1024@0xfbdff800 port 0xfbdffa00 irq 22
[    4.550829] ata6: SATA max UDMA/133 abar m1024@0xfbdff800 port 0xfbdffa80 irq 22
[    4.720382] ata2.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100
[    4.760383] ata2.00: configured for UDMA/100
[    4.765343] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
[    4.769507] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.769510] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.769646] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.769725] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    4.850031] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    4.900083] ata4: SATA link down (SStatus 0 SControl 300)
[    5.100033] ata3: softreset failed (device not ready)
[    5.100038] ata3: applying SB600 PMP SRST workaround and retrying
[    5.100056] ata6: softreset failed (device not ready)
[    5.100061] ata6: applying SB600 PMP SRST workaround and retrying
[    5.100080] ata5: softreset failed (device not ready)
[    5.100083] ata5: applying SB600 PMP SRST workaround and retrying
[    5.300040] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.300065] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.300084] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.301012] ata5.00: ATA-8: ST3250318AS, CC37, max UDMA/133
[    5.301014] ata5.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.301039] ata3.00: ATA-8: ST3250318AS, CC37, max UDMA/133
[    5.301041] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.301534] ata6.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB02, max UDMA/100
[    5.302124] ata5.00: configured for UDMA/133
[    5.302209] ata3.00: configured for UDMA/133
[    5.302342] scsi 2:0:0:0: Direct-Access     ATA      ST3250318AS      CC37 PQ: 0 ANSI: 5
[    5.302489] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    5.302526] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    5.302536] sd 2:0:0:0: [sda] Write Protect is off
[    5.302539] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.302559] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.302642] scsi 4:0:0:0: Direct-Access     ATA      ST3250318AS      CC37 PQ: 0 ANSI: 5
[    5.302782] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    5.302847] sd 4:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    5.302894] sd 4:0:0:0: [sdb] Write Protect is off
[    5.302897] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.302918] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.303462] ata6.00: configured for UDMA/100
[    5.305464]  sdb: sdb1
[    5.305751] sd 4:0:0:0: [sdb] Attached SCSI disk
[    5.306285]  sda: sda1
[    5.306541] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.307263] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB02 PQ: 0 ANSI: 5
[    5.310580] sr1: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.310693] sr 5:0:0:0: Attached scsi CD-ROM sr1
[    5.310772] sr 5:0:0:0: Attached scsi generic sg3 type 5
[    5.570026] usb 5-3: new full speed USB device using ohci_hcd and address 2
[    5.810223] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input2
[    5.810327] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-3/input0
[    5.814587] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.1/input/input3
[    5.814791] generic-usb 0003:046D:C52B.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-3/input1
[    5.823135] generic-usb 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-3/input2
[    5.823150] usbcore: registered new interface driver usbhid
[    5.823152] usbhid: USB HID core driver
[    6.100025] usb 6-1: new full speed USB device using ohci_hcd and address 2
[    6.305342] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.0/input/input4
[    6.305469] generic-usb 0003:046D:C526.0004: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-1/input0
[    6.313180] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.1/input/input5
[    6.313309] generic-usb 0003:046D:C526.0005: input,hiddev0,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.1-1/input1
[    6.654119] Btrfs loaded
[    6.659586] xor: automatically using best checksumming function: generic_sse
[    6.700016]    generic_sse:  8167.600 MB/sec
[    6.700018] xor: using function: generic_sse (8167.600 MB/sec)
[    6.702542] device-mapper: dm-raid45: initialized v0.2594b
[    8.636222] ISO 9660 Extensions: Microsoft Joliet Level 3
[    8.678946] ISO 9660 Extensions: RRIP_1991A
[    8.888606] aufs 2.1-standalone.tree-38-rcN-20110207
[    8.963784] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   52.511355] udev[1271]: starting version 167
[   59.123065] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   59.600030] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   59.692353] MCE: In-kernel MCE decoding enabled.
[   60.205706] Linux video capture interface: v2.00
[   60.409378] EDAC MC: Ver: 2.1.0 Feb 10 2011
[   60.503132] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   60.503304] SP5100 TCO timer: Watchdog reboot not detected.
[   60.503406] SP5100 TCO timer: initialized (0xffffc900017a20f0). heartbeat=60 sec (nowayout=0)
[   60.710769] parport_pc 00:06: reported by Plug and Play ACPI
[   60.710833] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   60.715444] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0809)
[   60.730854] input: UVC Camera (046d:0809) as /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/input/input6
[   60.730963] usbcore: registered new interface driver uvcvideo
[   60.730965] USB Video Class driver (v1.0.0)
[   60.928449] EDAC amd64_edac: v3.3.0
[   60.929758] EDAC amd64: DRAM ECC disabled.
[   60.929767] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   60.929768]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   60.929770]  (Note that use of the override may cause unknown side effects.)
[   61.887068] ppdev: user-space parallel port driver
[   62.802985] r8169 0000:02:00.0: eth0: link down
[   62.802992] r8169 0000:02:00.0: eth0: link down
[   62.805756] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   63.871718] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x7611
[   63.871772] usbcore: registered new interface driver usblp
[   64.662181] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   64.791262] set resolution quirk: cval->res = 384
[   64.791458] usbcore: registered new interface driver snd-usb-audio
[   64.794187] r8169 0000:02:00.0: eth0: link up
[   64.795124] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   64.954278] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   64.954352] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[   64.954376] HDA Intel 0000:01:00.1: setting latency timer to 64
[   66.852945] lp0: using parport0 (interrupt-driven).
[   72.688247] usb 1-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   75.710027] eth0: no IPv6 routers present
[  103.967264] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
[  398.003899] mtrr: no MTRR for d0000000,1000000 found 
```

---

### Post by ronacc on 2011-02-17
if its not booting where did you get the dmesg from ? the live cd ?

---

### Post by rbrick49 on 2011-02-17
yes

---

### Post by ronacc on 2011-02-17
are you able to look at your install from the live cd ?

---

### Post by cariboo on 2011-02-17
@rbrick49

Have you tried re-installing grub yet? If not when running the live CD, open a terminal and type the following commands:

[LIST=1]
[*]sudo mount /dev/sdXx /mnt
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

Where /dev/sdXx = the partion your Ubuntu install is on. Once at the root prompt, type:

```
grub-install /dev/sda
```

Once the above command has finished type:

```
update-grub
```

After update-grub has run, press Ctrl-d twice to exit, then reboot.

---

### Post by rbrick49 on 2011-02-17
cariboo
it wont even take the mount code from terminal on live cd I have windows on sda and ubuntu on sdb i am just wonderin I downloaded daily build from top of page not down the side to alternative but I guess they are the same

---

### Post by ronacc on 2011-02-18
If you can't mount it from terminal or see it listed in nautilus as a drive with the live cd your install went bad some how , try d/l'ing another live cd and reinstall , any version should be ok desktop or alternate , just make sure that if you are i386 you get the right architecture , 64 bit systems will work with either .

---

### Post by rbrick49 on 2011-02-18
well folks I have fixed the problem sort of, I remove the 6950 graphics card and run ubuntu on the old onboard graphics card ubuntu installs ok that way. i know its not the right way but it works the 6950 card is not letting ubuntu show any graphics or splash screen

---

### Post by Harry33 on 2011-02-20
> **Harry33 said:**
> So you do have quite a new graphics card: ATI Radeon HD6950.
Those 6*** series ATI cards (Northern Islands) need the newest open source drivers.
ATM there is not recent enough in Natty repos.
It should be v. 6.14.
You can find one from the xorg-edgers PPA. Download it from there.
To install that you need at least to get to the console or failsafe graphics mode (with vesa driver).

Read this too:
[http://www.phoronix.com/scan.php?page=news_item&px=OTA3Nw](http://www.phoronix.com/scan.php?page=news_item&px=OTA3Nw)

The new open source ati drivers (xserver-xorg-video-ati) version 6.14 is in Natty repos right now.
Here:
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-video-ati/1:6.14.0-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-video-ati/1:6.14.0-0ubuntu1)

---

### Post by poonforce on 2011-02-20
i also tried to install natty narwhal from live cd, but my monitor shows error "OUT OF RANGE".

---

### Post by cariboo on 2011-02-20
> **poonforce said:**
> i also tried to install natty narwhal from live cd, but my monitor shows error "OUT OF RANGE".

If you are getting out of range errors, check the horizontal and vertical refresh rates in /etc/X11/xorg.conf to see if they match the monitor manufacturers specifications.

---

### Post by jcer93705 on 2011-03-26
> **rbrick49 said:**
> just installed 15/2 daily build when trying to boot goes through bios boot screen then it goes to a black screen with a blinking cursor on the left side of the screen. I have an ati 6950 card installed on an asus dual core system I am writing this from yesterdays live cd I have no idea why I cant get a screen by the way sda is windows 7 sdb is ubuntu 
regards ron

Hello I am running ati 6950 2gb video and installed driver from ati. It's working great! Just installed my os once again this time making a partition instead running off c: drive. The ubunt 10.10 mavrikk work and booted without ati drivers when I installed it. After words I installed all the update and then vid drivers. How about you?

---

