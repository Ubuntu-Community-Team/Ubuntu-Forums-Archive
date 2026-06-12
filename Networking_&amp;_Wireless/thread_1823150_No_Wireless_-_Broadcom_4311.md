---
title: "No Wireless - Broadcom 4311"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by KemKev on 2011-08-11
OK...over the past two days I have read through every post in the sticky thread and tried just about everything, but no luck. I hope someone can point me in the right direction.

[COLOR="Blue"]$ sudo lshw -C network[/COLOR]

*-network 
description: Network controller
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:0 memory:b6000000-b6003fff
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:1a:73:02:6b:bd
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg

[COLOR="blue"]$ dmesg |grep b43[/COLOR]

[ 2.795109] b43-pci-bridge 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table
[ 2.795119] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 88.964315] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[ 89.042637] Registered led device: b43-phy0::tx
[ 89.042672] Registered led device: b43-phy0::rx
[ 89.042708] Registered led device: b43-phy0::radio
[ 89.784042] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 89.856563] b43-phy0 ERROR: Cannot request IRQ-0
[ 90.092046] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 90.164566] b43-phy0 ERROR: Cannot request IRQ-0

[COLOR="blue"]lsmod |grep b43[/COLOR]

b43 296610 0 
mac80211 257001 1 b43
cfg80211 156212 2 b43,mac80211
ssb 45942 1 b43

[COLOR="blue"]$ rfkill list[/COLOR]

0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

I have commented out the various entry in blacklist.conf, deactivated the STA driver, and have b43-fwcutter installed. And yeah, the wireless switch is "on" and works fine under Windows 7.

Thanks in advance.

---

### Post by pytheas22 on 2011-08-11
Those bits in your dmesg output about failing to request an IRQ address suggest the issue is related to your BIOS, not driver.  Someone [here]("http://forum.mandriva.com/en/viewtopic.php?t=97866") with the same problem found that disabling APIC took care of it.  I'd give that a try.

To disable APIC, open a terminal and type:

```
sudo gedit /boot/grub/grub.cfg
```

A file will open.  Search for the first instance of the word "menuentry"  A few lines down you should have a line that looks something like this (it will not look exactly like this):
```

linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=6ca6b2a3-c3a3-4ad0-81fd-1f49ab0c0dcc ro   quiet splash vt.handoff=7
```

Add "noapic" to the end of that line, so it looks like this (don't change any other parts of the line):
```

linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=6ca6b2a3-c3a3-4ad0-81fd-1f49ab0c0dcc ro   quiet splash vt.handoff=7 **noapic**
```

Then save and close the file, and reboot.  You should now be running without APIC.  Do you still get the same message in your "dmesg | grep b43" output about IRQ issues?

---

### Post by KemKev on 2011-08-11
Thanks for your response.  I edited the suggested file as shown below:

[COLOR="Green"]linux	/vmlinuz-2.6.38-8-generic root=UUID=f3680e13-d156-4b1f-b38d-01c88655cb63 ro   quiet splash vt.handoff=7 noapic[/COLOR]

When I rebooted, the orange light was still orange (still no wireless).

[COLOR="Blue"]dmesg | grep b43[/COLOR]

[    2.715784] b43-pci-bridge 0000:03:00.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    2.715797] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   16.515116] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   16.591160] Registered led device: b43-phy0::tx
[   16.591198] Registered led device: b43-phy0::rx
[   16.591229] Registered led device: b43-phy0::radio
[   17.200046] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   17.272572] b43-phy0 ERROR: Cannot request IRQ-0
[   17.500055] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   17.576989] b43-phy0 ERROR: Cannot request IRQ-0

[COLOR="Blue"]$ sudo lshw -C network[/COLOR]

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:0 memory:b6000000-b6003fff
  *-network [COLOR="Red"]DISABLED[/COLOR]
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:02:6b:bd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg

Any other thoughts / suggestions would be greatly appreciated.

PS: I should point out that when I reboot the **HP Pavilion dv6000** laptop, the orange light flashes blue a couple of times before becoming static on orange.

---

### Post by KemKev on 2011-08-11
The situation is still the same but I found something in the dmesg log that may be useful to someone in helping me resolve the problem:

0.147119] AppArmor: AppArmor Filesystem Enabled
[    0.147154] pnp: PnP ACPI: disabled
[    0.147159] PnPBIOS: Scanning system for PnP BIOS support...
[    0.147219] PnPBIOS: Found PnP BIOS installation structure at 0xc00f89c0
[    0.147223] PnPBIOS: PnP BIOS version 1.0, entry 0xe6e5:0x9acd, dseg 0x400
[    0.147230] PNPBIOS fault.. attempting recovery.
[    0.147233] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[    0.147236] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[    0.147238] PnPBIOS: Check with your vendor for an updated BIOS
[    0.147241] PnPBIOS: dev_node_info: unexpected status 0x3a
[    0.147244] PnPBIOS: Unable to get node info.  Aborting.

Is the "pnpbios=off" even worth trying and if so, how and where do I do that?

All of this is weird because the previous version of Ubuntu worked just fine on my laptop :confused:

HELP!

---

### Post by pytheas22 on 2011-08-12
hmmm, it seems the noapic option didn't change anything regarding the IRQs.  That other line in your dmesg is interesting, however.  I would try booting with the pnpbios=off option, as recommended.  To do that, simply follow the steps above for editing your /boot/grub/grub.cfg file, but instead of adding "noapic" to the line that starts with "linux", add "pnpbios=off" (without quotes) instead, then reboot.  Does this change anything?

---

### Post by KemKev on 2011-08-12
Thanks for the follow up. I edited the line in the file to read:

[COLOR="SeaGreen"]linux	/vmlinuz-2.6.38-8-generic root=UUID=f3680e13-d156-4b1f-b38d-01c88655cb63 ro   quiet splash vt.handoff=7 pnpbios=off
[/COLOR]
When I rebooted, the orange light again flashed blue a number of times before finally staying orange. 

From the dmesg log file:

 0.187428] AppArmor: AppArmor Filesystem Enabled
[    0.187463] pnp: PnP ACPI: disabled
[    0.187466] PnPBIOS: Disabled
[    0.2

Executing "dmesg | grep b43" produced the same output as before.

As an aside, I also went to the HP website and flashed the BIOS with the latest revision.  That didn't change anything.

Wireless continues to work like a charm under Windows 7 (I am dual booting) so I have to assume the BIOS shouldn't be the problem.

---

### Post by pytheas22 on 2011-08-12
Does dmesg still contain the same lines complaining "Warning! Your PnP BIOS caused a fatal error. Attempting to continue" after you rebooted with the "pnpbios=off" option?  It's possible the change is not actually taking effect.

Also, to clarify, I suspect the issue is BIOS-related, but I doubt you have a "bad" BIOS in that there's something wrong with your version.  It probably is just not agreeing with the Linux kernel for some reason, even though it works in Windows without issue, but making a few changes to the configuration should hopefully allow Linux to work around the bugs.  So I don't think you should worry about reflashing the BIOS and all that; that's probably not the source of the problem.

---

### Post by KemKev on 2011-08-12
> **pytheas22 said:**
> Does dmesg still contain the same lines complaining "Warning! Your PnP BIOS caused a fatal error. Attempting to continue" after you rebooted with the "pnpbios=off" option?  It's possible the change is not actually taking effect.
No, the warning wasn't there after the reboot. In my previous post, the dmesg log showed both "PnP ACPI" and "PnPBIOS" as disabled so I would imagine the off option worked. It still showed IRQ-0 could not be requested.

As for flashing the BIOS, I did it based on the line below from the dmesg log:

[COLOR="Red"][ 0.147238] PnPBIOS: Check with your vendor for an updated BIOS[/COLOR]

---

### Post by pytheas22 on 2011-08-12
At least the change did something, even if it didn't solve the problem.  My next suggestion for you would be to try disabling ACPI instead of APIC.  The post from another forum that I referenced yesterday said turning of APIC was the trick, but the poster may have confused that with ACPI.  (Unfortunately these are two separate things, despite their similar names.)

To disable APCI, add the string "noacpi acpi=off" (without quotes) to your /boot/grub/grub.cfg file as before.  After doing this and rebooting, does the dmesg output change?

---

### Post by KemKev on 2011-08-13
Thanks for dropping in again. I modified the string as per below:

[COLOR="Green"]linux /vmlinuz-2.6.38-8-generic root=UUID=f3680e13-d156-4b1f-b38d-01c88655cb63 ro quiet splash vt.handoff=7 noacpi acpi=off[/COLOR]

Net result is a low droning sound from the laptop after rebooting with the orange light still there. The "dmesg | grep b43" produced the same message as before; still unable to request IRQ-0.

---

### Post by nm_geo on 2011-08-14
You have an interesting problem.  Please do this command

```
dmesg | grep IRQ
```

Paste results.

---

### Post by pytheas22 on 2011-08-14
Sorry not to reply sooner; busy weekend.  It is strange that you're still having the IRQ issues even with ACPI disabled.  I suppose you can remove those additional boot parameters from your /boot/grub/grub.cfg file now, since they cause a strange noise and don't solve the problem.

It would be helpful to see the output of "dmesg | grep IRQ" as nm_geo suggests above.  It would also be good to know the exact model of your computer.  I'd like to google around and see if there are known issues with IRQ addresses and Linux on your motherboard.

Also, this is a bit of a shot in the dark, but it may be worth turning off your computer and removing the power plug (as well as the battery if it's a laptop), then holding the power button down for about thirty seconds.  After that, reboot into Linux and see if the IRQ issues persist.  I've seen situations in the past where Windows will leave wireless cards in states in which the Linux driver can't make them "wake up" and cutting off electricity to the motherboard forces the hardware to reset and solve the problem.  I think your issue may be different from those other situations, but resetting the hardware can't hurt anything and seems worth a try.

---

### Post by KemKev on 2011-08-14
> **nm_geo said:**
> You have an interesting problem.  Please do this command

```
dmesg | grep IRQ
```

Paste results.

Here goes:

```
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.172880] PCI: Discovered primary peer bus 04 [IRQ]
[    0.172895] pci 0000:00:0a.0: default IRQ router [10de:0260]
[    0.173299] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    2.048384] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.459833] pata_acpi 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
[    2.460790] ehci_hcd 0000:00:0b.1: can't find IRQ for PCI INT B; probably buggy MP table
[    2.472422] ohci_hcd 0000:00:0b.0: can't find IRQ for PCI INT A; probably buggy MP table
[    2.743703] b43-pci-bridge 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table
[    2.753797] forcedeth 0000:00:14.0: can't find IRQ for PCI INT A; probably buggy MP table
[    2.948000] firewire_ohci 0000:07:05.0: can't find IRQ for PCI INT B; probably buggy MP table
[    3.004173] sdhci-pci 0000:07:05.1: can't find IRQ for PCI INT C; probably buggy MP table
[    3.277257] sata_nv 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
[   50.756370] r852 0000:07:05.3: can't find IRQ for PCI INT C; probably buggy MP table
[   51.050502] HDA Intel 0000:00:10.1: can't find IRQ for PCI INT B; probably buggy MP table
[   53.108554] b43-phy0 ERROR: Cannot request IRQ-0
[   53.632744] b43-phy0 ERROR: Cannot request IRQ-0

```

Thanks in advance.

---

### Post by KemKev on 2011-08-14
> **pytheas22 said:**
> Sorry not to reply sooner; busy weekend.  It is strange that you're still having the IRQ issues even with ACPI disabled.  I suppose you can remove those additional boot parameters from your /boot/grub/grub.cfg file now, since they cause a strange noise and don't solve the problem.

It would be helpful to see the output of "dmesg | grep IRQ" as nm_geo suggests above.  It would also be good to know the exact model of your computer.  I'd like to google around and see if there are known issues with IRQ addresses and Linux on your motherboard.

Also, this is a bit of a shot in the dark, but it may be worth turning off your computer and removing the power plug (as well as the battery if it's a laptop), then holding the power button down for about thirty seconds.  After that, reboot into Linux and see if the IRQ issues persist.  I've seen situations in the past where Windows will leave wireless cards in states in which the Linux driver can't make them "wake up" and cutting off electricity to the motherboard forces the hardware to reset and solve the problem.  I think your issue may be different from those other situations, but resetting the hardware can't hurt anything and seems worth a try.
I understand busy. I'm just appreciative that you return to this thread and continue to offer your suggestions for a solution to my problem; thank you.

The laptop is a HP Pavilion dv6110ca from the dv6000 series. System board ID = 30B7, BIOS version = F.43, Processor type = AMD Turiton 64 x 2.

I tried the "shot in the dark" but no solution there.  I have posted the "dmesg | grep IRQ" output in my previous post.

---

### Post by pytheas22 on 2011-08-14
Thanks for the additional information.  Unfortunately, googling around doesn't turn up any useful clues.  It doesn't seem that there are any major problems associated with IRQ routing on your hardware.

There's a page about troubleshooting IRQ problems [here]("https://help.ubuntu.com/community/DebuggingIRQProblems") with several relatively straightforward solutions you could try.  Any chance they make a difference?  Adding boot parameters, as described on that page, simply means editing your /boot/grub/grub.cfg file as you've done earlier.

A few other possibly helpful boot parameters you could try which aren't mentioned on that page are:
```

apic
lapic
nolapic
pci=biosirq
```

Finally, if you add the boot parameter "loglevel=7" it should force the kernel to provide more detailed logging information, which could be helpful.  It would be useful to see the output of these commands after you've booted with the "loglevel=7" parameter enabled:
```

dmesg | grep -ie irq -ie ssb -ie b43
grep -ie irq -ie ssb -ie b43 /var/log/syslog
```

---

### Post by KemKev on 2011-08-14
Very interesting exercise trying all the different parameters. The wireless blue light flashes with options "pci=routeirq" and "pci=noacpi" before returning to static orange. Sort of like so close yet so far away!

The outputs of the commands you requested:

```
dmesg | grep -ie irq -ie ssb -ie b43
[    0.000000] nr_irqs_gsi: 40
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=2a11526d-8f5c-4ddf-b352-87cf14fb430d ro quiet splash vt.handoff=7 nolapic loglevel=7
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.043018] PCI: Discovered primary peer bus 04 [IRQ]
[    0.043034] pci 0000:00:0a.0: default IRQ router [10de:0260]
[    0.043493] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    1.968933] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.975054] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
[    2.029554] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
[    2.162682] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.162698] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.163035] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    3.354610] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    3.354615] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    3.372367] b43-pci-bridge 0000:03:00.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    3.372382] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    3.392074] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    3.392085] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    3.392093] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    3.392101] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    3.444324] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    3.870954] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 5
[    3.870959] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 5
[   21.986339] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   22.078751] Registered led device: b43-phy0::tx
[   22.078871] Registered led device: b43-phy0::rx
[   22.078987] Registered led device: b43-phy0::radio
[   22.336113] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   22.426414] b43-phy0 ERROR: Cannot request IRQ-0
[   22.628050] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   22.702159] b43-phy0 ERROR: Cannot request IRQ-0

```


```
OT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=2a11526d-8f5c-4ddf-b352-87cf14fb430d ro quiet splash vt.handoff=7 
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    0.060003] CPU 1 irqstacks, hard=f38aa000 soft=f38ac000
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    0.172835] PCI: Discovered primary peer bus 04 [IRQ]
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    0.172851] pci 0000:00:0a.0: default IRQ router [10de:0260]
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    0.173253] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.052412] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.471850] pata_acpi 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.472773] ehci_hcd 0000:00:0b.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.473003] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.484417] ohci_hcd 0000:00:0b.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.484585] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.561656] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.561666] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.562584] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.762464] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.762469] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.765567] sata_nv 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.773601] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 5
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.773606] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 5
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.773713] forcedeth 0000:00:14.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.776617] sdhci-pci 0000:07:05.1: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.780250] b43-pci-bridge 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.780261] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.800113] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.800122] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.800129] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.800136] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    2.840121] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Aug 14 22:39:38 colin-HP-Pavilion kernel: [    3.629286] firewire_ohci 0000:07:05.0: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [  142.609319] r852 0000:07:05.3: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [  142.672131] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Aug 14 22:39:38 colin-HP-Pavilion kernel: [  142.766065] HDA Intel 0000:00:10.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:39:38 colin-HP-Pavilion kernel: [  142.779250] Registered led device: b43-phy0::tx
Aug 14 22:39:38 colin-HP-Pavilion kernel: [  142.779383] Registered led device: b43-phy0::rx
Aug 14 22:39:38 colin-HP-Pavilion kernel: [  142.779426] Registered led device: b43-phy0::radio
Aug 14 22:39:38 colin-HP-Pavilion NetworkManager[705]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Aug 14 22:39:38 colin-HP-Pavilion NetworkManager[705]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 14 22:39:38 colin-HP-Pavilion NetworkManager[705]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Aug 14 22:39:38 colin-HP-Pavilion NetworkManager[705]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Aug 14 22:39:38 colin-HP-Pavilion kernel: [  143.536058] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 22:39:38 colin-HP-Pavilion kernel: [  143.614273] b43-phy0 ERROR: Cannot request IRQ-0
Aug 14 22:39:38 colin-HP-Pavilion kernel: [  144.036052] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 22:39:39 colin-HP-Pavilion kernel: [  144.108570] b43-phy0 ERROR: Cannot request IRQ-0
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.000000] nr_irqs_gsi: 40
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=2a11526d-8f5c-4ddf-b352-87cf14fb430d ro quiet splash vt.handoff=7 pci=routeirq
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.056003] CPU 1 irqstacks, hard=f38aa000 soft=f38ac000
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168804] PCI: Discovered primary peer bus 04 [IRQ]
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168820] pci 0000:00:0a.0: default IRQ router [10de:0260]
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168844] PCI: Routing PCI interrupts for all devices because "pci=routeirq" specified
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168863] pci 0000:00:05.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168873] pci 0000:00:0a.1: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168883] pci 0000:00:0a.3: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168888] pci 0000:00:0b.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168894] pci 0000:00:0b.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168901] pci 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168908] pci 0000:00:10.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168914] pci 0000:00:14.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168924] pci 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168931] pci 0000:07:05.0: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168938] pci 0000:07:05.1: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168944] pci 0000:07:05.2: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.168950] pci 0000:07:05.3: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    0.169333] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.052066] pcieport 0000:00:03.0: irq 40 for MSI/MSI-X
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.052499] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 14 22:49:21 colin-HP-Pavilion NetworkManager[738]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Aug 14 22:49:21 colin-HP-Pavilion NetworkManager[738]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 14 22:49:21 colin-HP-Pavilion NetworkManager[738]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Aug 14 22:49:21 colin-HP-Pavilion NetworkManager[738]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.467869] pata_acpi 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.468806] ehci_hcd 0000:00:0b.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.469033] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.480406] ohci_hcd 0000:00:0b.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.480575] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.555697] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.555706] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.557011] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.745482] sdhci-pci 0000:07:05.1: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.748887] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.748891] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.749028] sata_nv 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.752173] b43-pci-bridge 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.752185] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.753958] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 5
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.753963] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 5
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.758215] forcedeth 0000:00:14.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.772084] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.772094] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.772102] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.772109] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    2.813248] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Aug 14 22:49:21 colin-HP-Pavilion kernel: [    3.593879] firewire_ohci 0000:07:05.0: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   81.618449] r852 0000:07:05.3: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   81.834738] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   81.915775] HDA Intel 0000:00:10.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   81.917961] Registered led device: b43-phy0::tx
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   81.917994] Registered led device: b43-phy0::rx
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   81.918025] Registered led device: b43-phy0::radio
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   83.456036] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   83.528555] b43-phy0 ERROR: Cannot request IRQ-0
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   83.968077] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 22:49:21 colin-HP-Pavilion kernel: [   84.040561] b43-phy0 ERROR: Cannot request IRQ-0
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.000000] nr_irqs_gsi: 40
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=2a11526d-8f5c-4ddf-b352-87cf14fb430d ro quiet splash vt.handoff=7 pci=noacpi loglevel=7
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.020001] ...trying to set up timer (IRQ0) through the 8259A ...
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.028001] ...trying to set up timer as Virtual Wire IRQ...
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.028001] ...trying to set up timer as ExtINT IRQ...
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.072003] CPU 1 irqstacks, hard=f38aa000 soft=f38ac000
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.184971] PCI: Discovered primary peer bus 04 [IRQ]
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.184987] pci 0000:00:0a.0: default IRQ router [10de:0260]
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    0.185389] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.060411] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.483761] pata_acpi 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.484678] ehci_hcd 0000:00:0b.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.484909] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.496419] ohci_hcd 0000:00:0b.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.496588] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.572361] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.572370] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.573958] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.767510] sdhci-pci 0000:07:05.1: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.783312] firewire_ohci 0000:07:05.0: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.783771] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.783777] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.783884] forcedeth 0000:00:14.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.787733] b43-pci-bridge 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.787747] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.804133] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.804143] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.804150] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.804158] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    2.844139] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    3.300211] sata_nv 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    3.301118] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 5
Aug 14 22:58:48 colin-HP-Pavilion kernel: [    3.301123] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 5
Aug 14 22:58:48 colin-HP-Pavilion kernel: [  113.192047] r852 0000:07:05.3: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [  113.312869] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Aug 14 22:58:48 colin-HP-Pavilion kernel: [  113.371199] HDA Intel 0000:00:10.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 22:58:48 colin-HP-Pavilion kernel: [  113.395020] Registered led device: b43-phy0::tx
Aug 14 22:58:48 colin-HP-Pavilion kernel: [  113.395052] Registered led device: b43-phy0::rx
Aug 14 22:58:48 colin-HP-Pavilion kernel: [  113.395093] Registered led device: b43-phy0::radio
Aug 14 22:58:48 colin-HP-Pavilion NetworkManager[731]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Aug 14 22:58:48 colin-HP-Pavilion NetworkManager[731]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 14 22:58:48 colin-HP-Pavilion NetworkManager[731]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Aug 14 22:58:49 colin-HP-Pavilion NetworkManager[731]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Aug 14 22:58:49 colin-HP-Pavilion kernel: [  115.260063] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 22:58:49 colin-HP-Pavilion kernel: [  115.332555] b43-phy0 ERROR: Cannot request IRQ-0
Aug 14 22:58:49 colin-HP-Pavilion kernel: [  115.764071] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 22:58:49 colin-HP-Pavilion kernel: [  115.836818] b43-phy0 ERROR: Cannot request IRQ-0
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.000000] nr_irqs_gsi: 40
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=2a11526d-8f5c-4ddf-b352-87cf14fb430d ro quiet splash vt.handoff=7 acpi=off loglevel=7
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.024001] ...trying to set up timer (IRQ0) through the 8259A ...
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.032001] ...trying to set up timer as Virtual Wire IRQ...
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.032001] ...trying to set up timer as ExtINT IRQ...
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.180893] CPU 1 irqstacks, hard=f38aa000 soft=f38ac000
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.296842] PCI: Discovered primary peer bus 04 [IRQ]
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    0.296857] pci 0000:00:0a.0: default IRQ router [10de:0260]
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    1.952185] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.023999] pata_acpi 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.024938] ehci_hcd 0000:00:0b.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.040275] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.052549] ohci_hcd 0000:00:0b.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.064226] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.139201] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.139210] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.342380] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.342384] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.343242] forcedeth 0000:00:14.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.349116] b43-pci-bridge 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.349133] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.368334] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.368345] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.368352] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.368360] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.408334] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.535209] sdhci-pci 0000:07:05.1: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.545719] firewire_ohci 0000:07:05.0: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.865442] sata_nv 0000:00:0e.0: can't find IRQ for PCI INT A; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.866549] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 5
Aug 14 23:04:18 colin-HP-Pavilion kernel: [    3.866549] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 5
Aug 14 23:04:18 colin-HP-Pavilion kernel: [   52.056305] r852 0000:07:05.3: can't find IRQ for PCI INT C; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [   52.486560] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Aug 14 23:04:18 colin-HP-Pavilion kernel: [   52.518769] HDA Intel 0000:00:10.1: can't find IRQ for PCI INT B; probably buggy MP table
Aug 14 23:04:18 colin-HP-Pavilion kernel: [   52.560502] Registered led device: b43-phy0::tx
Aug 14 23:04:18 colin-HP-Pavilion kernel: [   52.560502] Registered led device: b43-phy0::rx
Aug 14 23:04:18 colin-HP-Pavilion kernel: [   52.560502] Registered led device: b43-phy0::radio
Aug 14 23:04:18 colin-HP-Pavilion NetworkManager[767]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Aug 14 23:04:18 colin-HP-Pavilion NetworkManager[767]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 14 23:04:18 colin-HP-Pavilion NetworkManager[767]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Aug 14 23:04:18 colin-HP-Pavilion NetworkManager[767]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Aug 14 23:04:18 colin-HP-Pavilion kernel: [   85.177368] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 23:04:18 colin-HP-Pavilion kernel: [   85.249839] b43-phy0 ERROR: Cannot request IRQ-0
Aug 14 23:04:19 colin-HP-Pavilion kernel: [   85.685439] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 23:04:19 colin-HP-Pavilion kernel: [   85.760286] b43-phy0 ERROR: Cannot request IRQ-0
Aug 14 23:04:55 colin-HP-Pavilion kernel: [  122.321097] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    0.000000] nr_irqs_gsi: 40
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=2a11526d-8f5c-4ddf-b352-87cf14fb430d ro quiet splash vt.handoff=7 nolapic loglevel=7
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    0.043018] PCI: Discovered primary peer bus 04 [IRQ]
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    0.043034] pci 0000:00:0a.0: default IRQ router [10de:0260]
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    0.043493] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    1.968933] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    1.975054] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    2.029554] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    2.162682] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    2.162698] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    2.163035] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.354610] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.354615] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.372367] b43-pci-bridge 0000:03:00.0: can't find IRQ for PCI INT A; please try using pci=biosirq
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.372382] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.392074] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.392085] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.392093] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.392101] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.444324] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.870954] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 5
Aug 14 23:08:44 colin-HP-Pavilion kernel: [    3.870959] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 5
Aug 14 23:08:45 colin-HP-Pavilion kernel: [   21.986339] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Aug 14 23:08:45 colin-HP-Pavilion kernel: [   22.078751] Registered led device: b43-phy0::tx
Aug 14 23:08:45 colin-HP-Pavilion kernel: [   22.078871] Registered led device: b43-phy0::rx
Aug 14 23:08:45 colin-HP-Pavilion kernel: [   22.078987] Registered led device: b43-phy0::radio
Aug 14 23:08:45 colin-HP-Pavilion NetworkManager[616]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Aug 14 23:08:45 colin-HP-Pavilion NetworkManager[616]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Aug 14 23:08:45 colin-HP-Pavilion kernel: [   22.336113] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 23:08:45 colin-HP-Pavilion kernel: [   22.426414] b43-phy0 ERROR: Cannot request IRQ-0
Aug 14 23:08:45 colin-HP-Pavilion NetworkManager[616]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Aug 14 23:08:45 colin-HP-Pavilion NetworkManager[616]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 14 23:08:45 colin-HP-Pavilion kernel: [   22.628050] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Aug 14 23:08:46 colin-HP-Pavilion kernel: [   22.702159] b43-phy0 ERROR: Cannot request IRQ-0

```

I have no idea what most of that stuff means but I hope you do :) I have also been using Google quite a bit to see if I can find any similar instances where this problem has been found and resolved. Quite a bit on this particular series of HP laptops but with different motherboards.

---

### Post by pytheas22 on 2011-08-15
Thanks again for the information.  I do see some more interesting stuff in there about IRQ issues.  It looks like several of your devices are having them, but in all cases except the wireless card the drivers are able to work around them.

I should have asked for this earlier as well, but it would be good to see the actual IRQ assignments.  What is the output of:
```

cat /proc/interrupts
```

Also, have you tried playing around with your BIOS options at all?  I would first disable any components of the system you don't use (like serial ports if you have them), which might free up IRQs and solve the issue.  If your BIOS is good enough to let you assign IRQs manually, that would be great; in that case, you should be able to assign IRQs to your devices individually to make sure there are no conflicts.

Finally, another thought I've had is whether the STA driver might be able to deal with these IRQ problems better than the b43 driver.  You wrote that you have the STA driver blacklisted, but did you actually try it?  If not, it would be worth it to black the b43 and ssb drivers, reboot and then try the STA driver.  (If you blacklist only b43 and leave ssb active, ssb will probably still claim the device and prevent the STA driver from driving it.)

---

### Post by KemKev on 2011-08-15
I am currently at work and will provide the output of the command you requested once I get home.

In the interim, I did try the STA driver immediately after installing and reinstalling the OS. Unfortunately, that did nothing and I did read in various places on the internet that it was incompatible with the BCM 4311.

As for the laptop's BIOS, I did have a look but besides a few generic things such as system date, time, and bootup sequence, there is not much else in there for user configuration. In other words, I cannot enable or disable any components. 

Incidentally, does the fact that my USB peripherals are working fine suggest there is some IRQ allocation going on?  

That fact that the blue light flashes with certain options makes me think we are close, but just missing that one piece of the puzzle to pull this off.

---

### Post by pytheas22 on 2011-08-15
Too bad about the BIOS...unfortunately many these days don't provide very many useful features at all.

[Broadcom's website]("http://www.broadcom.com/support/802.11/linux_sta.php") says the STA driver should support bcm4311 chips.  Before giving up entirely on that potential solution, please let me know the output of:
```

lspci -nn
```

so we'll know your exact wireless chipset and can look up whether the STA module will claim it.  Perhaps before it wasn't working simply because it wasn't activated or the ssb module was still claiming the device.

---

### Post by KemKev on 2011-08-15
Here goes:

```
 
 
cat /proc/interrupts

        CPU0       CPU1       
  0:         41          3   IO-APIC-edge      timer
  1:        114         29   IO-APIC-edge      i8042
  5:       4063      10943   IO-APIC-edge      sata_nv
  7:        814       9236   IO-APIC-edge      ehci_hcd:usb1
  8:          0          1   IO-APIC-edge      rtc0
 10:          0          0   IO-APIC-edge      eth0
 11:       4448         50   IO-APIC-edge      ohci_hcd:usb2, firewire_ohci, mmc0, r852, hda_intel
 12:       6756        136   IO-APIC-edge      i8042
 14:          2        856   IO-APIC-edge      pata_amd
 15:          0          0   IO-APIC-edge      pata_amd
NMI:          0          0   Non-maskable interrupts
LOC:      25845      27891   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RES:      25471      31175   Rescheduling interrupts
CAL:        311        226   Function call interrupts
TLB:        709        770   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          2          2   Machine check polls
ERR:          1
MIS:          0

```


```


lspci -nn

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

```

I will wait until you review and comment on these outputs before giving the STA another try.

---

### Post by pytheas22 on 2011-08-15
The STA driver will support your device (you can tell by typing "modinfo wl" and searching through the alias strings for one matching your card's PCI ID, which is 14e4:4311).  Because nothing looks out of the ordinary to me on your IRQ table, I think trying the STA driver would be worth it.

You should be able to deactivate b43 and put the STA driver (whose modules is named "wl" for reasons that I've never understood) in its place by typing these commands (no need for now to modify your blacklist files; you can do that later if this turns out to be a permanent solution):
```

sudo rmmod b43
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
```

At this point, if you haven't received any error messages, the device just might come up and work.  If not, please let me know the output at this point of:
```

dmesg | tail -25
lshw -C Network
```

---

### Post by KemKev on 2011-08-16
Mmmm....The first two went fine but the third didn't.

[COLOR="Blue"]sudo rmmod wl[/COLOR]

ERROR: Module wl does not exist in /proc/modules

According to [COLOR="Blue"]modinfo wl[/COLOR]

filename:       /lib/modules/2.6.38-8-generic/kernel/net/wireless/wl.ko

Should this file be somewhere else?

Also, when I ran [COLOR="Blue"]lsmod  | grep b43\|ssb\|wl[/COLOR] it returned nothing.

---

### Post by pytheas22 on 2011-08-16
Sorry, I should have warned you about that.  The error message about wl not being in /proc/modules simply means that wl wasn't loaded initially--which is fine (I only had you attempt to remove it just in case it was already loaded, since generally it needs to be unloaded and reloaded again to make it claim the hardware).  So you can ignore that error and continue on with the other commands.  Please try again and let me know how it goes.

Sorry I forgot to mention that that message might have come up.

---

### Post by KemKev on 2011-08-16
No problem at all.  Should I activate the STA driver?  I did do the [COLOR="Blue"]sudo modprobe wl[/COLOR] but nothing happened. I will post the output of the commands you requested when I get home.

Here goes:

```
[COLOR="Blue"]lsmod | grep wl[/COLOR]
wl                   2642531  0 
lib80211               14570  1 wl

```Just wanted to confirm wl was loaded. Orange light still static.

```
[COLOR="Blue"]dmesg | tail -25[/COLOR]
[  596.466756] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  596.466760] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  596.466764] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  596.466768] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  596.466771] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  596.466775] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  596.466779] cfg80211: World regulatory domain updated:
[  596.466784] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  596.466788] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  596.466792] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  596.466796] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  596.466800] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  596.466804] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  599.820351] usb 1-2: USB disconnect, address 2
[  599.824236] zd1211rw 1-2:1.0: error ioread32(CR_REG1): -19
[  607.430430] forcedeth 0000:00:14.0: eth0: link up
[  607.431013] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  617.928039] eth0: no IPv6 routers present
[ 1226.397323] wl 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table
[ 1226.397336] wl 0000:03:00.0: setting latency timer to 64
[ 1226.399672] malloc in abgphy done
[ 1226.399800] eth%d: 5.100.82.38 driver failed with code 21
[ 1317.206235] wl 0000:03:00.0: setting latency timer to 64
[ 1317.208609] malloc in abgphy done
[ 1317.208745] eth%d: 5.100.82.38 driver failed with code 21

```

```
[COLOR="Blue"]sudo lshw -C Network[/COLOR]
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b6000000-b6003fff

```

---

### Post by pytheas22 on 2011-08-16
"sudo modprobe wl" shouldn't produce any output unless there's an error, so no problems there.  From your dmesg output it looks like the wl module was indeed inserted properly and claimed the hardware.  Unfortunately, it also complains about IRQ routing problems ("[ 1226.397323] wl 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table"), which brings us back to where we started.  I was hoping the STA driver might be able to handle the IRQ issue better than b43, but it seems not.

Which kernel parameters were you booting with before that caused the light to turn green briefly?  We didn't really dig deeper there before, but that may give the key to this whole issue.  It would be useful to see the output of these commands after the light has flashed green:
```

dmesg
lshw -C Network
```

Finally, this may be a lot of work, but I'd love to see your BIOS screens myself to check whether there are any options that might be useful but that don't have obvious labels (or if there's anything that mentions something along the lines of "plug and play").  If it's not too much trouble to take some pictures of the BIOS screens, that would be great.  But don't worry about this if you don't have a camera.

---

### Post by KemKev on 2011-08-17
Thanks for the imput.  I will give those a go after work later. However, I have concluded that this version of the OS and the Pavilion dv6110ca have very little in common, which is weird considering everything - wireless, integrated webcam, etc. - worked fine before this upgrade.

As an aside, when the bluelight flashed with previous attempts, the [COLOR="Blue"]lshw -C Network [/COLOR] output was similar to that in my first post. I will repost later to confirm. In the meantime, would you happen to know if there is a later firmware upgrade available?

---

### Post by pytheas22 on 2011-08-17
I doubt the b43 firmware would have anything to do with the IRQ issues, but you can find a list of supported firmware at [http://linuxwireless.org/en/users/Drivers/b43#List_of_firmware](http://linuxwireless.org/en/users/Drivers/b43#List_of_firmware)  You would need to use the b43-fwcutter tool to extract it and copy into the /lib/firmware directory manually.  There's also reverse-engineered firmware available, which you can read about at [http://lwn.net/Articles/314313/](http://lwn.net/Articles/314313/) but I'm not sure what the status of that endeavor is.

Everything worked fine for you in an earlier Ubuntu release?  I don't think I knew that.  Which version did you last have installed?

---

### Post by KemKev on 2011-08-17
> **pytheas22 said:**
> 
Everything worked fine for you in an earlier Ubuntu release?  I don't think I knew that.  Which version did you last have installed?
Ubuntu 10.10

---

### Post by prosperoa on 2011-08-17
I'm having the same problem now, but I'm running 10.10. I've tried the recommended steps here with no luck.  I'm very interested to see the resolution to this, and hopefully can use the same information to get my 4311 to work.

My question is to see if there's a way to start from the beginning of the setup without reinstalling Ubuntu from scratch. In effect, what "should" the setup look like?  I'm concerned that I've changed so much that all of the settings and drivers are radically different than how they start upon a fresh install.

Oh, and i'm very new to Ubuntu, if you can't tell. :D

---

### Post by KemKev on 2011-08-18
> **pytheas22 said:**
> "sudo modprobe wl" shouldn't produce any output unless there's an error, so no problems there.  From your dmesg output it looks like the wl module was indeed inserted properly and claimed the hardware.  Unfortunately, it also complains about IRQ routing problems ("[ 1226.397323] wl 0000:03:00.0: can't find IRQ for PCI INT A; probably buggy MP table"), which brings us back to where we started.  I was hoping the STA driver might be able to handle the IRQ issue better than b43, but it seems not.

Which kernel parameters were you booting with before that caused the light to turn green briefly?  We didn't really dig deeper there before, but that may give the key to this whole issue.  It would be useful to see the output of these commands after the light has flashed green:
```

dmesg
lshw -C Network
```

Finally, this may be a lot of work, but I'd love to see your BIOS screens myself to check whether there are any options that might be useful but that don't have obvious labels (or if there's anything that mentions something along the lines of "plug and play").  If it's not too much trouble to take some pictures of the BIOS screens, that would be great.  But don't worry about this if you don't have a camera.

When I use either the "pci=routeirq" or the "noapic" option, the blue light flashes before returning to static orange. Here are the respective outputs with the "pci=routeirq" option enabled.

```

[COLOR="Blue"]lshw -C Network[/COLOR]

*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:0 memory:b6000000-b6003fff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:02:6b:bd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg

```

```
[COLOR="Blue"]dmesg[/COLOR]

in
[   75.808685]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   75.808689] ata3.00: status: { DRDY }
[   75.808692] ata3.00: failed command: READ FPDMA QUEUED
[   75.808700] ata3.00: cmd 60/30:d0:20:a4:75/00:00:24:00:00/40 tag 26 ncq 24576 in
[   75.808702]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   75.808706] ata3.00: status: { DRDY }
[   75.808709] ata3.00: failed command: READ FPDMA QUEUED
[   75.808717] ata3.00: cmd 60/30:d8:38:a5:75/00:00:24:00:00/40 tag 27 ncq 24576 in
[   75.808719]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   75.808723] ata3.00: status: { DRDY }
[   75.808726] ata3.00: failed command: READ FPDMA QUEUED
[   75.808734] ata3.00: cmd 60/20:e0:80:a5:75/00:00:24:00:00/40 tag 28 ncq 16384 in
[   75.808736]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   75.808740] ata3.00: status: { DRDY }
[   75.808743] ata3.00: failed command: READ FPDMA QUEUED
[   75.808751] ata3.00: cmd 60/58:e8:78:a7:75/00:00:24:00:00/40 tag 29 ncq 45056 in
[   75.808753]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   75.808757] ata3.00: status: { DRDY }
[   75.808761] ata3.00: failed command: READ FPDMA QUEUED
[   75.808769] ata3.00: cmd 60/d0:f0:18:a8:75/01:00:24:00:00/40 tag 30 ncq 237568 in
[   75.808771]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   75.808774] ata3.00: status: { DRDY }
[   75.808781] ata3: hard resetting link
[   75.808785] ata3: nv: skipping hardreset on occupied port
[   76.276031] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   76.329096] ata3.00: configured for UDMA/133
[   76.329102] ata3.00: device reported invalid CHS sector 0
[   76.329106] ata3.00: device reported invalid CHS sector 0
[   76.329110] ata3.00: device reported invalid CHS sector 0
[   76.329113] ata3.00: device reported invalid CHS sector 0
[   76.329117] ata3.00: device reported invalid CHS sector 0
[   76.329120] ata3.00: device reported invalid CHS sector 0
[   76.329124] ata3.00: device reported invalid CHS sector 0
[   76.329127] ata3.00: device reported invalid CHS sector 0
[   76.329131] ata3.00: device reported invalid CHS sector 0
[   76.329134] ata3.00: device reported invalid CHS sector 0
[   76.329138] ata3.00: device reported invalid CHS sector 0
[   76.329141] ata3.00: device reported invalid CHS sector 0
[   76.329145] ata3.00: device reported invalid CHS sector 0
[   76.329148] ata3.00: device reported invalid CHS sector 0
[   76.329152] ata3.00: device reported invalid CHS sector 0
[   76.329155] ata3.00: device reported invalid CHS sector 0
[   76.329159] ata3.00: device reported invalid CHS sector 0
[   76.329162] ata3.00: device reported invalid CHS sector 0
[   76.329166] ata3.00: device reported invalid CHS sector 0
[   76.329169] ata3.00: device reported invalid CHS sector 0
[   76.329173] ata3.00: device reported invalid CHS sector 0
[   76.329176] ata3.00: device reported invalid CHS sector 0
[   76.329179] ata3.00: device reported invalid CHS sector 0
[   76.329183] ata3.00: device reported invalid CHS sector 0
[   76.329186] ata3.00: device reported invalid CHS sector 0
[   76.329190] ata3.00: device reported invalid CHS sector 0
[   76.329193] ata3.00: device reported invalid CHS sector 0
[   76.329197] ata3.00: device reported invalid CHS sector 0
[   76.329200] ata3.00: device reported invalid CHS sector 0
[   76.329204] ata3.00: device reported invalid CHS sector 0
[   76.329207] ata3.00: device reported invalid CHS sector 0
[   76.329249] ata3: EH complete
[  111.804142] ata3: EH in SWNCQ mode,QC:qc_active 0x7FEE9FBF sactive 0x7FEE9FBF
[  111.804149] ata3: SWNCQ:qc_active 0x40401916 defer_bits 0x3FAE86A9 last_issue_tag 0x1e
[  111.804151]   dhfis 0x401916 dmafis 0x0 sdbfis 0x0
[  111.804156] ata3: ATA_REG 0x40 ERR_REG 0x0
[  111.804159] ata3: tag : dhfis dmafis sdbfis sacitve
[  111.804162] ata3: tag 0x1: 1 0 0 1  
[  111.804166] ata3: tag 0x2: 1 0 0 1  
[  111.804169] ata3: tag 0x4: 1 0 0 1  
[  111.804172] ata3: tag 0x8: 1 0 0 1  
[  111.804175] ata3: tag 0xb: 1 0 0 1  
[  111.804178] ata3: tag 0xc: 1 0 0 1  
[  111.804182] ata3: tag 0x16: 1 0 0 1  
[  111.804185] ata3: tag 0x1e: 0 0 0 1  
[  111.804198] ata3.00: exception Emask 0x0 SAct 0x7fee9fbf SErr 0x0 action 0x6 frozen
[  111.804204] ata3.00: failed command: READ FPDMA QUEUED
[  111.804214] ata3.00: cmd 60/a0:00:78:10:b8/00:00:24:00:00/40 tag 0 ncq 81920 in
[  111.804216]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804220] ata3.00: status: { DRDY }
[  111.804223] ata3.00: failed command: READ FPDMA QUEUED
[  111.804232] ata3.00: cmd 60/08:08:d8:00:b7/00:00:24:00:00/40 tag 1 ncq 4096 in
[  111.804234]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804237] ata3.00: status: { DRDY }
[  111.804241] ata3.00: failed command: READ FPDMA QUEUED
[  111.804249] ata3.00: cmd 60/08:10:00:32:b6/01:00:24:00:00/40 tag 2 ncq 135168 in
[  111.804251]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804255] ata3.00: status: { DRDY }
[  111.804258] ata3.00: failed command: READ FPDMA QUEUED
[  111.804266] ata3.00: cmd 60/20:18:40:12:b8/00:00:24:00:00/40 tag 3 ncq 16384 in
[  111.804268]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804272] ata3.00: status: { DRDY }
[  111.804275] ata3.00: failed command: READ FPDMA QUEUED
[  111.804283] ata3.00: cmd 60/08:20:e8:01:b7/00:00:24:00:00/40 tag 4 ncq 4096 in
[  111.804285]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804289] ata3.00: status: { DRDY }
[  111.804293] ata3.00: failed command: READ FPDMA QUEUED
[  111.804301] ata3.00: cmd 60/18:28:50:14:b8/00:00:24:00:00/40 tag 5 ncq 12288 in
[  111.804303]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804306] ata3.00: status: { DRDY }
[  111.804310] ata3.00: failed command: READ FPDMA QUEUED
[  111.804318] ata3.00: cmd 60/20:38:98:14:b8/00:00:24:00:00/40 tag 7 ncq 16384 in
[  111.804320]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804324] ata3.00: status: { DRDY }
[  111.804327] ata3.00: failed command: READ FPDMA QUEUED
[  111.804336] ata3.00: cmd 60/a0:40:28:43:b6/00:00:24:00:00/40 tag 8 ncq 81920 in
[  111.804337]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804341] ata3.00: status: { DRDY }
[  111.804344] ata3.00: failed command: READ FPDMA QUEUED
[  111.804353] ata3.00: cmd 60/48:48:00:13:b8/00:00:24:00:00/40 tag 9 ncq 36864 in
[  111.804354]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804358] ata3.00: status: { DRDY }
[  111.804361] ata3.00: failed command: READ FPDMA QUEUED
[  111.804370] ata3.00: cmd 60/18:50:38:19:b8/00:00:24:00:00/40 tag 10 ncq 12288 in
[  111.804371]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804375] ata3.00: status: { DRDY }
[  111.804379] ata3.00: failed command: READ FPDMA QUEUED
[  111.804387] ata3.00: cmd 60/b8:58:e0:2f:b6/00:00:24:00:00/40 tag 11 ncq 94208 in
[  111.804389]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804393] ata3.00: status: { DRDY }
[  111.804396] ata3.00: failed command: READ FPDMA QUEUED
[  111.804404] ata3.00: cmd 60/08:60:88:02:b7/00:00:24:00:00/40 tag 12 ncq 4096 in
[  111.804406]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804410] ata3.00: status: { DRDY }
[  111.804413] ata3.00: failed command: READ FPDMA QUEUED
[  111.804421] ata3.00: cmd 60/30:78:08:16:b8/00:00:24:00:00/40 tag 15 ncq 24576 in
[  111.804423]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804427] ata3.00: status: { DRDY }
[  111.804430] ata3.00: failed command: READ FPDMA QUEUED
[  111.804439] ata3.00: cmd 60/08:88:e0:5b:b7/00:00:24:00:00/40 tag 17 ncq 4096 in
[  111.804442]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804446] ata3.00: status: { DRDY }
[  111.804450] ata3.00: failed command: READ FPDMA QUEUED
[  111.804458] ata3.00: cmd 60/38:90:a8:17:b8/00:00:24:00:00/40 tag 18 ncq 28672 in
[  111.804459]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804463] ata3.00: status: { DRDY }
[  111.804466] ata3.00: failed command: READ FPDMA QUEUED
[  111.804475] ata3.00: cmd 60/58:98:48:16:b8/00:00:24:00:00/40 tag 19 ncq 45056 in
[  111.804476]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804480] ata3.00: status: { DRDY }
[  111.804484] ata3.00: failed command: READ FPDMA QUEUED
[  111.804492] ata3.00: cmd 60/18:a8:b0:11:b8/00:00:24:00:00/40 tag 21 ncq 12288 in
[  111.804494]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804497] ata3.00: status: { DRDY }
[  111.804501] ata3.00: failed command: READ FPDMA QUEUED
[  111.804509] ata3.00: cmd 60/70:b0:80:f2:b6/00:00:24:00:00/40 tag 22 ncq 57344 in
[  111.804511]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804514] ata3.00: status: { DRDY }
[  111.804518] ata3.00: failed command: READ FPDMA QUEUED
[  111.804526] ata3.00: cmd 60/20:b8:b8:8c:b7/00:00:24:00:00/40 tag 23 ncq 16384 in
[  111.804528]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804532] ata3.00: status: { DRDY }
[  111.804535] ata3.00: failed command: READ FPDMA QUEUED
[  111.804543] ata3.00: cmd 60/40:c0:a8:19:b8/00:00:24:00:00/40 tag 24 ncq 32768 in
[  111.804545]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804549] ata3.00: status: { DRDY }
[  111.804552] ata3.00: failed command: READ FPDMA QUEUED
[  111.804560] ata3.00: cmd 60/08:c8:d0:5c:b7/00:00:24:00:00/40 tag 25 ncq 4096 in
[  111.804562]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804566] ata3.00: status: { DRDY }
[  111.804570] ata3.00: failed command: READ FPDMA QUEUED
[  111.804578] ata3.00: cmd 60/00:d0:b8:88:b7/04:00:24:00:00/40 tag 26 ncq 524288 in
[  111.804580]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804583] ata3.00: status: { DRDY }
[  111.804587] ata3.00: failed command: READ FPDMA QUEUED
[  111.804595] ata3.00: cmd 60/00:d8:b8:84:b7/04:00:24:00:00/40 tag 27 ncq 524288 in
[  111.804597]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804601] ata3.00: status: { DRDY }
[  111.804604] ata3.00: failed command: READ FPDMA QUEUED
[  111.804612] ata3.00: cmd 60/30:e0:40:18:b8/00:00:24:00:00/40 tag 28 ncq 24576 in
[  111.804614]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804618] ata3.00: status: { DRDY }
[  111.804621] ata3.00: failed command: READ FPDMA QUEUED
[  111.804629] ata3.00: cmd 60/b0:e8:f8:38:b8/00:00:24:00:00/40 tag 29 ncq 90112 in
[  111.804631]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804635] ata3.00: status: { DRDY }
[  111.804638] ata3.00: failed command: READ FPDMA QUEUED
[  111.804646] ata3.00: cmd 60/38:f0:d0:02:b7/00:00:24:00:00/40 tag 30 ncq 28672 in
[  111.804648]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.804652] ata3.00: status: { DRDY }
[  111.804659] ata3: hard resetting link
[  111.804662] ata3: nv: skipping hardreset on occupied port
[  112.328033] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  112.376448] ata3.00: configured for UDMA/133
[  112.376454] ata3.00: device reported invalid CHS sector 0
[  112.376458] ata3.00: device reported invalid CHS sector 0
[  112.376462] ata3.00: device reported invalid CHS sector 0
[  112.376465] ata3.00: device reported invalid CHS sector 0
[  112.376468] ata3.00: device reported invalid CHS sector 0
[  112.376471] ata3.00: device reported invalid CHS sector 0
[  112.376475] ata3.00: device reported invalid CHS sector 0
[  112.376478] ata3.00: device reported invalid CHS sector 0
[  112.376481] ata3.00: device reported invalid CHS sector 0
[  112.376485] ata3.00: device reported invalid CHS sector 0
[  112.376488] ata3.00: device reported invalid CHS sector 0
[  112.376491] ata3.00: device reported invalid CHS sector 0
[  112.376494] ata3.00: device reported invalid CHS sector 0
[  112.376498] ata3.00: device reported invalid CHS sector 0
[  112.376501] ata3.00: device reported invalid CHS sector 0
[  112.376504] ata3.00: device reported invalid CHS sector 0
[  112.376508] ata3.00: device reported invalid CHS sector 0
[  112.376511] ata3.00: device reported invalid CHS sector 0
[  112.376514] ata3.00: device reported invalid CHS sector 0
[  112.376518] ata3.00: device reported invalid CHS sector 0
[  112.376521] ata3.00: device reported invalid CHS sector 0
[  112.376524] ata3.00: device reported invalid CHS sector 0
[  112.376527] ata3.00: device reported invalid CHS sector 0
[  112.376531] ata3.00: device reported invalid CHS sector 0
[  112.376534] ata3.00: device reported invalid CHS sector 0
[  112.376537] ata3.00: device reported invalid CHS sector 0
[  112.376571] ata3: EH complete
[  113.485526] <30>udev[336]: starting version 167
[  113.553643] Adding 3905532k swap on /dev/sda9.  Priority:-1 extents:1 across:3905532k 
[  113.581467] lp: driver loaded but no devices found
[  113.635118] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[  113.637310] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[  113.655628] NV_TCO: NV TCO WatchDog Timer Driver v0.01
[  113.655876] NV_TCO: Watchdog reboot not detected.
[  113.657184] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
[  113.657549] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[  113.719524] cfg80211: Calling CRDA to update world regulatory domain
[  113.815519] r852 0000:07:05.3: can't find IRQ for PCI INT C; probably buggy MP table
[  113.815532] r852 0000:07:05.3: setting latency timer to 64
[  113.822742] r852: Non dma capable device detected, dma disabled
[  113.822765] r852: driver loaded succesfully
[  113.845407] Linux video capture interface: v2.00
[  113.886743] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1810)
[  113.893545] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[  113.895131] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[  113.895146] uvcvideo: Failed to initialize the device (-5).
[  113.895250] usbcore: registered new interface driver uvcvideo
[  113.895253] USB Video Class driver (v1.0.0)
[  113.929114] EXT4-fs (sda10): re-mounted. Opts: errors=remount-ro
[  114.155599] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  114.220234] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  114.220241] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220246] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  114.220250] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220254] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  114.220258] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220261] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  114.220265] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220269] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  114.220273] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220276] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  114.220281] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220284] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  114.220288] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220291] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  114.220296] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220299] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  114.220303] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220307] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  114.220311] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220314] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  114.220318] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220322] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  114.220326] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220329] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  114.220333] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.220337] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  114.220341] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[  114.244138] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  114.245084] Registered led device: b43-phy0::tx
[  114.245121] Registered led device: b43-phy0::rx
[  114.245154] Registered led device: b43-phy0::radio
[  114.245181] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[  114.254792] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  114.254800] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254804] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  114.254809] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254812] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  114.254816] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254820] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  114.254824] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254827] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  114.254832] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254835] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  114.254839] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254842] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  114.254847] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254850] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  114.254854] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254858] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  114.254862] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254865] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  114.254869] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254873] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  114.254877] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254880] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  114.254884] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254888] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  114.254892] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254895] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  114.254900] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  114.254904] cfg80211: World regulatory domain updated:
[  114.254907] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  114.254911] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  114.254915] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  114.254919] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  114.254923] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  114.254927] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  114.326306] HDA Intel 0000:00:10.1: can't find IRQ for PCI INT B; probably buggy MP table
[  114.326314] hda_intel: Disable MSI for Nvidia chipset
[  114.326352] HDA Intel 0000:00:10.1: setting latency timer to 64
[  114.490567] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[  114.640198] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0
[  114.706400] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input1
[  115.214192] EXT4-fs (sda11): mounted filesystem with ordered data mode. Opts: (null)
[  117.380020] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0001
[  145.888040] ata3: EH in SWNCQ mode,QC:qc_active 0xFF sactive 0xFF
[  145.888054] ata3: SWNCQ:qc_active 0xFD defer_bits 0x2 last_issue_tag 0x7
[  145.888056]   dhfis 0x7D dmafis 0x0 sdbfis 0x0
[  145.888068] ata3: ATA_REG 0x40 ERR_REG 0x0
[  145.888074] ata3: tag : dhfis dmafis sdbfis sacitve
[  145.888081] ata3: tag 0x0: 1 0 0 1  
[  145.888087] ata3: tag 0x2: 1 0 0 1  
[  145.888092] ata3: tag 0x3: 1 0 0 1  
[  145.888098] ata3: tag 0x4: 1 0 0 1  
[  145.888103] ata3: tag 0x5: 1 0 0 1  
[  145.888109] ata3: tag 0x6: 1 0 0 1  
[  145.888117] ata3: tag 0x7: 0 0 0 1  
[  145.888133] ata3.00: NCQ disabled due to excessive errors
[  145.888139] ata3.00: exception Emask 0x0 SAct 0xff SErr 0x0 action 0x6 frozen
[  145.888151] ata3.00: failed command: READ FPDMA QUEUED
[  145.888166] ata3.00: cmd 60/10:00:30:38:e4/00:00:24:00:00/40 tag 0 ncq 8192 in
[  145.888168]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  145.888186] ata3.00: status: { DRDY }
[  145.888194] ata3.00: failed command: READ FPDMA QUEUED
[  145.888207] ata3.00: cmd 60/08:08:00:b8:e6/00:00:24:00:00/40 tag 1 ncq 4096 in
[  145.888209]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  145.888227] ata3.00: status: { DRDY }
[  145.888234] ata3.00: failed command: READ FPDMA QUEUED
[  145.888247] ata3.00: cmd 60/38:10:60:39:e4/00:00:24:00:00/40 tag 2 ncq 28672 in
[  145.888248]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  145.888266] ata3.00: status: { DRDY }
[  145.888273] ata3.00: failed command: READ FPDMA QUEUED
[  145.888286] ata3.00: cmd 60/08:18:20:38:e4/00:00:24:00:00/40 tag 3 ncq 4096 in
[  145.888288]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  145.888306] ata3.00: status: { DRDY }
[  145.888313] ata3.00: failed command: READ FPDMA QUEUED
[  145.888326] ata3.00: cmd 60/08:20:10:08:e5/00:00:24:00:00/40 tag 4 ncq 4096 in
[  145.888328]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  145.888345] ata3.00: status: { DRDY }
[  145.888352] ata3.00: failed command: READ FPDMA QUEUED
[  145.888365] ata3.00: cmd 60/08:28:98:88:e5/00:00:24:00:00/40 tag 5 ncq 4096 in
[  145.888367]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  145.888385] ata3.00: status: { DRDY }
[  145.888392] ata3.00: failed command: READ FPDMA QUEUED
[  145.888404] ata3.00: cmd 60/08:30:50:a1:e5/00:00:24:00:00/40 tag 6 ncq 4096 in
[  145.888406]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  145.888424] ata3.00: status: { DRDY }
[  145.888431] ata3.00: failed command: READ FPDMA QUEUED
[  145.888444] ata3.00: cmd 60/08:38:00:29:e6/00:00:24:00:00/40 tag 7 ncq 4096 in
[  145.888446]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  145.888464] ata3.00: status: { DRDY }
[  145.888475] ata3: hard resetting link
[  145.888478] ata3: nv: skipping hardreset on occupied port
[  146.412034] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  146.465230] ata3.00: configured for UDMA/133
[  146.465237] ata3.00: device reported invalid CHS sector 0
[  146.465241] ata3.00: device reported invalid CHS sector 0
[  146.465244] ata3.00: device reported invalid CHS sector 0
[  146.465248] ata3.00: device reported invalid CHS sector 0
[  146.465251] ata3.00: device reported invalid CHS sector 0
[  146.465255] ata3.00: device reported invalid CHS sector 0
[  146.465258] ata3.00: device reported invalid CHS sector 0
[  146.465262] ata3.00: device reported invalid CHS sector 0
[  146.465279] ata3: EH complete
[  147.149338] vesafb: framebuffer at 0xc0000000, mapped to 0xf9180000, using 3072k, total 3072k
[  147.149345] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[  147.149349] vesafb: scrolling: redraw
[  147.149353] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[  147.150954] Console: switching to colour frame buffer device 128x48
[  147.177235] ppdev: user-space parallel port driver
[  147.204338] fb0: VESA VGA frame buffer device
[  147.213934] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  147.296574] b43-phy0 ERROR: Cannot request IRQ-0
[  147.708118] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  147.782002] b43-phy0 ERROR: Cannot request IRQ-0
[  149.130111] EXT4-fs (sda10): re-mounted. Opts: errors=remount-ro,commit=0
[  149.134598] EXT4-fs (sda8): re-mounted. Opts: commit=0
[  149.214100] EXT4-fs (sda11): re-mounted. Opts: commit=0
[  151.630584] EXT4-fs (sda10): re-mounted. Opts: errors=remount-ro,commit=0
[  151.637250] EXT4-fs (sda8): re-mounted. Opts: commit=0
[  151.641991] EXT4-fs (sda11): re-mounted. Opts: commit=0
[  157.648024] eth0: no IPv6 routers present

```

Relevant BIOS screens below:

---

### Post by pytheas22 on 2011-08-18
**prosperoa**: I'm happy to try to help you, but it would be better if you could please start a new thread.  Your issue may or may not stem from the same problem as the one we've been dealing with here; either way, there's already enough here that I think it would make more sense for you to start your own thread.  Please do that, let me know the URL and I'll respond there.

**KemKev**: thanks for posting all that output, and for going to the trouble of snapping photos of the BIOS screen.  I believe you now that you've got no options!  That's really terrible.  I didn't know they were shipping BIOS programs that dumbed down these days.  But I guess I should have assumed they were, since they know better than us what we want our computers to do.

Unfortunately, I've scoured your dmesg output and I can't see any indication of why the green light would have come on during the session with "pci=rotueirq" enabled.  I was hoping there might be some clue to be pulled from this but it appears not.  In any case, it looks like the IRQ issue persists as usual regardless of whether the green light is on or not.

At this point, I think I might have to admit defeat rather than continuing to make you run around in circles posting more and more output.  Everything I've read suggests that you should be able to work around IRQ problems either by adding special kernel parameters or trying a different driver, but in your case it seems that nothing is helping.

Since you didn't have this problem in Ubuntu 10.10, one possible workaround would be to downgrade to the Ubuntu 10.10 kernel, where your IRQ routing should work properly.  You should be able to run a 10.10 kernel in 11.04 without trouble--your 11.04 applications will all still be there (and you won't have to reinstall the system), just with a slightly older kernel running in the background.  You could easily install the 10.10 kernel using the packages from [http://packages.ubuntu.com/search?keywords=linux-image&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=linux-image&searchon=names&suite=maverick&section=all)  If you want to go this route and need more specific instructions, let me know.

Otherwise, the only suggestion I can make is to file a bug report on Launchpad, where you will hopefully get the attention of people more qualified to troubleshoot IRQ problems than I.  Again, if you want to file a report and don't know how, just let me know.

By the way, I hate to tell you this, and I may be wrong (I'm no expert in hard drive issues), but those lines in your dmesg output that start with "ata3..." seem like they may be indicating a problem with your hard disk.  You may want to check its health with smartctl (there are some instructions [here]("https://help.ubuntu.com/community/Smartmontools")), and as always, backup your important data!  But again, I stress that I'm not an expert in these things and your drive may actually be perfectly fine, so don't panic just yet.

---

### Post by KemKev on 2011-08-19
OK. Thank you for all your help in troubleshooting the issue.  Like I mentioned several posts ago, I have concluded that there is a bug in the 11.04 kernel that makes it incompatible with this laptop. I recall seeing a thread with the same topic (i.e. incomaptible laptops and Ubuntu) so at least I am not alone in that regard.

I am curious as to how I would be able to run the 10.10 kernel in 11.04, so I will go through the linked page you included.

In the interim, during one of my many reboots, I was cleaning up my basement and found a couple of AirLink 101 USB adapters that a friend gave me years ago because she wasn't using them. Out of curiosity I plugged one in and would you know it, after simply entering my network info, presto, wireless was working like a charm via the adapter.  Nothing to install, nothing to fiddle with really. Ubuntu should work like that "out of the box" :)

As an aside, regarding the potential hard drive failure, I did Google that particular error and from what I could see in a number of forums around the web, that error is also bug driven. I have done a comprehensive test of the hard drive, the only diagnostic option provided in the BIOS, and it indicated the drive is fine.  Good catch though and thanks for the proactive suggestions.

I have one printing problem (I can add a network printer but get an error printing to it) and will open a separate thread for that.

Even though we did not get the results we wanted, thanks again for your patience in trying to work this through. Your directions / instructions were always clear and you were a real pro all the way.

---

### Post by KemKev on 2011-08-22
[QUOTE=pytheas22]
Since you didn't have this problem in Ubuntu 10.10, one possible workaround would be to downgrade to the Ubuntu 10.10 kernel, where your IRQ routing should work properly.  You should be able to run a 10.10 kernel in 11.04 without trouble--your 11.04 applications will all still be there (and you won't have to reinstall the system), just with a slightly older kernel running in the background.  You could easily install the 10.10 kernel using the packages from [http://packages.ubuntu.com/search?keywords=linux-image&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=linux-image&searchon=names&suite=maverick&section=all)  If you want to go this route and need more specific instructions, let me know.[/QUOTE]
Specific instructions, please.  Thanks much.

---

### Post by pytheas22 on 2011-08-23
Sure.  To downgrade your kernel, first go to [http://packages.ubuntu.com/maverick/linux-image-2.6.35-22-generic](http://packages.ubuntu.com/maverick/linux-image-2.6.35-22-generic) and download the appropriate kernel image for your architecture (i386 for 32-bit or amd64 for 64-bit).  Save the .deb file to your desktop.  Then run these commands to install it and add the new kernel entry to your grub boot menu:
```

cd ~/Desktop
sudo dpkg -i linux*deb
sudo update-grub
```

Now you can boot into the older kernel by selecting it at the boot menu (if the grub menu isn't displayed by default, hold down shift during boot to bring it up).  If you want to make the older kernel the default, you can edit the menuentry sections in the /boot/grub/grub.cfg file (the first section is the one that will be booted by default).

In general all of your applications, etc. *should* work without issue in this slightly older kernel and shouldn't care which kernel you're running.  But let me know if you run into problems.

---

