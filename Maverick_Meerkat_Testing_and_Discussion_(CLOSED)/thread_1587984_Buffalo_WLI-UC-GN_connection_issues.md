---
title: "Buffalo WLI-UC-GN connection issues"
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Calash on 2010-10-04
I made the plunge to 10.10 on my home PC this weekend and ran into an odd issue with the wireless USB adapter I run, the Buffalo WLI-UC-GN.

[http://www.buffalotech.com/products/wireless/client-adapters/airstation-nfiniti-wireless-n-ultra-compact-usb-20-adapter-wli-uc-gn/](http://www.buffalotech.com/products/wireless/client-adapters/airstation-nfiniti-wireless-n-ultra-compact-usb-20-adapter-wli-uc-gn/)

It makes use of the RaLink chipset, RT2870 I believe.

Before the upgrade this little key performed perfectly with great signal strength and stability.  However after the update it acts really odd.  It will connect but at random points it will drop the connection.

I switched over to wicd and it does the same thing, but it will make an attempt to try and reconnect.

I did some basic searching online based on some of the log files but so far have come up blank.

My next steps will be to get a different wireless USB and see if it is just the chipset or something worse.

Being that my internet is a bit sporadic on that computer I want to get everything I need ready before starting the diags again tonight.  Can anybody suggest any log files, or other hints/tricks to look for in trying to isolate the issue?


Edit:  The behavior is similar to what is described in this bug report

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/488340](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/488340)

However it is not a Broadcom chipset.  The fix still looks interesting and I will try it tonight

```

sudo iwconfig ethX power off

```

---

### Post by Calash on 2010-10-04
No luck.  I got this from the messages log

```


Oct  4 19:35:39 Ubuntu64 kernel: [ 6322.694532] cfg80211: Calling CRDA to update world regulatory domain
Oct  4 19:35:39 Ubuntu64 kernel: [ 6322.698998] cfg80211: World regulatory domain updated:
Oct  4 19:35:39 Ubuntu64 kernel: [ 6322.699003]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  4 19:35:39 Ubuntu64 kernel: [ 6322.699009]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:35:39 Ubuntu64 kernel: [ 6322.699013]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:35:39 Ubuntu64 kernel: [ 6322.699016]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:35:39 Ubuntu64 kernel: [ 6322.699019]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:35:39 Ubuntu64 kernel: [ 6322.699022]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:35:43 Ubuntu64 kernel: [ 6327.460202] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:35:43 Ubuntu64 kernel: [ 6327.543737] pcieport 0000:00:1c.5: wake-up capability enabled by ACPI
Oct  4 19:35:44 Ubuntu64 kernel: [ 6327.565968] pcieport 0000:00:1c.5: wake-up capability disabled by ACPI
Oct  4 19:35:44 Ubuntu64 kernel: [ 6327.580041] tg3 0000:04:00.0: BAR 0: set to [mem 0xebef0000-0xebefffff 64bit] (PCI address [0xebef0000-0xebefffff]
Oct  4 19:35:44 Ubuntu64 kernel: [ 6327.612704] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 19:35:48 Ubuntu64 kernel: [ 6332.260104] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:35:51 Ubuntu64 kernel: [ 6334.639993] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:35:51 Ubuntu64 kernel: [ 6334.710452] pcieport 0000:00:1c.5: wake-up capability enabled by ACPI
Oct  4 19:35:51 Ubuntu64 kernel: [ 6334.735745] pcieport 0000:00:1c.5: wake-up capability disabled by ACPI
Oct  4 19:35:51 Ubuntu64 kernel: [ 6334.750041] tg3 0000:04:00.0: BAR 0: set to [mem 0xebef0000-0xebefffff 64bit] (PCI address [0xebef0000-0xebefffff]
Oct  4 19:35:51 Ubuntu64 kernel: [ 6334.782722] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 19:35:52 Ubuntu64 kernel: [ 6335.575261] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:35:54 Ubuntu64 kernel: [ 6338.133698] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct  4 19:35:56 Ubuntu64 kernel: [ 6339.669490] type=1400 audit(1286235356.095:24): apparmor="DENIED" operation="open" parent=7085 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=7113 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct  4 19:36:22 Ubuntu64 kernel: [ 6365.710242] usb 1-8: USB disconnect, address 6
Oct  4 19:36:22 Ubuntu64 kernel: [ 6365.715879] cfg80211: Calling CRDA to update world regulatory domain
Oct  4 19:36:22 Ubuntu64 kernel: [ 6365.727661] cfg80211: World regulatory domain updated:
Oct  4 19:36:22 Ubuntu64 kernel: [ 6365.727666]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  4 19:36:22 Ubuntu64 kernel: [ 6365.727671]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:36:22 Ubuntu64 kernel: [ 6365.727674]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:36:22 Ubuntu64 kernel: [ 6365.727678]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:36:22 Ubuntu64 kernel: [ 6365.727681]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:36:22 Ubuntu64 kernel: [ 6365.727685]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:36:25 Ubuntu64 kernel: [ 6369.430020] usb 1-8: new high speed USB device using ehci_hcd and address 7
Oct  4 19:36:51 Ubuntu64 kernel: [ 6395.412075] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:37:09 Ubuntu64 kernel: [ 6412.927365] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:37:09 Ubuntu64 kernel: [ 6413.030466] pcieport 0000:00:1c.5: wake-up capability enabled by ACPI
Oct  4 19:37:09 Ubuntu64 kernel: [ 6413.055720] pcieport 0000:00:1c.5: wake-up capability disabled by ACPI
Oct  4 19:37:09 Ubuntu64 kernel: [ 6413.070031] tg3 0000:04:00.0: BAR 0: set to [mem 0xebef0000-0xebefffff 64bit] (PCI address [0xebef0000-0xebefffff]
Oct  4 19:37:09 Ubuntu64 kernel: [ 6413.102364] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 19:37:10 Ubuntu64 kernel: [ 6413.870113] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:37:11 Ubuntu64 kernel: [ 6414.900128] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:37:11 Ubuntu64 kernel: [ 6415.000487] pcieport 0000:00:1c.5: wake-up capability enabled by ACPI
Oct  4 19:37:11 Ubuntu64 kernel: [ 6415.025846] pcieport 0000:00:1c.5: wake-up capability disabled by ACPI
Oct  4 19:37:11 Ubuntu64 kernel: [ 6415.040058] tg3 0000:04:00.0: BAR 0: set to [mem 0xebef0000-0xebefffff 64bit] (PCI address [0xebef0000-0xebefffff]
Oct  4 19:37:11 Ubuntu64 kernel: [ 6415.072782] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 19:37:14 Ubuntu64 kernel: [ 6417.653780] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct  4 19:37:15 Ubuntu64 kernel: [ 6419.021966] type=1400 audit(1286235435.455:25): apparmor="DENIED" operation="open" parent=7225 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=7276 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.076212] usb 1-8: USB disconnect, address 7
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.083120] cfg80211: Calling CRDA to update world regulatory domain
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.092917] cfg80211: World regulatory domain updated:
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.092921]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.092925]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.092927]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.092930]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.092933]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.092935]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:37:26 Ubuntu64 kernel: [ 6429.670023] usb 1-7: new high speed USB device using ehci_hcd and address 8
Oct  4 19:37:30 Ubuntu64 kernel: [ 6434.161941] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:37:48 Ubuntu64 kernel: [ 6451.770081] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:37:52 Ubuntu64 kernel: [ 6456.029930] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:37:52 Ubuntu64 kernel: [ 6456.100451] pcieport 0000:00:1c.5: wake-up capability enabled by ACPI
Oct  4 19:37:52 Ubuntu64 kernel: [ 6456.125852] pcieport 0000:00:1c.5: wake-up capability disabled by ACPI
Oct  4 19:37:52 Ubuntu64 kernel: [ 6456.140033] tg3 0000:04:00.0: BAR 0: set to [mem 0xebef0000-0xebefffff 64bit] (PCI address [0xebef0000-0xebefffff]
Oct  4 19:37:52 Ubuntu64 kernel: [ 6456.172655] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 19:37:53 Ubuntu64 kernel: [ 6456.999913] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:37:57 Ubuntu64 kernel: [ 6460.794075] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct  4 19:37:57 Ubuntu64 kernel: [ 6461.107696] type=1400 audit(1286235477.535:26): apparmor="DENIED" operation="open" parent=7374 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=7405 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct  4 19:38:08 Ubuntu64 kernel: [ 6471.624379] lo: Disabled Privacy Extensions
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.614155] cfg80211: Calling CRDA to update world regulatory domain
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.618630] cfg80211: World regulatory domain updated:
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.618635]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.618639]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.618643]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.618646]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.618649]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.618652]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct  4 19:39:08 Ubuntu64 kernel: [ 6532.501645] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 19:39:09 Ubuntu64 kernel: [ 6532.640473] pcieport 0000:00:1c.5: wake-up capability enabled by ACPI
Oct  4 19:39:09 Ubuntu64 kernel: [ 6532.672681] pcieport 0000:00:1c.5: wake-up capability disabled by ACPI
Oct  4 19:39:09 Ubuntu64 kernel: [ 6532.690039] tg3 0000:04:00.0: BAR 0: set to [mem 0xebef0000-0xebefffff 64bit] (PCI address [0xebef0000-0xebefffff]
Oct  4 19:39:09 Ubuntu64 kernel: [ 6532.756106] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

and from the debug log

```

ct  4 19:37:14 Ubuntu64 kernel: [ 6417.621665] wlan0: authenticate with 00:1e:2a:64:37:3a (try 1)
Oct  4 19:37:14 Ubuntu64 kernel: [ 6417.623294] wlan0: authenticated
Oct  4 19:37:14 Ubuntu64 kernel: [ 6417.624034] wlan0: associate with 00:1e:2a:64:37:3a (try 1)
Oct  4 19:37:14 Ubuntu64 kernel: [ 6417.630795] wlan0: RX AssocResp from 00:1e:2a:64:37:3a (capab=0x411 status=0 aid=2)
Oct  4 19:37:14 Ubuntu64 kernel: [ 6417.630800] wlan0: associated
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.076624] wlan0: deauthenticating from 00:1e:2a:64:37:3a by local choice (reason=3)
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.083109] cfg80211: All devices are disconnected, going to restore regulatory settings
Oct  4 19:37:23 Ubuntu64 kernel: [ 6427.083115] cfg80211: Restoring regulatory settings
Oct  4 19:37:26 Ubuntu64 kernel: [ 6429.871564] phy3: Selected rate control algorithm 'minstrel'
Oct  4 19:37:26 Ubuntu64 kernel: [ 6429.872322] Registered led device: rt2800usb-phy3::radio
Oct  4 19:37:26 Ubuntu64 kernel: [ 6429.872348] Registered led device: rt2800usb-phy3::assoc
Oct  4 19:37:26 Ubuntu64 kernel: [ 6429.872373] Registered led device: rt2800usb-phy3::quality
Oct  4 19:37:52 Ubuntu64 kernel: [ 6456.100428] tg3 0000:04:00.0: PME# enabled
Oct  4 19:37:52 Ubuntu64 kernel: [ 6456.125872] tg3 0000:04:00.0: PME# disabled
Oct  4 19:37:57 Ubuntu64 kernel: [ 6460.751649] wlan0: authenticate with 00:1e:2a:64:37:3a (try 1)
Oct  4 19:37:57 Ubuntu64 kernel: [ 6460.753282] wlan0: authenticated
Oct  4 19:37:57 Ubuntu64 kernel: [ 6460.754020] wlan0: associate with 00:1e:2a:64:37:3a (try 1)
Oct  4 19:37:57 Ubuntu64 kernel: [ 6460.757401] wlan0: RX AssocResp from 00:1e:2a:64:37:3a (capab=0x411 status=0 aid=2)
Oct  4 19:37:57 Ubuntu64 kernel: [ 6460.757405] wlan0: associated
Oct  4 19:38:07 Ubuntu64 kernel: [ 6471.120013] wlan0: no IPv6 routers present
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.580072] No probe response from AP 00:1e:2a:64:37:3a after 500ms, disconnecting.
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.614143] cfg80211: All devices are disconnected, going to restore regulatory settings
Oct  4 19:39:03 Ubuntu64 kernel: [ 6526.614151] cfg80211: Restoring regulatory settings
Oct  4 19:39:04 Ubuntu64 kernel: [ 6528.171822] wlan0: authenticate with 00:1e:2a:64:37:3a (try 1)
Oct  4 19:39:04 Ubuntu64 kernel: [ 6528.370021] wlan0: authenticate with 00:1e:2a:64:37:3a (try 2)
Oct  4 19:39:05 Ubuntu64 kernel: [ 6528.570108] wlan0: authenticate with 00:1e:2a:64:37:3a (try 3)
Oct  4 19:39:05 Ubuntu64 kernel: [ 6528.770026] wlan0: authentication with 00:1e:2a:64:37:3a timed out
Oct  4 19:39:09 Ubuntu64 kernel: [ 6532.640454] tg3 0000:04:00.0: PME# enabled
Oct  4 19:39:09 Ubuntu64 kernel: [ 6532.672690] tg3 0000:04:00.0: PME# disabled
Oct  4 19:39:16 Ubuntu64 kernel: [ 6539.810446] tg3 0000:04:00.0: PME# enabled
Oct  4 19:39:16 Ubuntu64 kernel: [ 6539.842097] tg3 0000:04:00.0: PME# disabled
Oct  4 19:39:19 Ubuntu64 kernel: [ 6543.201716] wlan0: authenticate with 00:1e:2a:64:37:3a (try 1)
Oct  4 19:39:19 Ubuntu64 kernel: [ 6543.212363] wlan0: authenticated
Oct  4 19:39:19 Ubuntu64 kernel: [ 6543.213086] wlan0: associate with 00:1e:2a:64:37:3a (try 1)
Oct  4 19:39:19 Ubuntu64 kernel: [ 6543.220348] wlan0: RX AssocResp from 00:1e:2a:64:37:3a (capab=0x411 status=0 aid=2)
Oct  4 19:39:19 Ubuntu64 kernel: [ 6543.220354] wlan0: associated
Oct  4 19:39:30 Ubuntu64 kernel: [ 6554.130020] wlan0: no IPv6 routers present

```

Any thoughts?


Edit: Tried a newer kernel and same results.  Been searching and I am stumped.  Tried slowing the router to g, editing some settings, disabling power saving on the key, and switching between network manager and wicd.  

Bug reports that are similar, based off of the 500ms event in the logs, suggest a kernel issue.  Is there any way to get this working?

---

### Post by Calash on 2010-10-05
Loaded up the previous kernel in failsafe X mode and it works fine.  Did notice something odd in the lsmod.  Here is the one from 2.6.32-25

```


Module                  Size  Used by
parport_pc             29958  0 
ppdev                   6375  0 
iptable_nat             5219  0 
nf_nat                 19501  1 iptable_nat
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
snd_emu10k1_synth       6036  0 
nls_utf8                1421  0 
nf_conntrack           73966  3 iptable_nat,nf_nat,nf_conntrack_ipv4
snd_emux_synth         37367  1 snd_emu10k1_synth
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
iptable_mangle          3315  0 
cifs                  279302  0 
snd_emu10k1           149161  5 snd_emu10k1_synth
iptable_filter          2791  0 
snd_ac97_codec        125394  1 snd_emu10k1
ip_tables              18390  3 iptable_nat,iptable_mangle,iptable_filter
ac97_bus                1450  1 snd_ac97_codec
x_tables               22461  2 iptable_nat,ip_tables
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tuner_simple           15073  1 
tuner_types            18305  1 tuner_simple
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wm8775                  3725  1 
fbcon                  39270  71 
tuner                  23256  1 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1 
snd                    71187  20 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
cx25840                28607  1 
emu10k1_gp              1964  0 
ivtv                  155760  0 
i2c_algo_bit            6024  1 ivtv
cx2341x                13761  1 ivtv
rt2870sta             525366  1 
usb_storage            49961  0 
vgastate                9857  1 vga16fb
usbhid                 41084  0 
hid                    83472  1 usbhid
v4l2_common            18357  5 wm8775,tuner,cx25840,ivtv,cx2341x
gameport               10966  2 emu10k1_gp
psmouse                64576  0 
videodev               40518  5 wm8775,tuner,cx25840,ivtv,v4l2_common
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    11956  1 videodev
tveeprom               13882  1 ivtv
lp                      9336  0 
parport                37160  3 parport_pc,ppdev,lp
serio_raw               4918  0 
dell_wmi                2177  0 
dcdbas                  6886  0 
firewire_ohci          24735  0 
firewire_core          51697  1 firewire_ohci
crc_itu_t               1715  1 firewire_core
ahci                   37870  3 
tg3                   122382  0 

```

There are a lot less RT* modules loaded here than on the failing one.  I am going to check the new kernel and see if this is something that playing with the blacklist can resolve.


Edit : From the latest kernel.

```


Module                  Size  Used by
binfmt_misc             7984  1 
cryptd                  8140  0 
aes_x86_64              7936  2 
aes_generic            27631  1 aes_x86_64
parport_pc             30086  0 
ppdev                   6804  0 
nls_utf8                1453  4 
cifs                  269596  8 
nvidia              10221046  38 
iptable_nat             4593  0 
nf_nat                 20067  1 iptable_nat
nf_conntrack_ipv4      13143  3 iptable_nat,nf_nat
nf_conntrack           75238  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
iptable_mangle          1823  0 
iptable_filter          1778  0 
ip_tables              19107  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               24423  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_emu10k1_synth       6028  0 
snd_emux_synth         34336  1 snd_emu10k1_synth
snd_seq_virmidi         5165  1 snd_emux_synth
snd_seq_midi_emul       6999  1 snd_emux_synth
rt2870sta             445182  0 
tuner_simple           15137  1 
snd_emu10k1           149854  3 snd_emu10k1_synth
snd_ac97_codec        125227  1 snd_emu10k1
ac97_bus                1474  1 snd_ac97_codec
arc4                    1497  2 
tuner_types            18715  1 tuner_simple
snd_pcm                89104  2 snd_emu10k1,snd_ac97_codec
snd_page_alloc          8588  2 snd_emu10k1,snd_pcm
snd_util_mem            3842  2 snd_emux_synth,snd_emu10k1
snd_hwdep               6660  2 snd_emux_synth,snd_emu10k1
wm8775                  3861  1 
snd_seq_midi            5932  0 
tuner                  23302  1 
snd_rawmidi            22207  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7291  2 snd_seq_virmidi,snd_seq_midi
rt2800usb               9955  0 
rt2800lib              31970  1 rt2800usb
rt2x00usb              11316  2 rt2800usb,rt2800lib
cx25840                31895  1 
snd_seq                57512  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
rt2x00lib              31575  2 rt2800lib,rt2x00usb
snd_timer              23850  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6912  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
ivtv                  158941  0 
mac80211              266657  2 rt2x00usb,rt2x00lib
i2c_algo_bit            6208  1 ivtv
snd                    64117  14 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
emu10k1_gp              2020  0 
cfg80211              170293  2 rt2x00lib,mac80211
cx2341x                13689  1 ivtv
v4l2_common            20635  5 wm8775,tuner,cx25840,ivtv,cx2341x
led_class               3393  1 rt2x00lib
usb_storage            50372  0 
gameport               11224  2 emu10k1_gp
videodev               49359  5 wm8775,tuner,cx25840,ivtv,v4l2_common
crc_ccitt               1699  2 rt2870sta,rt2800usb
v4l1_compat            15519  1 videodev
v4l2_compat_ioctl32    12646  1 videodev
tveeprom               14098  1 ivtv
lp                     10201  0 
dcdbas                  6910  0 
psmouse                62080  0 
serio_raw               4910  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84678  1 usbhid
firewire_ohci          24679  0 
ahci                   21857  0 
tg3                   135768  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
libahci                26167  4 ahci

```




Edit:

For my reference I am testing the following entries in my blacklist file


```

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb

```

This is the first time in a while that my cifs drives have mapped and can be viewed.  It is also showing a good signal strength.  I will report back after more testing.

---

### Post by Calash on 2010-10-05
So far this has passed all my short-term tests that normally break it right away.  I am waiting until tonight to see if everything is stable before marking this as solved.

Question: Is this something that can, or should, be reported in a bug report or is it just a hardware specific tweak?

Also I am finding that some guides say to use /etc/modprobe.d/blacklist while others say to use /etc/modprobe.d/blacklist.conf.  Is their a different between the two or is one preferred over the other?

---

### Post by Calash on 2010-10-05
That solved it.  Hope this will help out others in a similar situation.

Still not sure if this is worthy of a bug report or not.


Edit:  Found this post as well that is related to this issue.

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

The blacklisting corrected the issue.

---

