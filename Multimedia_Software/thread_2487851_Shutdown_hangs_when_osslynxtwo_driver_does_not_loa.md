---
title: "Shutdown hangs when oss/lynxtwo driver does not load properly"
date: 2023-06-16
forum: Multimedia Software
---

### Post by davetherave1 on 2023-06-16
Hi,
I have re-installed Ubuntu 22.04.2 in my server used primarily for audio via OSS driver (v4) with LynxTwo card.
It worked well for few days  but then the reboot/shutdown started to hang (had to power off manually). When I restart, the oss driver does not load the sound device.
To make it work, either I have to reboot multiple times and remove the audio jack from the server just before powering it down.
Note, when it hangs, the console says Powering off or Rebooting but the audio device (DAC) still indicates its locked to the Ubuntu server.
ANY HELP WILL BE MUCH APPRECIATED PLEASE

Attached is the journal extract.
Below is the last bit of the kernel message during startup when the oss driver does NOT load ok:
```
Jun 17 02:08:35 vortexbox kernel: [   37.436868] Hardware name:  /DG41MJ, BIOS MJG4110H.86A.0006.2009.1223.1155 12/23/2009
Jun 17 02:08:35 vortexbox kernel: [   37.436902] RIP: 0010:init_lynx_hal+0x24/0x3f0 [lynxtwo]
Jun 17 02:08:35 vortexbox kernel: [   37.436946] Code: 00 00 00 00 00 90 f3 0f 1e fa 41 55 66 0f ef c0 41 54 55 53 48 89 fb 48 81 ec 28 01 00 00 48 c7 47 18 00 00 00 00 48 8b 7f 10 <0f> 29 04 24 0f 29 44 24 10 0f 29 44 24 20 48 c7 44 24 30 00 00 00
Jun 17 02:08:35 vortexbox kernel: [   37.437023] RSP: 0018:ffffbecf009a7838 EFLAGS: 00010292
Jun 17 02:08:35 vortexbox kernel: [   37.437049] RAX: 0000000000000000 RBX: ffffbecf00945010 RCX: ffff991f4393ef88
Jun 17 02:08:35 vortexbox kernel: [   37.437081] RDX: 0000000000000000 RSI: ffff991f4393ee00 RDI: ffffbecf00955000
Jun 17 02:08:35 vortexbox kernel: [   37.437113] RBP: ffffbecf00945010 R08: 0000000000000073 R09: 0000000000000000
Jun 17 02:08:35 vortexbox kernel: [   37.437146] R10: 0000000000000196 R11: ffffffffffffffff R12: 0000000000000000
Jun 17 02:08:35 vortexbox kernel: [   37.437177] R13: ffffbecf00945060 R14: ffff991f41add0d0 R15: ffff991f54e98368
Jun 17 02:08:35 vortexbox kernel: [   37.437210] FS:  00007f3c02e23c40(0000) GS:ffff991f7c680000(0000) knlGS:0000000000000000
Jun 17 02:08:35 vortexbox kernel: [   37.437247] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 17 02:08:35 vortexbox kernel: [   37.437274] CR2: 00007f75cbb2f560 CR3: 000000000f518000 CR4: 00000000000406e0
Jun 17 02:08:35 vortexbox kernel: [   37.437306] Call Trace:
Jun 17 02:08:35 vortexbox kernel: [   37.437322]  <TASK>
Jun 17 02:08:35 vortexbox kernel: [   37.437335]  ? mutex_lock+0x13/0x50
Jun 17 02:08:35 vortexbox kernel: [   37.437359]  ? __setup_irq+0x3fd/0x780
Jun 17 02:08:35 vortexbox kernel: [   37.437383]  ? kmem_cache_alloc_trace+0x19e/0x2e0
Jun 17 02:08:35 vortexbox kernel: [   37.437409]  ? request_threaded_irq+0x112/0x180
Jun 17 02:08:35 vortexbox kernel: [   37.437432]  ? uninit_lynx_audio+0x130/0x130 [lynxtwo]
Jun 17 02:08:35 vortexbox kernel: [   37.437470]  ? oss_register_interrupts+0xb0/0x130 [osscore]
Jun 17 02:08:35 vortexbox kernel: [   37.437524]  ? lynxtwo_attach+0x255/0x4b0 [lynxtwo]
Jun 17 02:08:35 vortexbox kernel: [   37.437557]  ? pci_enable_device_flags+0x104/0x170
Jun 17 02:08:35 vortexbox kernel: [   37.437585]  ? oss_cdev_compat_ioctl+0x20/0x20 [osscore]
Jun 17 02:08:35 vortexbox kernel: [   37.437625]  ? osspci_probe+0x99/0x150 [lynxtwo]
Jun 17 02:08:35 vortexbox kernel: [   37.437659]  ? local_pci_probe+0x4b/0x90
Jun 17 02:08:35 vortexbox kernel: [   37.437682]  ? pci_device_probe+0x119/0x1f0
Jun 17 02:08:35 vortexbox kernel: [   37.437704]  ? really_probe+0x222/0x420
Jun 17 02:08:35 vortexbox kernel: [   37.437727]  ? __driver_probe_device+0x119/0x190
Jun 17 02:08:35 vortexbox kernel: [   37.437752]  ? driver_probe_device+0x23/0xc0
Jun 17 02:08:35 vortexbox kernel: [   37.437777]  ? __driver_attach+0xf7/0x1f0
Jun 17 02:08:35 vortexbox kernel: [   37.437799]  ? __device_attach_driver+0x140/0x140
Jun 17 02:08:35 vortexbox kernel: [   37.437825]  ? bus_for_each_dev+0x7f/0xd0
Jun 17 02:08:35 vortexbox kernel: [   37.437848]  ? driver_attach+0x1e/0x30
Jun 17 02:08:35 vortexbox kernel: [   37.437869]  ? bus_add_driver+0x148/0x220
Jun 17 02:08:35 vortexbox kernel: [   37.437891]  ? vunmap_range_noflush+0x3d5/0x470
Jun 17 02:08:35 vortexbox kernel: [   37.437917]  ? driver_register+0x95/0x100
Jun 17 02:08:35 vortexbox kernel: [   37.437939]  ? 0xffffffffc0e59000
Jun 17 02:08:35 vortexbox kernel: [   37.437957]  ? __pci_register_driver+0x68/0x70
Jun 17 02:08:35 vortexbox kernel: [   37.437982]  ? pcidrv_init+0x23/0x1000 [lynxtwo]
Jun 17 02:08:35 vortexbox kernel: [   37.438015]  ? do_one_initcall+0x49/0x1e0
Jun 17 02:08:35 vortexbox kernel: [   37.438038]  ? kmem_cache_alloc_trace+0x19e/0x2e0
Jun 17 02:08:35 vortexbox kernel: [   37.438063]  ? do_init_module+0x52/0x260
Jun 17 02:08:35 vortexbox kernel: [   37.438085]  ? load_module+0xb2b/0xbc0
Jun 17 02:08:35 vortexbox kernel: [   37.438107]  ? __do_sys_finit_module+0xbf/0x120
Jun 17 02:08:35 vortexbox kernel: [   37.438131]  ? __x64_sys_finit_module+0x18/0x20
Jun 17 02:08:35 vortexbox kernel: [   37.438155]  ? do_syscall_64+0x5c/0xc0
Jun 17 02:08:35 vortexbox kernel: [   37.438179]  ? exit_to_user_mode_prepare+0x37/0xb0
Jun 17 02:08:35 vortexbox kernel: [   37.438206]  ? syscall_exit_to_user_mode+0x27/0x50
Jun 17 02:08:35 vortexbox kernel: [   37.438232]  ? __x64_sys_mmap+0x33/0x50
Jun 17 02:08:35 vortexbox kernel: [   37.438253]  ? do_syscall_64+0x69/0xc0
Jun 17 02:08:35 vortexbox kernel: [   37.438275]  ? do_syscall_64+0x69/0xc0
Jun 17 02:08:35 vortexbox kernel: [   37.438296]  ? do_user_addr_fault+0x1e7/0x670
Jun 17 02:08:35 vortexbox kernel: [   37.438320]  ? exit_to_user_mode_prepare+0x37/0xb0
Jun 17 02:08:35 vortexbox kernel: [   37.438346]  ? irqentry_exit_to_user_mode+0x9/0x20
Jun 17 02:08:35 vortexbox kernel: [   37.438373]  ? irqentry_exit+0x1d/0x30
Jun 17 02:08:35 vortexbox kernel: [   37.438394]  ? exc_page_fault+0x89/0x170
Jun 17 02:08:35 vortexbox kernel: [   37.438416]  ? entry_SYSCALL_64_after_hwframe+0x61/0xcb
Jun 17 02:08:35 vortexbox kernel: [   37.438443]  </TASK>
Jun 17 02:08:35 vortexbox kernel: [   37.438457] Modules linked in: lynxtwo(OE+) osscore(OE) binfmt_misc coretemp serio_raw at24 mac_hid sch_fq_codel dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua pstore_blk msr efi_pstore ramoops pstore_zone reed_solomon ip_tables x_tables autofs4 btrfs blake2b_generic zstd_compress raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear gpio_ich i915 i2c_algo_bit ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops cec rc_core psmouse i2c_i801 pata_acpi i2c_smbus lpc_ich r8169 drm realtek video
Jun 17 02:08:35 vortexbox kernel: [   37.440507] ---[ end trace 8df845ec2de9027e ]---
Jun 17 02:08:35 vortexbox kernel: [   37.442386] RIP: 0010:init_lynx_hal+0x24/0x3f0 [lynxtwo]
Jun 17 02:08:35 vortexbox kernel: [   37.444143] Code: 00 00 00 00 00 90 f3 0f 1e fa 41 55 66 0f ef c0 41 54 55 53 48 89 fb 48 81 ec 28 01 00 00 48 c7 47 18 00 00 00 00 48 8b 7f 10 <0f> 29 04 24 0f 29 44 24 10 0f 29 44 24 20 48 c7 44 24 30 00 00 00
Jun 17 02:08:35 vortexbox kernel: [   37.446006] RSP: 0018:ffffbecf009a7838 EFLAGS: 00010292
Jun 17 02:08:35 vortexbox kernel: [   37.447865] RAX: 0000000000000000 RBX: ffffbecf00945010 RCX: ffff991f4393ef88
Jun 17 02:08:35 vortexbox kernel: [   37.449731] RDX: 0000000000000000 RSI: ffff991f4393ee00 RDI: ffffbecf00955000
Jun 17 02:08:35 vortexbox kernel: [   37.451666] RBP: ffffbecf00945010 R08: 0000000000000073 R09: 0000000000000000
Jun 17 02:08:35 vortexbox kernel: [   37.453508] R10: 0000000000000196 R11: ffffffffffffffff R12: 0000000000000000
Jun 17 02:08:35 vortexbox kernel: [   37.455299] R13: ffffbecf00945060 R14: ffff991f41add0d0 R15: ffff991f54e98368
Jun 17 02:08:35 vortexbox kernel: [   37.456959] FS:  00007f3c02e23c40(0000) GS:ffff991f7c680000(0000) knlGS:0000000000000000
Jun 17 02:08:35 vortexbox kernel: [   37.458638] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 17 02:08:35 vortexbox kernel: [   37.460312] CR2: 00007f75cbb2f560 CR3: 000000000f518000 CR4: 00000000000406e0
Jun 17 02:10:52 vortexbox kernel: [   62.998214] loop5: detected capacity change from 0 to 8
```

---

### Post by davetherave1 on 2023-06-19
Anyone please?

---

