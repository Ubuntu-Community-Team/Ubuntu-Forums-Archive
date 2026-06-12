---
title: "my wifi disconnect all the time !"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by poulou on 2012-05-05
since upgrade to version 12.04, my wifi disconnect randomly,not possible to reconnect it !

[HTML]medion akoya E7214[/HTML]
[HTML]lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
06:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
[/HTML]

[HTML]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 0c45:6310 Microdia Sonix USB 2.0 Camera
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
[/HTML]

[HTML] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:bf:96:6c  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:febf:966c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55761 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:106064757 (106.0 MB)  TX bytes:8109028 (8.1 MB)
          Interrupt:49 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15576 (15.5 KB)  TX bytes:15576 (15.5 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:e5:c4:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:53794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70416391 (70.4 MB)  TX bytes:3240338 (3.2 MB)
[/HTML]

[HTML] iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
[/HTML]

[HTML]  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:bf:96:6c  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:febf:966c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55761 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:106064757 (106.0 MB)  TX bytes:8109028 (8.1 MB)
          Interrupt:49 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15576 (15.5 KB)  TX bytes:15576 (15.5 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:e5:c4:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:53794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70416391 (70.4 MB)  TX bytes:3240338 (3.2 MB)

poulou@poulou-E7214:~$  iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
poulou@poulou-E7214:~$  lsmod
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174055  1 
rtl8192se              94189  0 
rtlwifi                95804  1 rtl8192se
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              436455  2 rtl8192se,rtlwifi
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
cfg80211              178679  2 rtlwifi,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    36570  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
uvcvideo               67203  0 
intel_ips              17753  0 
acer_wmi               23612  0 
i915                  414603  8 
sparse_keymap          13658  1 acer_wmi
videodev               86588  1 uvcvideo
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
psmouse                72919  0 
serio_raw              13027  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mac_hid                13077  0 
wmi                    18744  1 acer_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
uas                    17699  0 
atl1c                  36718  0 
[/HTML]

[HTML]2000 mBm)
[ 1584.091105] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1584.091111] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1584.091116] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1584.091122] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1585.197957] wlan0: authenticate with 96:84:0d:da:69:9d (try 1)
[ 1585.199688] wlan0: authenticated
[ 1585.200134] wlan0: associate with 96:84:0d:da:69:9d (try 1)
[ 1585.205052] wlan0: RX ReassocResp from 96:84:0d:da:69:9d (capab=0x431 status=0 aid=1)
[ 1585.205063] wlan0: associated
[ 1585.216395] cfg80211: Calling CRDA for country: BE
[ 1585.223521] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223527] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223530] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223534] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223537] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223540] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223543] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223547] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223550] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223553] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223556] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223559] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223563] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223566] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223569] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223573] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223576] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223580] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223583] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223586] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223590] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223593] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223596] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223600] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223602] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1585.223606] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1585.223609] cfg80211: Disabling freq 2484 MHz
[ 1585.223615] cfg80211: Regulatory domain changed to country: BE
[ 1585.223618] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1585.223621] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1585.223624] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1585.223627] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1585.223630] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 1586.219439] wlan0: deauthenticated from 96:84:0d:da:69:9d (Reason: 2)
[ 1586.249877] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1586.249888] cfg80211: Restoring regulatory settings
[ 1586.249895] cfg80211: Calling CRDA to update world regulatory domain
[ 1586.258719] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1586.258727] cfg80211: World regulatory domain updated:
[ 1586.258732] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1586.258738] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1586.258744] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1586.258750] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1586.258756] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1586.258761] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1587.357711] wlan0: authenticate with 96:84:0d:da:69:9d (try 1)
[ 1587.359581] wlan0: authenticated
[ 1587.359920] wlan0: associate with 96:84:0d:da:69:9d (try 1)
[ 1587.364943] wlan0: RX ReassocResp from 96:84:0d:da:69:9d (capab=0x431 status=0 aid=1)
[ 1587.364951] wlan0: associated
[ 1587.376435] cfg80211: Calling CRDA for country: BE
[ 1587.385672] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385681] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385686] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385693] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385698] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385704] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385709] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385716] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385721] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385727] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385732] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385738] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385743] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385749] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385754] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385760] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385765] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385772] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385777] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385783] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385788] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385794] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385799] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385805] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385810] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1587.385816] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1587.385821] cfg80211: Disabling freq 2484 MHz
[ 1587.385830] cfg80211: Regulatory domain changed to country: BE
[ 1587.385834] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1587.385840] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1587.385845] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1587.385850] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1587.385855] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 1588.385091] wlan0: deauthenticated from 96:84:0d:da:69:9d (Reason: 2)
[ 1588.437536] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1588.437548] cfg80211: Restoring regulatory settings
[ 1588.437557] cfg80211: Calling CRDA to update world regulatory domain
[ 1588.445659] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1588.445668] cfg80211: World regulatory domain updated:
[ 1588.445673] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1588.445680] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1588.445686] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1588.445692] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1588.445697] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1588.445703] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1597.211913] wlan0: authenticate with 00:18:e7:e2:dc:14 (try 1)
[ 1597.213581] wlan0: authenticated
[ 1597.233670] wlan0: associate with 00:18:e7:e2:dc:14 (try 1)
[ 1597.238704] wlan0: RX AssocResp from 00:18:e7:e2:dc:14 (capab=0x421 status=0 aid=2)
[ 1597.238711] wlan0: associated
[ 1607.471403] wlan0: no IPv6 routers present
[ 3531.188097] show_signal_msg: 21 callbacks suppressed
[ 3531.188103] chromium-browse[4981]: segfault at 34 ip b00bfda9 sp bfe43f00 error 4 in npMyrMus.so[afe68000+2e7000]
[20440.318062] hub 1-1:1.0: unable to enumerate USB device on port 1
[21628.874854] usb 1-1.1: new low-speed USB device number 7 using ehci_hcd
[21628.946698] usb 1-1.1: device descriptor read/64, error -32
[21629.122422] usb 1-1.1: device descriptor read/64, error -32
[21629.298026] usb 1-1.1: new low-speed USB device number 8 using ehci_hcd
[21629.369882] usb 1-1.1: device descriptor read/64, error -32
[21629.545514] usb 1-1.1: device descriptor read/64, error -32
[21629.721154] usb 1-1.1: new low-speed USB device number 9 using ehci_hcd
[21630.128150] usb 1-1.1: device not accepting address 9, error -32
[21630.200214] usb 1-1.1: new low-speed USB device number 10 using ehci_hcd
[21630.607233] usb 1-1.1: device not accepting address 10, error -32
[21630.607415] hub 1-1:1.0: unable to enumerate USB device on port 1
[22687.572276] atl1c 0000:06:00.0: atl1c: eth0 NIC Link is Down
[22688.189513] atl1c 0000:06:00.0: irq 49 for MSI/MSI-X
[22688.249778] ADDRCONF(NETDEV_UP): eth0: link is not ready
[23241.646960] cfg80211: All devices are disconnected, going to restore regulatory settings
[23241.646972] cfg80211: Restoring regulatory settings
[23241.646981] cfg80211: Calling CRDA to update world regulatory domain
[23241.656808] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[23241.656816] cfg80211: World regulatory domain updated:
[23241.656820] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[23241.656827] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[23241.656833] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[23241.656838] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[23241.656844] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[23241.656850] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[23242.794725] wlan0: authenticate with 00:18:e7:e2:dc:14 (try 1)
[23242.992167] wlan0: authenticate with 00:18:e7:e2:dc:14 (try 2)
[23243.191750] wlan0: authenticate with 00:18:e7:e2:dc:14 (try 3)
[23243.391381] wlan0: authentication with 00:18:e7:e2:dc:14 timed out
[23249.385610] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23249.583028] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23249.782678] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23249.982261] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23255.976461] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23256.173964] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23256.373559] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23256.573147] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23257.182478] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23262.571325] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23262.768880] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23262.968436] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23263.168061] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23269.166065] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23269.363635] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23269.563248] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23269.762858] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23275.792956] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23275.990441] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23276.190023] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23276.389609] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23282.427671] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23282.625235] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23282.824833] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23283.024439] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23289.054526] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23289.252038] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23289.451644] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23289.651226] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23295.689366] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23295.886825] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23296.086441] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23296.286032] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23302.316108] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23302.513605] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23302.713204] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23302.912846] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23304.471950] atl1c 0000:06:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[23304.472194] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[23304.493761] usb 1-1.1: new low-speed USB device number 11 using ehci_hcd
[23304.569806] usb 1-1.1: device descriptor read/64, error -32
[23304.745309] usb 1-1.1: device descriptor read/64, error -32
[23304.921148] usb 1-1.1: new low-speed USB device number 12 using ehci_hcd
[23304.992950] usb 1-1.1: device descriptor read/64, error -32
[23305.168614] usb 1-1.1: device descriptor read/64, error -32
[23305.344264] usb 1-1.1: new low-speed USB device number 13 using ehci_hcd
[23305.755384] usb 1-1.1: device not accepting address 13, error -32
[23305.831303] usb 1-1.1: new low-speed USB device number 14 using ehci_hcd
[23306.242254] usb 1-1.1: device not accepting address 14, error -32
[23306.242495] hub 1-1:1.0: unable to enumerate USB device on port 1
[23308.954957] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23309.152387] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23309.351996] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23309.551644] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23315.000142] eth0: no IPv6 routers present
[23315.588764] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23315.786213] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23315.985780] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23316.185270] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23322.176465] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23322.373811] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23322.573391] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23322.772815] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23328.803953] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23329.001375] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23329.200838] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23329.400377] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23335.399502] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23335.596860] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23335.796356] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23335.995918] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23341.995009] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23342.192394] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23342.391960] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23342.591478] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23348.582668] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23348.779964] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23348.979482] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23349.179013] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23355.194119] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23355.391618] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23355.591098] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23355.790601] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23361.782377] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23361.979155] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23362.178679] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23362.378142] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23368.409184] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23368.606628] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23368.806099] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23369.005600] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23375.016709] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23375.214113] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23375.413586] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23375.613096] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23384.640969] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23384.838135] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23385.038332] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23385.241152] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23391.276226] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23391.473608] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23391.673082] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23391.872589] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23397.923623] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23398.121073] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23398.320641] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23398.520052] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23404.515183] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23404.712610] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23404.916135] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23405.115661] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23411.150691] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23411.348076] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23411.547575] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23411.747040] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23417.766224] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23417.963584] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23418.163064] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23418.362544] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23424.397716] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23424.595054] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23424.794557] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23424.994092] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23431.053050] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23431.250516] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23431.449959] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23431.649553] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23437.648563] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23437.846018] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23438.045599] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23438.245029] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23447.476064] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23447.673498] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23447.872983] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23448.072502] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23454.095569] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23454.292995] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23454.492512] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23454.691993] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23460.711100] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23460.908502] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23461.108019] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23461.307526] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23467.326712] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23467.524127] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23467.723615] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23467.923081] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23473.934226] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23474.131573] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23474.331143] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23474.530611] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23480.525770] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23480.723143] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23480.922697] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23481.122151] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23487.113310] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23487.310703] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23487.510204] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23487.709706] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23493.720856] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23493.918320] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23494.117823] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23494.317336] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23500.316395] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23500.513833] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23500.713358] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23500.912837] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23510.353361] wlan0: direct probe to 96:84:0d:da:69:9d (try 1/3)
[23510.552834] wlan0: direct probe to 96:84:0d:da:69:9d (try 2/3)
[23510.752339] wlan0: direct probe to 96:84:0d:da:69:9d (try 3/3)
[23510.951862] wlan0: direct probe to 96:84:0d:da:69:9d timed out
[23517.152465] wlan0: direct probe to 96:84:0d:da:69:9d (try 1/3)
[23517.351834] wlan0: direct probe to 96:84:0d:da:69:9d (try 2/3)
[23517.551324] wlan0: direct probe to 96:84:0d:da:69:9d (try 3/3)
[23517.750840] wlan0: direct probe to 96:84:0d:da:69:9d timed out
[23523.931564] wlan0: direct probe to 96:84:0d:da:69:9d (try 1/3)
[23524.134924] wlan0: direct probe to 96:84:0d:da:69:9d (try 2/3)
[23524.334498] wlan0: direct probe to 96:84:0d:da:69:9d (try 3/3)
[23524.533927] wlan0: direct probe to 96:84:0d:da:69:9d timed out
[23530.734630] wlan0: direct probe to 96:84:0d:da:69:9d (try 1/3)
[23530.934016] wlan0: direct probe to 96:84:0d:da:69:9d (try 2/3)
[23531.133521] wlan0: direct probe to 96:84:0d:da:69:9d (try 3/3)
[23531.333002] wlan0: direct probe to 96:84:0d:da:69:9d timed out
[23537.513710] wlan0: direct probe to 96:84:0d:da:69:9d (try 1/3)
[23537.713071] wlan0: direct probe to 96:84:0d:da:69:9d (try 2/3)
[23537.912578] wlan0: direct probe to 96:84:0d:da:69:9d (try 3/3)
[23538.112104] wlan0: direct probe to 96:84:0d:da:69:9d timed out
[23544.304775] wlan0: direct probe to 96:84:0d:da:69:9d (try 1/3)
[23544.504194] wlan0: direct probe to 96:84:0d:da:69:9d (try 2/3)
[23544.703675] wlan0: direct probe to 96:84:0d:da:69:9d (try 3/3)
[23544.903239] wlan0: direct probe to 96:84:0d:da:69:9d timed out
[23551.064021] wlan0: direct probe to 96:84:0d:da:69:9d (try 1/3)
[23551.263300] wlan0: direct probe to 96:84:0d:da:69:9d (try 2/3)
[23551.462871] wlan0: direct probe to 96:84:0d:da:69:9d (try 3/3)
[23551.662351] wlan0: direct probe to 96:84:0d:da:69:9d timed out
[23557.839136] wlan0: direct probe to 96:84:0d:da:69:9d (try 1/3)
[23558.038446] wlan0: direct probe to 96:84:0d:da:69:9d (try 2/3)
[23558.237919] wlan0: direct probe to 96:84:0d:da:69:9d (try 3/3)
[23558.437486] wlan0: direct probe to 96:84:0d:da:69:9d timed out
[23564.638389] wlan0: direct probe to 96:84:0d:da:69:9d (try 1/3)
[23564.837511] wlan0: direct probe to 96:84:0d:da:69:9d (try 2/3)
[23565.041026] wlan0: direct probe to 96:84:0d:da:69:9d (try 3/3)
[23565.240504] wlan0: direct probe to 96:84:0d:da:69:9d timed out
[23806.577052] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23806.774438] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23806.973947] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23807.173460] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23819.165659] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23819.363139] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23819.562632] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23819.762097] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23825.785256] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23825.982561] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23826.182133] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23826.381608] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23832.432665] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23832.630049] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23832.829550] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23833.029043] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23839.020150] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23839.217686] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23839.417111] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23839.616655] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23845.663658] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23845.861070] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23846.060508] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23846.260067] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23852.303183] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23852.500557] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23852.700075] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23852.899570] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23858.894620] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23859.092068] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23859.291546] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23859.491056] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23869.416501] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23869.613862] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23869.813379] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23870.012921] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23876.008034] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23876.205433] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23876.404900] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23876.604484] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23882.595637] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23882.793020] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23882.992545] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23883.192107] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23889.227115] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23889.424495] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23889.623972] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23889.823494] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23895.830627] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23896.027984] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23896.227501] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23896.426988] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23902.478083] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23902.675417] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23902.874953] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23903.074459] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23909.093576] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23909.290969] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23909.490466] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23909.694001] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23915.721059] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23915.918479] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23916.117997] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23916.321429] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[23922.356470] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 1/3)
[23922.553907] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 2/3)
[23922.753379] wlan0: direct probe to 00:18:e7:e2:dc:14 (try 3/3)
[23922.952986] wlan0: direct probe to 00:18:e7:e2:dc:14 timed out
[/HTML]

[HTML]sudo lshw -C network
[sudo] password for poulou: 
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c0
       serial: 00:26:2d:bf:96:6c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.196 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:49 memory:fbb00000-fbb3ffff ioport:d000(size=128)
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 10
       serial: 1c:4b:d6:e5:c4:00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:c000(size=256) memory:fba00000-fba03fff
[/HTML]

[HTML] iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 90:84:0D:DA:69:9D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Knokke ICED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003b2a38e9160
                    Extra: Last beacon: 824ms ago
                    IE: Unknown: 000B4B6E6F6B6B652049434544
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706424520010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010690840DDA699D
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 02 - Address: 00:18:E7:E2:DC:14
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"Seaweed-Sails Hospital"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011fc4c0180
                    Extra: Last beacon: 932ms ago
                    IE: Unknown: 0016536561776565642D5361696C7320486F73706974616C
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001800000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000000000000000000000000000000000000000000
                    IE: Unknown: 050400010004
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: 96:84:0D:DA:69:9D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Knokke ICED's Guest Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003b2a38e9160
                    Extra: Last beacon: 772ms ago
                    IE: Unknown: 001B4B6E6F6B6B6520494345442773204775657374204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 0706424520010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710208
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010690840DDA699D

eth0      Interface doesn't support scanning.

[/HTML]

[HTML]lsb_release -d
Description:	Ubuntu 12.04 LTS
 uname -mr
3.2.0-24-generic-pae i686

[HTML]sudo /etc/init.d/networking restart
[sudo] password for poulou: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/NetworkManager.conf.
[/HTML]
[/HTML]

---

