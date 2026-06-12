---
title: "Wireless stops working randomly, need to reboot to get it working"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by emreakbas on 2011-12-24
Sometimes my wireless connection gets lost and I cannot bring the connection back. I've tried "ifdown/ifup" and anything that can be done using the network managers interface (I'm using nm-applet). The only way to get it working is to reboot my computer. 

I'm trying to diagnose the problem and below is my dmesg output. I need help in understanding it: 

```

[21779.809888] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[21789.840116] wlan0: no IPv6 routers present
[27996.395119] npviewer.bin[2776]: segfault at 0 ip 00000000f5d5c0c1 sp 00000000ffd9b620 error 4 in libflashplayer.so[f58dd000+fc8000]
[28061.693776] npviewer.bin[22080]: segfault at 218 ip 00000000f5bf19c6 sp 00000000ffff5f28 error 6 in libflashplayer.so[f58c5000+fc8000]
[28277.046243] npviewer.bin[22379]: segfault at 218 ip 00000000f5b579c6 sp 00000000ffb88e78 error 6 in libflashplayer.so[f582b000+fc8000]
[32853.328480] npviewer.bin[22432]: segfault at 0 ip 00000000f5d350c1 sp 00000000ffef0f90 error 4 in libflashplayer.so[f58b6000+fc8000]
[33036.766212] npviewer.bin[25698]: segfault at 0 ip 00000000f58c78c1 sp 00000000ffaee070 error 4 in libflashplayer.so[f5818000+fc8000]
[33072.055833] npviewer.bin[25851]: segfault at f54570a4 ip 00000000f5cbc0b3 sp 00000000ffee05b0 error 4 in libflashplayer.so[f583d000+fc8000]
[36028.385247] npviewer.bin[25893]: segfault at f05a3004 ip 00000000f5fe262c sp 00000000ffba58d0 error 4 in libflashplayer.so[f58d0000+fc8000]
[37296.414831] npviewer.bin[28116]: segfault at 218 ip 00000000f5b6f9c6 sp 00000000ff836598 error 6 in libflashplayer.so[f5843000+fc8000]
[37390.226201] npviewer.bin[28981]: segfault at f543409c ip 00000000f5ce20d7 sp 00000000ffd90700 error 4 in libflashplayer.so[f5863000+fc8000]
[38888.790042] iwlagn 0000:04:00.0: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.
[39186.620150] iwlagn 0000:04:00.0: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.
[39186.620183] iwlagn 0000:04:00.0: Aborted scan still in progress after 100ms
[39187.192636] iwlagn 0000:04:00.0: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.
[39187.192739] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[39187.712544] iwlagn 0000:04:00.0: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.
[39188.212544] iwlagn 0000:04:00.0: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.
[39188.762539] iwlagn 0000:04:00.0: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.
[39189.260024] iwlagn 0000:04:00.0: Error sending REPLY_RXON: time out after 500ms.
[39189.260029] iwlagn 0000:04:00.0: Error setting new RXON (-110)
[39189.760937] iwlagn 0000:04:00.0: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.
[39189.783998] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[39189.789737] ------------[ cut here ]------------
[39189.789765] WARNING: at /build/buildd/linux-2.6.32/net/wireless/core.c:614 wdev_cleanup_work+0xe9/0x110 [cfg80211]()
[39189.789768] Hardware name: 2781                
[39189.789770] Modules linked in: binfmt_misc ppdev nfsd exportfs nfs lockd nfs_acl auth_rpcgss sunrpc joydev snd_hda_codec_conexant snd_hda_codec_intelhdmi fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi arc4 snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore i915 uvcvideo snd mac80211 drm_kms_helper videodev sdhci_pci v4l1_compat sdhci v4l2_compat_ioctl32 led_class cfg80211 intel_agp drm i2c_algo_bit soundcore snd_page_alloc psmouse serio_raw video output lp parport ohci1394 ieee1394 ahci tg3
[39189.789817] Pid: 10, comm: events/1 Tainted: G        W  2.6.32-33-generic #72-Ubuntu
[39189.789820] Call Trace:
[39189.789828]  [<ffffffff810664eb>] warn_slowpath_common+0x7b/0xc0
[39189.789832]  [<ffffffff81066544>] warn_slowpath_null+0x14/0x20
[39189.789839]  [<ffffffffa0105059>] wdev_cleanup_work+0xe9/0x110 [cfg80211]
[39189.789847]  [<ffffffffa0104f70>] ? wdev_cleanup_work+0x0/0x110 [cfg80211]
[39189.789852]  [<ffffffff810800e7>] run_workqueue+0xc7/0x1a0
[39189.789856]  [<ffffffff81080263>] worker_thread+0xa3/0x110
[39189.789860]  [<ffffffff81084cc0>] ? autoremove_wake_function+0x0/0x40
[39189.789864]  [<ffffffff810801c0>] ? worker_thread+0x0/0x110
[39189.789867]  [<ffffffff81084946>] kthread+0x96/0xa0
[39189.789871]  [<ffffffff810131ea>] child_rip+0xa/0x20
[39189.789874]  [<ffffffff810848b0>] ? kthread+0x0/0xa0
[39189.789877]  [<ffffffff810131e0>] ? child_rip+0x0/0x20
[39189.789879] ---[ end trace 7b853aa332540611 ]---
[39189.874691] Registered led device: iwl-phy0::radio
[39189.874722] Registered led device: iwl-phy0::assoc
[39189.874748] Registered led device: iwl-phy0::RX
[39189.874786] Registered led device: iwl-phy0::TX
[39189.900812] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[39190.075266] Registered led device: iwl-phy0::radio
[39190.075295] Registered led device: iwl-phy0::assoc
[39190.075324] Registered led device: iwl-phy0::RX
[39190.075350] Registered led device: iwl-phy0::TX
[39190.100825] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[39190.380412] tg3 0000:07:00.0: irq 32 for MSI/MSI-X
[39190.413682] ADDRCONF(NETDEV_UP): eth0: link is not ready
[39191.187050] Registered led device: iwl-phy0::radio
[39191.187080] Registered led device: iwl-phy0::assoc
[39191.187108] Registered led device: iwl-phy0::RX
[39191.187133] Registered led device: iwl-phy0::TX
[39191.231009] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[39197.439064] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)

```

It's a Kubuntu 10.04 on a Lenovo Y430 laptop. The wireless card is: 

```
emre@emre-laptop:~$ lspci  | grep -i wireless
04:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
```

I've been using the computer for more than 2 years now and this problem is recent which suggests it might be a hardware problem. But on the other hand, I've never had such a problem using Windows on the same machine. 

Any kind of help, hints will be most welcome. 

Thanks.

---

### Post by inobe on 2011-12-25
> **emreakbas said:**
> 

Any kind of help, hints will be most welcome. 

Thanks.

i think for 10.04 you can run this to restart the network.

```
sudo /etc/init.d/networking restart
```

i don't know what's up with npviewer.bin a flash app and why it's causing seg faults along with it's relationship to your network!

are you watching youtube when the wireless hit's rock bottom?

edit: 10.04 is dated, kubuntu has came a long way, currently at 11.10, kde is also upgradable to 4.7.4

run the live cd and test your wireless.

---

### Post by emreakbas on 2011-12-25
I also tried "sudo /etc/init.d/networking restart", it doesn't fix it.

---

### Post by praseodym on 2011-12-25
Update the driver via the "backports-modules" and reboot.

---

### Post by emreakbas on 2011-12-25
How do I do this? Is it as easy as installing linux-backports-modules-compat-wireless-2.6.37-2.6.32-34-generic?

---

### Post by praseodym on 2011-12-25
> **emreakbas said:**
> How do I do this? Is it as easy as installing linux-backports-modules-compat-wireless-2.6.37-2.6.32-34-generic?

Yes, just install the metapackage:

```
sudo apt-get install linux-backports-modules-wirless-lucid-generic
```
for the driver version from kernel 2.6.36. Your system should be up-to-date, because this package is for kernel 2.6.32-37 which is the latest in Lucid. The later kernel versions of iwlagn contain a bug with the N-mode.

---

### Post by emreakbas on 2011-12-25
I installed the package and reboot. Now, there is another problem. It is connected for about 1 minute, then the connection gets lost. After 10 seconds or so, it reconnects, and these repeat. Here is dmesg: 


```
[ 2271.662795] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2271.662804] cfg80211: Restoring regulatory settings
[ 2271.662809] cfg80211: Calling CRDA to update world regulatory domain
[ 2271.666193] cfg80211: World regulatory domain updated:
[ 2271.666198]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2271.666203]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2271.666208]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2271.666212]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2271.666216]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2271.666221]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2271.701308] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2271.739217] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2271.741176] wlan0: authenticated
[ 2271.741239] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2271.743545] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2271.743551] wlan0: associated
[ 2271.746194] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2271.790187] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2271.790195] cfg80211: Restoring regulatory settings
[ 2271.790200] cfg80211: Calling CRDA to update world regulatory domain
[ 2271.794867] cfg80211: World regulatory domain updated:
[ 2271.794873]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2271.794878]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2271.794883]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2271.794887]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2271.794891]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2271.794896]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2271.828788] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2271.866014] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2271.867999] wlan0: authenticated
[ 2271.868057] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2271.870437] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2271.870441] wlan0: associated
[ 2271.873044] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2271.950908] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2271.987876] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2271.990697] wlan0: authenticated
[ 2271.990734] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2271.996839] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2271.996844] wlan0: associated
[ 2271.999515] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.070847] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.107827] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2272.109886] wlan0: authenticated
[ 2272.109937] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2272.112314] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2272.112319] wlan0: associated
[ 2272.116040] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.194686] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.231632] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2272.233774] wlan0: authenticated
[ 2272.233820] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2272.236132] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2272.236137] wlan0: associated
[ 2272.240317] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.320394] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.357392] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2272.359543] wlan0: authenticated
[ 2272.359616] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2272.362025] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2272.362031] wlan0: associated
[ 2272.364276] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.452710] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.489936] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2272.491935] wlan0: authenticated
[ 2272.491997] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2272.494328] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2272.494333] wlan0: associated
[ 2272.498737] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.520173] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2272.520181] cfg80211: Restoring regulatory settings
[ 2272.520186] cfg80211: Calling CRDA to update world regulatory domain
[ 2272.523596] cfg80211: World regulatory domain updated:
[ 2272.523601]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2272.523606]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2272.523611]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2272.523615]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2272.523619]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2272.523623]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2272.559660] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.596592] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2272.599551] wlan0: authenticated
[ 2272.599614] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2272.602136] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2272.602142] wlan0: associated
[ 2272.606045] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.668815] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.707194] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2272.709258] wlan0: authenticated
[ 2272.709311] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2272.711860] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2272.711865] wlan0: associated
[ 2272.714975] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.781462] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.818382] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2272.821427] wlan0: authenticated
[ 2272.821490] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2272.823946] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2272.823952] wlan0: associated
[ 2272.826686] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.870189] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2272.870196] cfg80211: Restoring regulatory settings
[ 2272.870201] cfg80211: Calling CRDA to update world regulatory domain
[ 2272.873577] cfg80211: World regulatory domain updated:
[ 2272.873582]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2272.873587]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2272.873591]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2272.873596]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2272.873600]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2272.873604]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2272.909388] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2272.946349] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2272.948548] wlan0: authenticated
[ 2272.948624] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2272.951114] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2272.951120] wlan0: associated
[ 2272.953955] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.018883] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.055976] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2273.057966] wlan0: authenticated
[ 2273.058038] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2273.060399] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2273.060405] wlan0: associated
[ 2273.063651] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.090192] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2273.090201] cfg80211: Restoring regulatory settings
[ 2273.090206] cfg80211: Calling CRDA to update world regulatory domain
[ 2273.093523] cfg80211: World regulatory domain updated:
[ 2273.093528]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2273.093533]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.093537]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2273.093541]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2273.093545]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.093550]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.129408] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.166421] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2273.174802] wlan0: authenticated
[ 2273.190711] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2273.193140] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2273.193146] wlan0: associated
[ 2273.196585] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.371394] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.408388] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2273.410355] wlan0: authenticated
[ 2273.410409] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2273.412908] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2273.412913] wlan0: associated
[ 2273.415668] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.480280] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.517238] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2273.520146] wlan0: authenticated
[ 2273.520206] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2273.522653] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2273.522659] wlan0: associated
[ 2273.526535] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.550184] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2273.550193] cfg80211: Restoring regulatory settings
[ 2273.550198] cfg80211: Calling CRDA to update world regulatory domain
[ 2273.554971] cfg80211: World regulatory domain updated:
[ 2273.554977]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2273.554982]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.554986]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2273.554991]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2273.554995]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.554999]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.588722] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.625697] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2273.627858] wlan0: authenticated
[ 2273.627934] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2273.633621] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2273.633627] wlan0: associated
[ 2273.636206] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.680104] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.717040] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2273.719004] wlan0: authenticated
[ 2273.719067] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2273.721430] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2273.721435] wlan0: associated
[ 2273.724083] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.750178] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2273.750187] cfg80211: Restoring regulatory settings
[ 2273.750192] cfg80211: Calling CRDA to update world regulatory domain
[ 2273.753385] cfg80211: World regulatory domain updated:
[ 2273.753389]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2273.753394]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.753399]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2273.753403]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2273.753407]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.753412]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.788879] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.825781] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2273.827822] wlan0: authenticated
[ 2273.827896] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2273.830255] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2273.830262] wlan0: associated
[ 2273.837816] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.883041] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2273.883049] cfg80211: Restoring regulatory settings
[ 2273.883054] cfg80211: Calling CRDA to update world regulatory domain
[ 2273.888564] cfg80211: World regulatory domain updated:
[ 2273.888570]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2273.888576]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.888580]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2273.888584]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2273.888589]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.888593]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2273.910691] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2273.948015] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2273.951144] wlan0: authenticated
[ 2273.951220] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2273.953630] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2273.953636] wlan0: associated
[ 2273.956653] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.030820] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.067813] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2274.069834] wlan0: authenticated
[ 2274.069889] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2274.072350] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2274.072356] wlan0: associated
[ 2274.075035] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.139074] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.175924] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2274.178126] wlan0: authenticated
[ 2274.193213] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2274.199215] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2274.199221] wlan0: associated
[ 2274.202424] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.288747] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.325745] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2274.327900] wlan0: authenticated
[ 2274.327975] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2274.330308] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2274.330313] wlan0: associated
[ 2274.333116] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.402708] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.444270] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2274.446307] wlan0: authenticated
[ 2274.446359] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2274.452609] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2274.452614] wlan0: associated
[ 2274.456440] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.521308] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.558299] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2274.560350] wlan0: authenticated
[ 2274.560423] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2274.562864] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2274.562869] wlan0: associated
[ 2274.565174] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.650166] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.687125] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2274.689228] wlan0: authenticated
[ 2274.689293] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2274.691705] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2274.691710] wlan0: associated
[ 2274.694381] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.769495] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2274.807201] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2274.813012] wlan0: authenticated
[ 2274.813053] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2274.815449] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2274.815452] wlan0: associated
[ 2284.823999] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2284.891949] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2284.939211] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2284.941187] wlan0: authenticated
[ 2284.941219] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2284.944751] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2284.944756] wlan0: associated
[ 2294.958129] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2295.019643] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2295.056727] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2295.059738] wlan0: authenticated
[ 2295.059811] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2295.062248] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2295.062254] wlan0: associated
[ 2300.348995] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2300.410848] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2300.459670] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2300.462586] wlan0: authenticated
[ 2300.462648] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2300.464981] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2300.464986] wlan0: associated
[ 2310.474134] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2310.540407] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2310.577412] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2310.580403] wlan0: authenticated
[ 2310.580466] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2310.584676] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2310.584682] wlan0: associated
[ 2320.594384] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2320.661756] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2320.698745] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2320.701694] wlan0: authenticated
[ 2320.701759] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2320.704563] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2320.704569] wlan0: associated
[ 2330.712531] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2330.770804] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2330.770813] cfg80211: Restoring regulatory settings
[ 2330.770819] cfg80211: Calling CRDA to update world regulatory domain
[ 2330.774944] cfg80211: World regulatory domain updated:
[ 2330.774949]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2330.774955]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2330.774959]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2330.774963]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2330.774967]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2330.774972]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2330.810606] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2330.847580] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2330.850665] wlan0: authenticated
[ 2330.850714] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2330.853046] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2330.853051] wlan0: associated
[ 2340.859280] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2340.928775] wlan0: deauthenticating from 00:21:29:94:f3:4e by local choice (reason=3)
[ 2340.965801] wlan0: authenticate with 00:21:29:94:f3:4e (try 1)
[ 2340.968991] wlan0: authenticated
[ 2340.969064] wlan0: associate with 00:21:29:94:f3:4e (try 1)
[ 2340.971415] wlan0: RX AssocResp from 00:21:29:94:f3:4e (capab=0x411 status=0 aid=2)
[ 2340.971421] wlan0: associated

```

---

### Post by praseodym on 2011-12-25
Which encryption mode do you use? I recommend pure WPA2-AES if possible. Mixed WPA/WPA2 disconnects often with the NM. Alternaitively try Wicd if the router doesnt allow pure WPA2

---

### Post by emreakbas on 2011-12-25
I removed backport-modules package. I guess I'm using mixed WPA/WPA2. I'll try WPA2-AES.

---

### Post by inobe on 2011-12-25
> **emreakbas said:**
> I also tried "sudo /etc/init.d/networking restart", it doesn't fix it.

this doesn't restart your network?

---

### Post by emreakbas on 2012-01-26
Update: I reinstalled the "backport-modules" and I haven't had any problems with my network card since. Thanks, praseodym.

---

