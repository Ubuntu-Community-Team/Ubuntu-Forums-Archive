---
title: "Kernel oops after some time using ipheth"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by konradmb on 2011-08-13
After some time eth1 disconnects and sometimes hangs up system. I must rmmod ipheth and modprobe it to make it work again. I've compiled new version of ipheth (because Ubuntu's default is not working) from git and i'm using Ubuntu 11.04. Of course I've paired it with my computer. I have to add that I'm sharing this connection via hostapd and iptables. From /var/log/syslog:

Jul 19 12:14:46 0 wpa_supplicant[555]: Failed to initiate AP scan.
Jul 19 12:15:22 0 kernel: [ 1284.016052] ------------[ cut here ]------------ Jul 19 12:15:22 0 kernel: [ 1284.016089] WARNING: at /build/buildd/linux-2.6.38/net/sched/sch_generic.c:256 dev_watchdog+0x213/0x220()
Jul 19 12:15:22 0 kernel: [ 1284.016096] Hardware name: Aspire one

Jul 19 12:15:22 0 kernel: [ 1284.016209] NETDEV WATCHDOG: eth1 (ipheth): transmit queue 0 timed out
Jul 19 12:15:22 0 kernel: [ 1284.016214] Modules linked in: cryptd aes_i586 aes_generic ipt_REDIRECT xt_tcpudp ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 ip_tables x_tables ipheth hid_a4tech usbhid hid snd_hrtimer binfmt_misc parport_pc ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm arc4 snd_seq_midi ath9k nfsd snd_rawmidi lockd nfs_acl auth_rpcgss sunrpc exportfs mac80211 snd_seq_midi_event snd_seq snd_timer joydev snd_seq_device i915 ath9k_common uvcvideo ath9k_hw videodev ath drm_kms_helper snd drm cfg80211 psmouse soundcore serio_raw snd_page_alloc i2c_algo_bit video lp parport ahci libahci atl1c
Jul 19 12:15:22 0 kernel: [ 1284.016322] Pid: 0, comm: swapper Not tainted 2.6.38-10-generic #46-Ubuntu
Jul 19 12:15:22 0 kernel: [ 1284.016328] Call Trace:
Jul 19 12:15:22 0 kernel: [ 1284.016340] [] ? warn_slowpath_common+0x72/0xa0
Jul 19 12:15:22 0 kernel: [ 1284.016349] [] ? dev_watchdog+0x213/0x220
Jul 19 12:15:22 0 kernel: [ 1284.016357] [] ? dev_watchdog+0x213/0x220
Jul 19 12:15:22 0 kernel: [ 1284.016365] [] ? warn_slowpath_fmt+0x33/0x40
Jul 19 12:15:22 0 kernel: [ 1284.016373] [] ? dev_watchdog+0x213/0x220
Jul 19 12:15:22 0 kernel: [ 1284.016384] [] ? radix_tree_lookup+0xa/0x10
Jul 19 12:15:22 0 kernel: [ 1284.016393] [] ? call_timer_fn+0x2b/0xe0
Jul 19 12:15:22 0 kernel: [ 1284.016402] [] ? do_IRQ+0x4b/0xc0
Jul 19 12:15:22 0 kernel: [ 1284.016410] [] ? dev_watchdog+0x0/0x220
Jul 19 12:15:22 0 kernel: [ 1284.016417] [] ? run_timer_softirq+0xe9/0x1e0
Jul 19 12:15:22 0 kernel: [ 1284.016426] [] ? dev_watchdog+0x0/0x220
Jul 19 12:15:22 0 kernel: [ 1284.016434] [] ? __do_softirq+0x82/0x170
Jul 19 12:15:22 0 kernel: [ 1284.016441] [] ? __do_softirq+0x0/0x170
Jul 19 12:15:22 0 kernel: [ 1284.016446] [] ? irq_exit+0x6d/0x80
Jul 19 12:15:22 0 kernel: [ 1284.016459] [] ? smp_apic_timer_interrupt+0x5b/0x8a
Jul 19 12:15:22 0 kernel: [ 1284.016468] [] ? default_spin_lock_flags+0x8/0x10
Jul 19 12:15:22 0 kernel: [ 1284.016476] [] ? apic_timer_interrupt+0x31/0x38
Jul 19 12:15:22 0 kernel: [ 1284.016484] [] ? console_unlock+0x3b/0xe0
Jul 19 12:15:22 0 kernel: [ 1284.016493] [] ? intel_idle+0xb8/0x110
Jul 19 12:15:22 0 kernel: [ 1284.016502] [] ? cpuidle_idle_call+0x7d/0x160
Jul 19 12:15:22 0 kernel: [ 1284.016511] [] ? cpu_idle+0x8a/0xc0
Jul 19 12:15:22 0 kernel: [ 1284.016519] [] ? complete+0x4e/0x60
Jul 19 12:15:22 0 kernel: [ 1284.016528] [] ? rest_init+0x5d/0x70
Jul 19 12:15:22 0 kernel: [ 1284.016538] [] ? start_kernel+0x35f/0x366
Jul 19 12:15:22 0 kernel: [ 1284.016545] [] ? pass_all_bootoptions+0x0/0xa
Jul 19 12:15:22 0 kernel: [ 1284.016554] [] ? i386_start_kernel+0xe0/0xe8
Jul 19 12:15:22 0 kernel: [ 1284.016560] ---[ end trace 86464d6db7b2562c ]---
Jul 19 12:15:22 0 kernel: [ 1284.016565] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:15:27 0 kernel: [ 1289.008062] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:15:32 0 kernel: [ 1294.016045] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:15:37 0 kernel: [ 1299.008042] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:15:42 0 kernel: [ 1304.016042] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:15:46 0 wpa_supplicant[555]: Failed to initiate AP scan.
Jul 19 12:15:47 0 kernel: [ 1309.008049] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:15:52 0 kernel: [ 1314.016062] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:15:57 0 kernel: [ 1319.008061] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:16:02 0 kernel: [ 1324.016050] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:16:07 0 kernel: [ 1329.008054] ipheth: ipheth_tx_timeout: TX timeout
Jul 19 12:16:12 0 kernel: [ 1334.016051] ipheth: ipheth_tx_timeout: TX timeout

---

### Post by konradmb on 2011-08-14
bump

---

