---
title: "network stops randomly"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by strange on 2010-08-18
network stops working 

my server which shares my internet connection with the rest of the house recently started to randomly quit the eth0 connection and the sharing connected with that. after a reboot all is fine again /var/log/messages shows the following

```

Aug 18 19:53:36 Gomorrah kernel: [93072.000029] ------------[ cut here ]------------
Aug 18 19:53:36 Gomorrah kernel: [93072.000048] WARNING: at /build/buildd/linux-2.6.31/net/sched/sch_generic.c:246 dev_watchdog+0x1f6/0x210()
Aug 18 19:53:36 Gomorrah kernel: [93072.000054] Hardware name: System name
Aug 18 19:53:36 Gomorrah kernel: [93072.000059] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
Aug 18 19:53:36 Gomorrah kernel: [93072.000063] Modules linked in: ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs reiserfs ipt_MASQUERADE xt_tcp$
Aug 18 19:53:36 Gomorrah kernel: 9 mii
Aug 18 19:53:36 Gomorrah kernel: [93072.000192] Pid: 12606, comm: plugin-containe Not tainted 2.6.31-21-generic #59-Ubuntu
Aug 18 19:53:36 Gomorrah kernel: [93072.000197] Call Trace:
Aug 18 19:53:36 Gomorrah kernel: [93072.000210]  [<c014508d>] warn_slowpath_common+0x6d/0xa0
Aug 18 19:53:36 Gomorrah kernel: [93072.000218]  [<c04b4f36>] ? dev_watchdog+0x1f6/0x210
Aug 18 19:53:36 Gomorrah kernel: [93072.000225]  [<c04b4f36>] ? dev_watchdog+0x1f6/0x210
Aug 18 19:53:36 Gomorrah kernel: [93072.000232]  [<c0145106>] warn_slowpath_fmt+0x26/0x30
Aug 18 19:53:36 Gomorrah kernel: [93072.000239]  [<c04b4f36>] dev_watchdog+0x1f6/0x210
Aug 18 19:53:36 Gomorrah kernel: [93072.000261]  [<f859d162>] ? destroy_conntrack+0x92/0xc0 [nf_conntrack]
Aug 18 19:53:36 Gomorrah kernel: [93072.000270]  [<c04bf77f>] ? nf_conntrack_destroy+0xf/0x20
Aug 18 19:53:36 Gomorrah kernel: [93072.000288]  [<f859ce49>] ? death_by_timeout+0x69/0x130 [nf_conntrack]
Aug 18 19:53:36 Gomorrah kernel: [93072.000298]  [<c01582b1>] ? __queue_work+0x31/0x40
Aug 18 19:53:36 Gomorrah kernel: [93072.000305]  [<c0150097>] run_timer_softirq+0x117/0x200
Aug 18 19:53:36 Gomorrah kernel: [93072.000315]  [<c016a0a5>] ? tick_dev_program_event+0x45/0xe0
Aug 18 19:53:36 Gomorrah kernel: [93072.000321]  [<c04b4d40>] ? dev_watchdog+0x0/0x210
Aug 18 19:53:36 Gomorrah kernel: [93072.000329]  [<c014b290>] __do_softirq+0x90/0x1a0
Aug 18 19:53:36 Gomorrah kernel: [93072.000338]  [<c015fe43>] ? hrtimer_interrupt+0x183/0x210
Aug 18 19:53:36 Gomorrah kernel: [93072.000345]  [<c014b3dd>] do_softirq+0x3d/0x40
Aug 18 19:53:36 Gomorrah kernel: [93072.000352]  [<c014b51d>] irq_exit+0x5d/0x70
Aug 18 19:53:36 Gomorrah kernel: [93072.000361]  [<c011dc07>] smp_apic_timer_interrupt+0x57/0x90
Aug 18 19:53:36 Gomorrah kernel: [93072.000369]  [<c0103db1>] apic_timer_interrupt+0x31/0x40
Aug 18 19:53:36 Gomorrah kernel: [93072.000375] ---[ end trace 9bf27a1267a2b8d1 ]---
Aug 18 19:53:36 Gomorrah kernel: [93072.018627] r8169: eth0: link up


```

anyone have any suggestions on how to fix this?

---

### Post by strange on 2010-08-19
bump

---

### Post by strange on 2010-08-21
anyone?

---

