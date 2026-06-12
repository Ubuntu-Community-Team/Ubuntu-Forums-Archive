---
title: "OpenVPN problem"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by rogerdv on 2013-03-19
I was using a VPNsuccessfully until a week ago that it was reinstalled. I received the new config, but now it doesnt works, I get a LOT of kernel messages with errors:

```
Mar 19 10:29:35 gaara kernel: [69270.313888] general protection fault: 0000 [#10] SMP 
Mar 19 10:29:35 gaara kernel: [69270.313893] CPU 0 
Mar 19 10:29:35 gaara kernel: [69270.313895] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat bnep rfcomm bluetooth binfmt_misc vesafb snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep nvidia(P) snd_pcm snd_seq_midi ppdev snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw parport_pc asus_atk0110 mac_hid lp parport snd soundcore snd_page_alloc usbhid hid usb_storage atl1e
Mar 19 10:29:35 gaara kernel: [69270.313918] 
Mar 19 10:29:35 gaara kernel: [69270.313920] Pid: 9677, comm: ifconfig Tainted: P      D    O 3.2.0-38-generic #61-Ubuntu System manufacturer System Product Name/P5G41-M LE
Mar 19 10:29:35 gaara kernel: [69270.313925] RIP: 0010:[<ffffffff81163730>]  [<ffffffff81163730>] kfree+0x50/0x140
Mar 19 10:29:35 gaara kernel: [69270.313933] RSP: 0018:ffff88001fa79b88  EFLAGS: 00010207
Mar 19 10:29:35 gaara kernel: [69270.313935] RAX: 03fc01e1107c3c00 RBX: ff0000441f0f0b0f RCX: 0000000000000008
Mar 19 10:29:35 gaara kernel: [69270.313937] RDX: ffffffff7fffffff RSI: ffffffff8188b7e0 RDI: ff0000441f0f0b0f
Mar 19 10:29:35 gaara kernel: [69270.313939] RBP: ffff88001fa79bb8 R08: 03fbebe1107c3c00 R09: 00000000000002cb
Mar 19 10:29:35 gaara kernel: [69270.313940] R10: ffffffff81c9f384 R11: ffffc90000002000 R12: ffff88005cf4e280
Mar 19 10:29:35 gaara kernel: [69270.313942] R13: 0000000000000000 R14: ffffffff8119b35d R15: ffff88005b167850
Mar 19 10:29:35 gaara kernel: [69270.313945] FS:  00007f64630a3700(0000) GS:ffff88007fc00000(0000) knlGS:0000000000000000
Mar 19 10:29:35 gaara kernel: [69270.313947] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 19 10:29:35 gaara kernel: [69270.313949] CR2: 00007f6462b5b230 CR3: 00000000456cc000 CR4: 00000000000406f0
Mar 19 10:29:35 gaara kernel: [69270.313951] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 19 10:29:35 gaara kernel: [69270.313953] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Mar 19 10:29:35 gaara kernel: [69270.313955] Process ifconfig (pid: 9677, threadinfo ffff88001fa78000, task ffff880017f49700)
Mar 19 10:29:35 gaara kernel: [69270.313957] Stack:
Mar 19 10:29:35 gaara kernel: [69270.313958]  ffff88001fa79bb8 ffffffff815480e1 ffff88005cf4e280 0000000000000000
Mar 19 10:29:35 gaara kernel: [69270.313963]  ffff88007b7f1080 ffff88005b167850 ffff88001fa79bd8 ffffffff8119b35d
Mar 19 10:29:35 gaara kernel: [69270.313966]  ffff88001fa79be8 b80000000000841f ffff88001fa79bf8 ffffffff8119b3e5
Mar 19 10:29:35 gaara kernel: [69270.313970] Call Trace:
Mar 19 10:29:35 gaara kernel: [69270.313976]  [<ffffffff815480e1>] ? ethtool_get_feature_mask+0x11/0x90
Mar 19 10:29:35 gaara kernel: [69270.313980]  [<ffffffff8119b35d>] seq_release+0x1d/0x30
Mar 19 10:29:35 gaara kernel: [69270.313983]  [<ffffffff8119b3e5>] single_release+0x25/0x40
Mar 19 10:29:35 gaara kernel: [69270.313987]  [<ffffffff811e3c31>] seq_open_net+0x51/0xb0
Mar 19 10:29:35 gaara kernel: [69270.313991]  [<ffffffff8153ec4a>] dev_seq_open+0x1a/0x20
Mar 19 10:29:35 gaara kernel: [69270.313995]  [<ffffffff811d8a70>] proc_reg_open+0xb0/0x190
Mar 19 10:29:35 gaara kernel: [69270.313998]  [<ffffffff811e3d70>] ? single_release_net+0x50/0x50
Mar 19 10:29:35 gaara kernel: [69270.314001]  [<ffffffff8153ec30>] ? ptype_seq_open+0x20/0x20
Mar 19 10:29:35 gaara kernel: [69270.314004]  [<ffffffff811771b0>] __dentry_open+0x290/0x360
Mar 19 10:29:35 gaara kernel: [69270.314007]  [<ffffffff811d89c0>] ? proc_alloc_inode+0xb0/0xb0
Mar 19 10:29:35 gaara kernel: [69270.314011]  [<ffffffff8129ea9c>] ? security_inode_permission+0x1c/0x30
Mar 19 10:29:35 gaara kernel: [69270.314014]  [<ffffffff81184f2a>] ? inode_permission+0x4a/0x110
Mar 19 10:29:35 gaara kernel: [69270.314016]  [<ffffffff8117782d>] vfs_open+0x3d/0x40
Mar 19 10:29:35 gaara kernel: [69270.314019]  [<ffffffff81178730>] nameidata_to_filp+0x40/0x50
Mar 19 10:29:35 gaara kernel: [69270.314021]  [<ffffffff81187768>] do_last+0x3f8/0x730
Mar 19 10:29:35 gaara kernel: [69270.314024]  [<ffffffff81188e41>] path_openat+0xd1/0x3f0
Mar 19 10:29:35 gaara kernel: [69270.314027]  [<ffffffff81163634>] ? kmem_cache_free+0x104/0x110
Mar 19 10:29:35 gaara kernel: [69270.314029]  [<ffffffff81189282>] do_filp_open+0x42/0xa0
Mar 19 10:29:35 gaara kernel: [69270.314033]  [<ffffffff8131aff1>] ? strncpy_from_user+0x31/0x40
Mar 19 10:29:35 gaara kernel: [69270.314037]  [<ffffffff8165d39e>] ? _raw_spin_lock+0xe/0x20
Mar 19 10:29:35 gaara kernel: [69270.314040]  [<ffffffff81196587>] ? alloc_fd+0xf7/0x150
Mar 19 10:29:35 gaara kernel: [69270.314042]  [<ffffffff81178838>] do_sys_open+0xf8/0x240
Mar 19 10:29:35 gaara kernel: [69270.314045]  [<ffffffff811780a4>] ? sys_faccessat+0x114/0x1e0
Mar 19 10:29:35 gaara kernel: [69270.314047]  [<ffffffff811789a0>] sys_open+0x20/0x30
Mar 19 10:29:35 gaara kernel: [69270.314050]  [<ffffffff81665982>] system_call_fastpath+0x16/0x1b
Mar 19 10:29:35 gaara kernel: [69270.314052] Code: 48 89 fb 66 66 66 66 90 48 83 fb 10 76 77 48 89 df e8 45 24 ee ff 48 c1 e8 0c 49 b8 00 00 00 00 00 ea ff ff 48 c1 e0 06 49 01 c0 <49> 8b 00 f6 c4 80 0f 85 d0 00 00 00 49 8b 00 a8 80 0f 84 af 00 
Mar 19 10:29:35 gaara kernel: [69270.314083] RIP  [<ffffffff81163730>] kfree+0x50/0x140
Mar 19 10:29:35 gaara kernel: [69270.314086]  RSP <ffff88001fa79b88>
Mar 19 10:29:35 gaara kernel: [69270.314089] ---[ end trace 5abaf0abb2474196 ]---
```


also, the log show dozens of other "kernel bug", "openvpn tainted" and "unable to handle kernel NULL pointer dereference" messages. Is there some way to solve this?

---

