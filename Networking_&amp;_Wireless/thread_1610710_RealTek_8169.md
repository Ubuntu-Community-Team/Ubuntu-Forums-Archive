---
title: "RealTek 8169"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by bibble235 on 2010-11-01
Seen a pile of posts on this but thought I would log my own experience with this chipset.

I cannot get this network card, a surecom EP-320G-TX1 to work at all when plugged into a gigabyte switch using a cat6 cable.

I have tried,

The original driver for 10.04
The 6.something .14 (this causing the machine not to start)
The 6.something .13 machine does start but the network card does not work

Tried different kernels, the original boot disc.
Turn power off for fifteen seconds (I think this suggestion was to get the card to be recognised. Mine is, light does come on)

Used DHCP and none DCHP

Tried pre-up ethtool -s eth0 speed 1000 duplex full autoneg off with modules that support this.

Got two machines one on 64-bit and one on 32-bit server and both does not work with this card.

Put the cable in a PS3 to check it works and it does.

Seoond 100Mbps NIC works fine to the gigabyte switch

Tried 8168 driver but not recognised for my chip.

ethtool does say if support 1000Mbps and lspic reports it is a RealTek 8169S-32 chip.

Now some logs

Here is what happens with DHCP

ifup eth1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/00:02:44:9f:66:93
Sending on   LPF/eth1/00:02:44:9f:66:93
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ssh stop/waiting

And the syslog

Nov  1 19:28:44 iwiseman-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Nov  1 19:28:44 iwiseman-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Nov  1 19:28:44 iwiseman-desktop dhclient: All rights reserved.
Nov  1 19:28:44 iwiseman-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Nov  1 19:28:44 iwiseman-desktop dhclient:
Nov  1 19:28:46 iwiseman-desktop kernel: [  227.690028] r8169: eth1: link up
Nov  1 19:28:46 iwiseman-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 1)
Nov  1 19:28:46 iwiseman-desktop dhclient: Listening on LPF/eth1/00:02:44:9f:66:93
Nov  1 19:28:46 iwiseman-desktop dhclient: Sending on   LPF/eth1/00:02:44:9f:66:93
Nov  1 19:28:46 iwiseman-desktop dhclient: Sending on   Socket/fallback
Nov  1 19:28:47 iwiseman-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov  1 19:28:48 iwiseman-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov  1 19:28:51 iwiseman-desktop dhclient: No DHCPOFFERS received.
Nov  1 19:28:51 iwiseman-desktop dhclient: No working leases in persistent database - sleeping.
Nov  1 19:28:51 iwiseman-desktop avahi-autoipd(eth1)[2712]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 110).
Nov  1 19:28:51 iwiseman-desktop avahi-autoipd(eth1)[2712]: Successfully called chroot().
Nov  1 19:28:51 iwiseman-desktop avahi-autoipd(eth1)[2712]: Successfully dropped root privileges.
Nov  1 19:28:51 iwiseman-desktop avahi-autoipd(eth1)[2712]: Starting with address 169.254.7.223
Nov  1 19:28:52 iwiseman-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Nov  1 19:28:56 iwiseman-desktop avahi-autoipd(eth1)[2712]: Callout BIND, address 169.254.7.223 on interface eth1
Nov  1 19:28:56 iwiseman-desktop kernel: [  238.510010] eth1: no IPv6 routers present
Nov  1 19:29:00 iwiseman-desktop avahi-autoipd(eth1)[2712]: Successfully claimed IP address 169.254.7.223
Nov  1 19:29:00 iwiseman-desktop init: ssh main process (2609) terminated with status 255
Nov  1 19:29:02 iwiseman-desktop ntpdate[2778]: adjust time server 91.189.94.4 offset 0.013053 sec
Nov  1 19:29:03 iwiseman-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Nov  1 19:29:18 iwiseman-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Nov  1 19:29:37 iwiseman-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Nov  1 19:29:49 iwiseman-desktop dhclient: No DHCPOFFERS received.
Nov  1 19:29:49 iwiseman-desktop dhclient: No working leases in persistent database - sleeping.
Nov  1 19:29:49 iwiseman-desktop init: ssh main process (2786) terminated with status 255
Nov  1 19:29:50 iwiseman-desktop ntpdate[2883]: adjust time server 91.189.94.4 offset 0.001876 sec
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040011] ------------[ cut here ]------------
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040026] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x262/0x270()
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040030] Hardware name: System Product Name
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040034] NETDEV WATCHDOG: eth1 (r8169): transmit queue 0 timed out
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040037] Modules linked in: dvb_bt8xx dvb_core bt878 bttv v4l2_common ir_common videobuf_dma_sg videobuf_core btcx_risc tveeprom binfmt_misc nouveau ttm drm_kms_helper drm i2c_algo_bit snd_hda_codec_realtek snd_usb_audio snd_hda_intel snd_usb_lib snd_hda_codec snd_hwdep snd_seq_dummy snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq uvcvideo fbcon tileblit snd_timer snd_seq_device videodev snd font v4l1_compat bitblit soundcore v4l2_compat_ioctl32 usbhid asus_atk0110 softcursor nvidia(P) vga16fb vgastate snd_page_alloc atl2 hid ppdev parport_pc intel_agp lp parport floppy r8169 mii
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040119] Pid: 0, comm: swapper Tainted: P           2.6.32-24-generic #43-Ubuntu
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040124] Call Trace:
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040127]  <IRQ>  [<ffffffff81066ddb>] warn_slowpath_common+0x7b/0xc0
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040140]  [<ffffffff81066e81>] warn_slowpath_fmt+0x41/0x50
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040146]  [<ffffffff814796f2>] dev_watchdog+0x262/0x270
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040153]  [<ffffffff81080bf7>] ? insert_work+0x77/0xc0
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040160]  [<ffffffff810397a9>] ? default_spin_lock_flags+0x9/0x10
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040166]  [<ffffffff81479490>] ? dev_watchdog+0x0/0x270
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040172]  [<ffffffff8107778b>] run_timer_softirq+0x19b/0x340
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040179]  [<ffffffff81094ae0>] ? tick_sched_timer+0x0/0xc0
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040185]  [<ffffffff8108f743>] ? ktime_get+0x63/0xe0
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040191]  [<ffffffff8106e487>] __do_softirq+0xb7/0x1e0
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040197]  [<ffffffff810946ca>] ? tick_program_event+0x2a/0x30
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040203]  [<ffffffff810142ec>] call_softirq+0x1c/0x30
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040208]  [<ffffffff81015cb5>] do_softirq+0x65/0xa0
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040213]  [<ffffffff8106e325>] irq_exit+0x85/0x90
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040219]  [<ffffffff81549591>] smp_apic_timer_interrupt+0x71/0x9c
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040225]  [<ffffffff81013cb3>] apic_timer_interrupt+0x13/0x20
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040228]  <EOI>  [<ffffffff8101b5a1>] ? mwait_idle+0x71/0xd0
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040239]  [<ffffffff8154712a>] ? atomic_notifier_call_chain+0x1a/0x20
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040245]  [<ffffffff81011e73>] ? cpu_idle+0xb3/0x110
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040251]  [<ffffffff8152f29b>] ? rest_init+0x6b/0x80
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040258]  [<ffffffff8184ddcc>] ? start_kernel+0x368/0x371
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040263]  [<ffffffff8184d33a>] ? x86_64_start_reservations+0x125/0x129
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040269]  [<ffffffff8184d438>] ? x86_64_start_kernel+0xfa/0x109
Nov  1 19:29:52 iwiseman-desktop kernel: [  294.040273] ---[ end trace c337060a269db474 ]---

And the lspci

01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Surecom Technology Device 3202
        Flags: 66MHz, medium devsel, IRQ 21
        I/O ports at b800 [disabled] [size=256]
        [virtual] Memory at dbeffc00 (32-bit, non-prefetchable) [disabled] [size=256]
        Expansion ROM at 80400000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2
        Kernel driver in use: r8169
        Kernel modules: r8169

uname -a
Linux iwiseman-desktop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

For this test I used module

filename:       /lib/modules/2.6.32-24-generic/kernel/drivers/net/r8169.ko
version:        2.3LK-NAPI
license:        GPL
description:    RealTek RTL-8169 Gigabit Ethernet driver
author:         Realtek and the Linux r8169 crew <netdev@vger.kernel.org>
srcversion:     D37E06388C6313C1D062CC3
alias:          pci:v00000001d00008168sv*sd00002410bc*sc*i*
alias:          pci:v00001737d00001032sv*sd00000024bc*sc*i*
alias:          pci:v000016ECd00000116sv*sd*bc*sc*i*
alias:          pci:v00001259d0000C107sv*sd*bc*sc*i*
alias:          pci:v00001186d00004300sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008169sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008167sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008136sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008129sv*sd*bc*sc*i*
depends:        mii
vermagic:       2.6.32-24-generic SMP mod_unload modversions
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)

For other attempts I used

filename:       /lib/modules/2.6.32-25-generic/kernel/drivers/net/r8169.ko
version:        6.013.00-NAPI
license:        GPL
description:    RealTek RTL-8169 Gigabit Ethernet driver
author:         Realtek and the Linux r8169 crew <netdev@vger.kernel.org>
srcversion:     E4F620EFDC400F50E5C22A5
alias:          pci:v000010ECd00008169sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008167sv*sd*bc*sc*i*
depends:
vermagic:       2.6.32-25-generic SMP mod_unload modversions
parm:           speed:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           duplex:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           autoneg:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)

Windows will find the card but will only start it a 100Mbps.

---

