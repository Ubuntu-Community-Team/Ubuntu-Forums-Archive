---
title: "yet another perfect upgrade"
date: 2012-08-26
forum: Mythbuntu
---

### Post by zapstrap on 2012-08-26
Upgraded a working system from 10.04 lts to 12.04 lts; now it won't boot; some things never change. I now get a udev error about some 'colord' reference being wrong, followed by a notification that the disk is either not ready or not present, Continue to wait, press S to skip it, M to manually fix it.

If I wait; well, nothing happens. If I press S, I get a couple more gripes about drives not being found, followed by ... nothing. If I hit M to manually fix the problem, I get a shell; the unavailable drive is present but read-only. If I run fsck on it, it tells me no errors. I checked the UUIDs against the drives in fstab (there are 3), they match. Since the drive is mounted read-only, I can't edit anything, so this appears to be useful in a ****-on-a-bull sort of way.

Holding the shift key down on boot to get into the grub menu only works one boot out of 20; what's the window in which I must press the shift key, 100nS or something? If the shift key repeating isn't fast enough for grub to catch it, how am I supposed to get the menu up?

Anybody got a suggestion, other than a hammer?

---

### Post by zapstrap on 2012-08-26
After a day of reading posts and studying, I now can at least boot the machine. I remounted the offending drive read/write and did an apt-get -f update. This fixed up a tonne of broken things from the install, but broke the grub loader; fixed by downloading a separate iso image for 12.04, and executing a manual repair. After that, the new installation manages to break dns, requiring modification of the /etc/network/interfaces file. It was so worth-while sticking with the "rock solid" lts builds.

I'm back to the original problem I have now had for over two years: the HVR-1600 does not load its drivers properly. I am unable to operate the analogue tuner in this card; whereas I previously could work around the problem by unloading and reloading the drivers several times, now the cx18_alsa driver will not unload, reporting it's in use, but lsmod | grep cx18 shows cx18_alsa 1, but does not say which module or process is using it. Since the driver is destined to never work properly, is there some way of unloading cx18_alsa? I have tried forcing and setting the verbose flags, and reading the rmmod page, but all to no avail.

---

### Post by zapstrap on 2012-08-26
anyone?

Why can't I rmmod cx18_alsa?

Is there anyway to determine what's using it?

---

### Post by nickrout on 2012-08-26
> **zapstrap said:**
> anyone?

Why can't I rmmod cx18_alsa?



Is there anyway to determine what's using it?

hey you only posted a few hours ago. Be patient!

---

### Post by zapstrap on 2012-08-26
> **nickrout said:**
> hey you only posted a few hours ago. Be patient!

True, but I've lost my patience. Usually I keep it chained up in the back yard, but this morning it broke the chain, hopped the fence and escaped through the antenna connector on the hvr1600. If you see it heading for Redmond, please feel free to open fire.

---

### Post by nickrout on 2012-08-26
> **zapstrap said:**
> True, but I've lost my patience. Usually I keep it chained up in the back yard, but this morning it broke the chain, hopped the fence and escaped through the antenna connector on the hvr1600. If you see it heading for Redmond, please feel free to open fire.

well at least you made me laugh.

lsmod|grep alsa ?

lsof|grep "whatever the device node is" ?

---

### Post by zapstrap on 2012-08-26
Sorry, self-inflicted schadenfreude has a way of cheering me up.

Anyway...

```

lsmod | grep alsa

cx18_alsa              13488  1
cx18                  117668  2 cx18_alsa
snd_pcm                80845  3 cx18_alsa,snd_hda_intel,snd_hda_codec
snd                    62064  20 cx18_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x
```

...and the second command...well I'm not sure what device you mean. The major node for the hvr-1600 is 81, because it has four devices in it, they come out as video1, video25, video33, and vbi1.  There's also a set of dvb nodes (major is 212), demux0, dvr0, frontend0, and net0

An open lsof command produces about 2,000 lines of output; more than anyone wants to pore over, methinks. If I grep on any of the aforementioned node numbers or names, I get ... nothing!

---

### Post by zapstrap on 2012-08-26
Just thinking, the major goal of all this is to allow the hvr-1600 function reliably; often these problems end up pushing backward  into a series of other problems to solve just so the main issue can be addressed. If there's a slick way of getting the drivers to load, without stopping myth, unloading and reloading, that would be so much better. The load/unload method is the only thing that I have found to work, but that doesn't mean there aren't other ways. If I can delay loading, or load in the right sequence, or trick the card into functioning some other way, that's the main thing.

One other datapoint is that the machine goes into standby when not busy, using the rtc to wake-up; so it goes through a sleep/boot cycle at least daily.

Hmm, my patience might be circling in the distance; I can hear the chain dragging on the ground.

---

### Post by PhilWig on 2012-08-27
Can't comment about your presenting probem, but a remark about you not being able to load drivers for your card.

Is the 1600 like the Hauppauge T500 in that microcode is not loaded after a reboot?  It needs a cold boot where you need remove power completely.  I also press 'start' button when powered off to discharge any psu capacitors. 

Sorry if completely off course with this.
Phil

---

### Post by klc5555 on 2012-08-27
> **zapstrap said:**
> anyone?

Why can't I rmmod cx18_alsa?

Is there anyway to determine what's using it?

Seems to be a pulseaudio issue. Cf.: [http://www.spinics.net/lists/linux-media/msg33915.html](http://www.spinics.net/lists/linux-media/msg33915.html)

---

### Post by zapstrap on 2012-08-27
> **PhilWig said:**
> Is the 1600 like the Hauppauge T500 in that microcode is not loaded after a reboot?  It needs a cold boot where you need remove power completely.  I also press 'start' button when powered off to discharge any psu capacitors.

I hadn't considered this, but I have powered the machine off completely (main switch on power supply, not the button on the case) with no change in behaviour.

---

### Post by zapstrap on 2012-08-27
> **klc5555 said:**
> Seems to be a pulseaudio issue. Cf.: [http://www.spinics.net/lists/linux-media/msg33915.html](http://www.spinics.net/lists/linux-media/msg33915.html)

I spent a good deal of time yesterday on that theory, trying to get pulseaudio to not load, but I never really got anywhere with it. The driver loading script seems to be both in init.d and to have some form of upstart support, not to mention it has it's own config files in /etc/pulse. It's really entrenched.

Is it possible to delay loading pulseaudio? Like somehow blacklist it (I know this is for kernel modules) or add a manual override to the upstart directory? This might actually let me do the load/unload trick before pulseaudio takes over and locks the alsa driver in place.

---

### Post by klc5555 on 2012-08-27
> **zapstrap said:**
> I spent a good deal of time yesterday on that theory, trying to get pulseaudio to not load, but I never really got anywhere with it. The driver loading script seems to be both in init.d and to have some form of upstart support, not to mention it has it's own config files in /etc/pulse. It's really entrenched.

Is it possible to delay loading pulseaudio? Like somehow blacklist it (I know this is for kernel modules) or add a manual override to the upstart directory? This might actually let me do the load/unload trick before pulseaudio takes over and locks the alsa driver in place.

I am not a pulseaudio fan, to put it mildly. On my mythtv frontend machines (well, on all my machines, actually), I've found it more satisfactory to uninstall pulseaudio, extirpate it root and branch, and just rely on regular naked plain-vanilla alsa. As per many many guides, an example of which being: [http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/](http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/)

But that's not a preferred solution for everybody. 

But neither do I believe that the constant unload/load trick at boot is still necessary for versions of the cx18 driver later than the version included with kernel 2.6.35 or so. Running cx18s on kernels 2.6.38.2, 3.2.4 and 3.2.27, I think I've had 2 failed cx18 loads over the last 4 or 5 months, leading only to degraded audio until cx18 reloading but otherwise correctly functioning. So I'm curious as to what your actual symptoms are (as well as your dmesg  output).

That said, the 1600 does appear to have certain quirks nowadays that emerged with mythtv 0.24.0 and above. First, on a clean install with a new clean mythconverg, mythtv does not seem to able to find the 1600's analog tuner on device node /dev/videoX, even though this node was registered when the cx18 loaded at boot. So the analog tuner cannot be added in the backend setup. But if the tuner was added in an earlier mythconverg and this db was upgraded, the tuner continues to function in the upgraded db. 

Second, I've only recently noticed I can't get any of my 4 1600s to scan for DVB-C QAM channels in Mythtv 0.24+ The scan errors out instantly with a "channel could not be opened" error. When I need to scan for QAM channels, I have to do it with one of my pcHDTV-HD5500s (I haven't bothered trying to scan the 1600s with dvb-tools yet ...some weekend when I've nothing to do.) The 1600s all tune DVB correctly, once something else has scanned for them.

So you may indeed experience difficulties with your 1600 in your upgraded installation, but I'm not certain that any difficulties in your installation will necessarily stem from the cx18 load itself, particularly when using a 1600 card model that functioned more-or-less correctly in 10.04.

---

### Post by zapstrap on 2012-08-27
> **klc5555 said:**
> So you may indeed experience difficulties with your 1600 in your upgraded installation, but I'm not certain that any difficulties in your installation will necessarily stem from the cx18 load itself, particularly when using a 1600 card model that functioned more-or-less correctly in 10.04.

It always required the unload/reload business to get it working. I just put the whole operation in rc.local and stopped sweating it, until now.

The main symptom is the analogue tuner has either a red or black screen, and does not tune any channels. Some people have complained of no sound, but when the tuner works, I always get both picture and sound.

dmesg certainly has some grumbling about cx18 drivers; here is an excerpt:

```

[84630.434561] cx18-0: Skipped encoder IDX, MDL 401, 2 times - it must have dropped out of rotation
[84630.434565] cx18-0: Skipped encoder IDX, MDL 403, 2 times - it must have dropped out of rotation
[84630.434569] cx18-0: Skipped encoder IDX, MDL 402, 2 times - it must have dropped out of rotation
[84630.434573] cx18-0: Could not find MDL 399 for stream encoder IDX
[84637.138038] cx18-0: Could not find MDL 400 for stream encoder IDX
[84637.138098] cx18-0: Skipped encoder IDX, MDL 403, 2 times - it must have dropped out of rotation
[84637.138163] cx18-0: Skipped encoder IDX, MDL 404, 2 times - it must have dropped out of rotation
[84637.138167] cx18-0: Skipped encoder IDX, MDL 403, 1 times - it must have dropped out of rotation
[84637.138170] cx18-0: Could not find MDL 401 for stream encoder IDX
[84643.787570] cx18-0: Skipped encoder IDX, MDL 405, 2 times - it must have dropped out of rotation
[84643.787575] cx18-0: Skipped encoder IDX, MDL 404, 2 times - it must have dropped out of rotation
[84643.787579] cx18-0: Skipped encoder IDX, MDL 406, 1 times - it must have dropped out of rotation
[84643.787583] cx18-0: Could not find MDL 402 for stream encoder IDX
[84643.787614] cx18-0: Could not find MDL 403 for stream encoder IDX
[84643.787664] cx18-0: Skipped encoder IDX, MDL 405, 1 times - it must have dropped out of rotation
[84643.787670] cx18-0: Could not find MDL 402 for stream encoder IDX
[84650.452639] cx18-0: Could not find MDL 401 for stream encoder IDX
[84650.452700] cx18-0: Skipped encoder IDX, MDL 404, 2 times - it must have dropped out of rotation
[84650.452704] cx18-0: Skipped encoder IDX, MDL 406, 2 times - it must have dropped out of rotation
[84650.452708] cx18-0: Skipped encoder IDX, MDL 405, 2 times - it must have dropped out of rotation
[84650.452712] cx18-0: Could not find MDL 401 for stream encoder IDX
[84650.452762] cx18-0: Skipped encoder IDX, MDL 404, 1 times - it must have dropped out of rotation
[84650.452767] cx18-0: Could not find MDL 402 for stream encoder IDX
[84657.156226] cx18-0: Skipped encoder IDX, MDL 406, 2 times - it must have dropped out of rotation
[84657.156232] cx18-0: Skipped encoder IDX, MDL 405, 2 times - it must have dropped out of rotation
[84657.156236] cx18-0: Skipped encoder IDX, MDL 407, 1 times - it must have dropped out of rotation
[84657.156240] cx18-0: Could not find MDL 403 for stream encoder IDX
[84657.156715] cx18-0: Could not find MDL 403 for stream encoder IDX
[84663.805825] cx18-0: Skipped encoder IDX, MDL 406, 2 times - it must have dropped out of rotation
[84663.805830] cx18-0: Skipped encoder IDX, MDL 405, 2 times - it must have dropped out of rotation
[84663.805834] cx18-0: Skipped encoder IDX, MDL 407, 2 times - it must have dropped out of rotation
[84663.805838] cx18-0: Could not find MDL 404 for stream encoder IDX
[84663.805877] cx18-0: Skipped encoder IDX, MDL 406, 1 times - it must have dropped out of rotation
[84663.805882] cx18-0: Could not find MDL 403 for stream encoder IDX
[84663.805931] cx18-0: Skipped encoder IDX, MDL 405, 1 times - it must have dropped out of rotation
[84663.805935] cx18-0: Could not find MDL 406 for stream encoder IDX
```

There is quite a lot of complaining about cx18, now that you mention it.

---

### Post by klc5555 on 2012-08-28
This is "dmesg | grep cx18" immediately after boot? Looks like the sort of messages that clutter the log when the 1600 is  tuning and decoding a stream.

The usual first steps would be to blacklist the cx18 module, load cx18 the first time from rc.local, and sleep the backend start script for 15-30 seconds, so that the module still loads up before the backend starts. But you already know this from using the card in 10.04. And check the dmesg |grep cx18 output from directly after boot to see whether cx18 is correctly identifying the particular analog tuner your card has (since there are so many different ones in the 1600). 

The second try would be to compile and install the cx18 module yourself from source. Which will be the first recommendation the folks over at linuxtv.org will likely give you. I would try two versions of cx18, to see if either works better for you. The first would be the currentmost dvb-v4l tarball source from their repository; the second would be the last version that was archived in the old mercurial repository at linuxtv.org, which dates to late 2010. Just a bit later than the cx18 version included in 10.04, it seemed to fix most of the dvb headaches that bedeviled the cx18 at least through kernel 2.6.35 and was a version of the driver that I used for quite a long while.

A third possibility would be to see whether you can do your traditional unload/reload of your cx18_alsa/cx18 if pulseaudio has been removed from the machine. 

And finally, if none of this does it for your cx18 (and you've tried recompiling/reinstalling the module), you'll likely need to contact the driver's developers over at linuxtv.org with information about your particular 1600 model number, which analog tuner the cx18 is identifying it as, etc.

---

### Post by zapstrap on 2012-08-28
You are correct, this was long after booting. Here's what it looks like immediately after boot:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-29-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 (Ubuntu 3.2.0-29.46-generic 3.2.24)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffce000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: System Manufacturer System Product Name/LG-95C, BIOS 080012  11/06/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7ffc0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000002effe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 002ec00000 page 2M
[    0.000000]  002ec00000 - 002effe000 page 4k
[    0.000000] kernel direct mapping tables up to 2effe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35a46000 - 36d1b000
[    0.000000] Allocated new RAMDISK: 2dd29000 - 2effd287
[    0.000000] Move RAMDISK from 0000000035a46000 - 0000000036d1a286 to 2dd29000 - 2effd286
[    0.000000] ACPI: RSDP 000fa1d0 00014 (v00 synnex)
[    0.000000] ACPI: RSDT 7ffc0000 00038 (v01 A M I  OEMRSDT  11000706 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffc0200 00084 (v02 A M I  OEMFACP  11000706 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffc0440 04FFB (v01  12345 12345123 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7ffce000 00040
[    0.000000] ACPI: APIC 7ffc0390 0006C (v01 A M I  OEMAPIC  11000706 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffc0400 0003C (v01 A M I  OEMMCFG  11000706 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffce040 00061 (v01 A M I  AMI_OEM  11000706 MSFT 00000097)
[    0.000000] ACPI: HPET 7ffc5440 00038 (v01 A M I  OEMHPET  11000706 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1295MB HIGHMEM available.
[    0.000000] 751MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2effe000
[    0.000000]   low ram: 0 - 2effe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002effe
[    0.000000]   HighMem  0x0002effe -> 0x0007ffc0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffc0
[    0.000000] On node 0 totalpages: 524111
[    0.000000] free_area_init_node: node 0, pgdat c1822e80, node_mem_map ecd28200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1472 pages used for memmap
[    0.000000]   Normal zone: 186942 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2592 pages used for memmap
[    0.000000]   HighMem zone: 329122 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @ecce8000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520015
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=4d8dd2db-c27d-45a8-be54-eca03c8ece0b ro quiet splash vmalloc=256M
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8387328 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (0002effe:0007ffc0)
[    0.000000] Memory: 2041508k/2096896k available (5615k kernel code, 54936k reserved, 2765k data, 712k init, 1326856k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xef7fe000 - 0xff7fe000   ( 256 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xeeffe000   ( 751 MB)
[    0.000000]       .init : 0xc1830000 - 0xc18e2000   ( 712 kB)
[    0.000000]       .data : 0xc157be04 - 0xc182f580   (2765 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157be04   (5615 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=ec00a000 soft=ec00c000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2659.896 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5319.79 BogoMIPS (lpj=10639584)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.008020] Security Framework initialized
[    0.008036] AppArmor: AppArmor initialized
[    0.008037] Yama: becoming mindful.
[    0.008088] Mount-cache hash table entries: 512
[    0.008214] Initializing cgroup subsys cpuacct
[    0.008220] Initializing cgroup subsys memory
[    0.008227] Initializing cgroup subsys devices
[    0.008229] Initializing cgroup subsys freezer
[    0.008231] Initializing cgroup subsys blkio
[    0.008236] Initializing cgroup subsys perf_event
[    0.008260] CPU: Physical Processor ID: 0
[    0.008262] CPU: Processor Core ID: 0
[    0.008265] mce: CPU supports 6 MCE banks
[    0.008272] CPU0: Thermal monitoring enabled (TM2)
[    0.008276] using mwait in idle threads.
[    0.009997] ACPI: Core revision 20110623
[    0.016010] ftrace: allocating 25891 entries in 51 pages
[    0.024045] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024389] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065071] CPU0: Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz stepping 06
[    0.068003] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.068003] PEBS disabled due to CPU errata.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=ec0f2000 soft=ec0f4000
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.156038] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156074] Brought up 2 CPUs
[    0.156077] Total of 2 processors activated (10639.79 BogoMIPS).
[    0.157788] devtmpfs: initialized
[    0.157788] EVM: security.selinux
[    0.157788] EVM: security.SMACK64
[    0.157788] EVM: security.capability
[    0.157788] PM: Registering ACPI NVS region at 7ffce000 (204800 bytes)
[    0.157788] print_constraints: dummy:
[    0.157788] RTC time: 16:48:47, date: 08/28/12
[    0.157788] NET: Registered protocol family 16
[    0.157788] Trying to unpack rootfs image as initramfs...
[    0.157788] EISA bus registered
[    0.157788] ACPI: bus type pci registered
[    0.157788] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.157788] PCI: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub with MMCONFIG support
[    0.157788] PCI: not using MMCONFIG
[    0.157788] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.157788] PCI: Using configuration type 1 for base access
[    0.160531] bio: create slab <bio-0> at 0
[    0.160606] ACPI: Added _OSI(Module Device)
[    0.160609] ACPI: Added _OSI(Processor Device)
[    0.160611] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.160613] ACPI: Added _OSI(Processor Aggregator Device)
[    0.161587] ACPI: EC: Look up EC in DSDT
[    0.163345] ACPI: Executed 1 blocks of module-level executable AML code
[    0.165481] ACPI: SSDT 7ffce0b0 00214 (v01    AMI   CPU1PM 00000001 INTL 20051117)
[    0.165732] ACPI: Dynamic OEM Table Load:
[    0.165735] ACPI: SSDT   (null) 00214 (v01    AMI   CPU1PM 00000001 INTL 20051117)
[    0.165895] ACPI: SSDT 7ffce2d0 00143 (v01    AMI   CPU2PM 00000001 INTL 20051117)
[    0.166142] ACPI: Dynamic OEM Table Load:
[    0.166145] ACPI: SSDT   (null) 00143 (v01    AMI   CPU2PM 00000001 INTL 20051117)
[    0.166960] ACPI: Interpreter enabled
[    0.166971] ACPI: (supports S0 S3 S4 S5)
[    0.166989] ACPI: Using IOAPIC for interrupt routing
[    0.174472] ACPI: No dock devices found.
[    0.174475] HEST: Table not found.
[    0.174480] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.174539] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.174662] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.174665] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.174668] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.174670] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.174672] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xffffffff] (ignored)
[    0.174683] pci 0000:00:00.0: [8086:2770] type 0 class 0x000600
[    0.174724] pci 0000:00:01.0: [8086:2771] type 1 class 0x000604
[    0.174763] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.174766] pci 0000:00:01.0: PME# disabled
[    0.174807] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.174821] pci 0000:00:1b.0: reg 10: [mem 0xf5efc000-0xf5efffff 64bit]
[    0.174889] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.174893] pci 0000:00:1b.0: PME# disabled
[    0.174908] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.174947] pci 0000:00:1d.0: reg 20: [io  0xdc00-0xdc1f]
[    0.174976] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.175015] pci 0000:00:1d.1: reg 20: [io  0xd880-0xd89f]
[    0.175044] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.175082] pci 0000:00:1d.2: reg 20: [io  0xd800-0xd81f]
[    0.175111] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.175150] pci 0000:00:1d.3: reg 20: [io  0xd480-0xd49f]
[    0.175189] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.175207] pci 0000:00:1d.7: reg 10: [mem 0xf5efbc00-0xf5efbfff]
[    0.175286] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.175290] pci 0000:00:1d.7: PME# disabled
[    0.175306] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.175366] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    0.175447] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.175489] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.175501] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.175510] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.175519] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.175528] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.175537] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.175570] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    0.175583] pci 0000:00:1f.2: reg 10: [io  0xd400-0xd407]
[    0.175591] pci 0000:00:1f.2: reg 14: [io  0xd080-0xd083]
[    0.175598] pci 0000:00:1f.2: reg 18: [io  0xd000-0xd007]
[    0.175606] pci 0000:00:1f.2: reg 1c: [io  0xcc00-0xcc03]
[    0.175614] pci 0000:00:1f.2: reg 20: [io  0xc880-0xc88f]
[    0.175647] pci 0000:00:1f.2: PME# supported from D3hot
[    0.175650] pci 0000:00:1f.2: PME# disabled
[    0.175663] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.175714] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.175781] pci 0000:01:00.0: [10de:0161] type 0 class 0x000300
[    0.175790] pci 0000:01:00.0: reg 10: [mem 0xf7000000-0xf7ffffff]
[    0.175801] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.175811] pci 0000:01:00.0: reg 1c: [mem 0xf6000000-0xf6ffffff 64bit]
[    0.175823] pci 0000:01:00.0: reg 30: [mem 0xf5fe0000-0xf5ffffff pref]
[    0.175859] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.175867] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.175871] pci 0000:00:01.0:   bridge window [mem 0xf5f00000-0xf7ffffff]
[    0.175875] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.175908] pci 0000:02:01.0: [4444:0016] type 0 class 0x000400
[    0.175926] pci 0000:02:01.0: reg 10: [mem 0xf0000000-0xf3ffffff pref]
[    0.176033] pci 0000:02:02.0: [14f1:5b7a] type 0 class 0x000400
[    0.176051] pci 0000:02:02.0: reg 10: [mem 0xf8000000-0xfbffffff]
[    0.176148] pci 0000:02:05.0: [10ec:8139] type 0 class 0x000200
[    0.176165] pci 0000:02:05.0: reg 10: [io  0xe800-0xe8ff]
[    0.176175] pci 0000:02:05.0: reg 14: [mem 0xfebffc00-0xfebffcff]
[    0.176243] pci 0000:02:05.0: supports D1 D2
[    0.176245] pci 0000:02:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.176250] pci 0000:02:05.0: PME# disabled
[    0.176288] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.176291] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.176295] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfebfffff]
[    0.176301] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xf3ffffff 64bit pref]
[    0.176303] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.176306] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.176315] pci_bus 0000:00: on NUMA node 0
[    0.176318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.176426] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.176524]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.180617] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.180661] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.180704] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.180746] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.180788] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.180833] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.180876] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.180920] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.181024] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.181028] vgaarb: loaded
[    0.181029] vgaarb: bridge control possible 0000:01:00.0
[    0.181138] i2c-core: driver [aat2870] using legacy suspend method
[    0.181140] i2c-core: driver [aat2870] using legacy resume method
[    0.181219] SCSI subsystem initialized
[    0.184229] libata version 3.00 loaded.
[    0.184229] usbcore: registered new interface driver usbfs
[    0.184229] usbcore: registered new interface driver hub
[    0.184229] usbcore: registered new device driver usb
[    0.184235] PCI: Using ACPI for IRQ routing
[    0.184235] PCI: pci_cache_line_size set to 64 bytes
[    0.184262] reserve RAM buffer: 000000000009fc00 - 000000000009ffff
[    0.184265] reserve RAM buffer: 000000007ffc0000 - 000000007fffffff
[    0.184363] NetLabel: Initializing
[    0.184365] NetLabel:  domain hash size = 128
[    0.184366] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.184376] NetLabel:  unlabeled traffic allowed by default
[    0.184418] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.184422] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.184427] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.188050] Switching to clocksource hpet
[    0.195579] AppArmor: AppArmor Filesystem Enabled
[    0.195608] pnp: PnP ACPI init
[    0.195625] ACPI: bus type pnp registered
[    0.195719] pnp 00:00: [bus 00-ff]
[    0.195722] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.195724] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.195726] pnp 00:00: [io  0x0d00-0xffff window]
[    0.195729] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.195731] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.195733] pnp 00:00: [mem 0x80000000-0xffffffff window]
[    0.195786] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.195796] pnp 00:01: [mem 0xfed13000-0xfed19fff]
[    0.195842] system 00:01: [mem 0xfed13000-0xfed19fff] has been reserved
[    0.195845] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.195877] pnp 00:02: [dma 4]
[    0.195879] pnp 00:02: [io  0x0000-0x000f]
[    0.195881] pnp 00:02: [io  0x0081-0x0083]
[    0.195883] pnp 00:02: [io  0x0087]
[    0.195885] pnp 00:02: [io  0x0089-0x008b]
[    0.195887] pnp 00:02: [io  0x008f]
[    0.195889] pnp 00:02: [io  0x00c0-0x00df]
[    0.195915] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.195924] pnp 00:03: [io  0x0070-0x0071]
[    0.195936] pnp 00:03: [irq 8]
[    0.195964] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.195972] pnp 00:04: [io  0x0061]
[    0.196033] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.196044] pnp 00:05: [io  0x00f0-0x00ff]
[    0.196049] pnp 00:05: [irq 13]
[    0.196076] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.197152] pnp 00:06: [io  0x03f0-0x03f5]
[    0.197154] pnp 00:06: [io  0x03f7]
[    0.197159] pnp 00:06: [irq 6]
[    0.197160] pnp 00:06: [dma 2]
[    0.197215] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.198009] pnp 00:07: [io  0x0378-0x037f]
[    0.198015] pnp 00:07: [irq 7]
[    0.198017] pnp 00:07: [dma 0 disabled]
[    0.198310] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.198895] pnp 00:08: [io  0x0010-0x001f]
[    0.198897] pnp 00:08: [io  0x0022-0x003f]
[    0.198899] pnp 00:08: [io  0x0044-0x005f]
[    0.198901] pnp 00:08: [io  0x0062-0x0063]
[    0.198903] pnp 00:08: [io  0x0065-0x006f]
[    0.198905] pnp 00:08: [io  0x0072-0x007f]
[    0.198906] pnp 00:08: [io  0x0080]
[    0.198908] pnp 00:08: [io  0x0084-0x0086]
[    0.198910] pnp 00:08: [io  0x0088]
[    0.198912] pnp 00:08: [io  0x008c-0x008e]
[    0.198914] pnp 00:08: [io  0x0090-0x009f]
[    0.198915] pnp 00:08: [io  0x00a2-0x00bf]
[    0.198917] pnp 00:08: [io  0x00e0-0x00ef]
[    0.198919] pnp 00:08: [io  0x04d0-0x04d1]
[    0.198921] pnp 00:08: [io  0x0800-0x087f]
[    0.198923] pnp 00:08: [io  0x0000-0xffffffff disabled]
[    0.198925] pnp 00:08: [io  0x0480-0x04bf]
[    0.198927] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.198929] pnp 00:08: [mem 0xfed20000-0xfed8ffff]
[    0.198987] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.198989] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.198992] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.198997] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.198999] system 00:08: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.199002] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199053] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.199084] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.199142] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.199145] pnp 00:0a: [mem 0xfff80000-0xffffffff]
[    0.199174] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    0.199209] pnp 00:0b: [mem 0xffc00000-0xfff7ffff]
[    0.199255] system 00:0b: [mem 0xffc00000-0xfff7ffff] has been reserved
[    0.199258] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199300] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.199303] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.199346] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.199348] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.199351] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199507] pnp 00:0d: [io  0x0000-0xffffffff disabled]
[    0.199509] pnp 00:0d: [io  0x0a00-0x0a0f]
[    0.199511] pnp 00:0d: [io  0x0a10-0x0a1f]
[    0.199513] pnp 00:0d: [io  0x0a20-0x0a2f]
[    0.199515] pnp 00:0d: [io  0x0a30-0x0a3f]
[    0.199566] system 00:0d: [io  0x0a00-0x0a0f] has been reserved
[    0.199569] system 00:0d: [io  0x0a10-0x0a1f] has been reserved
[    0.199571] system 00:0d: [io  0x0a20-0x0a2f] has been reserved
[    0.199573] system 00:0d: [io  0x0a30-0x0a3f] has been reserved
[    0.199576] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200185] pnp 00:0e: [io  0x03f8-0x03ff]
[    0.200190] pnp 00:0e: [irq 4]
[    0.200192] pnp 00:0e: [dma 0 disabled]
[    0.200284] pnp 00:0e: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.200315] pnp 00:0f: [mem 0xe0000000-0xe3ffffff]
[    0.200362] system 00:0f: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.200365] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200505] pnp 00:10: [mem 0x00000000-0x0009ffff]
[    0.200507] pnp 00:10: [mem 0x000c0000-0x000cffff]
[    0.200509] pnp 00:10: [mem 0x000e0000-0x000fffff]
[    0.200511] pnp 00:10: [mem 0x00100000-0x7fffffff]
[    0.200513] pnp 00:10: [mem 0x00000000-0xffffffff disabled]
[    0.200565] system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.200567] system 00:10: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.200570] system 00:10: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.200572] system 00:10: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.200575] system 00:10: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.200690] pnp: PnP ACPI: found 17 devices
[    0.200692] ACPI: ACPI bus type pnp unregistered
[    0.200695] PnPBIOS: Disabled by ACPI PNP
[    0.236954] PCI: max bus depth: 1 pci_try_num: 2
[    0.236976] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.236980] pci 0000:00:01.0:   bridge window [mem 0xf5f00000-0xf7ffffff]
[    0.236984] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.236989] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.236992] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.236996] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfebfffff]
[    0.237000] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xf3ffffff 64bit pref]
[    0.237034] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.237039] pci 0000:00:01.0: setting latency timer to 64
[    0.237045] pci 0000:00:1e.0: setting latency timer to 64
[    0.237049] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.237051] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.237053] pci_bus 0000:01: resource 1 [mem 0xf5f00000-0xf7ffffff]
[    0.237055] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.237058] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.237060] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xfebfffff]
[    0.237062] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf3ffffff 64bit pref]
[    0.237064] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.237066] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.237110] NET: Registered protocol family 2
[    0.237182] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.237395] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.237875] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.238108] TCP: Hash tables configured (established 131072 bind 65536)
[    0.238110] TCP reno registered
[    0.238113] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.238123] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.238196] NET: Registered protocol family 1
[    0.238229] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.238246] pci 0000:00:1d.0: PCI INT A disabled
[    0.238256] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.238271] pci 0000:00:1d.1: PCI INT B disabled
[    0.238280] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.238295] pci 0000:00:1d.2: PCI INT C disabled
[    0.238303] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.238318] pci 0000:00:1d.3: PCI INT D disabled
[    0.238325] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.238349] pci 0000:00:1d.7: PCI INT A disabled
[    0.238372] pci 0000:01:00.0: Boot video device
[    0.238380] PCI: CLS 32 bytes, default 64
[    0.238730] audit: initializing netlink socket (disabled)
[    0.238742] type=2000 audit(1346172526.232:1): initialized
[    0.261241] highmem bounce pool size: 64 pages
[    0.261247] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.269643] VFS: Disk quotas dquot_6.5.2
[    0.269714] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.270223] fuse init (API version 7.17)
[    0.270307] msgmni has been set to 1395
[    0.270590] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.270613] io scheduler noop registered
[    0.270615] io scheduler deadline registered
[    0.270621] io scheduler cfq registered (default)
[    0.270772] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.270793] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.270869] intel_idle: MWAIT substates: 0x20
[    0.270871] intel_idle: does not run on family 6 model 15
[    0.270950] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.270956] ACPI: Power Button [PWRB]
[    0.271001] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.271004] ACPI: Power Button [PWRF]
[    0.274472] thermal LNXTHERM:00: registered as thermal_zone0
[    0.274475] ACPI: Thermal Zone [THRM] (40 C)
[    0.274513] ERST: Table is not found!
[    0.274515] GHES: HEST is not enabled!
[    0.274583] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.294963] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.295313] isapnp: Scanning for PnP cards...
[    0.515731] Freeing initrd memory: 19284k freed
[    0.648231] isapnp: No Plug & Play device found
[    0.724662] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.740395] Linux agpgart interface v0.103
[    0.742036] brd: module loaded
[    0.742798] loop: module loaded
[    0.742936] ata_piix 0000:00:1f.1: version 2.13
[    0.742952] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.742989] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.743309] scsi0 : ata_piix
[    0.743389] scsi1 : ata_piix
[    0.744336] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.744339] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.744359] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.744363] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.744384] ata2: port disabled--ignoring
[    0.744394] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.744747] scsi2 : ata_piix
[    0.744816] scsi3 : ata_piix
[    0.744863] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 19
[    0.744865] ata4: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 19
[    0.745231] Fixed MDIO Bus: probed
[    0.745250] tun: Universal TUN/TAP device driver, 1.6
[    0.745251] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.745347] PPP generic driver version 2.4.2
[    0.745451] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.745465] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.745477] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.745480] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.745530] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.745547] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.745556] ehci_hcd 0000:00:1d.7: debug port 1
[    0.749440] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.749453] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf5efbc00
[    0.764028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.764222] hub 1-0:1.0: USB hub found
[    0.764229] hub 1-0:1.0: 8 ports detected
[    0.764317] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.764329] uhci_hcd: USB Universal Host Controller Interface driver
[    0.764343] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.764350] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.764352] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.764399] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.764421] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000dc00
[    0.764542] hub 2-0:1.0: USB hub found
[    0.764546] hub 2-0:1.0: 2 ports detected
[    0.764605] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.764612] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.764614] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.764654] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.764675] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
[    0.764792] hub 3-0:1.0: USB hub found
[    0.764795] hub 3-0:1.0: 2 ports detected
[    0.764853] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.764859] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.764862] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.764902] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.764930] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    0.765045] hub 4-0:1.0: USB hub found
[    0.765048] hub 4-0:1.0: 2 ports detected
[    0.765107] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.765113] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.765116] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.765158] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.765187] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d480
[    0.765300] hub 5-0:1.0: USB hub found
[    0.765304] hub 5-0:1.0: 2 ports detected
[    0.765404] usbcore: registered new interface driver libusual
[    0.765463] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.765823] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.765829] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.765953] mousedev: PS/2 mouse device common for all mice
[    0.766088] rtc_cmos 00:03: RTC can wake from S4
[    0.766186] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.766208] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.766272] device-mapper: uevent: version 1.0.3
[    0.766339] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.766369] EISA: Probing bus 0 at eisa.0
[    0.766393] EISA: Detected 0 cards.
[    0.766402] cpufreq-nforce2: No nForce2 chipset.
[    0.766405] cpuidle: using governor ladder
[    0.766406] cpuidle: using governor menu
[    0.766408] EFI Variables Facility v0.08 2004-May-17
[    0.766645] TCP cubic registered
[    0.766762] NET: Registered protocol family 10
[    0.767312] NET: Registered protocol family 17
[    0.767319] Registering the dns_resolver key type
[    0.767340] Using IPI No-Shortcut mode
[    0.767438] PM: Hibernation image not present or could not be loaded.
[    0.767450] registered taskstats version 1
[    0.777425]   Magic number: 8:601:844
[    0.777509] rtc_cmos 00:03: setting system clock to 2012-08-28 16:48:47 UTC (1346172527)
[    0.777791] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.777793] EDD information not available.
[    0.943652] ata3.00: ATA-8: ST31500341AS, CC1H, max UDMA/133
[    0.943657] ata3.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.943747] ata4.00: ATA-8: ST31500341AS, CC1H, max UDMA/133
[    0.943752] ata4.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.943760] ata4.01: ATAPI: ATAPI   iHAS124   Y, BL0V, max UDMA/100
[    0.943844] ata3.01: ATA-8: ST2000DM001-9YN164, CC47, max UDMA/133
[    0.943848] ata3.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.999597] ata4.00: configured for UDMA/133
[    0.999681] ata3.00: configured for UDMA/133
[    1.012267] ata4.01: configured for UDMA/100
[    1.012375] ata3.01: configured for UDMA/133
[    1.012543] scsi 2:0:0:0: Direct-Access     ATA      ST31500341AS     CC1H PQ: 0 ANSI: 5
[    1.012718] sd 2:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    1.012768] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.012810] sd 2:0:0:0: [sda] Write Protect is off
[    1.012813] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.012834] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.012900] scsi 2:0:1:0: Direct-Access     ATA      ST2000DM001-9YN1 CC47 PQ: 0 ANSI: 5
[    1.013034] sd 2:0:1:0: Attached scsi generic sg1 type 0
[    1.013147] scsi 3:0:0:0: Direct-Access     ATA      ST31500341AS     CC1H PQ: 0 ANSI: 5
[    1.013244] sd 3:0:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    1.013267] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.013288] sd 3:0:0:0: [sdc] Write Protect is off
[    1.013290] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.013310] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.014601] scsi 3:0:1:0: CD-ROM            ATAPI    iHAS124   Y      BL0V PQ: 0 ANSI: 5
[    1.034034] sd 2:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.034039] sd 2:0:1:0: [sdb] 4096-byte physical blocks
[    1.034109] sd 2:0:1:0: [sdb] Write Protect is off
[    1.034113] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.034143] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.038535]  sdc: sdc1
[    1.039399] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.039403] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.039532] sd 3:0:0:0: [sdc] Attached SCSI disk
[    1.039558] sr 3:0:1:0: Attached scsi CD-ROM sr0
[    1.039683] sr 3:0:1:0: Attached scsi generic sg3 type 5
[    1.067727]  sda: sda1 sda2 sda3
[    1.071564]  sdb: sdb1
[    1.071591] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.071821] sd 2:0:1:0: [sdb] Attached SCSI disk
[    1.071847] Freeing unused kernel memory: 712k freed
[    1.072057] Write protecting the kernel text: 5616k
[    1.072100] Write protecting the kernel read-only data: 2324k
[    1.086948] udevd[94]: starting version 175
[    1.144876] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.144900] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.145259] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.145297] 8139too 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.146198] 8139too 0000:02:05.0: eth0: RealTek RTL8139 at 0xe800, 00:18:37:02:f7:34, IRQ 20
[    1.183969] FDC 0 is a post-1991 82077
[    1.236096] Refined TSC clocksource calibration: 2659.999 MHz.
[    1.236103] Switching to clocksource tsc
[    1.260047] usb 3-1: new low-speed USB device number 2 using uhci_hcd
[    1.447060] usbcore: registered new interface driver usbhid
[    1.447062] usbhid: USB HID core driver
[    7.686181] kjournald starting.  Commit interval 5 seconds
[    7.686233] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   24.479926] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.537381] udevd[360]: starting version 175
[   24.729467] Adding 4562456k swap on /dev/sda3.  Priority:-1 extents:1 across:4562456k
[   24.837307] type=1400 audit(1346172551.554:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=567 comm="apparmor_parser"
[   24.837685] type=1400 audit(1346172551.554:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=567 comm="apparmor_parser"
[   24.837906] type=1400 audit(1346172551.554:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=567 comm="apparmor_parser"
[   24.840397] type=1400 audit(1346172551.558:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=633 comm="apparmor_parser"
[   24.896379] parport_pc 00:07: reported by Plug and Play ACPI
[   24.896466] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   24.912710] 8139too 0000:02:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   25.077018] input: HOLTEK Wireless 2.4GHz TouchPad Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2
[   25.077102] LC RC1000MCE 0003:1241:F767.0001: input,hidraw0: USB HID v1.10 Keyboard [HOLTEK Wireless 2.4GHz TouchPad Keyboard] on usb-0000:00:1d.1-1/input0
[   25.104779] input: HOLTEK Wireless 2.4GHz TouchPad Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input3
[   25.106584] LC RC1000MCE 0003:1241:F767.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [HOLTEK Wireless 2.4GHz TouchPad Keyboard] on usb-0000:00:1d.1-1/input1
[   25.139072] Linux video capture interface: v2.00
[   25.192153] intel_rng: FWH not detected
[   25.203574] ppdev: user-space parallel port driver
[   25.204667] lp0: using parport0 (interrupt-driven).
[   25.308835] coretemp coretemp.0: Using relative temperature scale!
[   25.308846] coretemp coretemp.0: Using relative temperature scale!
[   25.322831] it87: Found IT8718F chip at 0xa10, revision 2
[   25.505494] nvidia: module license 'NVIDIA' taints kernel.
[   25.505499] Disabling lock debugging due to kernel taint
[   25.519289] leds_ss4200: no LED devices found
[   25.625027] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.625073] snd_hda_intel 0000:00:1b.0: irq 40 for MSI/MSI-X
[   25.625096] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   25.629852] cx18:  Start initialization, version 1.5.1
[   25.629879] cx18-0: Initializing card 0
[   25.629881] cx18-0: Autodetected Hauppauge card
[   25.629920] cx18 0000:02:02.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   25.636241] cx18-0: cx23418 revision 01010000 (B)
[   25.766398] hda_codec: ALC883: BIOS auto-probing.
[   25.774858] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   25.775039] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   25.775202] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   25.775364] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   25.775529] input: HDA Intel Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   25.775698] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   25.775860] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   25.776040] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   25.799046] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.799055] nvidia 0000:01:00.0: setting latency timer to 64
[   25.799060] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   25.800175] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.40  Thu Apr  5 21:28:09 PDT 2012
[   25.854528] tveeprom 0-0050: Hauppauge model 74541, rev C6A3, serial# 6230077
[   25.854532] tveeprom 0-0050: MAC address is 00:0d:fe:5f:10:3d
[   25.854535] tveeprom 0-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   25.854537] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   25.854539] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   25.854541] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   25.854543] tveeprom 0-0050: has radio
[   25.854545] cx18-0: Autodetected Hauppauge HVR-1600
[   25.854547] cx18-0: Simultaneous Digital and Analog TV capture supported
[   25.900143] ivtv: Start initialization, version 1.4.3
[   25.953353] i2c-core: driver [tuner] using legacy suspend method
[   25.953355] i2c-core: driver [tuner] using legacy resume method
[   26.015875] EXT3-fs (sda1): using internal journal
[   26.028753] tda9887 1-0043: creating new instance
[   26.028756] tda9887 1-0043: tda988[5/6/7] found
[   26.029664] tuner 1-0043: Tuner 74 found with type(s) Radio TV.
[   26.031908] tuner 1-0061: Tuner -1 found with type(s) Radio TV.
[   26.035303] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   26.044387] tuner-simple 1-0061: creating new instance
[   26.044391] tuner-simple 1-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   26.046502] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   26.046506] DVB: registering new adapter (cx18)
[   26.206268] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   26.208176] SGI XFS Quota Management subsystem
[   26.209046] MXL5005S: Attached at address 0x63
[   26.209051] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   26.209225] cx18-0: DVB Frontend registered
[   26.209228] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   26.209319] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   26.209397] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   26.209477] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   26.209554] cx18-0: Registered device radio0 for encoder radio
[   26.209556] cx18-0: Initialized card: Hauppauge HVR-1600
[   26.209609] ivtv0: Initializing card 0
[   26.209612] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   26.209820] cx18:  End initialization
[   26.215086] ivtv 0000:02:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.216830] XFS (sdc1): Mounting Filesystem
[   26.271428] tveeprom 2-0050: Hauppauge model 26582, rev F0B2, serial# 9602618
[   26.271432] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   26.271434] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   26.271436] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   26.271439] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   26.271440] tveeprom 2-0050: has no radio
[   26.271443] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   26.282870] cx18-alsa: module loading...
[   26.297263] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   26.317195] tuner 2-0061: Tuner -1 found with type(s) Radio TV.
[   26.329751] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   26.346785] tuner-simple 2-0061: creating new instance
[   26.346788] tuner-simple 2-0061: type set to 50 (TCL 2002N)
[   26.348199] ivtv0: Registered device video1 for encoder MPG (4096 kB)
[   26.348278] ivtv0: Registered device video33 for encoder YUV (2048 kB)
[   26.348354] ivtv0: Registered device vbi1 for encoder VBI (1024 kB)
[   26.348431] ivtv0: Registered device video25 for encoder PCM (320 kB)
[   26.348433] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   26.348896] ivtv: End initialization
[   26.355521] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   26.505821] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   26.512178] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   26.645381] XFS (sdc1): Ending clean mount
[   26.713012] XFS (sda2): Mounting Filesystem
[   26.844297] XFS (sda2): Ending clean mount
[   26.893520] XFS (sdb1): Mounting Filesystem
[   26.990684] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   27.025427] XFS (sdb1): Ending clean mount
[   27.057903] init: failsafe main process (963) killed by TERM signal
[   27.188159] ivtv0: Encoder revision: 0x02060039
[   27.324601] Bluetooth: Core ver 2.16
[   27.324640] NET: Registered protocol family 31
[   27.324642] Bluetooth: HCI device and connection manager initialized
[   27.324644] Bluetooth: HCI socket layer initialized
[   27.324646] Bluetooth: L2CAP socket layer initialized
[   27.325035] Bluetooth: SCO socket layer initialized
[   27.354919] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   27.376267] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   27.400025] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.400028] Bluetooth: BNEP filters: protocol multicast
[   27.410793] Bluetooth: RFCOMM TTY layer initialized
[   27.410798] Bluetooth: RFCOMM socket layer initialized
[   27.410800] Bluetooth: RFCOMM ver 1.11
[   27.439017] type=1400 audit(1346172554.154:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1066 comm="apparmor_parser"
[   27.441180] type=1400 audit(1346172554.158:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1066 comm="apparmor_parser"
[   27.441388] type=1400 audit(1346172554.158:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1066 comm="apparmor_parser"
[   27.450401] type=1400 audit(1346172554.166:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1067 comm="apparmor_parser"
[   27.455037] type=1400 audit(1346172554.170:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=1067 comm="apparmor_parser"
[   27.455930] type=1400 audit(1346172554.170:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=1067 comm="apparmor_parser"
[   27.617201] lirc_dev: IR Remote Control driver registered, major 250
[   27.713012] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[   28.612010] lirc_serial: auto-detected active low receiver
[   28.612083] lirc_serial lirc_serial.0: lirc_dev: driver lirc_serial registered at minor = 0
[   30.737906] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   31.523833] init: udev-fallback-graphics main process (1612) terminated with status 1
[   31.536723] init: gdm main process (1640) killed by TERM signal
[   35.056028] eth0: no IPv6 routers present
[   35.873836] init: plymouth-stop pre-start process (2010) terminated with status 1
[   41.260159] lirc_serial: ignoring spike: 1 1 503cf698 503cf698 39468 3945a
```

I should say, I've rebooted several times now and checked all three tuners (the two in the hvr-1600 plus the additional pvr-150). It seems awfully random; sometimes I don't get the pvr-150, others I do, but nothing from the hvr-1600; sometimes I get all three, but usually I get the pvr-150 and the hvr-1600 digital tuner, no analogue. The dmesg output above is from a boot in which the hvr-1600 analogue tuner failed to work.

Every time I reboot though, I must manually kill pulseaudio and let it restart, otherwise I get no sound (100% of the time).

---

### Post by nickrout on 2012-08-28
Last problem - simply delete pulseaudiio from your system. 

Is part of the problem that the tuners load in different order? So one time the 1600 is /dev/video0 and the 150 is /dev/video1 and the next time it is the other way round?

---

### Post by klc5555 on 2012-08-28
> **zapstrap said:**
> 
I should say, I've rebooted several times now and checked all three tuners (the two in the hvr-1600 plus the additional pvr-150). It seems awfully random; sometimes I don't get the pvr-150, others I do, but nothing from the hvr-1600; sometimes I get all three, but usually I get the pvr-150 and the hvr-1600 digital tuner, no analogue. The dmesg output above is from a boot in which the hvr-1600 analogue tuner failed to work.

Every time I reboot though, I must manually kill pulseaudio and let it restart, otherwise I get no sound (100% of the time).

It appears that the cx18 driver and firmware are loading correctly. It also looks like the analog tuners may be swapping /dev/videoX numbers and conflicting at reboot. You may wish to compel one (or the other) analog tuner to always load at /dev/video1 at boot, and allow its compatriot to always have /dev/video0 free and clear.

This would require adding a text configuration file, named, say, "tuners.conf" under /etc/modprobe.d/  If it's the 1600 you want always to load at /dev/video1, the single line in this config file would be ```
options cx18 cx18_first_minor=1
``` If, however, it's the 150 you need always to load at /dev/video1, the line in tuners.conf would be ```
options ivtv ivtv_first_minor=1
```

Then after reboot, you'd need to go into the mythbackend setup to assure that each of the two analog tuners was set up correctly on its now-permanent /dev/videoX device node.

As for killing pulseaudio, my initial impulse would be to kill it dead and proper --i.e. remove it and just use alsa. But otherwise, if you must kill it and let it respawn, since rc.local is supposed to the last script run at boot, and runs as root, you may be able to add a killall line for pulseaudio to the end of it to get the job done.

---

### Post by zapstrap on 2012-08-28
Thanks for the info, I'll try forcing the analogue tuner to /dev/video1. I don't mind poring over documentation, but this seems like sort of an obscure thing to expect the user to just know how to do; granting that building one of these boxes with even one tuner is not for the feint of heart.

Lastly, if you'll pardon a retarded question: What, exactly, does pulseaudio do for me? I notice on the mixer panel all of the hda-alsa controls look elaborate yet easy to configure, but the fancy-shmancy pulseaudio driver just looks like plain vanilla analogue control. None of the alsa controls work, but the ONE slider for pulseaudio does; so... why is this here? It looks regressive.

---

### Post by zapstrap on 2012-08-28
Just gave it a go, and it looks to my untrained eye like it did what I wanted; alas there's no picture on the hvr-1600 analogue tuner, though sound does work.  Here's some abridged dmesg info:

```

...$ dmesg | grep 'cx18\|ivtv'
[   25.583247] ivtv: Start initialization, version 1.4.3
[   25.583302] ivtv0: Initializing card 0
[   25.583304] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   25.583386] ivtv 0000:02:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   25.637236] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   25.675708] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   25.725738] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   25.740176] cx18:  Start initialization, version 1.5.1
[   25.826121] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   25.826184] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   25.826231] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   25.826278] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   25.826280] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   25.826304] cx18-0: Initializing card 0
[   25.826306] cx18-0: Autodetected Hauppauge card
[   25.826344] cx18 0000:02:02.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   25.832487] cx18-0: cx23418 revision 01010000 (B)
[   25.832534] ivtv: End initialization
[   26.055501] cx18-0: Autodetected Hauppauge HVR-1600
[   26.055504] cx18-0: Simultaneous Digital and Analog TV capture supported
[   26.166694] cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   26.174222] cx18-0: Registered device video1 for encoder MPEG (64 x 32.00 kB)
[   26.174225] DVB: registering new adapter (cx18)
[   26.235500] cx18-0: DVB Frontend registered
[   26.235503] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   26.235591] cx18-0: Registered device video33 for encoder YUV (20 x 101.25 kB)
[   26.235668] cx18-0: Registered device vbi1 for encoder VBI (20 x 51984 bytes)
[   26.235747] cx18-0: Registered device video25 for encoder PCM audio (256 x 4.00 kB)
[   26.235827] cx18-0: Registered device radio1 for encoder radio
[   26.235829] cx18-0: Initialized card: Hauppauge HVR-1600
[   26.236040] cx18:  End initialization
[   26.368836] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   26.493641] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   26.498223] cx18-alsa: module loading...
[   26.508507] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   26.508593] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   26.708219] ivtv0: Encoder revision: 0x02060039
[   27.366538] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   27.387864] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
```

---

### Post by klc5555 on 2012-08-28
> **zapstrap said:**
> Thanks for the info, I'll try forcing the analogue tuner to /dev/video1. I don't mind poring over documentation, but this seems like sort of an obscure thing to expect the user to just know how to do; granting that building one of these boxes with even one tuner is not for the feint of heart.

Lastly, if you'll pardon a retarded question: What, exactly, does pulseaudio do for me? I notice on the mixer panel all of the hda-alsa controls look elaborate yet easy to configure, but the fancy-shmancy pulseaudio driver just looks like plain vanilla analogue control. None of the alsa controls work, but the ONE slider for pulseaudio does; so... why is this here? It looks regressive.
I don't know what the pulseaudio sound server can really add to your machine, if it is just a pure mythtv machine. I'd refer you to the wikipedia article on pulseaudio, which lays many of the issues out better than I can. Pulseaudio was at one time mostly a Gnome thing that has by degrees leaked into other environments, like KDE4. It frequently would not play nicely at all with earlier versions of mythtv, say 0.21 and before and I just got into the habit of just not using it, relying instead on plain Alsa. Particularly since I stopped using Gnome a couple of years ago.

---

### Post by zapstrap on 2012-08-29
I feel like I'm trying to perform surgery with a sledge-hammer, but this is the best I can come up with:

```
#!/bin/sh -e
# 2012.08.28 - lj
# Load the cx18 module and all its friends.
# Compensate for buggy driver for cx18: analogue tuner doesn't work 1st try.
# Notes:
# - /etc/init/mythtv-backend.override is set to manual.
# - cx18 & cx18_alsa modules are NOT blacklisted (/etc/modprobe.d/blacklist.conf)
# - pulseaudio driver doesn't load reliably either, but since this script 
#   kills it, when it respawns all is well.
# - script is called from /etc/rc.local, and all output is directed to a local
#   log file ($0.log).

# Since I do this twice, make it a function.
KILLPULSEAUDIO() {
	echo killing pulseaudio server...
	if [ $(killall -q pulseaudio) ] ; then
		echo pulseaudio server not running.
	else
		# 1/2 second is too short! Process dies a slow agonizing death.
		echo sleeping for 1 second.
		sleep 1
	fi
}

# if the backend is running (it shouldn't be) kill it.
if [ "$(service mythtv-backend status | cut -d' ' -f2 | cut -d'/' -f1)" = "start" ] ; then
	echo Stopping backend...
	service mythtv-backend stop
	echo sleeping for 1 second.
	sleep 1
else
	echo Backend already stopped.
fi

KILLPULSEAUDIO

# unload the cx18 alsa module.
if [ "$(lsmod | grep ^cx18_alsa | cut -d' ' -f1)" = "cx18_alsa" ] ; then 
	echo removing cx18_alsa module...
	rmmod cx18_alsa
	echo sleeping for 0.5 seconds.
	sleep .5
fi
# unload the cx18 module.
if [ "$(lsmod | grep ^cx18 | cut -d' ' -f1)" = "cx18" ] ; then 
	echo removing cx18 module...
	rmmod cx18
	echo sleeping for 3 seconds.
	sleep 3
fi

# just in case the pulseaudio driver thinks it's Lazarus...
KILLPULSEAUDIO

# Reload cx18 module (drags the cx18_alsa module with it); restart the back end.
echo inserting cx18 module...
modprobe cx18
echo sleeping for 1 seconds.
sleep 1
echo restarting backend...
service mythtv-backend start
echo Done.

exit 0

```

I have tried shutting down and booting back up 3 times now, and it's worked each time. I wish the driver just worked properly, but for now, so long as I can get the machine to wake-up with the tuners all alive reliably, it will have to do.

---

### Post by klc5555 on 2012-08-29
Well done!

The primary test of a solution is whether it works, not whether it's pretty. Your script may in fact be about the best that can be done at the moment, pending improvements in the cx18 driver, or the fixing (or nuking :) ) of pulseaudio.

All the best!

---

### Post by zapstrap on 2012-08-29
Gracias amigo,

It does seem fairly robust, now that the machine's been up and down several more times.

The rtc wakeup mechanism also got broken in the upgrade; a problem I had not discovered until this one was fixed. It turned out that the sudoers file had been overwritten, so the mythtv user didn't have permission to write the wakeup time, or to shut the machine down. As problems go, much easier to solve.

Cheers!

---

