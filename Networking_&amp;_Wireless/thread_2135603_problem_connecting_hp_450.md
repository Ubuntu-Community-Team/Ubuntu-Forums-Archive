---
title: "problem connecting: hp 450"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by jcasanov on 2013-04-14
Hi everyone,

I just installed ubuntu 12.04 to an hp 450 laptop. 

lshw says this about the wireless card: BCM4313 802.11b/g/n Wireless LAN Controller and about the configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.204.108 latency=0 multicast=yes wireless=IEEE 802.11abg resources: irq:16 memoria:52500000-52503fff

As you can see it's connected to the network (so, i know the card is recognized, configured and working)

Now, when i move the laptop to another site it cannot connect to the network there. The router see the laptop and the client dhcp lists says an ip was assigned. But the negotiaton always fails.

Any ideas about how i can check what's going wrong?

PS: in that second site (where the laptop's final location will be) the wireless is hidden and protected by a password (using WPA/WPA2 personal). it's similar where i'm connected right now
Any additional info i should supply?

Thanks in advance

--
Jaime Casanova

---

### Post by sev1 on 2013-04-15
Step one should be to enable SSID broadcast at site #2. There is no benefit to disabling (hiding) it, as it can be easily discovered using several free wireless monitoring tools.

The laptop presumably connects to routers/APs which broadcast their SSIDs?

---

### Post by jcasanov on 2013-04-15
> **sev1 said:**
> Step one should be to enable SSID broadcast at site #2. There is no benefit to disabling (hiding) it, as it can be easily discovered using several free wireless monitoring tools.

The laptop presumably connects to routers/APs which broadcast their SSIDs?

I haven't tried enabling SSID broadcast yet, will do.

But i'm not seeing why i would need to do that, nor that "there is no benefit" by that logic will open the network entirely because there are free crackers that will give the password easily anyway

--
Jaime Casanova

---

### Post by jcasanov on 2013-04-18
> **sev1 said:**
> Step one should be to enable SSID broadcast at site #2. There is no benefit to disabling (hiding) it, as it can be easily discovered using several free wireless monitoring tools.

The laptop presumably connects to routers/APs which broadcast their SSIDs?

Ok, i enabled SSID broadcast, and eventually even dropped the security entirely with the same results. I'm attaching part of the messages in syslog also i'm pasting here a kernel failure i got:

Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081842] ------------[ cut here ]------------
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081862] WARNING: at /build/buildd/linux-lts-quantal-3.5.0/net/wireless/scan.c:594 copy_hidden_ies.isra.12+0x7c/0x80 [cfg80211]()
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081863] Hardware name: HP 450 Notebook PC
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081864] Modules linked in: hid_generic usbhid hid michael_mic arc4 rfcomm bnep parport_pc ppdev nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek coretemp kvm snd_hda_intel snd_hda_codec ghash_clmulni_intel lib80211_crypt_tkip snd_hwdep wl(PO) uvcvideo videobuf2_core videodev videobuf2_vmalloc btusb videobuf2_memops snd_pcm bluetooth cryptd snd_seq_midi snd_rawmidi snd_seq_midi_event joydev snd_seq cfg80211 snd_timer snd_seq_device microcode lib80211 snd soundcore snd_page_alloc i915 drm_kms_helper drm psmouse mei i2c_algo_bit video lpc_ich serio_raw rtsx_pci_ms hp_wmi sparse_keymap mac_hid wmi memstick lp parport rtsx_pci_sdmmc r8169 ahci libahci rtsx_pci
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081903] Pid: 730, comm: wl_event_handle Tainted: P        W  O 3.5.0-27-generic #46~precise1-Ubuntu
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081905] Call Trace:
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081911]  [<ffffffff81052c8f>] warn_slowpath_common+0x7f/0xc0
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081914]  [<ffffffff81052cea>] warn_slowpath_null+0x1a/0x20
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081920]  [<ffffffffa020905c>] copy_hidden_ies.isra.12+0x7c/0x80 [cfg80211]
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081927]  [<ffffffffa0209c3b>] cfg80211_bss_update+0x33b/0x430 [cfg80211]
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081933]  [<ffffffffa020aecd>] ? cfg80211_inform_bss_frame+0x8d/0x220 [cfg80211]
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081939]  [<ffffffffa020af71>] cfg80211_inform_bss_frame+0x131/0x220 [cfg80211]
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081964]  [<ffffffffa03f96f7>] wl_inform_single_bss+0x1d7/0x3f0 [wl]
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.081984]  [<ffffffffa03fa2e9>] wl_notify_scan_status+0x289/0x340 [wl]
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.082003]  [<ffffffffa03f9305>] wl_event_handler+0x55/0x1e0 [wl]
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.082023]  [<ffffffffa03f92b0>] ? wl_deinit_priv_mem+0xa0/0xa0 [wl]
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.082026]  [<ffffffff81077ce3>] kthread+0x93/0xa0
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.082030]  [<ffffffff816a5de4>] kernel_thread_helper+0x4/0x10
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.082033]  [<ffffffff81077c50>] ? flush_kthread_worker+0xb0/0xb0
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.082036]  [<ffffffff816a5de0>] ? gs_change+0x13/0x13
Apr 17 17:31:12 cindy-HP-450-Notebook-PC kernel: [ 3446.082038] ---[ end trace 90a0f0a543efdd35 ]---

---

