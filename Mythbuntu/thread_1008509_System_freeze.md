---
title: "System freeze?"
date: 2008-12-11
forum: Mythbuntu
---

### Post by ederopaa on 2008-12-11
Hi,

I'm experiencing odd system freezes/crashes on my amd 64/mythbuntu 8.10 system. Here is a clip from my /var/log/syslog:

```
Dec 11 18:50:01 karhu kernel: [180821.540392] BUG: unable to handle kernel NULL pointer dereference at 0000000000000101
Dec 11 18:50:01 karhu kernel: [180821.540405] IP: [<ffffffff802e3119>] __kmalloc+0x79/0x110
Dec 11 18:50:01 karhu kernel: [180821.540422] PGD b0d18067 PUD dacc067 PMD 0 
Dec 11 18:50:01 karhu kernel: [180821.540430] Oops: 0000 [1] SMP 
Dec 11 18:50:01 karhu kernel: [180821.540436] CPU 0 
Dec 11 18:50:01 karhu kernel: [180821.540439] Modules linked in: lirc_mceusb nfsd auth_rpcgss exportfs bridge stp bnep sco rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_stats cpufreq_conservative cpufreq_ondemand cpufreq_powersave freq_table cpufreq_userspace pci_slot sbs wmi sbshc container video output battery nfs lockd nfs_acl sunrpc ipv6 iptable_filter ip_tables x_tables xfs dm_crypt crypto_blkcipher dm_mod ac it87 hwmon_vid sbp2 lp nvidia(P) snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi tda1004x snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw psmouse snd k8temp pcspkr evdev shpchp pci_hotplug soundcore snd_page_alloc lirc_mceusb2 lirc_dev budget_av saa7146_vv videobuf_dma_sg videobuf_core videodev v4l1_compat budget_core dvb_core saa7146 ttpci_eeprom parport_pc parport cfi_cmdset_0002 cfi_util jedec_probe cfi_probe gen_probe ck804xrom mtd i2c_nforce2 chipreg button i2c_core map_funcs ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sata_
Dec 11 18:50:01 karhu kernel: v pata_amd sg usbhid hid ata_generic pata_jmicron ahci forcedeth ehci_hcd ohci1394 pata_acpi ieee1394 ohci_hcd libata scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Dec 11 18:50:01 karhu kernel: [180821.540598] Pid: 2925, comm: mythtv-status Tainted: P          2.6.27-9-generic #1
Dec 11 18:50:01 karhu kernel: [180821.540603] RIP: 0010:[<ffffffff802e3119>]  [<ffffffff802e3119>] __kmalloc+0x79/0x110
Dec 11 18:50:01 karhu kernel: [180821.540613] RSP: 0018:ffff8800d734dc18  EFLAGS: 00010002
Dec 11 18:50:01 karhu kernel: [180821.540617] RAX: 0000000000000000 RBX: 0000000000000101 RCX: ffff8801088c900c
Dec 11 18:50:01 karhu kernel: [180821.540622] RDX: ffff880028028b00 RSI: 00000000000080d0 RDI: 0000000000000040
Dec 11 18:50:01 karhu kernel: [180821.540627] RBP: ffff8800d734dc48 R08: 0000000002020202 R09: 0000000002020202
Dec 11 18:50:01 karhu kernel: [180821.540631] R10: 0000000002020202 R11: 0000000002022e2e R12: ffffffff806df220
Dec 11 18:50:01 karhu kernel: [180821.540636] R13: 0000000000000282 R14: 00000000000080d0 R15: ffffffffa01d0abc
Dec 11 18:50:01 karhu kernel: [180821.540642] FS:  00007f3dee2076e0(0000) GS:ffffffff806e1a80(0000) knlGS:0000000000000000
Dec 11 18:50:01 karhu kernel: [180821.540646] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 11 18:50:01 karhu kernel: [180821.540651] CR2: 0000000000000101 CR3: 0000000037d84000 CR4: 00000000000006e0
Dec 11 18:50:01 karhu kernel: [180821.540656] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 11 18:50:01 karhu kernel: [180821.540661] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 11 18:50:01 karhu kernel: [180821.540666] Process mythtv-status (pid: 2925, threadinfo ffff8800d734c000, task ffff880053d859c0)
Dec 11 18:50:01 karhu kernel: [180821.540670] Stack:  00000040195ded00 ffff8801088c900c ffff880110ca3e70 ffff8801088c900c
Dec 11 18:50:01 karhu kernel: [180821.540681]  00000000b75aed1a 000000005ce79e35 ffff8800d734dc88 ffffffffa01d0abc
Dec 11 18:50:01 karhu kernel: [180821.540688]  ffff8801198b7980 ffff8801088c900c ffff880110ca3e70 ffff8800d734dd58
Dec 11 18:50:01 karhu kernel: [180821.540695] Call Trace:
Dec 11 18:50:01 karhu kernel: [180821.540721]  [<ffffffffa01d0abc>] ext3_htree_store_dirent+0x3c/0x130 [ext3]
Dec 11 18:50:01 karhu kernel: [180821.540743]  [<ffffffffa01d7d90>] htree_dirblock_to_tree+0x120/0x1b0 [ext3]
Dec 11 18:50:01 karhu kernel: [180821.540764]  [<ffffffffa01dad29>] ext3_htree_fill_tree+0x189/0x240 [ext3]
Dec 11 18:50:01 karhu kernel: [180821.540773]  [<ffffffff802e2c59>] ? get_slab+0x9/0x70
Dec 11 18:50:01 karhu kernel: [180821.540780]  [<ffffffff802f8a90>] ? filldir+0x0/0xe0
Dec 11 18:50:01 karhu kernel: [180821.540797]  [<ffffffffa01d04ec>] ext3_dx_readdir+0xcc/0x1e0 [ext3]
Dec 11 18:50:01 karhu kernel: [180821.540815]  [<ffffffffa01d0a1f>] ext3_readdir+0x41f/0x480 [ext3]
Dec 11 18:50:01 karhu kernel: [180821.540821]  [<ffffffff802f8a90>] ? filldir+0x0/0xe0
Dec 11 18:50:01 karhu kernel: [180821.540828]  [<ffffffff802ed998>] ? cp_new_stat+0xe8/0x100
Dec 11 18:50:01 karhu kernel: [180821.540835]  [<ffffffff80386bb1>] ? aa_file_permission+0x21/0xf0
Dec 11 18:50:01 karhu kernel: [180821.540840]  [<ffffffff802f8a90>] ? filldir+0x0/0xe0
Dec 11 18:50:01 karhu kernel: [180821.540845]  [<ffffffff802f8a90>] ? filldir+0x0/0xe0
Dec 11 18:50:01 karhu kernel: [180821.540850]  [<ffffffff802f8d1b>] vfs_readdir+0xbb/0xe0
Dec 11 18:50:01 karhu kernel: [180821.540856]  [<ffffffff802f8ea8>] sys_getdents+0x88/0xe0
Dec 11 18:50:01 karhu kernel: [180821.540865]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Dec 11 18:50:01 karhu kernel: [180821.540869] 
Dec 11 18:50:01 karhu kernel: [180821.540871] 
Dec 11 18:50:01 karhu kernel: [180821.540873] Code: fa 66 66 66 90 66 66 90 65 8b 04 25 24 00 00 00 48 98 49 8b 94 c4 f0 02 00 00 8b 7a 18 89 7d d4 48 8b 1a 48 85 db 74 52 8b 42 14 <48> 8b 04 c3 48 89 02 4c 89 ef 57 9d 66 66 90 66 66 90 66 45 85 
Dec 11 21:20:20 karhu syslogd 1.5.0#2ubuntu6: restart.

```

Any idea what is causing this or how to further investigate?

---

