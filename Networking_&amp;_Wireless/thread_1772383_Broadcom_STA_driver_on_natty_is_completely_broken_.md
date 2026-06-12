---
title: "Broadcom STA driver on natty is completely broken for me"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by eantoranz on 2011-05-31
Hi!

Since sunday I've been using Broadcom's STA driver (from repositories) for my wireless card on Natty... it's completely unusable. The system always breaks after a while. The only thing that keeps the box from crashing is is I disable the card and use another medium to get connected to internet. Are there other people that have faced the same problem other than me? By the way, I had used the STA driver on Maverick and it didn't have problems.

PS Oh, and it the box doesn't freeze, then I have a module crash:

```

[ 1757.127398] divide error: 0000 [#1] SMP
[ 1757.127534] last sysfs file: /sys/devices/system/cpu/cpu1/cache/index2/shared_cpu_map
[ 1757.127757] Modules linked in: cryptd aes_i586 aes_generic nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack iptable_filter ip_tables x_tables rfcomm sco bnep l2cap parport_pc ppdev dm_crypt wl(P) lib80211 arc4 snd_hda_codec_realtek snd_hda_intel snd_hda_codec joydev snd_hwdep snd_pcm btusb snd_seq_midi bluetooth uvcvideo snd_rawmidi snd_seq_midi_event psmouse snd_seq videodev brcm80211(C) mac80211 serio_raw snd_timer snd_seq_device snd cfg80211 soundcore snd_page_alloc lp parport i915 ahci drm_kms_helper drm libahci sky2 i2c_algo_bit video
[ 1757.129388]
[ 1757.129439] Pid: 0, comm: swapper Tainted: P         C  2.6.38-8-generic #42-Ubuntu SAMSUNG ELECTRONICS CO., LTD. N150P/N210P/N220P          /N150P/N210P/N220P         
[ 1757.131284] EIP: 0060:[<f862c0fe>] EFLAGS: 00010246 CPU: 0
[ 1757.131284] EIP is at minstrel_ht_update_stats.clone.5+0x1fe/0x430 [mac80211]
[ 1757.145583] EAX: 0000006c EBX: 0000006c ECX: eec10050 EDX: 00000000
[ 1757.145583] ESI: 00000000 EDI: eec10068 EBP: f3c0bed4 ESP: f3c0be90
[ 1757.145583]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[ 1757.145583] Process swapper (pid: 0, ti=f3c0a000 task=c1731f60 task.ti=c172c000)
[ 1757.145583] Stack:
[ 1757.145583]  00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[ 1757.145583]  00004858 00000000 eec10000 eec10000 00000000 00000001 f075c800 eec10000
[ 1757.145583]  00000003 f3c0bf10 f862c744 00000001 f3c0bf20 00000000 00000001 ed980228
[ 1757.145583] Call Trace:
[ 1757.145583]  [<f862c744>] minstrel_ht_tx_status+0x414/0x4a0 [mac80211]
[ 1757.145583]  [<f8603538>] ieee80211_tx_status+0x1c8/0x880 [mac80211]
[ 1757.145583]  [<f8b4df6a>] ? wlc_bmac_txstatus+0xba/0x1a0 [brcm80211]
[ 1757.145583]  [<f8b11faa>] ? wlc_ps_check+0x2a/0x160 [brcm80211]
[ 1757.145583]  [<c14258a0>] ? skb_dequeue+0x50/0x70
[ 1757.145583]  [<f8602aa7>] ieee80211_tasklet_handler+0x97/0xc0 [mac80211]
[ 1757.145583]  [<c1509716>] ? _raw_spin_unlock_bh+0x16/0x20
[ 1757.145583]  [<f8b1f8a8>] ? wl_dpc+0x58/0xb0 [brcm80211]
[ 1757.145583]  [<c1055ee5>] tasklet_action+0x55/0xe0
[ 1757.145583]  [<c1056622>] __do_softirq+0x82/0x170
[ 1757.145583]  [<c10565a0>] ? __do_softirq+0x0/0x170
[ 1757.145583]  <IRQ>
[ 1757.145583]  [<c10567ed>] ? irq_exit+0x6d/0x80
[ 1757.145583]  [<c15107ab>] ? do_IRQ+0x4b/0xc0
[ 1757.145583]  [<c107cbca>] ? tick_notify+0x11a/0x1d0
[ 1757.145583]  [<c1003670>] ? common_interrupt+0x30/0x38
[ 1757.145583]  [<c105007b>] ? console_unlock+0xdb/0xe0
[ 1757.145583]  [<c12c2508>] ? intel_idle+0xb8/0x110
[ 1757.145583]  [<c14061fd>] ? cpuidle_idle_call+0x7d/0x160
[ 1757.145583]  [<c10019ca>] ? cpu_idle+0x8a/0xc0
[ 1757.145583]  [<c1038d2e>] ? complete+0x4e/0x60
[ 1757.145583]  [<c14f0d2d>] ? rest_init+0x5d/0x70
[ 1757.145583]  [<c178d7e1>] ? start_kernel+0x35f/0x366
[ 1757.145583]  [<c178d3d5>] ? pass_all_bootoptions+0x0/0xa
[ 1757.145583]  [<c178d0e0>] ? i386_start_kernel+0xe0/0xe8

```
Blah blah blah. Any ideas?

```
$ sudo lspci
[sudo] password for antoranz: 
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

```

---

### Post by SabreWolfy on 2011-06-17
I wasted a whole day trying to get my Broadcom B4311 to work under Kubuntu Natty. It has worked well under Lucid and Maverick Ubuntu by installing via the Additional/Restricted Drivers. In Kubuntu Natty, installing via the Additional Drivers did not work -- the installation completed by the wireless card was not detected. I installed fresh again and manually installed packages b43-fwcutter and firmware-b43-installer. Restarted. Still now wireless. Tried the Additional Drivers thing again. No wireless. Reinstalled and tried various other solutions involving source drivers and modprobe and recompling stuff. Also didn't work. Eventually gave up.

Got wireless working under Linux Mint 10 KDE (Additional Drivers I think) and Linux Mint Debian Edition (by installing the two b43 packages).

PS: A relative also recently tried FOSS/Linux/Ubuntu for the first time by installing Ubuntu Natty on his laptop. The wireless card (forget which it was now) does not work with Ubuntu at all. We searched and Googled and tried everything. There is some regression bug which prevents that particular wireless card from working in Natty. Some solutions involved source code this and recompile that. All useless to someone who is trying Linux for the first time and using the latest and greatest Natty version. Very disappointing! :(

---

