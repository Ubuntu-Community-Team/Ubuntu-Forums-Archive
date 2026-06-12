---
title: "NETDEV WATCHDOG: eth0 (r8169): transmit timed out"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by HeegeMcGee on 2009-04-27
I've got a nice backlog of issues that resulted in me buying brand new hardware for 9.04. Everything is working and stable, and for the most part i'm pleased.

Except for the networking card. It crashed last night about 6 hours into uptime. I was using Torrentflux and pegging the card with some local Samba transfers when the network traffic came to a halt. I thought the box was down, but i went down to the basement to check on it and was pleasantly surprised that it was back up, and it had even gotten eth0 back online in the short time it took me to go downstairs to the box. Below are some choice snippets from my box.

I suppose it could be user error, but this is the driver that was picked by the distro, so i'm posting here first. Is this a known issue? i've been googling and coming up dry. If this is a bug, should i report it in Launchpad or with the r8169 maintainer?

Snippet from the interface crash:
```

Apr 26 21:05:28 cinderella kernel: [ 6428.010031] ------------[ cut here ]------------
Apr 26 21:05:28 cinderella kernel: [ 6428.010039] WARNING: at /build/buildd/linux-2.6.28/net/sched/sch_generic.c:226 dev_watchdog+0x270/0x280()
Apr 26 21:05:28 cinderella kernel: [ 6428.010044] NETDEV WATCHDOG: eth0 (r8169): transmit timed out
Apr 26 21:05:28 cinderella kernel: [ 6428.010048] Modules linked in: video output input_polldev it87 hwmon_vid lp i2c_piix4 ppdev k8temp shpchp pcspkr parport_pc parport r8169 mii raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor
Apr 26 21:05:28 cinderella kernel: [ 6428.010090] Pid: 0, comm: swapper Not tainted 2.6.28-11-server #42-Ubuntu
Apr 26 21:05:28 cinderella kernel: [ 6428.010094] Call Trace:
Apr 26 21:05:28 cinderella kernel: [ 6428.010098]  <IRQ>  [<ffffffff80250927>] warn_slowpath+0xb7/0xf0
Apr 26 21:05:28 cinderella kernel: [ 6428.010117]  [<ffffffff80416a2a>] ? __next_cpu+0x1a/0x30
Apr 26 21:05:28 cinderella kernel: [ 6428.010122]  [<ffffffff80416a2a>] ? __next_cpu+0x1a/0x30
Apr 26 21:05:28 cinderella kernel: [ 6428.010131]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0
Apr 26 21:05:28 cinderella kernel: [ 6428.010138]  [<ffffffff802486cd>] ? enqueue_task_fair+0x3d/0x80
Apr 26 21:05:28 cinderella kernel: [ 6428.010144]  [<ffffffff8023e6a0>] ? enqueue_task+0x50/0x60
Apr 26 21:05:28 cinderella kernel: [ 6428.010149]  [<ffffffff8024a58d>] ? default_wake_function+0xd/0x10
Apr 26 21:05:28 cinderella kernel: [ 6428.010159]  [<ffffffff802688a1>] ? autoremove_wake_function+0x11/0x40
Apr 26 21:05:28 cinderella kernel: [ 6428.010168]  [<ffffffff802708b9>] ? getnstimeofday+0x59/0xe0
Apr 26 21:05:28 cinderella kernel: [ 6428.010175]  [<ffffffff8041cd0a>] ? strlcpy+0x4a/0x60
Apr 26 21:05:28 cinderella kernel: [ 6428.010180]  [<ffffffff805caf70>] dev_watchdog+0x270/0x280
Apr 26 21:05:28 cinderella kernel: [ 6428.010187]  [<ffffffff8026e61c>] ? sched_clock_cpu+0xcc/0x160
Apr 26 21:05:28 cinderella kernel: [ 6428.010193]  [<ffffffff80264bac>] ? __queue_work+0x3c/0x50
Apr 26 21:05:28 cinderella kernel: [ 6428.010198]  [<ffffffff805cad00>] ? dev_watchdog+0x0/0x280
Apr 26 21:05:28 cinderella kernel: [ 6428.010206]  [<ffffffff8025bdf9>] run_timer_softirq+0x179/0x260
Apr 26 21:05:28 cinderella kernel: [ 6428.010213]  [<ffffffff802736bf>] ? clockevents_program_event+0x4f/0x90
Apr 26 21:05:28 cinderella kernel: [ 6428.010220]  [<ffffffff80256a5c>] __do_softirq+0x9c/0x170
Apr 26 21:05:28 cinderella kernel: [ 6428.010227]  [<ffffffff80213d8c>] call_softirq+0x1c/0x30
Apr 26 21:05:28 cinderella kernel: [ 6428.010233]  [<ffffffff80214ffd>] do_softirq+0x5d/0xa0
Apr 26 21:05:28 cinderella kernel: [ 6428.010238]  [<ffffffff802567dd>] irq_exit+0x8d/0xa0
Apr 26 21:05:28 cinderella kernel: [ 6428.010247]  [<ffffffff80227658>] smp_apic_timer_interrupt+0x88/0xc0
Apr 26 21:05:28 cinderella kernel: [ 6428.010253]  [<ffffffff80213668>] apic_timer_interrupt+0x88/0x90
Apr 26 21:05:28 cinderella kernel: [ 6428.010256]  <EOI>  [<ffffffff8022e856>] ? native_safe_halt+0x6/0x10
Apr 26 21:05:28 cinderella kernel: [ 6428.010271]  [<ffffffff8021a9fd>] ? default_idle+0x4d/0x50
Apr 26 21:05:28 cinderella kernel: [ 6428.010277]  [<ffffffff8021aa51>] ? c1e_idle+0x51/0x130
Apr 26 21:05:28 cinderella kernel: [ 6428.010285]  [<ffffffff806a1085>] ? atomic_notifier_call_chain+0x15/0x20
Apr 26 21:05:28 cinderella kernel: [ 6428.010294]  [<ffffffff80210e85>] ? cpu_idle+0x65/0xc0
Apr 26 21:05:28 cinderella kernel: [ 6428.010302]  [<ffffffff806987a3>] ? start_secondary+0x9e/0xcb
Apr 26 21:05:28 cinderella kernel: [ 6428.010306] ---[ end trace 35196b3d935e4174 ]---
Apr 26 21:05:28 cinderella kernel: [ 6428.050970] r8169: eth0: link up

```

Output of lspci:
```
[07:37:31] root@cinderella:/etc/init.d -> lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

ifconfig:
```

[07:49:15] root@cinderella:/etc/init.d -> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:2b:7a:01
          inet addr:192.168.2.50  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe2b:7a01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4881798 (4.8 MB)  TX bytes:80833493 (80.8 MB)
          Interrupt:253 Base address:0x6000

```

Everything else:
```

[07:50:13] root@cinderella:/etc/init.d -> uname -a
Linux cinderella 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux
[07:50:43] root@cinderella:/etc/init.d -> cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
[07:50:47] root@cinderella:/etc/init.d -> lsmod
Module                  Size  Used by
usb_storage            94912  0
video                  29204  0
output                 11648  1 video
input_polldev          12688  0
it87                   35352  0
hwmon_vid              12160  1 it87
lp                     19588  0
ppdev                  16904  0
i2c_piix4              20112  0
pcspkr                 11136  0
shpchp                 44572  0
k8temp                 13440  0
parport_pc             45096  1
parport                49584  3 lp,ppdev,parport_pc
r8169                  46596  0
mii                    14464  1 r8169
raid10                 31872  0
raid456               140064  0
async_xor              12160  1 raid456
async_memcpy           10752  1 raid456
async_tx               16636  3 raid456,async_xor,async_memcpy
xor                    13968  2 raid456,async_xor
raid1                  32384  0
raid0                  15488  1
multipath              16512  0
linear                 13440  0
fbcon                  49792  0
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

---

### Post by mpiermar on 2009-04-28
The same exact thing happens to me as well.  Probably the same MB/chipset as the mentioned (AMD 780G MB), running 9.04 64Bit and using flgrx for video.

```

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

And the trap:
```

[36470.792030] ------------[ cut here ]------------
[36470.792038] WARNING: at /build/buildd/linux-2.6.28/net/sched/sch_generic.c:226 dev_watchdog+0x270/0x280()
[36470.792042] NETDEV WATCHDOG: eth0 (r8169): transmit timed out
[36470.792045] Modules linked in: uvcvideo binfmt_misc ppdev bnep ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables bridge stp kvm_amd kvm video output input_polldev nfsd auth_rpcgss exportfs nfs lockd nfs_acl sunrpc it87 hwmon_vid lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_usb_audio snd_usb_lib snd_pcm snd_seq_dummy snd_hwdep snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq compat_ioctl32 snd_timer snd_seq_device videodev psmouse snd usblp i2c_piix4 pcspkr v4l1_compat snd_page_alloc serio_raw joydev fglrx(P) soundcore btusb hid_microsoft usbhid r8169 mii raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor [last unloaded: uvcvideo]
[36470.792169] Pid: 0, comm: swapper Tainted: P           2.6.28-11-generic #42-Ubuntu
[36470.792173] Call Trace:
[36470.792176]  <IRQ>  [<ffffffff80250927>] warn_slowpath+0xb7/0xf0
[36470.792194]  [<ffffffff80248250>] ? check_preempt_curr_idle+0x10/0x20
[36470.792203]  [<ffffffff80416ffa>] ? __next_cpu+0x1a/0x30
[36470.792207]  [<ffffffff802476dc>] ? find_busiest_group+0x1dc/0x9a0
[36470.792216]  [<ffffffff802199e6>] ? read_tsc+0x16/0x40
[36470.792222]  [<ffffffff80270969>] ? getnstimeofday+0x59/0xe0
[36470.792228]  [<ffffffff8041d2da>] ? strlcpy+0x4a/0x60
[36470.792233]  [<ffffffff805cb6f0>] dev_watchdog+0x270/0x280
[36470.792238]  [<ffffffff8026e6cc>] ? sched_clock_cpu+0xcc/0x160
[36470.792243]  [<ffffffff802199e6>] ? read_tsc+0x16/0x40
[36470.792247]  [<ffffffff805cb480>] ? dev_watchdog+0x0/0x280
[36470.792253]  [<ffffffff8025be79>] run_timer_softirq+0x179/0x260
[36470.792259]  [<ffffffff8027375f>] ? clockevents_program_event+0x4f/0x90
[36470.792264]  [<ffffffff80256acc>] __do_softirq+0x9c/0x170
[36470.792269]  [<ffffffff80213d8c>] call_softirq+0x1c/0x30
[36470.792273]  [<ffffffff80214ffd>] do_softirq+0x5d/0xa0
[36470.792277]  [<ffffffff8025684d>] irq_exit+0x8d/0xa0
[36470.792285]  [<ffffffff80227648>] smp_apic_timer_interrupt+0x88/0xc0
[36470.792289]  [<ffffffff80213668>] apic_timer_interrupt+0x88/0x90
[36470.792291]  <EOI>  [<ffffffff8022e856>] ? native_safe_halt+0x6/0x10
[36470.792301]  [<ffffffff8021a9fd>] ? default_idle+0x4d/0x50
[36470.792306]  [<ffffffff8021aa51>] ? c1e_idle+0x51/0x130
[36470.792313]  [<ffffffff806a18a5>] ? atomic_notifier_call_chain+0x15/0x20
[36470.792319]  [<ffffffff80210e85>] ? cpu_idle+0x65/0xc0
[36470.792324]  [<ffffffff80698f23>] ? start_secondary+0x9e/0xcb
[36470.792328] ---[ end trace e560456c3e40fa4b ]---
[36470.809119] r8169: eth0: link up


```

---

### Post by HeegeMcGee on 2009-04-28
Actually, i've got a Gigabyte MB, and i'm running ubuntu server 9.04. Forunately, it was stable all last night.

Using google to search the forums turned up [another topic]("http://ubuntuforums.org/showthread.php?t=1019775") that indicated using the Realtek proprietary drivers may resolve the issue. I meant to try that last night, but i tried leaving the house instead. 

This is not the first time i've had problems with Realtek drivers; i may stay with Intel from now on.

---

### Post by tomasch on 2009-05-05
Same problem here - running 9.04 server on an Asus eee Box
Was accessing a Samba share from a Mac to load some photos into iPhoto

lspci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

Error Log:
May  5 07:30:55 mango kernel: [338669.970148] ------------[ cut here ]------------
May  5 07:30:55 mango kernel: [338669.970162] WARNING: at /build/buildd/linux-2.6.28/net/sched/sch_generic.c:226 dev_watchdog+0x219/0x230()
May  5 07:30:55 mango kernel: [338669.970174] NETDEV WATCHDOG: eth0 (r8169): transmit timed out
May  5 07:30:55 mango kernel: [338669.970182] Modules linked in: sha1_generic arc4 ecb ppp_mppe ppp_async crc_ccitt ppdev input_polldev lp parport snd_hda_intel iTCO_wdt iTCO_vendor_support snd_pcm snd_timer intel_agp psmouse snd agpgart serio_raw pcspkr video soundcore rt2860sta(C) eeepc_laptop snd_page_alloc output usb_storage r8169 mii fbcon tileblit font bitblit softcursor
May  5 07:30:55 mango kernel: [338669.970290] Pid: 0, comm: swapper Tainted: G         C 2.6.28-11-server #42-Ubuntu
May  5 07:30:55 mango kernel: [338669.970300] Call Trace:
May  5 07:30:55 mango kernel: [338669.970318]  [<c01411d0>] warn_slowpath+0x60/0x80
May  5 07:30:55 mango kernel: [338669.970335]  [<c0138a4d>] ? find_busiest_group+0x15d/0x7e0
May  5 07:30:55 mango kernel: [338669.970350]  [<c0133e6c>] ? enqueue_entity+0x13c/0x360
May  5 07:30:55 mango kernel: [338669.970367]  [<c015e4a3>] ? getnstimeofday+0x53/0x110
May  5 07:30:55 mango kernel: [338669.970381]  [<c02d379d>] ? strlcpy+0x1d/0x60
May  5 07:30:55 mango kernel: [338669.970394]  [<c043f5f2>] ? netdev_drivername+0x32/0x40
May  5 07:30:55 mango kernel: [338669.970408]  [<c0453c59>] dev_watchdog+0x219/0x230
May  5 07:30:55 mango kernel: [338669.970423]  [<c01596ea>] ? hrtimer_forward+0x12a/0x170
May  5 07:30:55 mango kernel: [338669.970436]  [<c015e4a3>] ? getnstimeofday+0x53/0x110
May  5 07:30:55 mango kernel: [338669.970449]  [<c011f2f3>] ? lapic_next_event+0x13/0x20
May  5 07:30:55 mango kernel: [338669.970463]  [<c01616c8>] ? clockevents_program_event+0x98/0x150
May  5 07:30:55 mango kernel: [338669.970477]  [<c014b6d0>] run_timer_softirq+0x130/0x200
May  5 07:30:55 mango kernel: [338669.970491]  [<c0453a40>] ? dev_watchdog+0x0/0x230
May  5 07:30:55 mango kernel: [338669.970504]  [<c0453a40>] ? dev_watchdog+0x0/0x230
May  5 07:30:55 mango kernel: [338669.970518]  [<c01467d7>] __do_softirq+0x97/0x170
May  5 07:30:55 mango kernel: [338669.970529]  [<c015a876>] ? hrtimer_interrupt+0x186/0x1b0
May  5 07:30:55 mango kernel: [338669.970543]  [<c015a6c9>] ? ktime_get+0x19/0x40
May  5 07:30:55 mango kernel: [338669.970556]  [<c014690d>] do_softirq+0x5d/0x60
May  5 07:30:55 mango kernel: [338669.970568]  [<c0146a85>] irq_exit+0x55/0x90
May  5 07:30:55 mango kernel: [338669.970581]  [<c011f8fb>] smp_apic_timer_interrupt+0x5b/0x90
May  5 07:30:55 mango kernel: [338669.970595]  [<c010ac2c>] apic_timer_interrupt+0x28/0x30
May  5 07:30:55 mango kernel: [338669.970610]  [<c0189230>] ? rcu_pending+0xd0/0x100
May  5 07:30:55 mango kernel: [338669.970624]  [<c0108866>] cpu_idle+0x86/0xd0
May  5 07:30:55 mango kernel: [338669.970637]  [<c050bc9e>] start_secondary+0xbe/0xf0
May  5 07:30:55 mango kernel: [338669.970647] ---[ end trace e16da4dd0a7ad0d8 ]---

---

### Post by wintrmute on 2009-05-09
Hi,
I'm hitting this bug a lot too at the moment. :(

It seems to occur whenever I try to transfer a large file from the machine to another; ie. heavy network load.

It's completely fine otherwise.

Any suggestions for a fix yet?

---

### Post by Hugolp on 2009-05-18
I am having the same proble. As well only with heavy load.

This is the official launchpad bug. Please leave a comment so the mantainers realize its a problem hitting a lot of people: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/76489]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/76489")

Hugo

---

### Post by Hugolp on 2009-05-18
Btw, my realtek card that is failing is 1Gb/s and was connected to a 1 Gb/s switch when it was failing. My router has only 100Mb/s connection. When connected to the router it doesnt seem to be failing, probably because its reduced to 1/10 of the speed, so it doesnt get heavy load.

Hope this help someone else as temporal solution.

---

### Post by t413 on 2009-06-05
I'm having trouble as well, network goes down seemingly randomly sometimes when I'm transferring large files. I found two somewhat helpful pages: 

[https://bugzilla.redhat.com/show_bug.cgi?id=436841]("https://bugzilla.redhat.com/show_bug.cgi?id=436841")
[http://graag.blogspot.com/2007/12/netdev-watchdog-eth0-transmit-timed-out.html]("http://graag.blogspot.com/2007/12/netdev-watchdog-eth0-transmit-timed-out.html")

I have this problem with my server and it's quite an inconvenience to fix. I wrote a simple shell script to check if the network is up and restart it if it isn't. Absolutely a major problem.

---

### Post by p0rnflake on 2009-06-09
I'm seeing the same problems with 9.04 and the same realtek r8169 NIC :(

Occurs under heavy network load (1 Gbit link)

---

### Post by Huufarted on 2009-07-18
I'm now following this thread as I'm seeing the exact same thing.

noapic doesn't work for me.

---

