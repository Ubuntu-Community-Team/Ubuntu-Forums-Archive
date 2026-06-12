---
title: "Temperamental Wired Network Card"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by BLaZuRE on 2012-04-24
So, I've been trying for hours to locate the source of my problem by booting in and out of Linux into Windows searching the Internet for the root of my problem.  Let me tell you, that's not fun.

I've tried Ubuntu, Kubuntu, and Mint to no avail.  Webpages fluctuate between unreachable, slow to load (15 seconds? .... gosh I think dialup was faster), and acting like it's going to load but times out.

Here is some of the output via troubleshooting my Realtek RTL8111/8168B:

     
     ```
$ sudo lspci -v
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at ee00 [size=256]
    Memory at fbdff000 (64-bit, prefetchable) [size=4K]
    Memory at fbdf8000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number *Some number that's probably the serial number*
    Kernel driver in use: r8169
    Kernel modules: r8169

```      
     ```
$ lspci -nn | grep -iA2 net
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
``````

     $ ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:c2:16:e2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fec2:16e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24064 errors:0 dropped:24064 overruns:0 frame:24064
          TX packets:17314 errors:0 dropped:73 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28162741 (28.1 MB)  TX bytes:1772726 (1.7 MB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20969 (20.9 KB)  TX bytes:20969 (20.9 KB)
```     ```
$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
snd_hda_intel          33390  2 
i2c_algo_bit           13423  1 i915
joydev                 17693  0 
mxm_wmi                12979  0 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
wmi                    19256  1 mxm_wmi
lp                     17799  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                46562  3 parport_pc,ppdev,lp
soundcore              12680  1 snd
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
xhci_hcd               78641  0 
```     ```
$ dmesg

[ 1003.906955] r8169 0000:06:00.0: eth0: link up
[ 1007.899545] r8169 0000:06:00.0: eth0: link up
[ 1012.167346] r8169 0000:06:00.0: eth0: link up
[ 1015.856802] r8169 0000:06:00.0: eth0: link up
[ 1019.586132] r8169 0000:06:00.0: eth0: link up
[ 1023.510904] r8169 0000:06:00.0: eth0: link up
[ 1027.503486] r8169 0000:06:00.0: eth0: link up
[ 1031.244784] r8169 0000:06:00.0: eth0: link up
[ 1344.173964] r8169 0000:06:00.0: eth0: link up
[ 1385.990394] r8169 0000:06:00.0: eth0: link up
[ 1849.692404] r8169 0000:06:00.0: eth0: link up
[ 1862.675299] r8169 0000:06:00.0: eth0: link up
[ 1875.869552] r8169 0000:06:00.0: eth0: link up
[ 1927.765174] r8169 0000:06:00.0: eth0: link up
[ 1934.250617] r8169 0000:06:00.0: eth0: link up
[ 2008.302876] r8169 0000:06:00.0: eth0: link up
[ 2421.070454] ------------[ cut here ]------------
[ 2421.070463] WARNING: at /build/buildd/linux-3.0.0/net/sched/sch_generic.c:255 dev_watchdog+0x25a/0x270()
[ 2421.070466] Hardware name: Z68X-UD3H-B3
[ 2421.070468] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
[ 2421.070470] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev binfmt_misc snd_hda_codec_hdmi snd_hda_codec_realtek i915 drm_kms_helper drm snd_hda_intel i2c_algo_bit joydev mxm_wmi snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer wmi lp snd_seq_device mei(C) snd parport soundcore video snd_page_alloc usbhid hid firewire_ohci firewire_core crc_itu_t r8169 xhci_hcd
[ 2421.070505] Pid: 0, comm: kworker/0:1 Tainted: G         C  3.0.0-12-generic #20-Ubuntu
[ 2421.070508] Call Trace:
[ 2421.070510]  <IRQ>  [<ffffffff8105e83f>] warn_slowpath_common+0x7f/0xc0
[ 2421.070520]  [<ffffffff8105e936>] warn_slowpath_fmt+0x46/0x50
[ 2421.070525]  [<ffffffff814f6afa>] dev_watchdog+0x25a/0x270
[ 2421.070530]  [<ffffffff81011593>] ? native_sched_clock+0x13/0x60
[ 2421.070536]  [<ffffffff8107a270>] ? __queue_work+0x320/0x320
[ 2421.070539]  [<ffffffff814f68a0>] ? qdisc_reset+0x50/0x50
[ 2421.070542]  [<ffffffff814f68a0>] ? qdisc_reset+0x50/0x50
[ 2421.070547]  [<ffffffff8106d596>] call_timer_fn+0x46/0x160
[ 2421.070551]  [<ffffffff8106e64c>] ? cascade+0x7c/0xa0
[ 2421.070554]  [<ffffffff814f68a0>] ? qdisc_reset+0x50/0x50
[ 2421.070558]  [<ffffffff8106eec2>] run_timer_softirq+0x132/0x2a0
[ 2421.070563]  [<ffffffff81026d5d>] ? lapic_next_event+0x1d/0x30
[ 2421.070566]  [<ffffffff81065f58>] __do_softirq+0xa8/0x210
[ 2421.070571]  [<ffffffff8109388f>] ? tick_program_event+0x1f/0x30
[ 2421.070576]  [<ffffffff815f34dc>] call_softirq+0x1c/0x30
[ 2421.070579]  [<ffffffff8100c2d5>] do_softirq+0x65/0xa0
[ 2421.070582]  [<ffffffff8106633e>] irq_exit+0x8e/0xb0
[ 2421.070586]  [<ffffffff815f3e1e>] smp_apic_timer_interrupt+0x6e/0x99
[ 2421.070590]  [<ffffffff815f2c93>] apic_timer_interrupt+0x13/0x20
[ 2421.070592]  <EOI>  [<ffffffff813496cb>] ? intel_idle+0xcb/0x120
[ 2421.070600]  [<ffffffff813496ad>] ? intel_idle+0xad/0x120
[ 2421.070605]  [<ffffffff814ab062>] cpuidle_idle_call+0xa2/0x1d0
[ 2421.070611]  [<ffffffff8100920b>] cpu_idle+0xab/0x100
[ 2421.070615]  [<ffffffff815cc2a6>] start_secondary+0xd9/0xdb
[ 2421.070618] ---[ end trace 6810ca0c9d27d7b6 ]---
[ 2421.086526] r8169 0000:06:00.0: eth0: link up
[ 2425.928644] r8169 0000:06:00.0: eth0: link up
```

---

### Post by BLaZuRE on 2012-04-28
I switched to the r8168 driver I found and it works now.

---

