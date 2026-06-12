---
title: "Realtek wlan connects to WiFi but no intent access"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by nanonils on 2010-08-06
edit: Title meant to say: "internet access", sorry. Stupid automatic spell checker before c/p. 
I&#8217;m pulling my hair over a cheap (subsidized with the usual bloatware) but suprisingly snazzy BestBuy **Compaq Presario CQ63** (&#8220;CQ63-228DX&#8221;) notebook I bought a few days ago for only $329. 
After realizing that the existing 4 partitions (restore, HP, Win7) prevented me from easily co-installing Lucid 64bit (wanted to have ext4 goodness and didn&#8217;t choose Wubi) I quickly confirmed my WiFi was connecting with the live CD in, played around a little and then killed Win7 with a devilish grin flattening the entire HD.

Foolish me I didn&#8217;t realize that the LAN was still connected and going online wirelessly &#8220;seemed&#8221; to be working because of that. I probably shouldn&#8217;t have given my wife&#8217;s old dying Compaq to a temporarily visiting family member (*cough*) without making sure that the spontaneous replacement is working 100%. Well, now I&#8217;m paying... and here is just the computer part of that:

Symptoms: 
The CQ63 connects instantly to our network when booting up. About every 5th time there is a brief successful connect to Google&#8217;s home page and Google News can be pulled up as well on these occasions but that&#8217;s it.
Toggling the network on and off manually via the network manager or via the keyboard button works as expected (connection is lost and re-established) but browsing still doesn&#8217;t work with two browsers (Chrome, FF). 
I&#8217;m using a **LINKSYS WRT160NL R router** and all our other computers and phones connect just fine. MAC filtering is off. The same internet settings are selected in the network manager as with our other wireless Lucid machine. The CQ63 has a** Realtek wlan chipset** and the driver should be part of the linux kernel for many years.
Someone with a CQ62-231NR who posted a similar WiFi problem (search for CQ62) had no problem after connecting via LAN and updating. We don't know what the differences are between the two CQ62s. Well, updating did not fix it for me. 

_**Summary:**_
Realtek 8171
Successful connect via WPA2 
working LINKSYS WRT160NL R router
MAC filtering off
Occasional initial data trickle, then nothing

What on earth is going on? I would very much appreciate your help and advice! That is above my head.

Here is a copy/paste of the data output following the WiFi forum sticky instructions:

1 ) Machine Brand and Model (PC/Laptop):
laptop Compaq Presario CQ63-228DX

2 ) Wireless Brand, Model and Wireless Chipset:
Code:
$ lspci
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
	Subsystem: Hewlett-Packard Company Device 1467
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at 3000 [size=256]
	Memory at d0100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-e0-4c-ff-fe-22-55-88
	Kernel driver in use: rtl819xSE
	Kernel modules: r8192se_pci

3 ) check interface:
Code:
$ ifconfig
eth0 Link encap:Ethernet HWaddr c8:0a:a9:c4:51:79
inet6 addr: fe80::ca0a:a9ff:fec4:5179/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:64941 errors:0 dropped:0 overruns:0 frame:0
TX packets:40051 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:91099544 (91.0 MB) TX bytes:4389896 (4.3 MB)
Interrupt:26 Base address:0x8000
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)
wlan0 Link encap:Ethernet HWaddr 70:f1:a1:be:74:47
inet addr:192.168.1.105 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::72f1:a1ff:febe:7447/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1201 errors:0 dropped:0 overruns:0 frame:0
TX packets:1283 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:202261 (202.2 KB) TX bytes:191323 (191.3 KB)
Interrupt:17 Memory:ffffc90002090000-ffffc90002090100

$ iwconfig wlan0
wlan0 802.11bgn ESSID:"nostrum" Nickname:"rtl8191SEVA2"
Mode:Managed Frequency=2.412 GHz Access Point: 00:23:69:98:2F:5E
Bit Rate=65 Mb/s
Retry:on RTS thr:off Fragment thr:off
Encryption key: [deleted by poster] Security mode:open
Power Management:off
Link Quality=88/100 Signal level=-54 dBm Noise level=-114 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

4 ) Check for modules:
Code:
$ lsmod
Module Size Used by
michael_mic 2164 4
arc4 1473 2
cryptd 8116 0
aes_x86_64 7912 389
aes_generic 27607 1 aes_x86_64
binfmt_misc 7960 1
dm_crypt 13043 0
snd_hda_codec_realtek 297355 1
joydev 11072 0
ppdev 6375 0
snd_hda_intel 23832 2
snd_hda_codec 99579 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 7034 1 snd_hda_codec
snd_pcm_oss 40633 0
snd_mixer_oss 16538 1 snd_pcm_oss
snd_pcm 88269 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 1910 0
snd_seq_oss 31906 0
snd_seq_midi 5797 0
snd_rawmidi 23289 1 snd_seq_midi
snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi
snd_seq 58036 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 23085 2 snd_pcm,snd_seq
snd_seq_device 7176 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx 2353422 32
snd 72583 18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8052 1 snd
snd_page_alloc 8692 2 snd_hda_intel,snd_pcm
r8192se_pci 489163 0
psmouse 64576 0
serio_raw 4918 0
shpchp 33711 0
i2c_piix4 9639 0
edac_core 45423 0
edac_mce_amd 9278 0
lp 9336 0
parport 37160 2 ppdev,lp
fbcon 39270 71
tileblit 2487 1 fbcon
font 8053 1 fbcon
bitblit 5811 1 fbcon
softcursor 1565 1 bitblit
vga16fb 12757 1
vgastate 9857 1 vga16fb
r8169 39650 0
mii 5237 1 r8169
ahci 37870 2
video 20623 0
output 2503 1 video

5 ) Kernel boot messages
Code:
$ dmesg
(hint) the same as in (4)
[ 2976.709370] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 2982.650363] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 2982.650374] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 2982.650379] ====>remove Tx_TS_admin_list
[ 2982.650708] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2982.650719] notify_wx_assoc_event(): Tell user space disconnected
[ 2982.650781] ===>rtllib_associate_procedure_wq(), chan:1
[ 2982.650786] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 2982.663120] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2982.666910] Associated successfully
[ 2982.666913] normal associate
[ 2982.666922] Using G rates:108
[ 2982.666923] Successfully associated, ht enabled
[ 2982.666926] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 2982.676952] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2982.734258] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 2982.734273] ====>to send ADDBARSP
[ 2982.735542] RX: IEEE802.1X EPAOL frame!
[ 2982.742375] RX: IEEE802.1X EPAOL frame!
[ 2982.742580] alg name:CCMP
[ 2982.742605] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 2982.743709] alg name:TKIP
[ 2982.743740] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 2988.650557] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 2988.650568] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 2988.650573] ====>remove Tx_TS_admin_list
[ 2988.650902] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2988.650914] notify_wx_assoc_event(): Tell user space disconnected
[ 2988.650978] ===>rtllib_associate_procedure_wq(), chan:1
[ 2988.650983] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 2988.662429] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2988.666221] Associated successfully
[ 2988.666224] normal associate
[ 2988.666232] Using G rates:108
[ 2988.666233] Successfully associated, ht enabled
[ 2988.666236] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 2988.676261] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2988.681148] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 2988.681158] ====>to send ADDBARSP
[ 2988.682468] RX: IEEE802.1X EPAOL frame!
[ 2988.689690] RX: IEEE802.1X EPAOL frame!
[ 2988.689832] alg name:CCMP
[ 2988.689846] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 2988.689918] alg name:TKIP
[ 2988.689931] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 2994.650326] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 2994.650336] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 2994.650342] ====>remove Tx_TS_admin_list
[ 2994.650671] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2994.650682] notify_wx_assoc_event(): Tell user space disconnected
[ 2994.650743] ===>rtllib_associate_procedure_wq(), chan:1
[ 2994.650749] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 2994.662202] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2994.666091] Associated successfully
[ 2994.666094] normal associate
[ 2994.666100] Using G rates:108
[ 2994.666102] Successfully associated, ht enabled
[ 2994.666104] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 2994.676129] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2994.716556] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 2994.716570] ====>to send ADDBARSP
[ 2994.723467] RX: IEEE802.1X EPAOL frame!
[ 2994.728445] RX: IEEE802.1X EPAOL frame!
[ 2994.728645] alg name:CCMP
[ 2994.728667] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 2994.729776] alg name:TKIP
[ 2994.729806] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3000.650368] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3000.650379] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3000.650384] ====>remove Tx_TS_admin_list
[ 3000.650714] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3000.650724] notify_wx_assoc_event(): Tell user space disconnected
[ 3000.650786] ===>rtllib_associate_procedure_wq(), chan:1
[ 3000.650791] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3000.662239] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3000.666106] Associated successfully
[ 3000.666109] normal associate
[ 3000.666115] Using G rates:108
[ 3000.666117] Successfully associated, ht enabled
[ 3000.666119] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3000.676157] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3000.756979] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3000.756996] ====>to send ADDBARSP
[ 3000.764167] RX: IEEE802.1X EPAOL frame!
[ 3000.769127] RX: IEEE802.1X EPAOL frame!
[ 3000.769326] alg name:CCMP
[ 3000.769348] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3000.770794] alg name:TKIP
[ 3000.770825] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3006.650256] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3006.650267] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3006.650272] ====>remove Tx_TS_admin_list
[ 3006.650601] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3006.650611] notify_wx_assoc_event(): Tell user space disconnected
[ 3006.650673] ===>rtllib_associate_procedure_wq(), chan:1
[ 3006.650678] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3006.662123] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3006.666024] Associated successfully
[ 3006.666027] normal associate
[ 3006.666035] Using G rates:108
[ 3006.666036] Successfully associated, ht enabled
[ 3006.666039] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3006.676061] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3006.697657] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3006.697681] ====>to send ADDBARSP
[ 3006.701591] RX: IEEE802.1X EPAOL frame!
[ 3006.709396] RX: IEEE802.1X EPAOL frame!
[ 3006.709587] alg name:CCMP
[ 3006.709610] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3006.711104] alg name:TKIP
[ 3006.711134] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3012.650328] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3012.650339] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3012.650344] ====>remove Tx_TS_admin_list
[ 3012.650673] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3012.650683] notify_wx_assoc_event(): Tell user space disconnected
[ 3012.650744] ===>rtllib_associate_procedure_wq(), chan:1
[ 3012.650750] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3012.663246] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3012.667058] Associated successfully
[ 3012.667061] normal associate
[ 3012.667067] Using G rates:108
[ 3012.667069] Successfully associated, ht enabled
[ 3012.667071] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3012.677093] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3012.738173] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3012.738187] ====>to send ADDBARSP
[ 3012.739495] RX: IEEE802.1X EPAOL frame!
[ 3012.746756] RX: IEEE802.1X EPAOL frame!
[ 3012.746948] alg name:CCMP
[ 3012.746971] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3012.748265] alg name:TKIP
[ 3012.748296] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3018.650328] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3018.650339] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3018.650344] ====>remove Tx_TS_admin_list
[ 3018.650673] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3018.650683] notify_wx_assoc_event(): Tell user space disconnected
[ 3018.650743] ===>rtllib_associate_procedure_wq(), chan:1
[ 3018.650748] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3018.662165] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3018.666021] Associated successfully
[ 3018.666024] normal associate
[ 3018.666030] Using G rates:108
[ 3018.666031] Successfully associated, ht enabled
[ 3018.666034] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3018.676057] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3018.785728] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3018.785735] ====>to send ADDBARSP
[ 3018.790088] RX: IEEE802.1X EPAOL frame!
[ 3018.794207] RX: IEEE802.1X EPAOL frame!
[ 3018.794371] alg name:CCMP
[ 3018.794384] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3018.794463] alg name:TKIP
[ 3018.794475] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3024.653819] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3024.653829] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3024.653834] ====>remove Tx_TS_admin_list
[ 3024.654205] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3024.654229] notify_wx_assoc_event(): Tell user space disconnected
[ 3024.654274] ===>rtllib_associate_procedure_wq(), chan:1
[ 3024.654280] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3024.665723] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3024.677225] Associated successfully
[ 3024.677229] normal associate
[ 3024.677237] Using G rates:108
[ 3024.677239] Successfully associated, ht enabled
[ 3024.677243] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3024.687275] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3024.725745] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3024.725754] ====>to send ADDBARSP
[ 3024.727042] RX: IEEE802.1X EPAOL frame!
[ 3024.730612] RX: IEEE802.1X EPAOL frame!
[ 3024.730712] alg name:CCMP
[ 3024.730733] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3024.730790] alg name:TKIP
[ 3024.730800] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3030.650353] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3030.650364] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3030.650369] ====>remove Tx_TS_admin_list
[ 3030.650699] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3030.650709] notify_wx_assoc_event(): Tell user space disconnected
[ 3030.650772] ===>rtllib_associate_procedure_wq(), chan:1
[ 3030.650786] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3030.662231] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3030.666032] Associated successfully
[ 3030.666035] normal associate
[ 3030.666041] Using G rates:108
[ 3030.666043] Successfully associated, ht enabled
[ 3030.666046] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3030.676068] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3030.696108] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3030.696123] ====>to send ADDBARSP
[ 3030.700889] RX: IEEE802.1X EPAOL frame!
[ 3030.705849] RX: IEEE802.1X EPAOL frame!
[ 3030.706040] alg name:CCMP
[ 3030.706063] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3030.707344] alg name:TKIP
[ 3030.707374] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3036.650352] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3036.650363] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3036.650368] ====>remove Tx_TS_admin_list
[ 3036.650698] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3036.650707] notify_wx_assoc_event(): Tell user space disconnected
[ 3036.650768] ===>rtllib_associate_procedure_wq(), chan:1
[ 3036.650773] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3036.662211] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3036.666575] Associated successfully
[ 3036.666578] normal associate
[ 3036.666585] Using G rates:108
[ 3036.666586] Successfully associated, ht enabled
[ 3036.666589] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3036.676610] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3036.736988] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3036.737003] ====>to send ADDBARSP
[ 3036.738302] RX: IEEE802.1X EPAOL frame!
[ 3036.744556] RX: IEEE802.1X EPAOL frame!
[ 3036.744741] alg name:CCMP
[ 3036.744764] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3036.745833] alg name:TKIP
[ 3036.745862] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3042.651118] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3042.651126] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3042.651129] ====>remove Tx_TS_admin_list
[ 3042.651453] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3042.651461] notify_wx_assoc_event(): Tell user space disconnected
[ 3042.651516] ===>rtllib_associate_procedure_wq(), chan:1
[ 3042.651519] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3042.662910] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3042.668002] Associated successfully
[ 3042.668007] normal associate
[ 3042.668021] Using G rates:108
[ 3042.668023] Successfully associated, ht enabled
[ 3042.668026] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3042.678062] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3042.680393] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3042.680400] ====>to send ADDBARSP
[ 3042.686469] RX: IEEE802.1X EPAOL frame!
[ 3042.691511] RX: IEEE802.1X EPAOL frame!
[ 3042.691704] alg name:CCMP
[ 3042.691727] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3042.691850] alg name:TKIP
[ 3042.691870] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3048.650359] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3048.650370] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3048.650375] ====>remove Tx_TS_admin_list
[ 3048.650705] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3048.650715] notify_wx_assoc_event(): Tell user space disconnected
[ 3048.650776] ===>rtllib_associate_procedure_wq(), chan:1
[ 3048.650781] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3048.663589] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3048.667412] Associated successfully
[ 3048.667415] normal associate
[ 3048.667422] Using G rates:108
[ 3048.667423] Successfully associated, ht enabled
[ 3048.667426] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3048.677447] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3048.718522] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3048.718537] ====>to send ADDBARSP
[ 3048.719857] RX: IEEE802.1X EPAOL frame!
[ 3048.727573] RX: IEEE802.1X EPAOL frame!
[ 3048.727778] alg name:CCMP
[ 3048.727801] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3048.728889] alg name:TKIP
[ 3048.728918] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3054.650353] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3054.650364] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3054.650369] ====>remove Tx_TS_admin_list
[ 3054.650698] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3054.650709] notify_wx_assoc_event(): Tell user space disconnected
[ 3054.650771] ===>rtllib_associate_procedure_wq(), chan:1
[ 3054.650776] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3054.662212] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3054.668201] Associated successfully
[ 3054.668204] normal associate
[ 3054.668211] Using G rates:108
[ 3054.668212] Successfully associated, ht enabled
[ 3054.668215] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3054.678235] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3054.759054] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3054.759069] ====>to send ADDBARSP
[ 3054.765899] RX: IEEE802.1X EPAOL frame!
[ 3054.771190] RX: IEEE802.1X EPAOL frame!
[ 3054.771384] alg name:CCMP
[ 3054.771406] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3054.772496] alg name:TKIP
[ 3054.772525] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3060.650328] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3060.650339] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3060.650344] ====>remove Tx_TS_admin_list
[ 3060.650674] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3060.650684] notify_wx_assoc_event(): Tell user space disconnected
[ 3060.650744] ===>rtllib_associate_procedure_wq(), chan:1
[ 3060.650749] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3060.662166] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3060.666012] Associated successfully
[ 3060.666015] normal associate
[ 3060.666022] Using G rates:108
[ 3060.666023] Successfully associated, ht enabled
[ 3060.666026] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3060.676049] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3060.700587] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3060.700601] ====>to send ADDBARSP
[ 3060.706070] RX: IEEE802.1X EPAOL frame!
[ 3060.711007] RX: IEEE802.1X EPAOL frame!
[ 3060.711201] alg name:CCMP
[ 3060.711224] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3060.712306] alg name:TKIP
[ 3060.712335] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3066.650367] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3066.650377] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3066.650382] ====>remove Tx_TS_admin_list
[ 3066.650713] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3066.650722] notify_wx_assoc_event(): Tell user space disconnected
[ 3066.650785] ===>rtllib_associate_procedure_wq(), chan:1
[ 3066.650790] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3066.662231] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3066.666080] Associated successfully
[ 3066.666083] normal associate
[ 3066.666090] Using G rates:108
[ 3066.666091] Successfully associated, ht enabled
[ 3066.666094] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3066.676117] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3066.741857] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3066.741872] ====>to send ADDBARSP
[ 3066.743225] RX: IEEE802.1X EPAOL frame!
[ 3066.751328] RX: IEEE802.1X EPAOL frame!
[ 3066.751526] alg name:CCMP
[ 3066.751550] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3066.752641] alg name:TKIP
[ 3066.752671] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3071.332774] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3071.332874] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3072.970179] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3080.650272] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3080.650282] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3080.650287] ====>remove Tx_TS_admin_list
[ 3080.650616] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3080.650626] notify_wx_assoc_event(): Tell user space disconnected
[ 3080.650689] ===>rtllib_associate_procedure_wq(), chan:1
[ 3080.650694] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3080.667210] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3080.671451] Associated successfully
[ 3080.671459] normal associate
[ 3080.671474] Using G rates:108
[ 3080.671477] Successfully associated, ht enabled
[ 3080.671483] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3080.681527] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3080.773020] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3080.773036] ====>to send ADDBARSP
[ 3080.774431] RX: IEEE802.1X EPAOL frame!
[ 3080.780643] RX: IEEE802.1X EPAOL frame!
[ 3080.780819] alg name:CCMP
[ 3080.780844] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3080.781970] alg name:TKIP
[ 3080.782001] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3086.650315] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3086.650326] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3086.650331] ====>remove Tx_TS_admin_list
[ 3086.650663] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3086.650673] notify_wx_assoc_event(): Tell user space disconnected
[ 3086.650736] ===>rtllib_associate_procedure_wq(), chan:1
[ 3086.650742] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3086.662174] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3086.666055] Associated successfully
[ 3086.666058] normal associate
[ 3086.666067] Using G rates:108
[ 3086.666069] Successfully associated, ht enabled
[ 3086.666071] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3086.676094] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3086.708973] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3086.708988] ====>to send ADDBARSP
[ 3086.710259] RX: IEEE802.1X EPAOL frame!
[ 3086.715234] RX: IEEE802.1X EPAOL frame!
[ 3086.715433] alg name:CCMP
[ 3086.715456] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3086.716566] alg name:TKIP
[ 3086.716596] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3092.654755] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3092.654759] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3092.654761] ====>remove Tx_TS_admin_list
[ 3092.655079] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3092.655086] notify_wx_assoc_event(): Tell user space disconnected
[ 3092.655109] ===>rtllib_associate_procedure_wq(), chan:1
[ 3092.655111] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3092.666527] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3092.684189] Associated successfully
[ 3092.684193] normal associate
[ 3092.684200] Using G rates:108
[ 3092.684202] Successfully associated, ht enabled
[ 3092.684205] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3092.694240] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3092.732299] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3092.732310] ====>to send ADDBARSP
[ 3092.736909] RX: IEEE802.1X EPAOL frame!
[ 3092.741381] RX: IEEE802.1X EPAOL frame!
[ 3092.741494] alg name:CCMP
[ 3092.741514] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3092.741577] alg name:TKIP
[ 3092.741586] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3098.650338] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3098.650348] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3098.650353] ====>remove Tx_TS_admin_list
[ 3098.650684] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3098.650694] notify_wx_assoc_event(): Tell user space disconnected
[ 3098.650756] ===>rtllib_associate_procedure_wq(), chan:1
[ 3098.650762] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3098.663540] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3098.669810] Associated successfully
[ 3098.669817] normal associate
[ 3098.669831] Using G rates:108
[ 3098.669833] Successfully associated, ht enabled
[ 3098.669837] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3098.679874] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3098.773424] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3098.773441] ====>to send ADDBARSP
[ 3098.774813] RX: IEEE802.1X EPAOL frame!
[ 3098.782440] RX: IEEE802.1X EPAOL frame!
[ 3098.782640] alg name:CCMP
[ 3098.782663] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3098.783761] alg name:TKIP
[ 3098.783791] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3104.650272] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3104.650282] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3104.650287] ====>remove Tx_TS_admin_list
[ 3104.650619] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3104.650629] notify_wx_assoc_event(): Tell user space disconnected
[ 3104.650693] ===>rtllib_associate_procedure_wq(), chan:1
[ 3104.650698] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3104.662148] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3104.666069] Associated successfully
[ 3104.666074] normal associate
[ 3104.666080] Using G rates:108
[ 3104.666081] Successfully associated, ht enabled
[ 3104.666084] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3104.676107] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3104.713039] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3104.713048] ====>to send ADDBARSP
[ 3104.718644] RX: IEEE802.1X EPAOL frame!
[ 3104.722274] RX: IEEE802.1X EPAOL frame!
[ 3104.722381] alg name:CCMP
[ 3104.722403] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3104.722461] alg name:TKIP
[ 3104.722470] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3110.650370] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3110.650381] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3110.650386] ====>remove Tx_TS_admin_list
[ 3110.650715] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3110.650725] notify_wx_assoc_event(): Tell user space disconnected
[ 3110.650789] ===>rtllib_associate_procedure_wq(), chan:1
[ 3110.650794] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3110.662226] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3110.666107] Associated successfully
[ 3110.666110] normal associate
[ 3110.666116] Using G rates:108
[ 3110.666117] Successfully associated, ht enabled
[ 3110.666120] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3110.676144] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3110.752800] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3110.752814] ====>to send ADDBARSP
[ 3110.754149] RX: IEEE802.1X EPAOL frame!
[ 3110.761709] RX: IEEE802.1X EPAOL frame!
[ 3110.761902] alg name:CCMP
[ 3110.761924] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3110.763027] alg name:TKIP
[ 3110.763057] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3116.650361] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3116.650371] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3116.650376] ====>remove Tx_TS_admin_list
[ 3116.650706] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3116.650716] notify_wx_assoc_event(): Tell user space disconnected
[ 3116.650776] ===>rtllib_associate_procedure_wq(), chan:1
[ 3116.650782] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3116.662203] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3116.666032] Associated successfully
[ 3116.666035] normal associate
[ 3116.666042] Using G rates:108
[ 3116.666043] Successfully associated, ht enabled
[ 3116.666046] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3116.676068] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3116.695079] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3116.695094] ====>to send ADDBARSP
[ 3116.701141] RX: IEEE802.1X EPAOL frame!
[ 3116.705974] RX: IEEE802.1X EPAOL frame!
[ 3116.706166] alg name:CCMP
[ 3116.706189] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3116.707256] alg name:TKIP
[ 3116.707285] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[ 3122.650335] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[ 3122.650345] ===========>RemovePeerTS,00:23:69:98:2f:5e
[ 3122.650350] ====>remove Tx_TS_admin_list
[ 3122.650679] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3122.650690] notify_wx_assoc_event(): Tell user space disconnected
[ 3122.650751] ===>rtllib_associate_procedure_wq(), chan:1
[ 3122.650756] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3122.663002] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3122.666802] Associated successfully
[ 3122.666804] normal associate
[ 3122.666812] Using G rates:108
[ 3122.666813] Successfully associated, ht enabled
[ 3122.666816] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 3122.676838] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3122.734492] ====>rx ADDBAREQ from :00:23:69:98:2f:5e
[ 3122.734508] ====>to send ADDBARSP
[ 3122.739403] RX: IEEE802.1X EPAOL frame!
[ 3122.746843] RX: IEEE802.1X EPAOL frame!
[ 3122.747026] alg name:CCMP
[ 3122.747049] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 3122.748963] alg name:TKIP
[ 3122.748993] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0

6 ) Network configuration
Code:
$ sudo lshw -C network
*-network
description: Wireless interface
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 10
serial: 70:f1:a1:be:74:47
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=192.168.1.105 latency=0 link=yes multicast=yes wireless=802.11bgn
resources: irq:17 ioport:3000(size=256) memory:d0100000-d0103fff
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 02
serial: c8:0a:a9:c4:51:79
size: 10MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
resources: irq:26 ioport:2000(size=256) memory:d0010000-d0010fff(prefetchable) memory:d0000000-d000ffff(prefetchable) memory:d0020000-d002ffff(prefetchable)

7 ) Scan for networks:
Code:
$ iwlist scan
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wlan0 Scan completed :
Cell 01 - Address: 00:23:69:98:2F:5E
ESSID:"nostrum"
Protocol:IEEE802.11N-24G
Mode:Master
Channel:1
Encryption key:on
Bit Rates:130 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54
Quality=87/100 Signal level=-58 dBm Noise level=-113 dBm
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD0E0050F204104A0001101044000102
Extra: Last beacon: 292ms ago

8 ) Ubuntu Version:
Code:
$ lsb_release -d
Ubuntu 10.04.1 LTS
9 ) Kernel/architectlure (including 32 vs. 64 bit):
Code:
$ uname -mr
2.6.32-24-generic x86_64

10 ) Restarting the network:
Code:
$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... [ OK ]
	[ OK ]

---

### Post by Brotherbrat13 on 2010-08-06
I posted this in the brightness thread. I feel bad for Hijacking it into a wireless troubleshoot thread.

...Does compaq even have a CQ63 Model yet? I can't find ANYTHING about a  CQ63 on google, at all. There is, however, a CQ62-228DX.

But yes, we have the same card. The Realtek 8171 (rev 10).

$ iwconfig wlan0
wlan0 802.11bgn ESSID:"nostrum" Nickname:"rtl8191SEVA2"
Mode :Managed Frequency=2.412 GHz Access Point: 00:23:69:98:2F:5E
Bit Rate=65 Mb/s
Retry: on RTS thr: off Fragment thr: off
Encryption key: [deleted by poster] Security mode: open
**[COLOR=Red]Power Management: off[/COLOR]**
Link Quality=88/100 Signal level=-54 dBm Noise level=-114 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0                      


Mine is much different.

iwconfig wlan0
wlan0     802.11bgn  ESSID:"Wizard"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:25:9C:A5:88:21   
          Bit Rate=120 Mb/s   
          Retry: on   RTS thr: off   Fragment thr: off
          **[COLOR=Red]Power Management period:0us  mode:All packets received[/COLOR]**
          Link Quality=82/100  Signal level=-58 dBm  Noise level=-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




Hope we find a fix for this soon. My Wifi stays connected for about 30 minutes, then starts the cycle of 10 seconds per re-connect until I put it to sleep/resume, then I get another 30 minutes.

---

### Post by nanonils on 2010-08-07
> **Brotherbrat13 said:**
> 
...Does compaq even have a CQ63 Model yet? I can't find ANYTHING about a  CQ63 on google, at all. There is, however, a CQ62-228DX.

You are completely right, it is a CQ62 model. 

Glad I could fool you into thinking I had already bought the much anticipated next $329 magic (surely there will be a press conference at launch day). Ha!

I'm now working my way again through the WiFi guide ([https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)) to see whether I overlooked something (I'm encouraged after virtualbox iOS4 upgrading, jailbreaking and unlocking my 3GS phone while waiting for the Dell Streak...).

---

### Post by nanonils on 2010-08-07
Very odd: 
[LIST]
[*]I have no problem starting and checking with the Update Manager but the downloading of package files doesn't work (error: "Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)")
[/LIST]
[LIST]
[*]the weather applet is always up-to-date
[/LIST]
[LIST]
[*]with a bit of luck I can connect to the Google homepage and to Google news
[/LIST]

Guess that means I have a connection that works for a few seconds and then stops to transfer?

---

### Post by nanonils on 2010-08-07
Another thing that is curious is that "lspi" calls the device 8171 (rev 10) but the driver in use are rtl8192 throughout the output in above post:

```
$ lspci
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
Subsystem: Hewlett-Packard Company Device 1467
[...]
Kernel driver in use: rtl819xSE
Kernel modules: r8192se_pci
```

Maybe we ought to try a different driver? They are available for download here: [http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

I just can't find anything for "8171"...

Also above the network is called "rtl8191SEVA2" and not 819**2**

---

### Post by nanonils on 2010-08-07
There could be two competing drivers: 

"The Realtek **RTL8191SE** is a highly integrated single-chip MIMO (Multiple In, Multiple Out) Wireless LAN (WLAN) solution for the wireless high throughput 802.11n specification. It combines a MAC, a **1T2R** capable baseband, and RF in a single chip. The RTL8191SE provides a complete solution for a high throughput performance wireless client." ([http://www.realtek.com/products/productsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226](http://www.realtek.com/products/productsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226))

The Realtek **RTL8192SE** is a highly integrated single-chip MIMO (Multiple In, Multiple Out) Wireless LAN (WLAN) solution for the wireless high throughput 802.11n specification. It combines a MAC, a **2T2R** capable baseband, and RF in a single chip. The RTL8192SE provides a complete solution for a high throughput performance wireless client. [http://www.realtek.com/products/productsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=230](http://www.realtek.com/products/productsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=230)

---

### Post by nanonils on 2010-08-07
Uurgh: looks like we are going through the same motions here that Wtfrak did [http://ubuntuforums.org/showthread.php?t=1491899](http://ubuntuforums.org/showthread.php?t=1491899)

Other distros are affected as well: [https://bugzilla.redhat.com/show_bug.cgi?id=562902](https://bugzilla.redhat.com/show_bug.cgi?id=562902)

Guess I'll stick with system76.com in the future... Compaq "cheap" is costly in man hours needed to fix stuff after the purchase.

---

### Post by nanonils on 2010-08-07
Update: downloading the 0017 driver ([http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)) and installing as in the included txt file doesn't change anything...

---

### Post by Brotherbrat13 on 2010-08-07
I have no idea whats going on inside your install, because for some reason, after a random restart, my wireless works flawlessly. It works so well, even, that Its connected and waiting for me before I can even log on.

Try blacklisting one of the drivers to see if your wifi either starts working, or completely stops. With both of them. I'm just an ubuntu beginner, so I'm not sure if that will work or not... but its how I fixed my old wireless USB stick on my desktop back in the day.

```
 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci 
```is what my output reads.


Something else that might be useful, I'm using wubi.

---

### Post by nanonils on 2010-08-07
How do I blackist that?

I added "blacklist rtl819xSE" to the end of my blacklist.conf but it still seems to load when I check with lspci. Do I have to replace the "x" in that name? 

Sorry, I'm such a noob...

Funny - after rebooting my sound panel control has disappeared...

---

### Post by nanonils on 2010-08-07
added to blacklist 

blacklist rtl8191SE
blacklist rtl8192SE
blacklist 8171

But the thing is still loading. OK off for the day now, enough Linux tinkering already.

---

### Post by Brotherbrat13 on 2010-08-07
You blacklisted them correctly, but I think there was a line you had to run to remove the driver from the kernal.

Something like modprobe -r rtl8191SE to make it use 8192. Don't quote me on that though, it was a long time ago. I'm not that much better then you when it comes to linux. =l

Its at the point now where I can't actually try out what I'm telling you, since my Wifi works and I don't want to screw with it. Hopefully I don't kill your chances of getting your Wifi working.

---

### Post by nanonils on 2010-08-08
> **Brotherbrat13 said:**
> You blacklisted them correctly, but I think there was a line you had to run to remove the driver from the kernal.

Something like modprobe -r rtl8191SE to make it use 8192. Don't quote me on that though, it was a long time ago. I'm not that much better then you when it comes to linux. =l

Its at the point now where I can't actually try out what I'm telling you, since my Wifi works and I don't want to screw with it. Hopefully I don't kill your chances of getting your Wifi working.

WHAT THE HELL?! It was a trivial DNS server issue?! Zippy now! [http://ubuntuforums.org/showthread.php?p=9693360#post9693360](http://ubuntuforums.org/showthread.php?p=9693360#post9693360)

Hahaha - I found this thread when searching for how to look up the driver name. After I had blacklisted a ton and it still didn't work I figured there must be other associated driver names/IDs (that's what this suggests: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)). Looking up drivers is really not straight forward with Linux for a noob like me.

Strange thing is I have always had the same settings on all Ubuntu notebooks with the same router: we currently have 3 more Lucid notebooks leaching on the same access point without any issues. WHY, WHY, WHY was that a problem now?

Update: stable up for >1 hour.

---

### Post by Brotherbrat13 on 2010-08-08
Glad you solved it! Guess I was thinking a little too much on the techinical side of it. Didn't even think to check IP configs.

---

