---
title: "X-server crashing: dead card or something else?"
date: 2009-02-17
forum: Multimedia Software
---

### Post by kcavagnolo on 2009-02-17
X-server keeps going belly-up on me for no apparent reason. From my sys log:

```
Feb 17 14:35:23 apocalypse -- MARK --
Feb 17 14:51:39 apocalypse kernel: [1288044.908198] NVRM: Xid (0001:00): 6, PE0001 
Feb 17 14:51:43 apocalypse kernel: [1288044.924599] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000e08 00190000 00000040
Feb 17 14:51:43 apocalypse kernel: [1288044.924923] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000e08 00190000 00000000
Feb 17 14:51:45 apocalypse kernel: [1288049.070211] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000e08 02da0115 00000040
Feb 17 14:51:45 apocalypse kernel: [1288049.070543] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000e08 02da0115 00000000
Feb 17 14:51:48 apocalypse kernel: [1288054.012231] NVRM: Xid (0001:00): 13, 0004 00000000 00008297 00000e08 041a040a 00000040
Feb 17 14:51:48 apocalypse kernel: [1288054.012552] NVRM: Xid (0001:00): 13, 0004 00000000 00008297 00000e08 041a040a 00000000
Feb 17 14:51:53 apocalypse kernel: [1288058.089202] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001314 00000207 00000040
Feb 17 14:54:29 apocalypse kernel: [1288214.393232] Unable to handle kernel NULL pointer dereference at 0000000000000064 RIP: 
Feb 17 14:54:29 apocalypse kernel: [1288214.393236]  [nvidia:_nv005703rm+0x0/0x2f] :nvidia:_nv005703rm+0x0/0x2f
Feb 17 14:54:29 apocalypse kernel: [1288214.393352] PGD 198fc1067 PUD 1995a2067 PMD 0 
Feb 17 14:54:29 apocalypse kernel: [1288214.393354] Oops: 0000 [1] SMP 
Feb 17 14:54:29 apocalypse kernel: [1288214.393357] CPU 0 
Feb 17 14:54:29 apocalypse kernel: [1288214.393358] Modules linked in: snd_rtctimer video1394 raw1394 ext2 binfmt_misc ppdev cpufreq_stats cpufreq_conservative cpufreq_ondemand freq_table cpufreq_userspace cpufreq_powersave dock container sbs video output sbshc battery ipv6 ac coretemp it87 hwmon_vid ds1621 i2c_i801 lp af_packet snd_hda_intel snd_usb_audio snd_pcm_oss snd_mixer_oss snd_pcm uvcvideo snd_page_alloc snd_seq_dummy compat_ioctl32 snd_usb_lib nvidia(P) serio_raw snd_seq_oss parport_pc videodev v4l1_compat snd_seq_midi snd_rawmidi intel_agp snd_seq_midi_event i2c_core v4l2_common snd_hwdep parport evdev snd_seq psmouse pcspkr iTCO_wdt iTCO_vendor_support button shpchp pci_hotplug snd_timer snd_seq_device snd soundcore ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_jmicron sbp2 usb_storage libusual pata_acpi floppy ata_piix ohci1394 ata_generic ahci libata scsi_mod ieee1394 r8169 ehci_hcd uhci_hcd usbcore raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_snap
Feb 17 14:54:29 apocalypse kernel: hot dm_mod thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor
Feb 17 14:54:29 apocalypse kernel: [1288214.393410] Pid: 1988, comm: nvidia-settings Tainted: P        2.6.24-23-generic #1
Feb 17 14:54:29 apocalypse kernel: [1288214.393411] RIP: 0010:[nvidia:_nv005703rm+0x0/0x2f]  [nvidia:_nv005703rm+0x0/0x2f] :nvidia:_nv005703rm+0x0/0x2f
Feb 17 14:54:29 apocalypse kernel: [1288214.393506] RSP: 0018:ffff81016df1ba50  EFLAGS: 00010286
Feb 17 14:54:29 apocalypse kernel: [1288214.393507] RAX: 0000000000000000 RBX: 0000000000000001 RCX: 0000000000000007
Feb 17 14:54:29 apocalypse kernel: [1288214.393509] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000000
Feb 17 14:54:29 apocalypse kernel: [1288214.393510] RBP: ffff8101005ae1e8 R08: 0000000000000006 R09: ffff8101005ae1f0
Feb 17 14:54:29 apocalypse kernel: [1288214.393512] R10: 0000000000000003 R11: 0000000000000004 R12: 0000000000000004
Feb 17 14:54:29 apocalypse kernel: [1288214.393513] R13: ffff810189b35000 R14: ffff81019641e800 R15: ffff810198fdc000
Feb 17 14:54:29 apocalypse kernel: [1288214.393515] FS:  00007fed2faf46f0(0000) GS:ffffffff805b9000(0000) knlGS:0000000000000000
Feb 17 14:54:29 apocalypse kernel: [1288214.393517] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Feb 17 14:54:29 apocalypse kernel: [1288214.393518] CR2: 0000000000000064 CR3: 0000000114113000 CR4: 00000000000006e0
Feb 17 14:54:29 apocalypse kernel: [1288214.393520] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 17 14:54:29 apocalypse kernel: [1288214.393522] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 17 14:54:29 apocalypse kernel: [1288214.393523] Process nvidia-settings (pid: 1988, threadinfo ffff81016df1a000, task ffff81017529c7f0)
Feb 17 14:54:29 apocalypse kernel: [1288214.393525] Stack:  ffffffff884ce592 000000000000000d ffff810189b35000 ffff81019641e800
Feb 17 14:54:29 apocalypse kernel: [1288214.393528]  ffff8101005ae2f8 ffff810198fdc000 ffffffff884ea66d 0000000000000003
Feb 17 14:54:29 apocalypse kernel: [1288214.393531]  ffff810189b35000 ffff81017bc22400 000000000000000d ffff81002e7ae800
Feb 17 14:54:29 apocalypse kernel: [1288214.393534] Call Trace:
Feb 17 14:54:29 apocalypse kernel: [1288214.393629]  [nvidia:_nv009459rm+0x92/0x199] :nvidia:_nv009459rm+0x92/0x199
Feb 17 14:54:29 apocalypse kernel: [1288214.393730]  [nvidia:_nv009452rm+0x228/0x26a] :nvidia:_nv009452rm+0x228/0x26a
Feb 17 14:54:29 apocalypse kernel: [1288214.393824]  [nvidia:_nv003147rm+0x1b2/0x228] :nvidia:_nv003147rm+0x1b2/0x228
Feb 17 14:54:29 apocalypse kernel: [1288214.393916]  [nvidia:_nv003146rm+0x525/0x62e] :nvidia:_nv003146rm+0x525/0x62e
Feb 17 14:54:29 apocalypse kernel: [1288214.394020]  [nvidia:_nv007828rm+0xf86/0xf98] :nvidia:_nv007828rm+0xf86/0xf98
Feb 17 14:54:29 apocalypse kernel: [1288214.394126]  [nvidia:_nv007581rm+0x656/0x126e] :nvidia:_nv007581rm+0x656/0x126e
Feb 17 14:54:29 apocalypse kernel: [1288214.394224]  [nvidia:_nv005783rm+0x390/0x62c] :nvidia:_nv005783rm+0x390/0x62c
Feb 17 14:54:29 apocalypse kernel: [1288214.394325]  [nvidia:_nv009571rm+0x3d7/0x5a6] :nvidia:_nv009571rm+0x3d7/0x5a6
Feb 17 14:54:29 apocalypse kernel: [1288214.394425]  [nvidia:_nv009461rm+0xcb/0x185] :nvidia:_nv009461rm+0xcb/0x185
Feb 17 14:54:29 apocalypse kernel: [1288214.394517]  [nvidia:_nv003147rm+0xdf/0x228] :nvidia:_nv003147rm+0xdf/0x228
Feb 17 14:54:29 apocalypse kernel: [1288214.394609]  [nvidia:_nv003146rm+0x525/0x62e] :nvidia:_nv003146rm+0x525/0x62e
Feb 17 14:54:29 apocalypse kernel: [1288214.394711]  [nvidia:_nv007828rm+0xf86/0xf98] :nvidia:_nv007828rm+0xf86/0xf98
Feb 17 14:54:29 apocalypse kernel: [1288214.394817]  [nvidia:_nv007581rm+0x656/0x126e] :nvidia:_nv007581rm+0x656/0x126e
Feb 17 14:54:29 apocalypse kernel: [1288214.394915]  [nvidia:_nv005783rm+0x390/0x62c] :nvidia:_nv005783rm+0x390/0x62c
Feb 17 14:54:29 apocalypse kernel: [1288214.395015]  [nvidia:_nv009440rm+0x1be/0x5ec] :nvidia:_nv009440rm+0x1be/0x5ec
Feb 17 14:54:29 apocalypse kernel: [1288214.395113]  [nvidia:_nv009445rm+0x157/0x180] :nvidia:_nv009445rm+0x157/0x180
Feb 17 14:54:29 apocalypse kernel: [1288214.395211]  [nvidia:_nv009446rm+0x8b/0x191] :nvidia:_nv009446rm+0x8b/0x191
Feb 17 14:54:29 apocalypse kernel: [1288214.395306]  [nvidia:_nv002930rm+0x4bf/0x4ee] :nvidia:_nv002930rm+0x4bf/0x4ee
Feb 17 14:54:29 apocalypse kernel: [1288214.395401]  [nvidia:_nv002931rm+0x133/0x2cf] :nvidia:_nv002931rm+0x133/0x2cf
Feb 17 14:54:29 apocalypse kernel: [1288214.395495]  [nvidia:_nv005042rm+0x72/0x9f] :nvidia:_nv005042rm+0x72/0x9f
Feb 17 14:54:29 apocalypse kernel: [1288214.395588]  [nvidia:_nv002878rm+0x1e5/0x6f9] :nvidia:_nv002878rm+0x1e5/0x6f9
Feb 17 14:54:29 apocalypse kernel: [1288214.395684]  [nvidia:rm_ioctl+0x2f/0x67] :nvidia:rm_ioctl+0x2f/0x67
Feb 17 14:54:29 apocalypse kernel: [1288214.395761]  [nvidia:nv_kern_ioctl+0x12b/0x3a0] :nvidia:nv_kern_ioctl+0x12b/0x3a0
Feb 17 14:54:29 apocalypse kernel: [1288214.395842]  [nvidia:nv_kern_unlocked_ioctl+0x1c/0x30] :nvidia:nv_kern_unlocked_ioctl+0x1c/0x30
Feb 17 14:54:29 apocalypse kernel: [1288214.395847]  [do_ioctl+0x2f/0xa0] do_ioctl+0x2f/0xa0
Feb 17 14:54:29 apocalypse kernel: [1288214.395852]  [vfs_ioctl+0x220/0x2c0] vfs_ioctl+0x220/0x2c0
Feb 17 14:54:29 apocalypse kernel: [1288214.395858]  [sys_ioctl+0x91/0xb0] sys_ioctl+0x91/0xb0
Feb 17 14:54:29 apocalypse kernel: [1288214.395865]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Feb 17 14:54:29 apocalypse kernel: [1288214.395875] 
Feb 17 14:54:29 apocalypse kernel: [1288214.395875] 
Feb 17 14:54:29 apocalypse kernel: [1288214.395876] Code: 8b 47 64 48 01 c6 83 7f 24 00 74 08 48 89 f0 48 03 47 68 c3 
Feb 17 14:54:29 apocalypse kernel: [1288214.395883] RIP  [nvidia:_nv005703rm+0x0/0x2f] :nvidia:_nv005703rm+0x0/0x2f
Feb 17 14:54:29 apocalypse kernel: [1288214.395976]  RSP <ffff81016df1ba50>
Feb 17 14:54:29 apocalypse kernel: [1288214.395977] CR2: 0000000000000064
Feb 17 14:54:29 apocalypse kernel: [1288214.395981] ---[ end trace 500a88ddc8c327c2 ]---
```

I hope this is software related and not hardware. Anyone able to interpret the above for me?

---

