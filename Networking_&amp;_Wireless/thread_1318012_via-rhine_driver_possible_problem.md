---
title: "via-rhine driver possible problem?"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by chronos87lm on 2009-11-07
I recently installed Ubuntu 9.10. When I looked in Log file Viewer I noticed some strange messages related to my network card:

Nov  7 11:24:36 ubuntu kernel: [ 5415.000055] ------------[ cut here ]------------
Nov  7 11:24:36 ubuntu kernel: [ 5415.000080] WARNING: at /build/buildd/linux-2.6.31/net/sched/sch_generic.c:246 dev_watchdog+0x1f6/0x210()
Nov  7 11:24:36 ubuntu kernel: [ 5415.000084] Hardware name: KT600-8237
Nov  7 11:24:36 ubuntu kernel: [ 5415.000087] NETDEV WATCHDOG: eth0 (via-rhine): transmit queue 0 timed out
Nov  7 11:24:36 ubuntu kernel: [ 5415.000090] Modules linked in: binfmt_misc snd_via82xx gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_mpu401_uart uvcvideo ppdev videodev psmouse lp parport_pc i2c_viapro v4l1_compat snd_seq_dummy serio_raw shpchp parport snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore iptable_filter ip_tables x_tables via_agp via_rhine radeon ttm drm i2c_algo_bit floppy mii agpgart sata_via
Nov  7 11:24:36 ubuntu kernel: [ 5415.000140] Pid: 0, comm: swapper Not tainted 2.6.31-14-generic #48-Ubuntu
Nov  7 11:24:36 ubuntu kernel: [ 5415.000144] Call Trace:
Nov  7 11:24:36 ubuntu kernel: [ 5415.000158]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
Nov  7 11:24:36 ubuntu kernel: [ 5415.000164]  [<c04b07c6>] ? dev_watchdog+0x1f6/0x210
Nov  7 11:24:36 ubuntu kernel: [ 5415.000169]  [<c04b07c6>] ? dev_watchdog+0x1f6/0x210
Nov  7 11:24:36 ubuntu kernel: [ 5415.000175]  [<c0145206>] warn_slowpath_fmt+0x26/0x30
Nov  7 11:24:36 ubuntu kernel: [ 5415.000180]  [<c04b07c6>] dev_watchdog+0x1f6/0x210
Nov  7 11:24:36 ubuntu kernel: [ 5415.000189]  [<c0157fdb>] ? insert_work+0x5b/0xa0
Nov  7 11:24:36 ubuntu kernel: [ 5415.000197]  [<c0127c38>] ? default_spin_lock_flags+0x8/0x10
Nov  7 11:24:36 ubuntu kernel: [ 5415.000204]  [<c05707da>] ? _spin_lock_irqsave+0x2a/0x40
Nov  7 11:24:36 ubuntu kernel: [ 5415.000210]  [<c01501b7>] run_timer_softirq+0x117/0x200
Nov  7 11:24:36 ubuntu kernel: [ 5415.000219]  [<c01699f4>] ? tick_handle_oneshot_broadcast+0x124/0x130
Nov  7 11:24:36 ubuntu kernel: [ 5415.000225]  [<c04b05d0>] ? dev_watchdog+0x0/0x210
Nov  7 11:24:36 ubuntu kernel: [ 5415.000233]  [<c014b3b0>] __do_softirq+0x90/0x1a0
Nov  7 11:24:36 ubuntu kernel: [ 5415.000243]  [<c018f8fc>] ? handle_IRQ_event+0x4c/0x140
Nov  7 11:24:36 ubuntu kernel: [ 5415.000247]  [<c0161f1c>] ? sched_clock_tick+0x7c/0xb0
Nov  7 11:24:36 ubuntu kernel: [ 5415.000253]  [<c01925a4>] ? move_native_irq+0x14/0x50
Nov  7 11:24:36 ubuntu kernel: [ 5415.000258]  [<c014b4fd>] do_softirq+0x3d/0x40
Nov  7 11:24:36 ubuntu kernel: [ 5415.000262]  [<c014b63d>] irq_exit+0x5d/0x70
Nov  7 11:24:36 ubuntu kernel: [ 5415.000269]  [<c0104f10>] do_IRQ+0x50/0xc0
Nov  7 11:24:36 ubuntu kernel: [ 5415.000274]  [<c01039b0>] common_interrupt+0x30/0x40
Nov  7 11:24:36 ubuntu kernel: [ 5415.000285]  [<c0369b05>] ? acpi_idle_enter_simple+0x100/0x130
Nov  7 11:24:36 ubuntu kernel: [ 5415.000296]  [<c0468406>] cpuidle_idle_call+0x76/0xd0
Nov  7 11:24:36 ubuntu kernel: [ 5415.000300]  [<c010202c>] cpu_idle+0x8c/0xd0
Nov  7 11:24:36 ubuntu kernel: [ 5415.000309]  [<c055e875>] rest_init+0x55/0x60
Nov  7 11:24:36 ubuntu kernel: [ 5415.000318]  [<c078e8cd>] start_kernel+0x2e6/0x2ec
Nov  7 11:24:36 ubuntu kernel: [ 5415.000323]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
Nov  7 11:24:36 ubuntu kernel: [ 5415.000329]  [<c078e07c>] i386_start_kernel+0x7c/0x83
Nov  7 11:24:36 ubuntu kernel: [ 5415.000333] ---[ end trace 3e817a63ec266116 ]---
Nov  7 11:24:36 ubuntu kernel: [ 5415.000478] eth0: Transmit timed out, status 0000, PHY status 786d, resetting...
Nov  7 11:24:36 ubuntu kernel: [ 5415.001170] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  7 11:24:40 ubuntu kernel: [ 5419.000185] eth0: Transmit timed out, status 0000, PHY status 786d, resetting...
Nov  7 11:24:40 ubuntu kernel: [ 5419.000880] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  7 11:43:23 ubuntu kernel: [ 6541.398375] eth0: link down
Nov  7 11:43:23 ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Nov  7 11:43:25 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Nov  7 11:43:25 ubuntu kernel: [ 6543.705878] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  7 11:43:30 ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Nov  7 11:43:30 ubuntu kernel: [ 6549.282104] eth0: link down
Nov  7 11:43:33 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Nov  7 11:43:33 ubuntu kernel: [ 6551.589581] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  7 11:50:29 ubuntu kernel: [ 6968.000197] eth0: Transmit timed out, status 0000, PHY status 786d, resetting...
Nov  7 11:50:29 ubuntu kernel: [ 6968.000896] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  7 11:50:36 ubuntu kernel: [ 6974.624858] eth0: link down
Nov  7 11:50:36 ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Nov  7 11:50:38 ubuntu kernel: [ 6976.920725] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  7 11:50:38 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Nov  7 11:50:43 ubuntu pulseaudio[1440]: ratelimit.c: 142 events suppressed
Nov  7 11:51:30 ubuntu pulseaudio[1440]: ratelimit.c: 1 events suppressed
Nov  7 11:51:31 ubuntu kernel: [ 7030.213431] eth0: link down
Nov  7 11:51:32 ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Nov  7 11:51:34 ubuntu kernel: [ 7032.520918] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  7 11:51:34 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Nov  7 11:51:36 ubuntu kernel: [ 7035.104936] eth0: link down
Nov  7 11:51:36 ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Nov  7 11:51:39 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Nov  7 11:51:39 ubuntu kernel: [ 7037.412419] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  7 11:51:39 ubuntu kernel: [ 7037.447550] eth0: link down
Nov  7 11:51:40 ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Nov  7 11:51:41 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Nov  7 11:51:41 ubuntu kernel: [ 7039.755021] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  7 11:51:41 ubuntu kernel: [ 7039.837690] eth0: link down

I think these messages apear when I upload large amounts of data with transmission torrent client. Is there a serious problem with via-rhine kernel driver? Should I worry?

---

