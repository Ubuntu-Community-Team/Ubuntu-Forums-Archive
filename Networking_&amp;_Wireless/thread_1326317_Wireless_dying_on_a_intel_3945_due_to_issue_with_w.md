---
title: "Wireless dying on a intel 3945 due to issue with wireless core"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by zuke on 2009-11-14
My intel 3945 has been randomly cutting out, if I run ifconfig or look at the network manager it still thinks I'm online but I cannot ping out. I have to modprobe -r iwl3945 and reload it to get the wireless working again but this only works for a little bit then it freezes again. 

here is my dmesg out put 
> [  544.325373] WARNING: at /build/buildd/linux-backports-modules-2.6.31-2.6.31/debian/build/build-generic/compat-wireless-2.6/net/wireless/core.c:614 wdev_cleanup_work+0x9f/0xc0 [/COLOR[/COLOR]][cfg80211]()
[  544.325376] Hardware name: Latitude D830                   
[  544.325378] Modules linked in: binfmt_misc ppdev aes_i586 aes_generic nls_iso8859_1 nls_cp437 vfat fat microcode joydev dell_wmi dell_laptop psmouse serio_raw arc4 ecb iwl3945(-) iwlcore lp parport dcdbas mac80211 nvidia(P) led_class snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi iptable_filter snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd ip_tables x_tables soundcore snd_page_alloc cfg80211 usbhid usb_storage intel_agp tg3 agpgart video output
[  544.325421] Pid: 10, comm: events/1 Tainted: P           2.6.31-14-generic #48-Ubuntu
[  544.325423] Call Trace:
[  544.325432]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
[  544.325441]  [<f808e29f>] ? wdev_cleanup_work+0x9f/0xc0 [cfg80211]
[  544.325451]  [<f808e29f>] ? wdev_cleanup_work+0x9f/0xc0 [cfg80211]
[  544.325455]  [<c01451d5>] warn_slowpath_null+0x15/0x20
[  544.325465]  [<f808e29f>] wdev_cleanup_work+0x9f/0xc0 [cfg80211]
[  544.325469]  [<c0157a7e>] run_workqueue+0x6e/0x140
[  544.325480]  [<f808e200>] ? wdev_cleanup_work+0x0/0xc0 [cfg80211]
[  544.325483]  [<c0157bd8>] worker_thread+0x88/0xe0
[  544.325487]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
[  544.325490]  [<c0157b50>] ? worker_thread+0x0/0xe0
[  544.325493]  [<c015bf8c>] kthread+0x7c/0x90
[  544.325496]  [<c015bf10>] ? kthread+0x0/0x90
[  544.325500]  [<c0104007>] kernel_thread_helper+0x7/0x10
[  544.325502] ---[ end trace 6c3c8c407ccf274c ]---
[  544.565772] iwl3945 0000:0c:00.0: PCI INT A disabled
[  547.601194] cfg80211: Calling CRDA to update world regulatory domain
[  547.643120] cfg80211: World regulatory domain updated:
[  547.643127] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  547.643135] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  547.643142] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  547.643148] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  547.643155] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  547.643162] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  547.666582] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[  547.666585] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[  547.666648] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  547.666668] iwl3945 0000:0c:00.0: setting latency timer to 64
[  547.724406] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[  547.724410] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  547.724557] iwl3945 0000:0c:00.0: irq 30 for MSI/MSI-X
[  547.725707] phy0: Selected rate control algorithm 'iwl-3945-rs'
[  547.740737] iwl3945 0000:0c:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[  547.747547] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[  547.822366] Registered led device: iwl-phy0::radio
[  547.822415] Registered led device: iwl-phy0::assoc
[  547.822458] Registered led device: iwl-phy0::RX
[  547.822499] Registered led device: iwl-phy0::TX
[  547.844410] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  556.226769] wlan0: deauthenticating from 00:26:18:48:93:1e by local choice (reason=3)
[  556.231701] wlan0: direct probe to AP 00:26:18:48:93:1e (try 1)
[  556.234205] wlan0: direct probe responded
[  556.234211] wlan0: authenticate with AP 00:26:18:48:93:1e (try 1)
[  556.236103] wlan0: authenticated
[  556.236136] wlan0: associate with AP 00:26:18:48:93:1e (try 1)
[  556.242363] wlan0: RX AssocResp from 00:26:18:48:93:1e (capab=0x411 status=0 aid=1)
[  556.242372] wlan0: associated
[  556.254018] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  567.136036] wlan0: no IPv6 routers present
[  674.284149] iwl3945 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000008.
[  674.284174] iwl3945 0000:0c:00.0: Error Reply type 0x00000000 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x00000000
[  674.359831] Registered led device: iwl-phy0::radio
[  674.359865] Registered led device: iwl-phy0::assoc
[  674.359894] Registered led device: iwl-phy0::RX
[  674.359923] Registered led device: iwl-phy0::TX
[  678.748031] CE: hpet increasing min_delta_ns to 15000 nsec
[  681.775939] CE: hpet increasing min_delta_ns to 22500 nsec
[  697.867027] iwl3945 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000008.
[  697.867047] iwl3945 0000:0c:00.0: Error Reply type 0x00000000 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x00000000


---

### Post by zuke on 2009-11-14
> zedster@zedster-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
zedster@zedster-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:d9:b3:da  
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
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36259 (36.2 KB)  TX bytes:36259 (36.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:a7:c3:e8  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fea7:c3e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:353496 (353.4 KB)  TX bytes:112365 (112.3 KB)


I also noticed this

---

### Post by zuke on 2009-11-15
sorry to bump this, but I've tried everything short a re-install that I can I think of

---

### Post by bpeyser on 2009-11-16
I might be having a similar problem on my Latitude D820 with the Intel PRO/Wireless 3945ABG. Sometimes I will lose my wireless connection. When this happens the network manager does not list me as connected and will not reconnect. I can still get online with my mobile broadband, but so far I haven't found a way to get the WiFi to work again without a reboot.

This worked flawlessly on Jaunty, but ever since I upgraded to 9.10 I've had this problem. It happens occasionally, and seems like maybe it's a problem with low-power mode or something. I'll leave the computer sitting for a while and when I come back, the wireless is disconnected.

-bpeyser

---

### Post by zuke on 2009-11-16
I was able to fix my problem, I removed all the backports and then reconfigured the generic kernal. 

ie.
sudo apt-get remove linux-backports-modules-*

sudo dpkg-reconfigue linux-image-generic

---

### Post by bpeyser on 2009-11-16
I may give that a try--thanks!

---

### Post by bpeyser on 2009-11-22
Just an update--I tried that and it didn't fix my problem. However, I did find a fix: I went back to 9.04!

I'm pretty sure there is some kind of problem with power management in Karmic. I think that's why my wireless dropped my connection, but maybe it's unrelated.

-bpeyser

---

