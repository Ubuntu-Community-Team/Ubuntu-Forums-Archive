---
title: "My ORiNOCO Silver card crashes ubuntu at startup"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by PB_G3 on 2009-01-27
Hello,

I have an ORiNOCO Silver 802.11b card that I have been using for a while, (in OS 9) on my powerbook G3 lombard.  It works fine, but not in the PowerPC version of ubuntu 8.04 (kernel 2.6.24-19 now 2.6.24-23).
When I go to tty1 I see this output:

```
Jan 25 20:14:09 angelo-laptop kernel: [   56.319743] Caused by (from SRR1=49030): Transfer error ack signal
Jan 25 20:14:09 angelo-laptop kernel: [   56.320084] Oops: Machine check, sig: 7 [#1]
Jan 25 20:14:09 angelo-laptop kernel: [   56.320321] PowerMac
Jan 25 20:14:09 angelo-laptop kernel: [   56.320428] Modules linked in: pcmcia pmac_zilog serial_core evdev yenta_socket rsrc_nonstatic pcmcia_core ext3 jbd mbcache ide_cd cdrom mesh ide_disk scsi_mod bmac ohci_hcd usbcore windfarm_core fuse
Jan 25 20:14:09 angelo-laptop kernel: [   56.321581] NIP: d58d6d48 LR: d58d6d1c CTR: c0015138
Jan 25 20:14:09 angelo-laptop kernel: [   56.321813] REGS: d1ca3b50 TRAP: 0200   Not tainted  (2.6.24-19-powerpc)
Jan 25 20:14:09 angelo-laptop kernel: [   56.322111] MSR: 00049030 <EE,ME,IR,DR>  CR: 84024424  XER: 00000000
Jan 25 20:14:09 angelo-laptop kernel: [   56.322516] TASK = d383ccc0[3328] 'modprobe' THREAD: d1ca2000
Jan 25 20:14:09 angelo-laptop kernel: [   56.322771] GPR00: 000000ff d1ca3c00 d383ccc0 d591c000 00000014 00000070 00000002 d1ca3c59 
Jan 25 20:14:09 angelo-laptop kernel: [   56.323275] GPR08: d5058800 00001000 d591c000 d591d000 24024422 1001fef8 00000000 fd000000 
Jan 25 20:14:09 angelo-laptop kernel: [   56.323779] GPR16: d5070000 fd100000 fe000000 fd000000 00200000 c1d0fc40 fd080000 000004fb 
Jan 25 20:14:09 angelo-laptop kernel: [   56.324283] GPR24: d1ca3c59 00000000 00000002 c1d0fc40 00000021 00000000 00000002 d1ca3c59 
Jan 25 20:14:09 angelo-laptop kernel: [   56.324814] NIP [d58d6d48] pcmcia_read_cis_mem+0x178/0x26c [pcmcia_core]
Jan 25 20:14:09 angelo-laptop kernel: [   56.325191] LR [d58d6d1c] pcmcia_read_cis_mem+0x14c/0x26c [pcmcia_core]
Jan 25 20:14:09 angelo-laptop kernel: [   56.325514] Call Trace:
Jan 25 20:14:09 angelo-laptop kernel: [   56.325631] [d1ca3c00] [d58d6d1c] pcmcia_read_cis_mem+0x14c/0x26c [pcmcia_core] (unreliable)
Jan 25 20:14:09 angelo-laptop kernel: [   56.326058] [d1ca3c30] [d58d6fa4] read_cis_cache+0x168/0x16c [pcmcia_core]
Jan 25 20:14:09 angelo-laptop kernel: [   56.326402] [d1ca3c50] [d58d7200] pccard_get_next_tuple+0x1b4/0x478 [pcmcia_core]
Jan 25 20:14:09 angelo-laptop kernel: [   56.326771] [d1ca3c90] [d58d755c] pccard_get_first_tuple+0x98/0x144 [pcmcia_core]
Jan 25 20:14:09 angelo-laptop kernel: [   56.327140] [d1ca3cc0] [d58d7bc4] pccard_validate_cis+0xa0/0x248 [pcmcia_core]
Jan 25 20:14:09 angelo-laptop kernel: [   56.327499] [d1ca3cf0] [d5069ebc] readable+0x54/0xd8 [rsrc_nonstatic]
Jan 25 20:14:09 angelo-laptop kernel: [   56.327828] [d1ca3d10] [d506a1e8] pcmcia_nonstatic_validate_mem+0x16c/0x408 [rsrc_nonstatic]
Jan 25 20:14:09 angelo-laptop kernel: [   56.328230] [d1ca3d90] [d58d7d94] pcmcia_validate_mem+0x28/0x40 [pcmcia_core]
Jan 25 20:14:09 angelo-laptop kernel: [   56.328604] [d1ca3da0] [d59466a4] pcmcia_card_add+0x40/0xd0 [pcmcia]
Jan 25 20:14:09 angelo-laptop kernel: [   56.328955] [d1ca3e10] [d59467dc] ds_event+0xa8/0xd4 [pcmcia]
Jan 25 20:14:09 angelo-laptop kernel: [   56.329248] [d1ca3e30] [d58d44c4] send_event+0x6c/0x94 [pcmcia_core]
Jan 25 20:14:09 angelo-laptop kernel: [   56.329570] [d1ca3e40] [d58d4688] pccard_register_pcmcia+0x8c/0x90 [pcmcia_core]
Jan 25 20:14:09 angelo-laptop kernel: [   56.329936] [d1ca3e60] [d5946d30] pcmcia_bus_add_socket+0x7c/0xc4 [pcmcia]
Jan 25 20:14:09 angelo-laptop kernel: [   56.330277] [d1ca3e70] [c01ccd90] class_interface_register+0xf4/0x158
Jan 25 20:14:09 angelo-laptop kernel: [   56.330608] [d1ca3e90] [d5047038] init_pcmcia_bus+0x38/0xb4 [pcmcia]
Jan 25 20:14:09 angelo-laptop kernel: [   56.330925] [d1ca3ea0] [c005c9d0] sys_init_module+0x154/0x1664
Jan 25 20:14:09 angelo-laptop kernel: [   56.331224] [d1ca3f40] [c00140f4] ret_from_syscall+0x0/0x38
Jan 25 20:14:09 angelo-laptop kernel: [   56.331523] --- Exception: c01 at 0xff62174
Jan 25 20:14:09 angelo-laptop kernel: [   56.331733]     LR = 0x10003cf4
Jan 25 20:14:09 angelo-laptop kernel: [   56.331877] Instruction dump:
Jan 25 20:14:09 angelo-laptop kernel: [   56.332028] 4bfffd91 2c030000 41820104 813b00ec 3809ffff 7d634a14 7c00e838 7d430214 
Jan 25 20:14:09 angelo-laptop kernel: [   56.332515] 7f8b5000 419e006c 7c0004ac 7c0300ae <0c000000> 4c00012c 3bdeffff 981f0000 
Jan 25 20:14:09 angelo-laptop kernel: [   56.332998] ---[ end trace 85f3226eb2e2abc2 ]---
```
:(

Thanks,
PB_G3

---

### Post by PB_G3 on 2009-02-10
Breaking News: CODE UPDATE!!!

after upgrading my silver to gold (firmware)

```

 5592.604085] pccard: PCMCIA card inserted into slot 0
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.604128] cs: memory probe 0x80000000-0xfcffffff: excluding 0x80000000-0x81ffffff
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.728285] cs: memory probe 0xfd000000-0xfdffffff:Machine check in kernel mode.
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.728321] Caused by (from SRR1=49030): Transfer error ack signal
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.731868] Oops: Machine check, sig: 7 [#1]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.731891] PowerMac
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.731898] Modules linked in: ipv6 af_packet rfcomm l2cap bluetooth uinput ppdev lp parport cpufreq_stats cpufreq_userspace cpufreq_powersave cpufreq_conservative cpufreq_ondemand iptable_filter ip_tables x_tables apm_emu apm_emulation snd_powermac snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc pcmcia pmac_zilog serial_core yenta_socket rsrc_nonstatic pcmcia_core evdev ext3 jbd mbcache ide_cd cdrom mesh ide_disk bmac scsi_mod ohci_hcd usbcore windfarm_core fuse
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732129] NIP: e18d6d48 LR: e18d6d1c CTR: c0015138
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732147] REGS: de427c90 TRAP: 0200   Not tainted  (2.6.24-19-powerpc)
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732159] MSR: 00049030 <EE,ME,IR,DR>  CR: 84004024  XER: 00000000
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732189] TASK = de9d0000[2758] 'pccardd' THREAD: de426000
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732201] GPR00: 000000ff de427d40 de9d0000 e1a42000 00000014 00000070 00000002 de427d99 
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732231] GPR08: e1046800 00001000 e1a42000 e1a43000 24000022 00000000 00000000 fd000000 
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732262] GPR16: e1080000 fd100000 fe000000 fd000000 00200000 de5c7040 fd080000 000004fb 
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732293] GPR24: de427d99 00000000 00000002 de5c7040 00000021 00000000 00000002 de427d99 
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732325] NIP [e18d6d48] pcmcia_read_cis_mem+0x178/0x26c [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732409] LR [e18d6d1c] pcmcia_read_cis_mem+0x14c/0x26c [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732440] Call Trace:
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732450] [de427d40] [e18d6d1c] pcmcia_read_cis_mem+0x14c/0x26c [pcmcia_core] (unreliable)
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732488] [de427d70] [e18d6fa4] read_cis_cache+0x168/0x16c [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732523] [de427d90] [e18d7200] pccard_get_next_tuple+0x1b4/0x478 [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732558] [de427dd0] [e18d755c] pccard_get_first_tuple+0x98/0x144 [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732593] [de427e00] [e18d7bc4] pccard_validate_cis+0xa0/0x248 [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732628] [de427e30] [e1077ebc] readable+0x54/0xd8 [rsrc_nonstatic]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732665] [de427e50] [e10781e8] pcmcia_nonstatic_validate_mem+0x16c/0x408 [rsrc_nonstatic]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732693] [de427ed0] [e18d7d94] pcmcia_validate_mem+0x28/0x40 [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732727] [de427ee0] [e19466a4] pcmcia_card_add+0x40/0xd0 [pcmcia]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732790] [de427f50] [e19467dc] ds_event+0xa8/0xd4 [pcmcia]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732819] [de427f70] [e18d44c4] send_event+0x6c/0x94 [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732851] [de427f80] [e18d4a88] socket_insert+0xbc/0x130 [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732884] [de427f90] [e18d5178] pccardd+0x278/0x2c8 [pcmcia_core]
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732917] [de427fd0] [c004bed0] kthread+0x48/0x84
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.732962] [de427ff0] [c0013e60] kernel_thread+0x44/0x60
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.733001] Instruction dump:
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.733023] 4bfffd91 2c030000 41820104 813b00ec 3809ffff 7d634a14 7c00e838 7d430214 
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.733070] 7f8b5000 419e006c 7c0004ac 7c0300ae <0c000000> 4c00012c 3bdeffff 981f0000 
Feb  9 11:06:45 angelo-powerbook-lombard kernel: [ 5592.733132] ---[ end trace 4cab26d459bb30cd ]---

```

---

### Post by PB_G3 on 2009-11-10
Now, I use a Netgear WG111v2, it always helps ALOT! :mrgreen:

---

