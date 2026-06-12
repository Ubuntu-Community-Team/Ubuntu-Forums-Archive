---
title: "MythBuntu (ivtv driver) not working"
date: 2008-01-12
forum: Mythbuntu
---

### Post by trubblemaker on 2008-01-12
This is  a fresh install of a MythBuntu box.

I'm failing with an "Error -12 on initialization" my card doesn't seem to be able to recognize my Swap space.  I've tried adding 

```
 noapic acpi=off vmalloc=192m vga=791
```

to my boot parameters to help out, any one have any other ideas?

ivtv output:

```
[   83.098219] ivtv:  ==================== START INIT IVTV ====================
[   83.098231] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   83.114465] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   83.114483] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   83.114505] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   83.114515] wifi0: mac 7.8 phy 4.5 radio 5.6
[   83.114530] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   83.114535] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   83.114540] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   83.114545] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   83.114551] wifi0: Use hw queue 8 for CAB traffic
[   83.114556] wifi0: Use hw queue 9 for beacons
[   83.182500] wifi0: Atheros 5212: mem=0xf0100000, irq=10
[   83.183011] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   83.187192] PCI: Enabling device 0000:01:0b.0 (0114 -> 0116)
[   83.187222] PCI: setting IRQ 9 as level-triggered
[   83.187229] PCI: Assigned IRQ 9 for device 0000:01:0b.0
[   83.996978] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3334972568 bytes)
[   84.085718] ivtv0: loaded v4l-cx2341x-dec.fw firmware (3334972576 bytes)
[   84.309159] ivtv0: Encoder revision: 0x02050032
[   84.309172] ivtv0: Recommended firmware version is 0x02060039.
[   84.317173] ivtv0: Decoder revision: 0x02020023
[   84.393803] tveeprom 2-0050: Hauppauge model 48132, rev K268, serial# 8603182
[   84.393818] tveeprom 2-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   84.393826] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   84.393834] tveeprom 2-0050: audio processor is MSP4448 (idx 27)
[   84.393841] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[   84.393848] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[   84.393856] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   84.442573] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   84.442669] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   84.445900] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   84.523924] saa7115 2-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   84.726291] saa7127 2-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   84.780239] msp3400 2-0040: MSP4448G-B3 found @ 0x80 (ivtv i2c driver #0)
[   84.780250] msp3400 2-0040: MSP4448G-B3 supports radio, mode is autodetect and autoselect
[   84.780673] tuner 2-0061: type set to 47 (LG NTSC (TAPE series))
[   85.037728] NET: Registered protocol family 17
[   85.061416] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   85.062641] modprobe: page allocation failure. order:4, mode:0x40d0
[   85.062686]  [<c0163970>] __alloc_pages+0x320/0x340
[   85.062743]  [<c017c475>] __slab_alloc+0x125/0x4f0
[   85.062781]  [<c017cfd5>] __kmalloc+0x95/0xa0
[   85.062790]  [<c8b4da61>] ivtv_stream_alloc+0xa1/0x2f0 [ivtv]
[   85.062855]  [<c8b4da61>] ivtv_stream_alloc+0xa1/0x2f0 [ivtv]
[   85.062877]  [<c8ac53a9>] video_register_device+0x139/0x280 [videodev]
[   85.062909]  [<c8b4e665>] ivtv_streams_setup+0x1a5/0x430 [ivtv]
[   85.062947]  [<c8b43838>] ivtv_probe+0x1068/0x1380 [ivtv]
[   85.062973]  [<c02f6de4>] kprobe_flush_task+0x44/0x90
[   85.063007]  [<c01c3e60>] __sysfs_new_dirent+0x20/0x50
[   85.063022]  [<c01c3f1a>] __sysfs_make_dirent+0x1a/0x90
[   85.063039]  [<c01c3fbf>] sysfs_make_dirent+0x2f/0x50
[   85.063051]  [<c01c00ff>] ldm_partition+0x54f/0xdb0
[   85.063088]  [<c0209a66>] pci_device_probe+0x56/0x80
[   85.063121]  [<c026110e>] driver_probe_device+0x8e/0x190
[   85.063142]  [<c026137e>] __driver_attach+0x9e/0xa0
[   85.063153]  [<c02604fb>] bus_for_each_dev+0x3b/0x60
[   85.063189]  [<c0260f86>] driver_attach+0x16/0x20
[   85.063196]  [<c02612e0>] __driver_attach+0x0/0xa0
[   85.063204]  [<c02608ca>] bus_add_driver+0x8a/0x1b0
[   85.063223]  [<c0209c13>] __pci_register_driver+0x53/0xa0
[   85.063237]  [<c8b4230b>] module_start+0x5b/0xc0 [ivtv]
[   85.063258]  [<c014a7d1>] sys_init_module+0x151/0x1a00
[   85.063271]  [<c01fb39f>] prio_tree_insert+0x1f/0x250
[   85.063356]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   85.063380]  [<c02f0000>] clip_ioctl+0x440/0x510
[   85.063398]  =======================
[   85.063403] Mem-info:
[   85.063408] DMA per-cpu:
[   85.063414] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[   85.063420] Normal per-cpu:
[   85.063426] CPU    0: Hot: hi:   42, btch:   7 usd:  37   Cold: hi:   14, btch:   3 usd:  12
[   85.063438] Active:3944 inactive:23277 dirty:0 writeback:0 unstable:0
[   85.063441]  free:651 slab:2312 mapped:647 pagetables:46 bounce:0
[   85.063452] DMA free:796kB min:180kB low:224kB high:268kB active:284kB inactive:9708kB present:16256kB pages_scanned:224 all_unreclaimable? no
[   85.063460] lowmem_reserve[]: 0 110 110
[   85.063471] Normal free:1808kB min:1252kB low:1564kB high:1876kB active:15492kB inactive:83400kB present:112716kB pages_scanned:0 all_unreclaimable? no
[   85.063479] lowmem_reserve[]: 0 0 0
[   85.063486] DMA: 25*4kB 33*8kB 9*16kB 7*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 796kB
[   85.063506] Normal: 48*4kB 50*8kB 30*16kB 19*32kB 0*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1808kB
[   85.063528] Swap cache: add 0, delete 0, find 0/0, race 0+0
[   85.063532] Free swap  = 0kB
[   85.063536] Total swap = 0kB
[   85.063540] Free swap:            0kB
[   85.070196] 32496 pages of RAM
[   85.070206] 0 pages of HIGHMEM
[   85.070210] 1269 reserved pages
[   85.070214] 2762 pages shared
[   85.070217] 0 pages swap cached
[   85.070221] 0 pages dirty
[   85.070225] 0 pages writeback
[   85.070229] 647 pages mapped
[   85.070233] 2312 pages slab
[   85.070236] 46 pages pagetables
[   85.070247] ivtv0: Couldn't allocate buffers for encoder MPEG stream
[   85.071243] ivtv0: Error -12 setting up streams
[   85.076788] ivtv0: Error -12 on initialization
[   85.076821] ivtv: probe of 0000:01:0b.0 failed with error -12
[   85.076882] ivtv:  ====================  END INIT IVTV  ====================
```

I have posted this already to the ivtv mailing list and got 0 responses so I was hoping Unbuntu community might be able to help out.

---

### Post by am4c130d on 2008-03-02
I have a similar issue.  Running Gutsy, system boots OK, however as soon as MythTV attempts to configure/use the Haupauge PVR-250 card the system crashes.  Then it gets stuck in to a boot loop.  The system only gets stuck in the loop when the RAID system is dirty - which is every time as myth is trying to record when it accesses the card.  Interestingly pulling all the HDD of the RAID controller also allows the system to reboot OK - but this is not a solution as it requires the system being dismantled.

I"ve had the card for nearly 5 years without thus sort of crash, but have had the problem as soon as I added it to a server running gutsy.

Any more thoughts?  I am going to move the card to another system if  can't resolve the problem.

Thanks

Alan

---

