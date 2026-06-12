---
title: "Unexpected Kernel Problems"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Nullack on 2010-08-31
Gday folks,

So I decided to give 10.10 a whirl. Since it's using a production kernel I was not expecting to run into significant kernel problems, but I have.

It seems to be related to MD raid, which is confusing me because my test system is simply running the old ICH10 southbridge from Intel - its certainly not some fancy hardware accelerated raid card.....

Kinda out of ideas on this one, would appreciate any insights before logging a bug

```
Aug 31 19:46:14 Bizmark kernel: [    9.031392] ------------[ cut here ]------------
Aug 31 19:46:14 Bizmark kernel: [    9.031448] kernel BUG at /build/buildd/linux-2.6.35/drivers/md/dm.c:2190!
Aug 31 19:46:14 Bizmark kernel: [    9.031513] invalid opcode: 0000 [#1] SMP 
Aug 31 19:46:14 Bizmark kernel: [    9.031649] last sysfs file: /sys/devices/virtual/block/dm-0/dm/suspended
Aug 31 19:46:14 Bizmark kernel: [    9.031713] CPU 8 
Aug 31 19:46:14 Bizmark kernel: [    9.031762] Modules linked in: dm_raid45 xor usbhid hid nouveau ttm drm_kms_helper pata_jmicron sky2 ahci drm i2c_algo_bit libahci
Aug 31 19:46:14 Bizmark kernel: [    9.032428] 
Aug 31 19:46:14 Bizmark kernel: [    9.032473] Pid: 625, comm: dmraid Tainted: G   M        2.6.35-19-generic #28-Ubuntu EVGA Classified SR-2/To Be Filled By O.E.M.
Aug 31 19:46:14 Bizmark kernel: [    9.032546] RIP: 0010:[<ffffffff81455aa2>]  [<ffffffff81455aa2>] dm_put+0x112/0x120
Aug 31 19:46:14 Bizmark kernel: [    9.032650] RSP: 0018:ffff880238089be8  EFLAGS: 00010202
Aug 31 19:46:14 Bizmark kernel: [    9.032705] RAX: ffff8802365b8000 RBX: ffff880236459800 RCX: 02000000000040c1
Aug 31 19:46:14 Bizmark kernel: [    9.032764] RDX: 000000000000001e RSI: ffffea0007bdf340 RDI: ffff880236459800
Aug 31 19:46:14 Bizmark kernel: [    9.032824] RBP: ffff880238089c08 R08: 000000000000006f R09: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.032884] R10: ffff880237cc4400 R11: 0000000000000001 R12: ffff88023645b400
Aug 31 19:46:14 Bizmark kernel: [    9.032944] R13: ffff880236459800 R14: ffffc90012636040 R15: 0000000000000020
Aug 31 19:46:14 Bizmark kernel: [    9.033005] FS:  00007f2d4975e7a0(0000) GS:ffff880001e80000(0000) knlGS:0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.033067] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 31 19:46:14 Bizmark kernel: [    9.033147] CR2: 00007f5245bff4f0 CR3: 000000023657f000 CR4: 00000000000006e0
Aug 31 19:46:14 Bizmark kernel: [    9.033231] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.033318] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 31 19:46:14 Bizmark kernel: [    9.033404] Process dmraid (pid: 625, threadinfo ffff880238088000, task ffff88023653adc0)
Aug 31 19:46:14 Bizmark kernel: [    9.033515] Stack:
Aug 31 19:46:14 Bizmark kernel: [    9.033584]  ffffc90012636040 0000000000000003 ffff88023645b400 ffff880236459800
Aug 31 19:46:14 Bizmark kernel: [    9.033789] <0> ffff880238089d38 ffffffffa01b1dd6 ffff880238346200 00000001000000d2
Aug 31 19:46:14 Bizmark kernel: [    9.034098] <0> 0000000000000000 ffff880238089ca0 00000000ffffffff 0000000000000001
Aug 31 19:46:14 Bizmark kernel: [    9.034470] Call Trace:
Aug 31 19:46:14 Bizmark kernel: [    9.034544]  [<ffffffffa01b1dd6>] raid_ctr+0x5f6/0xa50 [dm_raid45]
Aug 31 19:46:14 Bizmark kernel: [    9.034627]  [<ffffffff81458855>] ? dm_split_args+0x75/0x140
Aug 31 19:46:14 Bizmark kernel: [    9.034707]  [<ffffffff81458a1f>] dm_table_add_target+0xff/0x240
Aug 31 19:46:14 Bizmark kernel: [    9.034789]  [<ffffffff8145acf5>] populate_table+0x85/0x140
Aug 31 19:46:14 Bizmark kernel: [    9.034869]  [<ffffffff8145ae3f>] table_load+0x8f/0x1f0
Aug 31 19:46:14 Bizmark kernel: [    9.034948]  [<ffffffff8145adb0>] ? table_load+0x0/0x1f0
Aug 31 19:46:14 Bizmark kernel: [    9.035027]  [<ffffffff8145bf05>] ctl_ioctl+0x1a5/0x250
Aug 31 19:46:14 Bizmark kernel: [    9.035106]  [<ffffffff8145bfc3>] dm_ctl_ioctl+0x13/0x20
Aug 31 19:46:14 Bizmark kernel: [    9.035186]  [<ffffffff8116172d>] vfs_ioctl+0x3d/0xd0
Aug 31 19:46:14 Bizmark kernel: [    9.035264]  [<ffffffff81162001>] do_vfs_ioctl+0x81/0x340
Aug 31 19:46:14 Bizmark kernel: [    9.035343]  [<ffffffff81162341>] sys_ioctl+0x81/0xa0
Aug 31 19:46:14 Bizmark kernel: [    9.035423]  [<ffffffff8158831e>] ? do_device_not_available+0xe/0x10
Aug 31 19:46:14 Bizmark kernel: [    9.035507]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Aug 31 19:46:14 Bizmark kernel: [    9.035587] Code: 00 00 48 89 df e8 2f e3 ff ff e9 44 ff ff ff eb 08 90 90 90 90 90 90 90 90 4c 89 e7 e8 98 15 00 00 4c 89 e7 e8 b0 15 00 00 eb 85 <0f> 0b eb fe eb 08 90 90 90 90 90 90 90 90 55 48 89 e5 0f 1f 44 
Aug 31 19:46:14 Bizmark kernel: [    9.038348] RIP  [<ffffffff81455aa2>] dm_put+0x112/0x120
Aug 31 19:46:14 Bizmark kernel: [    9.038467]  RSP <ffff880238089be8>
Aug 31 19:46:14 Bizmark kernel: [    9.038546] ---[ end trace 9e7a26a65c902240 ]---
Aug 31 19:46:14 Bizmark kernel: [    9.056849] ------------[ cut here ]------------
Aug 31 19:46:14 Bizmark kernel: [    9.056938] kernel BUG at /build/buildd/linux-2.6.35/drivers/md/dm.c:2190!
Aug 31 19:46:14 Bizmark kernel: [    9.057024] invalid opcode: 0000 [#2] SMP 
Aug 31 19:46:14 Bizmark kernel: [    9.057185] last sysfs file: /sys/devices/virtual/block/dm-0/dm/suspended
Aug 31 19:46:14 Bizmark kernel: [    9.057272] CPU 4 
Aug 31 19:46:14 Bizmark kernel: [    9.057319] Modules linked in: dm_raid45 xor usbhid hid nouveau ttm drm_kms_helper pata_jmicron sky2 ahci drm i2c_algo_bit libahci
Aug 31 19:46:14 Bizmark kernel: [    9.058076] 
Aug 31 19:46:14 Bizmark kernel: [    9.058145] Pid: 627, comm: dmraid Tainted: G   M  D     2.6.35-19-generic #28-Ubuntu EVGA Classified SR-2/To Be Filled By O.E.M.
Aug 31 19:46:14 Bizmark kernel: [    9.058265] RIP: 0010:[<ffffffff81455aa2>]  [<ffffffff81455aa2>] dm_put+0x112/0x120
Aug 31 19:46:14 Bizmark kernel: [    9.058419] RSP: 0018:ffff8803b46c1dc8  EFLAGS: 00010202
Aug 31 19:46:14 Bizmark kernel: [    9.058499] RAX: 0000000000000000 RBX: ffff880236459800 RCX: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.058584] RDX: 0000000000000286 RSI: 0000000000000286 RDI: ffff880236459800
Aug 31 19:46:14 Bizmark kernel: [    9.058668] RBP: ffff8803b46c1de8 R08: ffff8803b55bc660 R09: ffff8803b46c1bb4
Aug 31 19:46:14 Bizmark kernel: [    9.058753] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.058838] R13: ffffc90013853000 R14: 0000000000004000 R15: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.058924] FS:  00007f40768c77a0(0000) GS:ffff880245600000(0000) knlGS:0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.059034] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 31 19:46:14 Bizmark kernel: [    9.059115] CR2: 00007f40768c6000 CR3: 00000003b50ea000 CR4: 00000000000006e0
Aug 31 19:46:14 Bizmark kernel: [    9.059200] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.059285] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 31 19:46:14 Bizmark kernel: [    9.059370] Process dmraid (pid: 627, threadinfo ffff8803b46c0000, task ffff8803b532adc0)
Aug 31 19:46:14 Bizmark kernel: [    9.059480] Stack:
Aug 31 19:46:14 Bizmark kernel: [    9.059549]  0000000000000000 ffff880236459800 0000000000000000 ffffc90013853000
Aug 31 19:46:14 Bizmark kernel: [    9.059757] <0> ffff8803b46c1e28 ffffffff8145a864 ffff8803b46c1e00 ffff8803b532adc0
Aug 31 19:46:14 Bizmark kernel: [    9.060069] <0> 0000000000632620 ffffffff8145a810 000000000000000c 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.060444] Call Trace:
Aug 31 19:46:14 Bizmark kernel: [    9.060518]  [<ffffffff8145a864>] table_status+0x54/0xa0
Aug 31 19:46:14 Bizmark kernel: [    9.060599]  [<ffffffff8145a810>] ? table_status+0x0/0xa0
Aug 31 19:46:14 Bizmark kernel: [    9.060680]  [<ffffffff8145bf05>] ctl_ioctl+0x1a5/0x250
Aug 31 19:46:14 Bizmark kernel: [    9.060761]  [<ffffffff8145bfc3>] dm_ctl_ioctl+0x13/0x20
Aug 31 19:46:14 Bizmark kernel: [    9.060842]  [<ffffffff8116172d>] vfs_ioctl+0x3d/0xd0
Aug 31 19:46:14 Bizmark kernel: [    9.060922]  [<ffffffff81162001>] do_vfs_ioctl+0x81/0x340
Aug 31 19:46:14 Bizmark kernel: [    9.061002]  [<ffffffff81162341>] sys_ioctl+0x81/0xa0
Aug 31 19:46:14 Bizmark kernel: [    9.061084]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Aug 31 19:46:14 Bizmark kernel: [    9.061165] Code: 00 00 48 89 df e8 2f e3 ff ff e9 44 ff ff ff eb 08 90 90 90 90 90 90 90 90 4c 89 e7 e8 98 15 00 00 4c 89 e7 e8 b0 15 00 00 eb 85 <0f> 0b eb fe eb 08 90 90 90 90 90 90 90 90 55 48 89 e5 0f 1f 44 
Aug 31 19:46:14 Bizmark kernel: [    9.063951] RIP  [<ffffffff81455aa2>] dm_put+0x112/0x120
Aug 31 19:46:14 Bizmark kernel: [    9.064072]  RSP <ffff8803b46c1dc8>
Aug 31 19:46:14 Bizmark kernel: [    9.064149] ------------[ cut here ]------------
Aug 31 19:46:14 Bizmark kernel: [    9.064153] ---[ end trace 9e7a26a65c902241 ]---
Aug 31 19:46:14 Bizmark kernel: [    9.064303] kernel BUG at /build/buildd/linux-2.6.35/drivers/md/dm.c:2190!
Aug 31 19:46:14 Bizmark kernel: [    9.064386] invalid opcode: 0000 [#3] SMP 
Aug 31 19:46:14 Bizmark kernel: [    9.064543] last sysfs file: /sys/devices/virtual/block/dm-0/dm/suspended
Aug 31 19:46:14 Bizmark kernel: [    9.064626] CPU 12 
Aug 31 19:46:14 Bizmark kernel: [    9.064672] Modules linked in: dm_raid45 xor usbhid hid nouveau ttm drm_kms_helper pata_jmicron sky2 ahci drm i2c_algo_bit libahci
Aug 31 19:46:14 Bizmark kernel: [    9.065419] 
Aug 31 19:46:14 Bizmark kernel: [    9.065487] Pid: 626, comm: dmraid Tainted: G   M  D     2.6.35-19-generic #28-Ubuntu EVGA Classified SR-2/To Be Filled By O.E.M.
Aug 31 19:46:14 Bizmark kernel: [    9.065607] RIP: 0010:[<ffffffff81455aa2>]  [<ffffffff81455aa2>] dm_put+0x112/0x120
Aug 31 19:46:14 Bizmark kernel: [    9.065756] RSP: 0018:ffff8803b401fdc8  EFLAGS: 00010202
Aug 31 19:46:14 Bizmark kernel: [    9.065834] RAX: 0000000000000000 RBX: ffff880236459800 RCX: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.065917] RDX: 0000000000000286 RSI: 0000000000000286 RDI: ffff880236459800
Aug 31 19:46:14 Bizmark kernel: [    9.066001] RBP: ffff8803b401fde8 R08: ffff8803b56800c0 R09: ffff8803b401fbb4
Aug 31 19:46:14 Bizmark kernel: [    9.066085] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.066168] R13: ffffc9001385f000 R14: 0000000000004000 R15: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.066253] FS:  00007f543a6c97a0(0000) GS:ffff880245680000(0000) knlGS:0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.066362] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 31 19:46:14 Bizmark kernel: [    9.066441] CR2: 00007f543a6c8000 CR3: 0000000237c60000 CR4: 00000000000006e0
Aug 31 19:46:14 Bizmark kernel: [    9.066525] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.066609] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 31 19:46:14 Bizmark kernel: [    9.066693] Process dmraid (pid: 626, threadinfo ffff8803b401e000, task ffff8803b55d44a0)
Aug 31 19:46:14 Bizmark kernel: [    9.066801] Stack:
Aug 31 19:46:14 Bizmark kernel: [    9.066869]  0000000000000000 ffff880236459800 0000000000000000 ffffc9001385f000
Aug 31 19:46:14 Bizmark kernel: [    9.067075] <0> ffff8803b401fe28 ffffffff8145a864 ffff8803b401fe00 ffff8803b55d44a0
Aug 31 19:46:14 Bizmark kernel: [    9.067384] <0> 0000000000be6620 ffffffff8145a810 000000000000000c 0000000000000000
Aug 31 19:46:14 Bizmark kernel: [    9.067756] Call Trace:
Aug 31 19:46:14 Bizmark kernel: [    9.067828]  [<ffffffff8145a864>] table_status+0x54/0xa0
Aug 31 19:46:14 Bizmark kernel: [    9.067907]  [<ffffffff8145a810>] ? table_status+0x0/0xa0
Aug 31 19:46:14 Bizmark kernel: [    9.067986]  [<ffffffff8145bf05>] ctl_ioctl+0x1a5/0x250
Aug 31 19:46:14 Bizmark kernel: [    9.068065]  [<ffffffff8145bfc3>] dm_ctl_ioctl+0x13/0x20
Aug 31 19:46:14 Bizmark kernel: [    9.068144]  [<ffffffff8116172d>] vfs_ioctl+0x3d/0xd0
Aug 31 19:46:14 Bizmark kernel: [    9.068222]  [<ffffffff81162001>] do_vfs_ioctl+0x81/0x340
Aug 31 19:46:14 Bizmark kernel: [    9.068301]  [<ffffffff81162341>] sys_ioctl+0x81/0xa0
Aug 31 19:46:14 Bizmark kernel: [    9.068380]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Aug 31 19:46:14 Bizmark kernel: [    9.068461] Code: 00 00 48 89 df e8 2f e3 ff ff e9 44 ff ff ff eb 08 90 90 90 90 90 90 90 90 4c 89 e7 e8 98 15 00 00 4c 89 e7 e8 b0 15 00 00 eb 85 <0f> 0b eb fe eb 08 90 90 90 90 90 90 90 90 55 48 89 e5 0f 1f 44 
Aug 31 19:46:14 Bizmark kernel: [    9.071221] RIP  [<ffffffff81455aa2>] dm_put+0x112/0x120
Aug 31 19:46:14 Bizmark kernel: [    9.071340]  RSP <ffff8803b401fdc8>
Aug 31 19:46:14 Bizmark kernel: [    9.071424] ---[ end trace 9e7a26a65c902242 ]---
```

---

### Post by Nullack on 2010-09-02
Ive been looking at this. Interesting to see that DMRAID is tainted, so it looks like Canonical is doing something with a raid module outside of the normal kernel.

I've reported a bug here but so far no bites from a kernel guru on fixing.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627495](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/627495)

The other kernel oops issue appears to be around the three NVIDIA HDA HDMI sound drivers and my Azuntech HD sound card.

---

### Post by ranch hand on 2010-09-02
You won't get any movement on that bug until you can get at least one person to Me To it for you, it needs to veverified.

---

### Post by Nullack on 2010-09-03
Not sure of the logic for needing a "me too" on that - the logs are clear and describe the problem complete with kernel oops report. Especially given Canonical have chosen for a tainted MD RAID module.

Anyway if someone could kindly confirm the bug that would be good if it is required.

---

### Post by Nullack on 2010-09-06
BUMP - hoping someone will share the love and validate/confirm this bug. In good faith, its a big issue on my own particular system and I do know that fellow users with similar systems will be effected by this so please do confirm. Love it, go open source ;)

---

### Post by dino99 on 2010-09-06
sorry, cant help you directly on that issue

[http://ubuntuforums.org/search.php?searchid=75749642](http://ubuntuforums.org/search.php?searchid=75749642)

---

