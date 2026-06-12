---
title: "Bonded network device dropping"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by Celauran on 2009-06-19
I'm running a Hardy box with 4 Adaptec Starfire cards bonded to interface bond0. For the most part this is working quite well, but over the last week I've had the network go down a number of times for no reason I can ascertain -- I haven't been able to pinpoint a particular trigger. The network becomes completely unreachable for a few minutes, then begins responding to ping but with considerable packet loss then, after a further few minutes, I'm able to ssh in. Can't ping out from, though. Restarting networking has no effect, either.

I've looked through the logs, but most of what I've found has, quite frankly, been gibberish to me. Trying to Google a solution but so far no luck.

/var/log/syslog:
```
Jun 19 15:03:17 hardy kernel: [262013.370493] NETDEV WATCHDOG: eth3: transmit timed out
Jun 19 15:03:17 hardy kernel: [262013.370507] eth3: Transmit timed out, status 0x00000000, resetting...
Jun 19 15:03:17 hardy kernel: [262013.370512] eth3: Shutting down ethercard, Intr status 0x00000000.
Jun 19 15:03:17 hardy kernel: [262013.370516] eth3: Queue pointers were Tx 149352 / 149323, Rx 232988 / 232988.
Jun 19 15:03:17 hardy kernel: [262013.370522] WARNING: at /build/buildd/linux-2.6.24/kernel/irq/manage.c:425 free_irq()
Jun 19 15:03:17 hardy kernel: [262013.370528] Pid: 0, comm: swapper Not tainted 2.6.24-23-server #1
Jun 19 15:03:17 hardy kernel: [262013.370565]  [snd_mpu401_uart:free_irq+0x132/0x2e0] free_irq+0x132/0x140
Jun 19 15:03:17 hardy kernel: [262013.370587]  [<e087ace9>] netdev_close+0xa9/0x230 [starfire]
Jun 19 15:03:17 hardy kernel: [262013.370607]  [<e087ca6e>] tx_timeout+0x4e/0xb0 [starfire]
Jun 19 15:03:17 hardy kernel: [262013.370619]  [dev_watchdog+0xc4/0xd0] dev_watchdog+0xc4/0xd0
Jun 19 15:03:17 hardy kernel: [262013.370630]  [run_timer_softirq+0x169/0x1e0] run_timer_softirq+0x169/0x1e0
Jun 19 15:03:17 hardy kernel: [262013.370640]  [dev_watchdog+0x0/0xd0] dev_watchdog+0x0/0xd0
Jun 19 15:03:17 hardy kernel: [262013.370648]  [dev_watchdog+0x0/0xd0] dev_watchdog+0x0/0xd0
Jun 19 15:03:17 hardy kernel: [262013.370656]  [__do_softirq+0x82/0x110] __do_softirq+0x82/0x110
Jun 19 15:03:17 hardy kernel: [262013.370664]  [do_softirq+0x55/0x60] do_softirq+0x55/0x60
Jun 19 15:03:17 hardy kernel: [262013.370669]  [irq_exit+0x6d/0x80] irq_exit+0x6d/0x80
Jun 19 15:03:17 hardy kernel: [262013.370674]  [smp_apic_timer_interrupt+0x55/0x80] smp_apic_timer_interrupt+0x55/0x80
Jun 19 15:03:17 hardy kernel: [262013.370684]  [ktime_get+0x18/0x40] ktime_get+0x18/0x40
Jun 19 15:03:17 hardy kernel: [262013.370693]  [apic_timer_interrupt+0x28/0x30] apic_timer_interrupt+0x28/0x30
Jun 19 15:03:17 hardy kernel: [262013.370705]  [default_idle+0x0/0x60] default_idle+0x0/0x60
Jun 19 15:03:17 hardy kernel: [262013.370716]  [native_safe_halt+0x2/0x10] native_safe_halt+0x2/0x10
Jun 19 15:03:17 hardy kernel: [262013.370726]  [default_idle+0x3c/0x60] default_idle+0x3c/0x60
Jun 19 15:03:17 hardy kernel: [262013.370731]  [cpu_idle+0x73/0xd0] cpu_idle+0x73/0xd0
Jun 19 15:03:17 hardy kernel: [262013.370748]  =======================
Jun 19 15:03:17 hardy kernel: [262013.371110] eth3: netdev_open() irq 18.
Jun 19 15:03:17 hardy kernel: [262013.371358] eth3: Filling in the station address.
Jun 19 15:03:17 hardy kernel: [262013.372374] eth3: Setting the Rx and Tx modes.
Jun 19 15:03:17 hardy kernel: [262013.373116] eth3: Done netdev_open().
Jun 19 15:03:17 hardy kernel: [262013.373359] eth3: Link is down
Jun 19 15:03:17 hardy kernel: [262013.410633] bonding: bond0: link status down for idle  interface eth3, disabling it in 200 ms.
Jun 19 15:03:17 hardy kernel: [262013.600578] bonding: bond0: link status definitely down for interface eth3, disabling it
Jun 19 15:03:19 hardy kernel: [262015.078175] eth3: Link is up, running at 100Mbit full-duplex
Jun 19 15:03:19 hardy kernel: [262015.108555] bonding: bond0: link status up for interface eth3, enabling it in 200 ms.
Jun 19 15:03:19 hardy kernel: [262015.298499] bonding: bond0: link status definitely up for interface eth3.
Jun 19 15:03:19 hardy kernel: [262015.370557] NETDEV WATCHDOG: eth2: transmit timed out
Jun 19 15:03:19 hardy kernel: [262015.370570] eth2: Transmit timed out, status 0x00000000, resetting...
Jun 19 15:03:19 hardy kernel: [262015.370576] eth2: Shutting down ethercard, Intr status 0x00000000.
Jun 19 15:03:19 hardy kernel: [262015.370580] eth2: Queue pointers were Tx 149357 / 149328, Rx 232284 / 232284.
Jun 19 15:03:19 hardy kernel: [262015.370586] WARNING: at /build/buildd/linux-2.6.24/kernel/irq/manage.c:425 free_irq()
Jun 19 15:03:19 hardy kernel: [262015.370592] Pid: 0, comm: swapper Not tainted 2.6.24-23-server #1
Jun 19 15:03:19 hardy kernel: [262015.370629]  [snd_mpu401_uart:free_irq+0x132/0x2e0] free_irq+0x132/0x140
Jun 19 15:03:19 hardy kernel: [262015.370650]  [<e087ace9>] netdev_close+0xa9/0x230 [starfire]
Jun 19 15:03:19 hardy kernel: [262015.370671]  [<e087ca6e>] tx_timeout+0x4e/0xb0 [starfire]
Jun 19 15:03:19 hardy kernel: [262015.370682]  [dev_watchdog+0xc4/0xd0] dev_watchdog+0xc4/0xd0
Jun 19 15:03:19 hardy kernel: [262015.370693]  [run_timer_softirq+0x169/0x1e0] run_timer_softirq+0x169/0x1e0
Jun 19 15:03:19 hardy kernel: [262015.370703]  [dev_watchdog+0x0/0xd0] dev_watchdog+0x0/0xd0
Jun 19 15:03:19 hardy kernel: [262015.370711]  [dev_watchdog+0x0/0xd0] dev_watchdog+0x0/0xd0
Jun 19 15:03:19 hardy kernel: [262015.370719]  [__do_softirq+0x82/0x110] __do_softirq+0x82/0x110
Jun 19 15:03:19 hardy kernel: [262015.370728]  [do_softirq+0x55/0x60] do_softirq+0x55/0x60
Jun 19 15:03:19 hardy kernel: [262015.370732]  [irq_exit+0x6d/0x80] irq_exit+0x6d/0x80
Jun 19 15:03:19 hardy kernel: [262015.370737]  [smp_apic_timer_interrupt+0x55/0x80] smp_apic_timer_interrupt+0x55/0x80
Jun 19 15:03:19 hardy kernel: [262015.370747]  [ktime_get+0x18/0x40] ktime_get+0x18/0x40
Jun 19 15:03:19 hardy kernel: [262015.370756]  [apic_timer_interrupt+0x28/0x30] apic_timer_interrupt+0x28/0x30
Jun 19 15:03:19 hardy kernel: [262015.370768]  [default_idle+0x0/0x60] default_idle+0x0/0x60
Jun 19 15:03:19 hardy kernel: [262015.370779]  [native_safe_halt+0x2/0x10] native_safe_halt+0x2/0x10
Jun 19 15:03:19 hardy kernel: [262015.370789]  [default_idle+0x3c/0x60] default_idle+0x3c/0x60
Jun 19 15:03:19 hardy kernel: [262015.370793]  [cpu_idle+0x73/0xd0] cpu_idle+0x73/0xd0
Jun 19 15:03:19 hardy kernel: [262015.370810]  =======================
Jun 19 15:03:19 hardy kernel: [262015.371173] eth2: netdev_open() irq 16.
Jun 19 15:03:19 hardy kernel: [262015.371437] eth2: Filling in the station address.
Jun 19 15:03:19 hardy kernel: [262015.372453] eth2: Setting the Rx and Tx modes.
Jun 19 15:03:19 hardy kernel: [262015.373194] eth2: Done netdev_open().
Jun 19 15:03:19 hardy kernel: [262015.373449] eth2: Link is down
Jun 19 15:03:19 hardy kernel: [262015.408005] NETDEV WATCHDOG: eth1: transmit timed out
Jun 19 15:03:19 hardy kernel: [262015.408016] eth1: Transmit timed out, status 0x00000000, resetting...
Jun 19 15:03:19 hardy kernel: [262015.408021] eth1: Shutting down ethercard, Intr status 0x00000000.
Jun 19 15:03:19 hardy kernel: [262015.408024] eth1: Queue pointers were Tx 149359 / 149330, Rx 231891 / 231891.
Jun 19 15:03:19 hardy kernel: [262015.408031] WARNING: at /build/buildd/linux-2.6.24/kernel/irq/manage.c:425 free_irq()
Jun 19 15:03:19 hardy kernel: [262015.408036] Pid: 0, comm: swapper Not tainted 2.6.24-23-server #1
Jun 19 15:03:19 hardy kernel: [262015.408072]  [snd_mpu401_uart:free_irq+0x132/0x2e0] free_irq+0x132/0x140
Jun 19 15:03:19 hardy kernel: [262015.408093]  [<e087ace9>] netdev_close+0xa9/0x230 [starfire]
Jun 19 15:03:19 hardy kernel: [262015.408114]  [<e087ca6e>] tx_timeout+0x4e/0xb0 [starfire]
Jun 19 15:03:19 hardy kernel: [262015.408126]  [dev_watchdog+0xc4/0xd0] dev_watchdog+0xc4/0xd0
Jun 19 15:03:19 hardy kernel: [262015.408137]  [run_timer_softirq+0x169/0x1e0] run_timer_softirq+0x169/0x1e0
Jun 19 15:03:19 hardy kernel: [262015.408147]  [dev_watchdog+0x0/0xd0] dev_watchdog+0x0/0xd0
Jun 19 15:03:19 hardy kernel: [262015.408155]  [dev_watchdog+0x0/0xd0] dev_watchdog+0x0/0xd0
Jun 19 15:03:19 hardy kernel: [262015.408162]  [__do_softirq+0x82/0x110] __do_softirq+0x82/0x110
Jun 19 15:03:19 hardy kernel: [262015.408171]  [do_softirq+0x55/0x60] do_softirq+0x55/0x60
Jun 19 15:03:19 hardy kernel: [262015.408176]  [irq_exit+0x6d/0x80] irq_exit+0x6d/0x80
Jun 19 15:03:19 hardy kernel: [262015.408180]  [smp_apic_timer_interrupt+0x55/0x80] smp_apic_timer_interrupt+0x55/0x80
Jun 19 15:03:19 hardy kernel: [262015.408190]  [ktime_get+0x18/0x40] ktime_get+0x18/0x40
Jun 19 15:03:19 hardy kernel: [262015.408200]  [apic_timer_interrupt+0x28/0x30] apic_timer_interrupt+0x28/0x30
Jun 19 15:03:19 hardy kernel: [262015.408212]  [default_idle+0x0/0x60] default_idle+0x0/0x60
Jun 19 15:03:19 hardy kernel: [262015.408223]  [native_safe_halt+0x2/0x10] native_safe_halt+0x2/0x10
Jun 19 15:03:19 hardy kernel: [262015.408233]  [default_idle+0x3c/0x60] default_idle+0x3c/0x60
Jun 19 15:03:19 hardy kernel: [262015.408238]  [cpu_idle+0x73/0xd0] cpu_idle+0x73/0xd0
Jun 19 15:03:19 hardy kernel: [262015.408244]  [start_kernel+0x31f/0x3b0] start_kernel+0x31f/0x3b0
Jun 19 15:03:19 hardy kernel: [262015.408252]  [unknown_bootoption+0x0/0x1f0] unknown_bootoption+0x0/0x1f0
Jun 19 15:03:19 hardy kernel: [262015.408263]  =======================
Jun 19 15:03:19 hardy kernel: [262015.408628] eth1: netdev_open() irq 17.
Jun 19 15:03:19 hardy kernel: [262015.408887] eth1: Filling in the station address.
Jun 19 15:03:19 hardy kernel: [262015.409903] eth1: Setting the Rx and Tx modes.
Jun 19 15:03:19 hardy kernel: [262015.410646] eth1: Done netdev_open().
Jun 19 15:03:19 hardy kernel: [262015.410651] NETDEV WATCHDOG: eth4: transmit timed out
Jun 19 15:03:19 hardy kernel: [262015.410655] eth4: Transmit timed out, status 0x00000000, resetting...
Jun 19 15:03:19 hardy kernel: [262015.410658] eth4: Shutting down ethercard, Intr status 0x00000000.
Jun 19 15:03:19 hardy kernel: [262015.410662] eth4: Queue pointers were Tx 149354 / 149325, Rx 232723 / 232723.
Jun 19 15:03:19 hardy kernel: [262015.410666] WARNING: at /build/buildd/linux-2.6.24/kernel/irq/manage.c:425 free_irq()
Jun 19 15:03:19 hardy kernel: [262015.410671] Pid: 0, comm: swapper Not tainted 2.6.24-23-server #1
Jun 19 15:03:19 hardy kernel: [262015.410684]  [snd_mpu401_uart:free_irq+0x132/0x2e0] free_irq+0x132/0x140
Jun 19 15:03:19 hardy kernel: [262015.410697]  [<e087ace9>] netdev_close+0xa9/0x230 [starfire]
Jun 19 15:03:19 hardy kernel: [262015.410713]  [<e087ca6e>] tx_timeout+0x4e/0xb0 [starfire]
Jun 19 15:03:19 hardy kernel: [262015.410723]  [dev_watchdog+0xc4/0xd0] dev_watchdog+0xc4/0xd0
Jun 19 15:03:19 hardy kernel: [262015.410731]  [run_timer_softirq+0x169/0x1e0] run_timer_softirq+0x169/0x1e0
Jun 19 15:03:19 hardy kernel: [262015.410738]  [dev_watchdog+0x0/0xd0] dev_watchdog+0x0/0xd0
Jun 19 15:03:19 hardy kernel: [262015.410746]  [dev_watchdog+0x0/0xd0] dev_watchdog+0x0/0xd0
Jun 19 15:03:19 hardy kernel: [262015.410754]  [__do_softirq+0x82/0x110] __do_softirq+0x82/0x110
Jun 19 15:03:19 hardy kernel: [262015.410884] eth1: Link is down
Jun 19 15:03:19 hardy kernel: [262015.410889]  [do_softirq+0x55/0x60] do_softirq+0x55/0x60
Jun 19 15:03:19 hardy kernel: [262015.410894]  [irq_exit+0x6d/0x80] irq_exit+0x6d/0x80
Jun 19 15:03:19 hardy kernel: [262015.410898]  [smp_apic_timer_interrupt+0x55/0x80] smp_apic_timer_interrupt+0x55/0x80
Jun 19 15:03:19 hardy kernel: [262015.410903]  [ktime_get+0x18/0x40] ktime_get+0x18/0x40
Jun 19 15:03:19 hardy kernel: [262015.410910]  [apic_timer_interrupt+0x28/0x30] apic_timer_interrupt+0x28/0x30
Jun 19 15:03:19 hardy kernel: [262015.410917]  [default_idle+0x0/0x60] default_idle+0x0/0x60
Jun 19 15:03:19 hardy kernel: [262015.410928]  [native_safe_halt+0x2/0x10] native_safe_halt+0x2/0x10
Jun 19 15:03:19 hardy kernel: [262015.410934]  [default_idle+0x3c/0x60] default_idle+0x3c/0x60
Jun 19 15:03:19 hardy kernel: [262015.410939]  [cpu_idle+0x73/0xd0] cpu_idle+0x73/0xd0
Jun 19 15:03:19 hardy kernel: [262015.410945]  [start_kernel+0x31f/0x3b0] start_kernel+0x31f/0x3b0
Jun 19 15:03:19 hardy kernel: [262015.410950]  [unknown_bootoption+0x0/0x1f0] unknown_bootoption+0x0/0x1f0
Jun 19 15:03:19 hardy kernel: [262015.410960]  =======================
Jun 19 15:03:19 hardy kernel: [262015.411276] eth4: netdev_open() irq 19.
Jun 19 15:03:19 hardy kernel: [262015.411518] eth4: Filling in the station address.
Jun 19 15:03:19 hardy kernel: [262015.412530] eth4: Setting the Rx and Tx modes.
Jun 19 15:03:19 hardy kernel: [262015.413270] eth4: Done netdev_open().
Jun 19 15:03:19 hardy kernel: [262015.413524] eth4: Link is down
Jun 19 15:03:19 hardy kernel: [262015.420511] bonding: bond0: link status down for idle  interface eth1, disabling it in 200 ms.
Jun 19 15:03:19 hardy kernel: [262015.420612] bonding: bond0: link status down for idle  interface eth2, disabling it in 200 ms.
Jun 19 15:03:19 hardy kernel: [262015.420797] bonding: bond0: link status down for idle  interface eth4, disabling it in 200 ms.
Jun 19 15:03:19 hardy kernel: [262015.620252] bonding: bond0: link status definitely down for interface eth1, disabling it
Jun 19 15:03:19 hardy kernel: [262015.620349] bonding: bond0: link status definitely down for interface eth2, disabling it
Jun 19 15:03:19 hardy kernel: [262015.620531] bonding: bond0: link status definitely down for interface eth4, disabling it
Jun 19 15:03:21 hardy kernel: [262016.958077] eth2: Link is up, running at 100Mbit full-duplex
Jun 19 15:03:21 hardy kernel: [262017.018649] bonding: bond0: link status up for interface eth2, enabling it in 200 ms.
Jun 19 15:03:21 hardy kernel: [262017.028076] eth4: Link is up, running at 100Mbit full-duplex
Jun 19 15:03:21 hardy kernel: [262017.118697] bonding: bond0: link status up for interface eth4, enabling it in 200 ms.
Jun 19 15:03:21 hardy kernel: [262017.148605] eth1: Link is up, running at 100Mbit full-duplex
Jun 19 15:03:21 hardy kernel: [262017.218304] bonding: bond0: link status up for interface eth1, enabling it in 200 ms.
Jun 19 15:03:21 hardy kernel: [262017.218492] bonding: bond0: link status definitely up for interface eth2.
Jun 19 15:03:21 hardy kernel: [262017.318181] bonding: bond0: link status definitely up for interface eth1.
Jun 19 15:03:21 hardy kernel: [262017.318457] bonding: bond0: link status definitely up for interface eth4.
Jun 19 15:14:58 hardy syslogd 1.5.0#1ubuntu1: restart.
```

Anyone encountered something similar or have any insight to offer?

---

