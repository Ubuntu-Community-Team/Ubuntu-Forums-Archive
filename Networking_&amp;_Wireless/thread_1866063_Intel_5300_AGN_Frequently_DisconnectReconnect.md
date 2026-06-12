---
title: "Intel 5300 AGN Frequently Disconnect/Reconnect"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by msmith0957 on 2011-10-20
Ubuntu x64 11.10, on Dell XPS Studio 1640

```
lspci | grep 5300
04:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
```


I am connecting to a Linksys Router (tomato firmware) with WPA TKIP active. I can connect fine, but the connection frequently goes offline and back online. This appears to occur randomly, and as often as every couple minutes.

I've done a lot of reading about this and most actual 'fixes' included removing wpa_supplicant and/or network  manager. I haven't attempted either yet, and wanted to get some advice first. Which, if any should I try first, and if removed, is there a working alternative (GUI) network manager I can use?

I should note, I dual-boot ubuntu w/ windows 7. On Windows the connection is strong, and rarely, if ever disconnects like it does on Ubuntu.

The following is probably what I will try first.. unless there is advice otherwise.

```
sudo apt-get purge network-manager network-manager-gnome
```

Any help is appreciated, thank you.

```
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
bnep                   18436  2 
joydev                 17693  0 
rfcomm                 47946  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
arc4                   12529  2 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_hdmi     32040  1 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
r852                   18277  0 
sm_common              16865  1 r852
nand                   54966  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
v4l2_compat_ioctl32    17083  1 videodev
mtd                    33181  2 sm_common,nand
iwlagn                314213  0 
snd_hda_codec_idt      70553  1 
fglrx                2929009  141 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              310872  1 iwlagn
psmouse                73882  0 
serio_raw              13166  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
cfg80211              199587  2 iwlagn,mac80211
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc6_decoder         12546  0 
soundcore              12680  1 snd
ir_rc5_decoder         12546  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rc_rc6_mce             12502  0 
ir_nec_decoder         12546  0 
wmi                    19256  1 dell_wmi
ite_cir                25775  0 
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ite_cir
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ahci                   26002  4 
libahci                26861  1 ahci
tg3                   147729  0 

```

```
[ 7460.868897] wlan0: deauthenticated from 00:12:17:ca:33:1d (Reason: 3)
[ 7460.912229] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 7460.912240] cfg80211: Restoring regulatory settings
[ 7460.912278] cfg80211: Calling CRDA to update world regulatory domain
[ 7460.920340] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 7460.920349] cfg80211: World regulatory domain updated:
[ 7460.920354] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7460.920362] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7460.920370] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7460.920377] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7460.920384] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7460.920391] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7464.277917] wlan0: authenticate with 00:12:17:ca:33:1d (try 1)
[ 7464.279746] wlan0: authenticated
[ 7479.535570] wlan0: authenticate with 00:12:17:ca:33:1d (try 1)
[ 7479.541054] wlan0: authenticated
[ 7479.543139] wlan0: associate with 00:12:17:ca:33:1d (try 1)
[ 7479.546923] wlan0: RX ReassocResp from 00:12:17:ca:33:1d (capab=0x431 status=0 aid=3)
[ 7479.546933] wlan0: associated
[ 7539.557466] ------------[ cut here ]------------
[ 7539.557515] WARNING: at /build/buildd/linux-3.0.0/net/mac80211/mlme.c:1412 ieee80211_rx_mgmt_disassoc+0xfa/0x100 [mac80211]()
[ 7539.557523] Hardware name: Studio XPS 1640
[ 7539.557527] Modules linked in: parport_pc ppdev vesafb bnep joydev rfcomm usbhid hid bluetooth binfmt_misc arc4 dell_wmi sparse_keymap snd_hda_codec_hdmi uvcvideo videodev dell_laptop dcdbas r852 sm_common nand nand_ids nand_bch bch nand_ecc v4l2_compat_ioctl32 mtd iwlagn snd_hda_codec_idt fglrx(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq mac80211 psmouse serio_raw snd_timer snd_seq_device ir_lirc_codec lirc_dev cfg80211 ir_sony_decoder ir_jvc_decoder snd ir_rc6_decoder soundcore ir_rc5_decoder snd_page_alloc rc_rc6_mce ir_nec_decoder wmi ite_cir rc_core video lp parport firewire_ohci firewire_core sdhci_pci sdhci crc_itu_t ahci libahci tg3
[ 7539.557647] Pid: 5014, comm: kworker/u:0 Tainted: P        W   3.0.0-12-generic #20-Ubuntu
[ 7539.557653] Call Trace:
[ 7539.557670]  [<ffffffff8105e83f>] warn_slowpath_common+0x7f/0xc0
[ 7539.557679]  [<ffffffff8105e89a>] warn_slowpath_null+0x1a/0x20
[ 7539.557703]  [<ffffffffa04206ea>] ieee80211_rx_mgmt_disassoc+0xfa/0x100 [mac80211]
[ 7539.557730]  [<ffffffffa04228ff>] ieee80211_sta_rx_queued_mgmt+0x2cf/0x350 [mac80211]
[ 7539.557756]  [<ffffffffa042629b>] ieee80211_iface_work+0x25b/0x350 [mac80211]
[ 7539.557782]  [<ffffffffa0426040>] ? ieee80211_teardown_sdata+0xe0/0xe0 [mac80211]
[ 7539.557793]  [<ffffffff8107c09a>] process_one_work+0x11a/0x480
[ 7539.557801]  [<ffffffff8107cd65>] worker_thread+0x165/0x370
[ 7539.557808]  [<ffffffff8107cc00>] ? manage_workers.isra.30+0x130/0x130
[ 7539.557817]  [<ffffffff8108120c>] kthread+0x8c/0xa0
[ 7539.557827]  [<ffffffff815f33e4>] kernel_thread_helper+0x4/0x10
[ 7539.557836]  [<ffffffff81081180>] ? flush_kthread_worker+0xa0/0xa0
[ 7539.557843]  [<ffffffff815f33e0>] ? gs_change+0x13/0x13
[ 7539.557849] ---[ end trace bd957c842999b36f ]---
[ 7539.557981] wlan0: deauthenticated from 00:12:17:ca:33:1d (Reason: 3)
[ 7539.592335] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 7539.592348] cfg80211: Restoring regulatory settings
[ 7539.592379] cfg80211: Calling CRDA to update world regulatory domain
[ 7539.600175] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 7539.600184] cfg80211: World regulatory domain updated:
[ 7539.600189] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7539.600197] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7539.600205] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7539.600212] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7539.600219] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7539.600226] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7542.920207] wlan0: authenticate with 00:12:17:ca:33:1d (try 1)
[ 7542.923158] wlan0: authenticated
[ 7542.925500] wlan0: associate with 00:12:17:ca:33:1d (try 1)
[ 7542.929522] wlan0: RX ReassocResp from 00:12:17:ca:33:1d (capab=0x431 status=0 aid=3)
[ 7542.929531] wlan0: associated
[ 7617.245151] ------------[ cut here ]------------
[ 7617.245200] WARNING: at /build/buildd/linux-3.0.0/net/mac80211/mlme.c:1412 ieee80211_rx_mgmt_disassoc+0xfa/0x100 [mac80211]()
[ 7617.245207] Hardware name: Studio XPS 1640
[ 7617.245211] Modules linked in: parport_pc ppdev vesafb bnep joydev rfcomm usbhid hid bluetooth binfmt_misc arc4 dell_wmi sparse_keymap snd_hda_codec_hdmi uvcvideo videodev dell_laptop dcdbas r852 sm_common nand nand_ids nand_bch bch nand_ecc v4l2_compat_ioctl32 mtd iwlagn snd_hda_codec_idt fglrx(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq mac80211 psmouse serio_raw snd_timer snd_seq_device ir_lirc_codec lirc_dev cfg80211 ir_sony_decoder ir_jvc_decoder snd ir_rc6_decoder soundcore ir_rc5_decoder snd_page_alloc rc_rc6_mce ir_nec_decoder wmi ite_cir rc_core video lp parport firewire_ohci firewire_core sdhci_pci sdhci crc_itu_t ahci libahci tg3
[ 7617.245331] Pid: 256, comm: kworker/u:4 Tainted: P        W   3.0.0-12-generic #20-Ubuntu
[ 7617.245337] Call Trace:
[ 7617.245353]  [<ffffffff8105e83f>] warn_slowpath_common+0x7f/0xc0
[ 7617.245362]  [<ffffffff8105e89a>] warn_slowpath_null+0x1a/0x20
[ 7617.245386]  [<ffffffffa04206ea>] ieee80211_rx_mgmt_disassoc+0xfa/0x100 [mac80211]
[ 7617.245412]  [<ffffffffa04228ff>] ieee80211_sta_rx_queued_mgmt+0x2cf/0x350 [mac80211]
[ 7617.245438]  [<ffffffffa042629b>] ieee80211_iface_work+0x25b/0x350 [mac80211]
[ 7617.245463]  [<ffffffffa0426040>] ? ieee80211_teardown_sdata+0xe0/0xe0 [mac80211]
[ 7617.245475]  [<ffffffff8107c09a>] process_one_work+0x11a/0x480
[ 7617.245482]  [<ffffffff8107cd65>] worker_thread+0x165/0x370
[ 7617.245490]  [<ffffffff8107cc00>] ? manage_workers.isra.30+0x130/0x130
[ 7617.245499]  [<ffffffff8108120c>] kthread+0x8c/0xa0
[ 7617.245509]  [<ffffffff815f33e4>] kernel_thread_helper+0x4/0x10
[ 7617.245517]  [<ffffffff81081180>] ? flush_kthread_worker+0xa0/0xa0
[ 7617.245525]  [<ffffffff815f33e0>] ? gs_change+0x13/0x13
[ 7617.245530] ---[ end trace bd957c842999b370 ]---
[ 7617.245667] wlan0: deauthenticated from 00:12:17:ca:33:1d (Reason: 3)
[ 7617.264762] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 7617.264773] cfg80211: Restoring regulatory settings
[ 7617.264798] cfg80211: Calling CRDA to update world regulatory domain
[ 7617.272490] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 7617.272499] cfg80211: World regulatory domain updated:
[ 7617.272504] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7617.272512] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7617.272520] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7617.272527] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7617.272534] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7617.272541] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7620.642458] wlan0: authenticate with 00:12:17:ca:33:1d (try 1)
[ 7620.674740] wlan0: authenticated
[ 7620.676814] wlan0: associate with 00:12:17:ca:33:1d (try 1)
[ 7620.680384] wlan0: RX ReassocResp from 00:12:17:ca:33:1d (capab=0x431 status=0 aid=3)
[ 7620.680392] wlan0: associated
[ 7695.933011] ------------[ cut here ]------------
[ 7695.933039] WARNING: at /build/buildd/linux-3.0.0/net/mac80211/mlme.c:1412 ieee80211_rx_mgmt_disassoc+0xfa/0x100 [mac80211]()
[ 7695.933041] Hardware name: Studio XPS 1640
[ 7695.933042] Modules linked in: parport_pc ppdev vesafb bnep joydev rfcomm usbhid hid bluetooth binfmt_misc arc4 dell_wmi sparse_keymap snd_hda_codec_hdmi uvcvideo videodev dell_laptop dcdbas r852 sm_common nand nand_ids nand_bch bch nand_ecc v4l2_compat_ioctl32 mtd iwlagn snd_hda_codec_idt fglrx(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq mac80211 psmouse serio_raw snd_timer snd_seq_device ir_lirc_codec lirc_dev cfg80211 ir_sony_decoder ir_jvc_decoder snd ir_rc6_decoder soundcore ir_rc5_decoder snd_page_alloc rc_rc6_mce ir_nec_decoder wmi ite_cir rc_core video lp parport firewire_ohci firewire_core sdhci_pci sdhci crc_itu_t ahci libahci tg3
[ 7695.933082] Pid: 5014, comm: kworker/u:0 Tainted: P        W   3.0.0-12-generic #20-Ubuntu
[ 7695.933085] Call Trace:
[ 7695.933092]  [<ffffffff8105e83f>] warn_slowpath_common+0x7f/0xc0
[ 7695.933095]  [<ffffffff8105e89a>] warn_slowpath_null+0x1a/0x20
[ 7695.933102]  [<ffffffffa04206ea>] ieee80211_rx_mgmt_disassoc+0xfa/0x100 [mac80211]
[ 7695.933110]  [<ffffffffa04228ff>] ieee80211_sta_rx_queued_mgmt+0x2cf/0x350 [mac80211]
[ 7695.933118]  [<ffffffffa042629b>] ieee80211_iface_work+0x25b/0x350 [mac80211]
[ 7695.933126]  [<ffffffffa0426040>] ? ieee80211_teardown_sdata+0xe0/0xe0 [mac80211]
[ 7695.933130]  [<ffffffff8107c09a>] process_one_work+0x11a/0x480
[ 7695.933132]  [<ffffffff8107cd65>] worker_thread+0x165/0x370
[ 7695.933135]  [<ffffffff8107cc00>] ? manage_workers.isra.30+0x130/0x130
[ 7695.933138]  [<ffffffff8108120c>] kthread+0x8c/0xa0
[ 7695.933141]  [<ffffffff815f33e4>] kernel_thread_helper+0x4/0x10
[ 7695.933144]  [<ffffffff81081180>] ? flush_kthread_worker+0xa0/0xa0
[ 7695.933146]  [<ffffffff815f33e0>] ? gs_change+0x13/0x13
[ 7695.933148] ---[ end trace bd957c842999b371 ]---
[ 7695.933422] wlan0: deauthenticated from 00:12:17:ca:33:1d (Reason: 3)
[ 7695.996191] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 7695.996197] cfg80211: Restoring regulatory settings
[ 7695.996201] cfg80211: Calling CRDA to update world regulatory domain
[ 7695.999069] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 7695.999071] cfg80211: World regulatory domain updated:
[ 7695.999073] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7695.999075] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7695.999078] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7695.999080] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7695.999082] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7695.999084] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7699.386310] wlan0: authenticate with 00:12:17:ca:33:1d (try 1)
[ 7699.388337] wlan0: authenticated
[ 7699.392343] wlan0: associate with 00:12:17:ca:33:1d (try 1)
[ 7699.396139] wlan0: RX ReassocResp from 00:12:17:ca:33:1d (capab=0x431 status=0 aid=3)
[ 7699.396147] wlan0: associated
[ 7773.920784] ------------[ cut here ]------------
[ 7773.920816] WARNING: at /build/buildd/linux-3.0.0/net/mac80211/mlme.c:1412 ieee80211_rx_mgmt_disassoc+0xfa/0x100 [mac80211]()
[ 7773.920818] Hardware name: Studio XPS 1640
[ 7773.920820] Modules linked in: parport_pc ppdev vesafb bnep joydev rfcomm usbhid hid bluetooth binfmt_misc arc4 dell_wmi sparse_keymap snd_hda_codec_hdmi uvcvideo videodev dell_laptop dcdbas r852 sm_common nand nand_ids nand_bch bch nand_ecc v4l2_compat_ioctl32 mtd iwlagn snd_hda_codec_idt fglrx(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq mac80211 psmouse serio_raw snd_timer snd_seq_device ir_lirc_codec lirc_dev cfg80211 ir_sony_decoder ir_jvc_decoder snd ir_rc6_decoder soundcore ir_rc5_decoder snd_page_alloc rc_rc6_mce ir_nec_decoder wmi ite_cir rc_core video lp parport firewire_ohci firewire_core sdhci_pci sdhci crc_itu_t ahci libahci tg3
[ 7773.920861] Pid: 256, comm: kworker/u:4 Tainted: P        W   3.0.0-12-generic #20-Ubuntu
[ 7773.920864] Call Trace:
[ 7773.920871]  [<ffffffff8105e83f>] warn_slowpath_common+0x7f/0xc0
[ 7773.920874]  [<ffffffff8105e89a>] warn_slowpath_null+0x1a/0x20
[ 7773.920882]  [<ffffffffa04206ea>] ieee80211_rx_mgmt_disassoc+0xfa/0x100 [mac80211]
[ 7773.920890]  [<ffffffffa04228ff>] ieee80211_sta_rx_queued_mgmt+0x2cf/0x350 [mac80211]
[ 7773.920898]  [<ffffffffa042629b>] ieee80211_iface_work+0x25b/0x350 [mac80211]
[ 7773.920906]  [<ffffffffa0426040>] ? ieee80211_teardown_sdata+0xe0/0xe0 [mac80211]
[ 7773.920910]  [<ffffffff8107c09a>] process_one_work+0x11a/0x480
[ 7773.920913]  [<ffffffff8107cd65>] worker_thread+0x165/0x370
[ 7773.920915]  [<ffffffff8107cc00>] ? manage_workers.isra.30+0x130/0x130
[ 7773.920918]  [<ffffffff8108120c>] kthread+0x8c/0xa0
[ 7773.920922]  [<ffffffff815f33e4>] kernel_thread_helper+0x4/0x10
[ 7773.920925]  [<ffffffff81081180>] ? flush_kthread_worker+0xa0/0xa0
[ 7773.920927]  [<ffffffff815f33e0>] ? gs_change+0x13/0x13
[ 7773.920929] ---[ end trace bd957c842999b372 ]---
[ 7773.921339] wlan0: deauthenticated from 00:12:17:ca:33:1d (Reason: 3)
[ 7773.968208] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 7773.968214] cfg80211: Restoring regulatory settings
[ 7773.968217] cfg80211: Calling CRDA to update world regulatory domain
[ 7773.971633] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 7773.971638] cfg80211: World regulatory domain updated:
[ 7773.971640] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7773.971643] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7773.971646] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7773.971648] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7773.971651] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7773.971654] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7777.210262] wlan0: authenticate with 00:12:17:ca:33:1d (try 1)
[ 7777.212151] wlan0: authenticated
[ 7777.214635] wlan0: associate with 00:12:17:ca:33:1d (try 1)
[ 7777.217220] wlan0: RX ReassocResp from 00:12:17:ca:33:1d (capab=0x431 status=0 aid=3)
[ 7777.217225] wlan0: associated
```

---

### Post by karmada on 2011-10-21
i did just that and installed WICD

---

### Post by varunendra on 2011-10-21
> **msmith0957 said:**
> ```
lspci | grep 5300
04:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
```......the connection frequently goes offline and back online....
```
Module                  Size  Used by
....
iwlagn                314213  0 
....

```
You may not need to change your network manager. The problem may be related to this one: [http://ubuntuforums.org/showthread.php?p=11360822](http://ubuntuforums.org/showthread.php?p=11360822)

Just for confirmation, please post outputs of these:
```
sudo lshw -C network
ifconfig
iwconfig
```

---

### Post by msmith0957 on 2011-10-21
> **varunendra said:**
> You may not need to change your network manager. The problem may be related to this one: [http://ubuntuforums.org/showthread.php?p=11360822](http://ubuntuforums.org/showthread.php?p=11360822)

Wow, thank you so much for the find. That seems to have done the trick. But I suppose this also means I will not be able to connect to 802.11n networks :(

Currently, I am testing this on a different network, one that is WEP enabled. When I first connected (prior to the fix), I tried pinging google, and it took between 2 and 5 seconds each packet. Now its less than 20ms. I will test again later on a WPA network to see if this problem is fully resolved.

Below is what I did, from the link above:

> **varunendra said:**
> Nothing seems abnormal to me except this:
which is also normal for other kernels, but apparently there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/836250") in Oniric related with N-channel which might be affecting you too. Accordingly, please try the following:
```
sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1
```Then start browsing and see if there is improvement. If there is, then make this change permanent by creating an 'options' file:
```
gksu gedit /etc/modprobe.d/options.conf
```Add this line to the file:
```
options iwlagn 11n_disable=1
```proofread, save and exit.

And some diagnostics (post-fix) for anyone interested:

```

mike@MikeXPS:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:63:8f:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=8.83.5.1 build 33692 ip=192.168.2.27 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:26:b9:09:35:1f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:49 memory:fc000000-fc00ffff

``````

mike@MikeXPS:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:09:35:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60563 (60.5 KB)  TX bytes:60563 (60.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:63:8f:a2  
          inet addr:192.168.2.27  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe63:8fa2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7017 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8061452 (8.0 MB)  TX bytes:4282977 (4.2 MB)

``````

mike@MikeXPS:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Chinksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:C2:7E:33   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:138   Missed beacon:0


```

---

### Post by varunendra on 2011-10-21
Yes it is meant to disable the N channel on the card, meaning not being able to use it. It is just a workaround to be able to use at least other channels flawlessly. For a proper N channel support, we may have to wait until it gets fixed in newer kernels/patches.

However, as we can see in the bug-report page, it has been given 'High Importance', so hopefully we can expect a fix as soon as possible.

Awaiting your confirmation regarding other tests :)


**_EDIT_:**
It may be useful if you also confirm whether the above output of ifconfig was before or after applying the workaround. I guess most of us would be interested in the earlier status to see if there were packet losses.

---

