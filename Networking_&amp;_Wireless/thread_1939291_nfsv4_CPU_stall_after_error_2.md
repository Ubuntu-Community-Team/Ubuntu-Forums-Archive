---
title: "nfsv4: CPU stall after error 2"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by pref on 2012-03-11
I came across really strange issue with NFSv4 share on ubuntu desktop. It happens only with share mounted with Kerberos security. If a network activity is high I'm very likely to have these errors in my log. The system hangs if you try listing files in this share.
```
[  885.553185] Error: state manager failed on NFSv4 server server1 with error 2
[ 3620.567977] Error: state manager failed on NFSv4 server server1 with error 2
[ 3680.576617] INFO: rcu_sched_state detected stall on CPU 2 (t=15000 jiffies)
[ 3860.463749] INFO: rcu_sched_state detected stall on CPU 2 (t=60030 jiffies)
[ 4040.350876] INFO: rcu_sched_state detected stall on CPU 2 (t=105060 jiffies)
[ 4220.238003] INFO: rcu_sched_state detected stall on CPU 2 (t=150090 jiffies)
[ 4400.125132] INFO: rcu_sched_state detected stall on CPU 2 (t=195120 jiffies)
[ 4580.012261] INFO: rcu_sched_state detected stall on CPU 2 (t=240150 jiffies)
[ 4759.899390] INFO: rcu_sched_state detected stall on CPU 2 (t=285180 jiffies)
[ 4939.786519] INFO: rcu_sched_state detected stall on CPU 2 (t=330210 jiffies)
[ 5119.673649] INFO: rcu_sched_state detected stall on CPU 2 (t=375240 jiffies)
[ 5154.228923] INFO: task jbd2/sda2-8:295 blocked for more than 120 seconds.
[ 5154.228927] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5154.228930] jbd2/sda2-8     D ffffffff81805120     0   295      2 0x00000000
[ 5154.228936]  ffff880133c97ce0 0000000000000046 ffff880133c97c90 0000000300000001
[ 5154.228941]  ffff880133c97fd8 ffff880133c97fd8 ffff880133c97fd8 0000000000012a40
[ 5154.228957]  ffffffff81c0b020 ffff880133cb1720 ffff880133c97cf0 ffff880133c97df8
[ 5154.228963] Call Trace:
[ 5154.228972]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[ 5154.228978]  [<ffffffff8124867a>] jbd2_journal_commit_transaction+0x18a/0x1250
[ 5154.228984]  [<ffffffff81048398>] ? hrtick_update+0x38/0x40
[ 5154.228989]  [<ffffffff815f303e>] ? _raw_spin_lock_irqsave+0x2e/0x40
[ 5154.228996]  [<ffffffff8106e848>] ? lock_timer_base.isra.29+0x38/0x70
[ 5154.229001]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[ 5154.229006]  [<ffffffff8124d5cb>] kjournald2+0xbb/0x220
[ 5154.229011]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[ 5154.229015]  [<ffffffff8124d510>] ? commit_timeout+0x10/0x10
[ 5154.229020]  [<ffffffff8108135c>] kthread+0x8c/0xa0
[ 5154.229026]  [<ffffffff815fc324>] kernel_thread_helper+0x4/0x10
[ 5154.229031]  [<ffffffff810812d0>] ? flush_kthread_worker+0xa0/0xa0
[ 5154.229036]  [<ffffffff815fc320>] ? gs_change+0x13/0x13
[ 5154.229040] INFO: task flush-8:0:314 blocked for more than 120 seconds.
[ 5154.229042] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5154.229045] flush-8:0       D ffffffff81805120     0   314      2 0x00000000
[ 5154.229051]  ffff8801356bd920 0000000000000046 0000000000000006 ffffea0000b02360
[ 5154.229056]  ffff8801356bdfd8 ffff8801356bdfd8 ffff8801356bdfd8 0000000000012a40
[ 5154.229062]  ffffffff81c0b020 ffff880133cb5c80 ffff8801356bd930 ffff880136285000
[ 5154.229067] Call Trace:
[ 5154.229071]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[ 5154.229077]  [<ffffffff81245eea>] start_this_handle.isra.9+0x2aa/0x3e0
[ 5154.229082]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[ 5154.229087]  [<ffffffff812460ea>] jbd2__journal_start+0xca/0x110
[ 5154.229092]  [<ffffffff81246143>] jbd2_journal_start+0x13/0x20
[ 5154.229098]  [<ffffffff81222c79>] ext4_journal_start_sb+0x69/0x170
[ 5154.229103]  [<ffffffff812061d5>] ? ext4_meta_trans_blocks+0x75/0xe0
[ 5154.229108]  [<ffffffff8120cb4b>] ext4_da_writepages+0x2fb/0x5e0
[ 5154.229114]  [<ffffffff81115451>] do_writepages+0x21/0x40
[ 5154.229119]  [<ffffffff81190143>] writeback_single_inode+0x103/0x280
[ 5154.229123]  [<ffffffff81190561>] writeback_sb_inodes+0xe1/0x1b0
[ 5154.229128]  [<ffffffff811908c6>] writeback_inodes_wb+0xa6/0xf0
[ 5154.229131]  [<ffffffff81190c5f>] wb_writeback+0x34f/0x450
[ 5154.229136]  [<ffffffff81048398>] ? hrtick_update+0x38/0x40
[ 5154.229140]  [<ffffffff81190df8>] wb_check_old_data_flush+0x98/0xa0
[ 5154.229145]  [<ffffffff81190f51>] wb_do_writeback+0x151/0x1f0
[ 5154.229150]  [<ffffffff8106e1a0>] ? usleep_range+0x50/0x50
[ 5154.229154]  [<ffffffff81191073>] bdi_writeback_thread+0x83/0x2a0
[ 5154.229159]  [<ffffffff81190ff0>] ? wb_do_writeback+0x1f0/0x1f0
[ 5154.229163]  [<ffffffff8108135c>] kthread+0x8c/0xa0
[ 5154.229168]  [<ffffffff815fc324>] kernel_thread_helper+0x4/0x10
[ 5154.229173]  [<ffffffff810812d0>] ? flush_kthread_worker+0xa0/0xa0
[ 5154.229178]  [<ffffffff815fc320>] ? gs_change+0x13/0x13
[ 5154.229185] INFO: task rs:main Q:Reg:1223 blocked for more than 120 seconds.
[ 5154.229187] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5154.229190] rs:main Q:Reg   D ffffffff81805120     0  1223      1 0x00000000
[ 5154.229195]  ffff880111f099f8 0000000000000086 ffff880111f09ab8 ffffffff811136de
[ 5154.229201]  ffff880111f09fd8 ffff880111f09fd8 ffff880111f09fd8 0000000000012a40
[ 5154.229207]  ffff880139340000 ffff880135d19720 ffff880111f09a08 ffff880136285000
[ 5154.229212] Call Trace:
[ 5154.229216]  [<ffffffff811136de>] ? __alloc_pages_nodemask+0x10e/0x820
[ 5154.229221]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[ 5154.229226]  [<ffffffff81245eea>] start_this_handle.isra.9+0x2aa/0x3e0
[ 5154.229231]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[ 5154.229236]  [<ffffffff812460ea>] jbd2__journal_start+0xca/0x110
[ 5154.229241]  [<ffffffff81246143>] jbd2_journal_start+0x13/0x20
[ 5154.229245]  [<ffffffff81222c79>] ext4_journal_start_sb+0x69/0x170
[ 5154.229250]  [<ffffffff810566b0>] ? load_balance_fair+0x100/0x150
[ 5154.229254]  [<ffffffff8120d1c6>] ext4_dirty_inode+0x26/0x60
[ 5154.229258]  [<ffffffff8118f660>] __mark_inode_dirty+0x40/0x280
[ 5154.229264]  [<ffffffff81181d82>] file_update_time+0x102/0x170
[ 5154.229270]  [<ffffffff8110c328>] __generic_file_aio_write+0x1f8/0x440
[ 5154.229275]  [<ffffffff815f0874>] ? __schedule+0x3d4/0x700
[ 5154.229280]  [<ffffffff8110c5df>] generic_file_aio_write+0x6f/0xe0
[ 5154.229291]  [<ffffffff8120122f>] ext4_file_write+0xbf/0x260
[ 5154.229296]  [<ffffffff81096578>] ? futex_wait+0x108/0x210
[ 5154.229303]  [<ffffffff81167ed2>] do_sync_write+0xd2/0x110
[ 5154.229308]  [<ffffffff8128453c>] ? security_file_permission+0x2c/0xb0
[ 5154.229313]  [<ffffffff81168321>] ? rw_verify_area+0x61/0xf0
[ 5154.229318]  [<ffffffff81168683>] vfs_write+0xb3/0x180
[ 5154.229323]  [<ffffffff811689aa>] sys_write+0x4a/0x90
[ 5154.229328]  [<ffffffff815fb202>] system_call_fastpath+0x16/0x1b
[ 5154.229334] INFO: task dhclient:1459 blocked for more than 120 seconds.
[ 5154.229336] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5154.229339] dhclient        D ffffffff81805120     0  1459   1236 0x00000000
[ 5154.229345]  ffff88011013d9f8 0000000000000086 0000000000000000 0000000000000002
[ 5154.229350]  ffff88011013dfd8 ffff88011013dfd8 ffff88011013dfd8 0000000000012a40
[ 5154.229356]  ffffffff81c0b020 ffff880110c91720 ffff88011013da08 ffff880136285000
[ 5154.229361] Call Trace:
[ 5154.229366]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[ 5154.229371]  [<ffffffff81245eea>] start_this_handle.isra.9+0x2aa/0x3e0
[ 5154.229376]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[ 5154.229381]  [<ffffffff812460ea>] jbd2__journal_start+0xca/0x110
[ 5154.229386]  [<ffffffff81246143>] jbd2_journal_start+0x13/0x20
[ 5154.229390]  [<ffffffff81222c79>] ext4_journal_start_sb+0x69/0x170
[ 5154.229395]  [<ffffffff81182d3c>] ? destroy_inode+0x3c/0x70
[ 5154.229400]  [<ffffffff812f18a9>] ? put_dec+0x59/0x60
[ 5154.229405]  [<ffffffff8120d1c6>] ext4_dirty_inode+0x26/0x60
[ 5154.229408]  [<ffffffff8118f660>] __mark_inode_dirty+0x40/0x280
[ 5154.229413]  [<ffffffff81181d82>] file_update_time+0x102/0x170
[ 5154.229418]  [<ffffffff8110c328>] __generic_file_aio_write+0x1f8/0x440
[ 5154.229423]  [<ffffffff8103e6b8>] ? flush_tlb_page+0x48/0xb0
[ 5154.229429]  [<ffffffff8110c5df>] generic_file_aio_write+0x6f/0xe0
[ 5154.229434]  [<ffffffff8120122f>] ext4_file_write+0xbf/0x260
[ 5154.229438]  [<ffffffff8113018b>] ? handle_pte_fault+0x1db/0x210
[ 5154.229443]  [<ffffffff81167ed2>] do_sync_write+0xd2/0x110
[ 5154.229449]  [<ffffffff8106259c>] ? do_wait+0x12c/0x260
[ 5154.229453]  [<ffffffff8128453c>] ? security_file_permission+0x2c/0xb0
[ 5154.229458]  [<ffffffff81168321>] ? rw_verify_area+0x61/0xf0
[ 5154.229463]  [<ffffffff81168683>] vfs_write+0xb3/0x180
[ 5154.229468]  [<ffffffff811689aa>] sys_write+0x4a/0x90
[ 5154.229472]  [<ffffffff815fb202>] system_call_fastpath+0x16/0x1b
[ 5154.229493] INFO: task akonadi_nepomuk:1951 blocked for more than 120 seconds.
[ 5154.229496] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5154.229499] akonadi_nepomuk D ffffffff81805120     0  1951   1890 0x00000000
[ 5154.229504]  ffff880101b8fa88 0000000000000086 ffff880101b8fa78 ffffffff810573de
[ 5154.229509]  ffff880101b8ffd8 ffff880101b8ffd8 ffff880101b8ffd8 0000000000012a40
[ 5154.229515]  ffff880139340000 ffff88010191c560 ffff880101b8fa98 ffff880136285000
[ 5154.229521] Call Trace:
[ 5154.229525]  [<ffffffff810573de>] ? try_to_wake_up+0x18e/0x200
[ 5154.229529]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[ 5154.229534]  [<ffffffff81245eea>] start_this_handle.isra.9+0x2aa/0x3e0
[ 5154.229539]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[ 5154.229544]  [<ffffffff812460ea>] jbd2__journal_start+0xca/0x110
[ 5154.229549]  [<ffffffff81246143>] jbd2_journal_start+0x13/0x20
[ 5154.229553]  [<ffffffff81222c79>] ext4_journal_start_sb+0x69/0x170
[ 5154.229558]  [<ffffffff8120d1c6>] ext4_dirty_inode+0x26/0x60
[ 5154.229561]  [<ffffffff8118f660>] __mark_inode_dirty+0x40/0x280
[ 5154.229566]  [<ffffffff81181f27>] touch_atime+0x137/0x180
[ 5154.229571]  [<ffffffff8110ba87>] do_generic_file_read.constprop.36+0x367/0x440
[ 5154.229577]  [<ffffffff8110c770>] generic_file_aio_read+0x120/0x290
[ 5154.229582]  [<ffffffff81167fe2>] do_sync_read+0xd2/0x110
[ 5154.229587]  [<ffffffff81153d9d>] ? kmem_cache_alloc+0x11d/0x140
[ 5154.229592]  [<ffffffff812845a3>] ? security_file_permission+0x93/0xb0
[ 5154.229597]  [<ffffffff81168321>] ? rw_verify_area+0x61/0xf0
[ 5154.229602]  [<ffffffff81168800>] vfs_read+0xb0/0x180
[ 5154.229606]  [<ffffffff8116891a>] sys_read+0x4a/0x90
[ 5154.229611]  [<ffffffff815fb202>] system_call_fastpath+0x16/0x1b
[ 5154.229619] INFO: task chrome:2309 blocked for more than 120 seconds.
[ 5154.229622] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5154.229624] chrome          D ffffffff81805120     0  2309   1695 0x00000000
[ 5154.229630]  ffff8800a552da88 0000000000000082 ffff88012e015410 ffff88012e064618
[ 5154.229635]  ffff8800a552dfd8 ffff8800a552dfd8 ffff8800a552dfd8 0000000000012a40
[ 5154.229641]  ffffffff81c0b020 ffff8800b32d0000 ffff8800a552da98 ffff880136285000
[ 5154.229646] Call Trace:
[ 5154.229650]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[ 5154.229655]  [<ffffffff81245eea>] start_this_handle.isra.9+0x2aa/0x3e0
[ 5154.229660]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[ 5154.229665]  [<ffffffff812460ea>] jbd2__journal_start+0xca/0x110
[ 5154.229670]  [<ffffffff81246143>] jbd2_journal_start+0x13/0x20
[ 5154.229673]  [<ffffffff81222c79>] ext4_journal_start_sb+0x69/0x170
[ 5154.229677]  [<ffffffff815f2dae>] ? _raw_spin_lock+0xe/0x20
[ 5154.229680]  [<ffffffff8117e02f>] ? __d_instantiate+0x8f/0x110
[ 5154.229684]  [<ffffffff8120d1c6>] ext4_dirty_inode+0x26/0x60
[ 5154.229687]  [<ffffffff8118f660>] __mark_inode_dirty+0x40/0x280
[ 5154.229691]  [<ffffffff8117eb3b>] ? d_splice_alias+0x4b/0x60
[ 5154.229695]  [<ffffffff81181f27>] touch_atime+0x137/0x180
[ 5154.229699]  [<ffffffff8110ba87>] do_generic_file_read.constprop.36+0x367/0x440
[ 5154.229704]  [<ffffffff8110c770>] generic_file_aio_read+0x120/0x290
[ 5154.229707]  [<ffffffff81176eb9>] ? path_lookupat+0xc9/0x700
[ 5154.229711]  [<ffffffff81167fe2>] do_sync_read+0xd2/0x110
[ 5154.229715]  [<ffffffff815f2dae>] ? _raw_spin_lock+0xe/0x20
[ 5154.229719]  [<ffffffff812845a3>] ? security_file_permission+0x93/0xb0
[ 5154.229724]  [<ffffffff81168321>] ? rw_verify_area+0x61/0xf0
[ 5154.229729]  [<ffffffff81168800>] vfs_read+0xb0/0x180
[ 5154.229733]  [<ffffffff8116891a>] sys_read+0x4a/0x90
[ 5154.229737]  [<ffffffff815fb202>] system_call_fastpath+0x16/0x1b
[ 5154.229739] INFO: task chrome:2311 blocked for more than 120 seconds.
[ 5154.229741] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5154.229743] chrome          D ffffffff81805120     0  2311   1695 0x00000000
[ 5154.229747]  ffff8800a55279f8 0000000000000082 ffff880136291800 ffff880136298800
[ 5154.229762]  ffff8800a5527fd8 ffff8800a5527fd8 ffff8800a5527fd8 0000000000012a40
[ 5154.229765]  ffffffff81c0b020 ffff8800a57d1720 ffff8800a5527a08 ffff880136285000
[ 5154.229769] Call Trace:
[ 5154.229771]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[ 5154.229775]  [<ffffffff81245eea>] start_this_handle.isra.9+0x2aa/0x3e0
[ 5154.229778]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[ 5154.229782]  [<ffffffff812460ea>] jbd2__journal_start+0xca/0x110
[ 5154.229785]  [<ffffffff81246143>] jbd2_journal_start+0x13/0x20
[ 5154.229789]  [<ffffffff81222c79>] ext4_journal_start_sb+0x69/0x170
[ 5154.229792]  [<ffffffff8120d1c6>] ext4_dirty_inode+0x26/0x60
[ 5154.229794]  [<ffffffff8118f660>] __mark_inode_dirty+0x40/0x280
[ 5154.229798]  [<ffffffff81181d82>] file_update_time+0x102/0x170
[ 5154.229802]  [<ffffffff8110c328>] __generic_file_aio_write+0x1f8/0x440
[ 5154.229805]  [<ffffffff81103d10>] ? __perf_event_task_sched_out+0x30/0x60
[ 5154.229811]  [<ffffffff811a8edb>] ? ep_poll_callback+0xbb/0xf0
[ 5154.229815]  [<ffffffff8110c5df>] generic_file_aio_write+0x6f/0xe0
[ 5154.229819]  [<ffffffff8120122f>] ext4_file_write+0xbf/0x260
[ 5154.229823]  [<ffffffff81167ed2>] do_sync_write+0xd2/0x110
[ 5154.229826]  [<ffffffff8128453c>] ? security_file_permission+0x2c/0xb0
[ 5154.229829]  [<ffffffff81168321>] ? rw_verify_area+0x61/0xf0
[ 5154.229832]  [<ffffffff81168683>] vfs_write+0xb3/0x180
[ 5154.229836]  [<ffffffff811689aa>] sys_write+0x4a/0x90
[ 5154.229838]  [<ffffffff815fb202>] system_call_fastpath+0x16/0x1b
[ 5154.229841] INFO: task chrome:2319 blocked for more than 120 seconds.
[ 5154.229843] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5154.229845] chrome          D ffffffff81805120     0  2319   1695 0x00000000
[ 5154.229848]  ffff8800a55e5988 0000000000000082 ffff8800a55e5938 ffffffff810819c7
[ 5154.229851]  ffff8800a55e5fd8 ffff8800a55e5fd8 ffff8800a55e5fd8 0000000000012a40
[ 5154.229855]  ffff88013935c560 ffff8800a57d2e40 ffff8800a55e5958 ffff88013fb932c0
[ 5154.229858] Call Trace:
[ 5154.229861]  [<ffffffff810819c7>] ? bit_waitqueue+0x17/0xd0
[ 5154.229864]  [<ffffffff8110a360>] ? __lock_page+0x70/0x70
[ 5154.229867]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[ 5154.229869]  [<ffffffff815f0f7f>] io_schedule+0x8f/0xd0
[ 5154.229872]  [<ffffffff8110a36e>] sleep_on_page+0xe/0x20
[ 5154.229874]  [<ffffffff815f179f>] __wait_on_bit+0x5f/0x90
[ 5154.229877]  [<ffffffff8110a558>] wait_on_page_bit+0x78/0x80
[ 5154.229880]  [<ffffffff81081e40>] ? autoremove_wake_function+0x40/0x40
[ 5154.229884]  [<ffffffff8110b392>] grab_cache_page_write_begin+0x92/0xe0
[ 5154.229887]  [<ffffffff8120acb0>] ext4_da_write_begin+0x130/0x270
[ 5154.229889]  [<ffffffff81246866>] ? jbd2_journal_stop+0x1b6/0x2a0
[ 5154.229893]  [<ffffffff8110a817>] generic_perform_write+0xb7/0x1c0
[ 5154.229896]  [<ffffffff8120d1f0>] ? ext4_dirty_inode+0x50/0x60
[ 5154.229900]  [<ffffffff8110a97d>] generic_file_buffered_write+0x5d/0x90
[ 5154.229903]  [<ffffffff8110c359>] __generic_file_aio_write+0x229/0x440
[ 5154.229907]  [<ffffffff8110c5df>] generic_file_aio_write+0x6f/0xe0
[ 5154.229910]  [<ffffffff8120122f>] ext4_file_write+0xbf/0x260
[ 5154.229914]  [<ffffffff81167ed2>] do_sync_write+0xd2/0x110
[ 5154.229917]  [<ffffffff8128453c>] ? security_file_permission+0x2c/0xb0
[ 5154.229920]  [<ffffffff81168321>] ? rw_verify_area+0x61/0xf0
[ 5154.229923]  [<ffffffff81168683>] vfs_write+0xb3/0x180
[ 5154.229927]  [<ffffffff81168b42>] sys_pwrite64+0xa2/0xb0
[ 5154.229930]  [<ffffffff815fb202>] system_call_fastpath+0x16/0x1b
[ 5154.229933] INFO: task chrome:2330 blocked for more than 120 seconds.
[ 5154.229935] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 5154.229936] chrome          D 0000000000000000     0  2330   1695 0x00000000
[ 5154.229940]  ffff8800a00d59f8 0000000000000082 ffff880136291800 ffff880136298800
[ 5154.229944]  ffff8800a00d5fd8 ffff8800a00d5fd8 ffff8800a00d5fd8 0000000000012a40
[ 5154.229947]  ffff8800b32d5c80 ffff88010ab35c80 ffff8800a00d5a08 ffff880136285000
[ 5154.229951] Call Trace:
[ 5154.229954]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[ 5154.229957]  [<ffffffff81245eea>] start_this_handle.isra.9+0x2aa/0x3e0
[ 5154.229960]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[ 5154.229964]  [<ffffffff812460ea>] jbd2__journal_start+0xca/0x110
[ 5154.229968]  [<ffffffff81246143>] jbd2_journal_start+0x13/0x20
[ 5154.229971]  [<ffffffff81222c79>] ext4_journal_start_sb+0x69/0x170
[ 5154.229974]  [<ffffffff8120d1c6>] ext4_dirty_inode+0x26/0x60
[ 5154.229977]  [<ffffffff8118f660>] __mark_inode_dirty+0x40/0x280
[ 5154.229981]  [<ffffffff81181d82>] file_update_time+0x102/0x170
[ 5154.229985]  [<ffffffff8110c328>] __generic_file_aio_write+0x1f8/0x440
[ 5154.229988]  [<ffffffff815f0874>] ? __schedule+0x3d4/0x700
[ 5154.229991]  [<ffffffff8110c5df>] generic_file_aio_write+0x6f/0xe0
[ 5154.229995]  [<ffffffff8120122f>] ext4_file_write+0xbf/0x260
[ 5154.229999]  [<ffffffff81096578>] ? futex_wait+0x108/0x210
[ 5154.230003]  [<ffffffff81167ed2>] do_sync_write+0xd2/0x110
[ 5154.230006]  [<ffffffff8128453c>] ? security_file_permission+0x2c/0xb0
[ 5154.230010]  [<ffffffff81168321>] ? rw_verify_area+0x61/0xf0
[ 5154.230013]  [<ffffffff81168683>] vfs_write+0xb3/0x180
[ 5154.230017]  [<ffffffff811689aa>] sys_write+0x4a/0x90
[ 5154.230020]  [<ffffffff815fb202>] system_call_fastpath+0x16/0x1b
[ 5170.019097] Error: state manager failed on NFSv4 server server1 with error 2
[ 5230.158618] INFO: rcu_sched_state detected stall on CPU 2 (t=15000 jiffies)
[ 5410.045747] INFO: rcu_sched_state detected stall on CPU 2 (t=60030 jiffies)
[ 5589.932876] INFO: rcu_sched_state detected stall on CPU 2 (t=105060 jiffies)
[ 5769.820004] INFO: rcu_sched_state detected stall on CPU 2 (t=150090 jiffies)
[ 5949.707134] INFO: rcu_sched_state detected stall on CPU 2 (t=195120 jiffies)
```

---

