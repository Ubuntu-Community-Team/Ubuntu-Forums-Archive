---
title: "eMachines M5310 /w BCM4306 wireless card, ubuntu 9.10, speed fluctations"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by gmcbpi on 2010-03-19
Hello, I have an old eMachines M5310 with a mini pci Broadcom 4306 wireless card. I have activated the card using the hardware drivers option in administration. I'm pretty sure it just downloads b43-fwcutter, then downloads wl_apsta.o then installs it to lib/firmware. It works, everything connects but at the first use i download at my full speed of 350Kb/s(3mbps). But then when i restart the computer the speed drops to 150kB/s. It seems to fluctuate up and down for some reason. I don't know why, but can anyone help me on this? Here are some outputs from various commands:
lspci 
```
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

```ifconfig of wlan0 and wmaster0-00
```
wlan0     Link encap:Ethernet  HWaddr 00:90:96:5b:df:0e  
          inet addr:192.168.1.78  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fe5b:df0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58134914 (58.1 MB)  TX bytes:7200759 (7.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-96-5B-DF-0E-35-62-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```iwconfig of wlan0 
```
wlan0     IEEE 802.11bg  ESSID:"2WIRE356"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:7C:7C:92:39   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:A1FB-7758-8133-85AE-BF4C-CDA1-4B4B-6294-0619-9E54-ED80
```lsmod
```
Module                  Size  Used by
binfmt_misc             8356  1 
snd_ali5451            18888  2 
snd_ac97_codec        101216  1 snd_ali5451
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
arc4                    1660  2 
snd_seq_midi            6464  0 
ecb                     2524  2 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10240  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 36808  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6688  0 
b43legacy             117784  0 
lp                      8964  0 
snd                    59204  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali15x3             6336  0 
yenta_socket           24296  1 
soundcore               7264  1 snd
mac80211              181140  1 b43legacy
parport_pc             31940  1 
i2c_ali1535             5792  0 
rsrc_nonstatic         11644  1 yenta_socket
psmouse                56500  0 
cfg80211               93052  2 b43legacy,mac80211
shpchp                 32272  0 
snd_page_alloc          9156  1 snd_pcm
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               4096  1 b43legacy
serio_raw               5280  0 
parport                35340  3 ppdev,lp,parport_pc
b44                    28652  0 
mii                     5212  1 b44
ssb                    35524  2 b43legacy,b44
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  1 
agpgart                34988  3 ttm,drm,ati_agp

```dmesg
```
   23.709814] b43legacy-phy0: Broadcom 4306 WLAN found
[   23.716778] ppdev: user-space parallel port driver
[   23.733099] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   23.733129] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   23.733580] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0078, PCI irq 10
[   23.733585] yenta_cardbus 0000:00:0a.0: Socket status: 30000006
[   23.756933] b43legacy-phy0 debug: Radio initialized
[   23.801634] cfg80211: World regulatory domain updated:
[   23.801643]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.801649]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.801653]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.801657]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.801661]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.801664]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.067611] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x2348b3, caps: 0x904713/0x10008
[   24.101993] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   24.323762] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.458281] phy0: Selected rate control algorithm 'minstrel'
[   24.459290] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
[   24.556360] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   24.558962] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   24.559985] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   24.560952] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   24.562110] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   24.814702] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[   24.831850] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 11
[   24.831863] ALI 5451 0000:00:08.0: PCI INT A -> Link[LNK7] -> GSI 11 (level, low) -> IRQ 11
[   25.376229] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   25.436366] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   25.632070] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   25.696556] b43legacy-phy0 debug: Chip initialized
[   25.697070] b43legacy-phy0 debug: 30-bit DMA initialized
[   25.697321] Registered led device: b43legacy-phy0::tx
[   25.697345] Registered led device: b43legacy-phy0::rx
[   25.697371] Registered led device: b43legacy-phy0::radio
[   25.697407] b43legacy-phy0 debug: Wireless interface started
[   25.697422] b43legacy-phy0 debug: Adding Interface type 2
[   25.704268] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.295292] type=1505 audit(1269034666.756:12): operation="profile_replace" pid=920 name=/usr/share/gdm/guest-session/Xsession
[   26.298653] type=1505 audit(1269034666.760:13): operation="profile_replace" pid=921 name=/sbin/dhclient3
[   26.299056] type=1505 audit(1269034666.760:14): operation="profile_replace" pid=921 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   26.299282] type=1505 audit(1269034666.760:15): operation="profile_replace" pid=921 name=/usr/lib/connman/scripts/dhclient-script
[   26.314335] type=1505 audit(1269034666.776:16): operation="profile_replace" pid=922 name=/usr/bin/evince
[   26.323071] type=1505 audit(1269034666.784:17): operation="profile_replace" pid=922 name=/usr/bin/evince-previewer
[   26.328526] type=1505 audit(1269034666.792:18): operation="profile_replace" pid=922 name=/usr/bin/evince-thumbnailer
[   26.338417] type=1505 audit(1269034666.800:19): operation="profile_replace" pid=924 name=/usr/lib/cups/backend/cups-pdf
[   26.338942] type=1505 audit(1269034666.800:20): operation="profile_replace" pid=924 name=/usr/sbin/cupsd
[   29.832038] AC'97 1 does not respond - RESET
[   29.848033] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   29.848089] ali mixer 1 creating error.
[   30.937290] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   30.937324] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   30.937380] pci 0000:01:05.0: putting AGP V2 device into 4x mode
[   31.072474] [drm] Setting GART location based on new memory map
[   31.072491] [drm] Loading R100 Microcode
[   31.072541] [drm] writeback test succeeded in 1 usecs
[   37.333290] glxinfo:1479 freeing invalid memtype d4102000-d4112000
[   37.333305] glxinfo:1479 freeing invalid memtype d4112000-d4122000
[   37.333314] glxinfo:1479 freeing invalid memtype d4122000-d4132000
[   37.333322] glxinfo:1479 freeing invalid memtype d4132000-d4142000
[   37.333330] glxinfo:1479 freeing invalid memtype d4142000-d4152000
[   37.333339] glxinfo:1479 freeing invalid memtype d4152000-d4162000
[   37.333347] glxinfo:1479 freeing invalid memtype d4162000-d4172000
[   37.333355] glxinfo:1479 freeing invalid memtype d4172000-d4182000
[   37.333363] glxinfo:1479 freeing invalid memtype d4182000-d4192000
[   37.333371] glxinfo:1479 freeing invalid memtype d4192000-d41a2000
[   37.333380] glxinfo:1479 freeing invalid memtype d41a2000-d41b2000
[   37.333388] glxinfo:1479 freeing invalid memtype d41b2000-d41c2000
[   37.333396] glxinfo:1479 freeing invalid memtype d41c2000-d41d2000
[   37.333404] glxinfo:1479 freeing invalid memtype d41d2000-d41e2000
[   37.333412] glxinfo:1479 freeing invalid memtype d41e2000-d41f2000
[   37.333421] glxinfo:1479 freeing invalid memtype d41f2000-d4202000
[   37.333429] glxinfo:1479 freeing invalid memtype d4202000-d4212000
[   37.333437] glxinfo:1479 freeing invalid memtype d4212000-d4222000
[   37.333445] glxinfo:1479 freeing invalid memtype d4222000-d4232000
[   37.333453] glxinfo:1479 freeing invalid memtype d4232000-d4242000
[   37.333461] glxinfo:1479 freeing invalid memtype d4242000-d4252000
[   37.333469] glxinfo:1479 freeing invalid memtype d4252000-d4262000
[   37.333478] glxinfo:1479 freeing invalid memtype d4262000-d4272000
[   37.333486] glxinfo:1479 freeing invalid memtype d4272000-d4282000
[   37.333494] glxinfo:1479 freeing invalid memtype d4282000-d4292000
[   37.333502] glxinfo:1479 freeing invalid memtype d4292000-d42a2000
[   37.333510] glxinfo:1479 freeing invalid memtype d42a2000-d42b2000
[   37.333519] glxinfo:1479 freeing invalid memtype d42b2000-d42c2000
[   37.333527] glxinfo:1479 freeing invalid memtype d42c2000-d42d2000
[   37.333535] glxinfo:1479 freeing invalid memtype d42d2000-d42e2000
[   37.333543] glxinfo:1479 freeing invalid memtype d42e2000-d42f2000
[   37.333550] glxinfo:1479 freeing invalid memtype d42f2000-d4302000
[   43.987203] wlan0: authenticate with AP 00:21:7c:7c:92:39
[   43.995272] wlan0: authenticated
[   43.995286] wlan0: associate with AP 00:21:7c:7c:92:39
[   43.997047] wlan0: RX AssocResp from 00:21:7c:7c:92:39 (capab=0x431 status=0 aid=2)
[   43.997055] wlan0: associated
[   44.011386] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   44.028352] cfg80211: Calling CRDA for country: US
[   44.038887] cfg80211: Received country IE:
[   44.038896] cfg80211: Regulatory domain: US
[   44.038900]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   44.038904]     (2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   44.038907] cfg80211: CRDA thinks this should applied:
[   44.038910] cfg80211: Regulatory domain: US
[   44.038912]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   44.038916]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   44.038919]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   44.038923]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.038927]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.038931]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   44.038933] cfg80211: We intersect both of these and get:
[   44.038936] cfg80211: Regulatory domain: 98
[   44.038938]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   44.038942]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   44.038953] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[   44.038956] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   44.038959] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   44.038966] cfg80211: Current regulatory domain updated by AP to: US
[   44.038968]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   44.038972]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   54.384035] wlan0: no IPv6 routers present
[   77.560997] b43legacy-phy0 ERROR: PHY transmission error
[   87.516213] b43legacy-phy0 ERROR: PHY transmission error
[   92.116066] Clocksource tsc unstable (delta = -157434477 ns)
[   98.404431] b43legacy-phy0 ERROR: PHY transmission error
[   98.687344] b43legacy-phy0 ERROR: PHY transmission error
[  100.787875] b43legacy-phy0 ERROR: PHY transmission error
[  100.813968] b43legacy-phy0 ERROR: PHY transmission error
[  105.665984] b43legacy-phy0 ERROR: PHY transmission error
[  106.724874] b43legacy-phy0 ERROR: PHY transmission error
[  110.630626] b43legacy-phy0 ERROR: PHY transmission error
[  110.630660] b43legacy-phy0 ERROR: PHY transmission error
[  110.826936] b43legacy-phy0 ERROR: PHY transmission error
[  110.826974] b43legacy-phy0 ERROR: PHY transmission error
[  113.412758] b43legacy-phy0 ERROR: PHY transmission error
[  113.412793] b43legacy-phy0 ERROR: PHY transmission error
[  113.646757] b43legacy-phy0 ERROR: PHY transmission error
[  113.646790] b43legacy-phy0 ERROR: PHY transmission error
[  115.542019] b43legacy-phy0 ERROR: PHY transmission error
[  115.542056] b43legacy-phy0 ERROR: PHY transmission error
[  115.864872] b43legacy-phy0 ERROR: PHY transmission error
[  115.864906] b43legacy-phy0 ERROR: PHY transmission error
[  127.722584] b43legacy-phy0 ERROR: PHY transmission error
[  129.542468] b43legacy-phy0 ERROR: PHY transmission error
[  130.924270] b43legacy-phy0 ERROR: PHY transmission error
[  134.577653] b43legacy-phy0 ERROR: PHY transmission error
[  136.355981] b43legacy-phy0 ERROR: PHY transmission error
[  136.806836] b43legacy-phy0 ERROR: PHY transmission error
[  140.261325] b43legacy-phy0 ERROR: PHY transmission error
[  140.974983] b43legacy-phy0 ERROR: PHY transmission error
[  143.065641] b43legacy-phy0 ERROR: PHY transmission error
[  143.536083] b43legacy-phy0 ERROR: PHY transmission error
[  149.157402] b43legacy-phy0 ERROR: PHY transmission error
[  150.759034] b43legacy-phy0 ERROR: PHY transmission error
[  156.870020] b43legacy-phy0 ERROR: PHY transmission error
[  157.505808] b43legacy-phy0 ERROR: PHY transmission error
[  179.768685] b43legacy-phy0 ERROR: PHY transmission error
[  184.535320] b43legacy-phy0 ERROR: PHY transmission error
[  199.906143] b43legacy-phy0 ERROR: PHY transmission error
[  200.419152] b43legacy-phy0 ERROR: PHY transmission error
[  221.041390] b43legacy-phy0 ERROR: PHY transmission error
[  221.471799] b43legacy-phy0 ERROR: PHY transmission error
[  224.460034] b43legacy-phy0 ERROR: PHY transmission error
[  225.805485] b43legacy-phy0 ERROR: PHY transmission error
[  226.483661] b43legacy-phy0 ERROR: PHY transmission error
[  229.733454] b43legacy-phy0 ERROR: PHY transmission error
[  231.288474] b43legacy-phy0 ERROR: PHY transmission error
[  231.537460] b43legacy-phy0 ERROR: PHY transmission error
[  236.062277] b43legacy-phy0 ERROR: PHY transmission error
[  236.729599] b43legacy-phy0 ERROR: PHY transmission error
[  239.669327] b43legacy-phy0 ERROR: PHY transmission error
[  239.669362] b43legacy-phy0 ERROR: PHY transmission error
[  239.909726] b43legacy-phy0 ERROR: PHY transmission error
[  239.909762] b43legacy-phy0 ERROR: PHY transmission error
[  244.008067] b43legacy-phy0 ERROR: PHY transmission error
[  244.539543] b43legacy-phy0 ERROR: PHY transmission error
[  244.539580] b43legacy-phy0 ERROR: PHY transmission error
[  248.622789] b43legacy-phy0 ERROR: PHY transmission error
[  249.503260] b43legacy-phy0 ERROR: PHY transmission error
[  253.474681] b43legacy-phy0 ERROR: PHY transmission error
[  253.965335] b43legacy-phy0 ERROR: PHY transmission error
[  265.679410] b43legacy-phy0 ERROR: PHY transmission error
[  265.952668] b43legacy-phy0 ERROR: PHY transmission error
[  268.734726] b43legacy-phy0 ERROR: PHY transmission error
[  268.908333] b43legacy-phy0 ERROR: PHY transmission error
[  268.908365] b43legacy-phy0 ERROR: PHY transmission error
[  271.950216] b43legacy-phy0 ERROR: PHY transmission error
[  272.992078] b43legacy-phy0 ERROR: PHY transmission error
[  273.669253] b43legacy-phy0 ERROR: PHY transmission error
[  276.017036] b43legacy-phy0 ERROR: PHY transmission error
[  278.047555] b43legacy-phy0 ERROR: PHY transmission error
[  278.085014] b43legacy-phy0 ERROR: PHY transmission error
[  293.149617] b43legacy-phy0 ERROR: PHY transmission error
[  305.357427] b43legacy-phy0 ERROR: PHY transmission error
[  337.537177] b43legacy-phy0 ERROR: PHY transmission error
[  347.965415] b43legacy-phy0 ERROR: PHY transmission error
[  367.519366] b43legacy-phy0 ERROR: PHY transmission error
[  375.681185] b43legacy-phy0 ERROR: PHY transmission error
[  399.147011] b43legacy-phy0 ERROR: PHY transmission error
[  399.147040] b43legacy-phy0 ERROR: PHY transmission error
[  408.359525] b43legacy-phy0 ERROR: PHY transmission error
[  425.329849] b43legacy-phy0 ERROR: PHY transmission error
[  425.361673] b43legacy-phy0 ERROR: PHY transmission error
[  483.769651] b43legacy-phy0 ERROR: PHY transmission error
[  484.129875] b43legacy-phy0 ERROR: PHY transmission error
[  488.648702] b43legacy-phy0 ERROR: PHY transmission error
[  489.571747] b43legacy-phy0 ERROR: PHY transmission error
[  498.948797] b43legacy-phy0 ERROR: PHY transmission error
[  501.219571] b43legacy-phy0 ERROR: PHY transmission error
[  502.585102] b43legacy-phy0 ERROR: PHY transmission error
[  505.441827] b43legacy-phy0 ERROR: PHY transmission error
[  505.874830] b43legacy-phy0 ERROR: PHY transmission error
[  505.909010] b43legacy-phy0 ERROR: PHY transmission error
[  507.948309] b43legacy-phy0 ERROR: PHY transmission error
[  508.729055] b43legacy-phy0 ERROR: PHY transmission error
[  509.819111] b43legacy-phy0 ERROR: PHY transmission error
[  510.046497] b43legacy-phy0 ERROR: PHY transmission error
[  512.948068] b43legacy-phy0 ERROR: PHY transmission error
[  513.419442] b43legacy-phy0 ERROR: PHY transmission error
[  519.179111] b43legacy-phy0 ERROR: PHY transmission error
[  520.339404] b43legacy-phy0 ERROR: PHY transmission error
[  586.924395] b43legacy-phy0 ERROR: PHY transmission error
[  617.425509] b43legacy-phy0 ERROR: PHY transmission error
[  668.304865] b43legacy-phy0 ERROR: PHY transmission error
[  668.515205] b43legacy-phy0 ERROR: PHY transmission error
[  899.076574] b43legacy-phy0 ERROR: PHY transmission error
[  899.415530] b43legacy-phy0 ERROR: PHY transmission error
[  930.719409] b43legacy-phy0 ERROR: PHY transmission error
[  942.803140] b43legacy-phy0 ERROR: PHY transmission error
[ 1025.964972] b43legacy-phy0 ERROR: PHY transmission error
[ 1074.527842] b43legacy-phy0 ERROR: PHY transmission error
[ 1075.059638] b43legacy-phy0 ERROR: PHY transmission error
[ 1075.551621] b43legacy-phy0 ERROR: PHY transmission error
[ 1077.414736] b43legacy-phy0 ERROR: PHY transmission error
[ 1077.793098] b43legacy-phy0 ERROR: PHY transmission error
[ 1079.212532] b43legacy-phy0 ERROR: PHY transmission error
[ 1079.477034] b43legacy-phy0 ERROR: PHY transmission error
[ 1081.447864] b43legacy-phy0 ERROR: PHY transmission error
[ 1081.770019] b43legacy-phy0 ERROR: PHY transmission error
[ 1084.507915] b43legacy-phy0 ERROR: PHY transmission error
[ 1085.209770] b43legacy-phy0 ERROR: PHY transmission error
[ 1087.011593] b43legacy-phy0 ERROR: PHY transmission error
[ 1087.201593] b43legacy-phy0 ERROR: PHY transmission error
[ 1088.868508] b43legacy-phy0 ERROR: PHY transmission error
[ 1089.052701] b43legacy-phy0 ERROR: PHY transmission error
[ 1090.968099] b43legacy-phy0 ERROR: PHY transmission error
[ 1091.214999] b43legacy-phy0 ERROR: PHY transmission error
[ 1093.289233] b43legacy-phy0 ERROR: PHY transmission error
[ 1094.425748] b43legacy-phy0 ERROR: PHY transmission error
[ 1095.527225] b43legacy-phy0 ERROR: PHY transmission error
[ 1097.871156] b43legacy-phy0 ERROR: PHY transmission error
[ 1098.812618] b43legacy-phy0 ERROR: PHY transmission error
[ 1099.047708] b43legacy-phy0 ERROR: PHY transmission error
[ 1101.100622] b43legacy-phy0 ERROR: PHY transmission error
[ 1101.587718] b43legacy-phy0 ERROR: PHY transmission error
[ 1102.999206] b43legacy-phy0 ERROR: PHY transmission error
[ 1103.235220] b43legacy-phy0 ERROR: PHY transmission error
[ 1105.476873] b43legacy-phy0 ERROR: PHY transmission error
[ 1105.670843] b43legacy-phy0 ERROR: PHY transmission error
[ 1111.287744] b43legacy-phy0 ERROR: PHY transmission error
[ 1111.847961] b43legacy-phy0 ERROR: PHY transmission error
[ 1114.549761] b43legacy-phy0 ERROR: PHY transmission error
[ 1114.780886] b43legacy-phy0 ERROR: PHY transmission error
[ 1116.783979] b43legacy-phy0 ERROR: PHY transmission error
[ 1117.130712] b43legacy-phy0 ERROR: PHY transmission error
[ 1119.217858] b43legacy-phy0 ERROR: PHY transmission error
[ 1119.451258] b43legacy-phy0 ERROR: PHY transmission error
[ 1121.272824] b43legacy-phy0 ERROR: PHY transmission error
[ 1122.371774] b43legacy-phy0 ERROR: PHY transmission error
[ 1123.180299] b43legacy-phy0 ERROR: PHY transmission error
[ 1125.122581] b43legacy-phy0 ERROR: PHY transmission error
[ 1126.101528] b43legacy-phy0 ERROR: PHY transmission error
[ 1126.376699] b43legacy-phy0 ERROR: PHY transmission error
[ 1128.245450] b43legacy-phy0 ERROR: PHY transmission error
[ 1128.488712] b43legacy-phy0 ERROR: PHY transmission error
[ 1129.836647] b43legacy-phy0 ERROR: PHY transmission error
[ 1130.076904] b43legacy-phy0 ERROR: PHY transmission error
[ 1132.440440] b43legacy-phy0 ERROR: PHY transmission error
[ 1132.718674] b43legacy-phy0 ERROR: PHY transmission error
[ 1135.558947] b43legacy-phy0 ERROR: PHY transmission error
[ 1136.088742] b43legacy-phy0 ERROR: PHY transmission error
[ 1138.370302] b43legacy-phy0 ERROR: PHY transmission error
[ 1138.510182] b43legacy-phy0 ERROR: PHY transmission error
[ 1140.103937] b43legacy-phy0 ERROR: PHY transmission error
[ 1140.391951] b43legacy-phy0 ERROR: PHY transmission error
[ 1141.980115] b43legacy-phy0 ERROR: PHY transmission error
[ 1142.095251] b43legacy-phy0 ERROR: PHY transmission error
[ 1143.597653] b43legacy-phy0 ERROR: PHY transmission error
[ 1144.638458] b43legacy-phy0 ERROR: PHY transmission error
[ 1145.251013] b43legacy-phy0 ERROR: PHY transmission error
[ 1146.865729] b43legacy-phy0 ERROR: PHY transmission error
[ 1147.771426] b43legacy-phy0 ERROR: PHY transmission error
[ 1147.951630] b43legacy-phy0 ERROR: PHY transmission error
[ 1188.937721] b43legacy-phy0 ERROR: PHY transmission error
[ 1190.993203] b43legacy-phy0 ERROR: PHY transmission error
[ 1213.152225] b43legacy-phy0 ERROR: PHY transmission error
[ 1213.468080] b43legacy-phy0 ERROR: PHY transmission error
[ 1221.041961] b43legacy-phy0 ERROR: PHY transmission error
[ 1221.140349] b43legacy-phy0 ERROR: PHY transmission error
[ 1221.140378] b43legacy-phy0 ERROR: PHY transmission error
[ 1230.537323] b43legacy-phy0 ERROR: PHY transmission error
[ 1232.823640] b43legacy-phy0 ERROR: PHY transmission error
[ 1242.054483] b43legacy-phy0 ERROR: PHY transmission error
[ 1242.288817] b43legacy-phy0 ERROR: PHY transmission error
[ 1244.194127] b43legacy-phy0 ERROR: PHY transmission error
[ 1244.236287] b43legacy-phy0 ERROR: PHY transmission error
[ 1245.608662] b43legacy-phy0 ERROR: PHY transmission error
[ 1246.144748] b43legacy-phy0 ERROR: PHY transmission error
[ 1248.155634] b43legacy-phy0 ERROR: PHY transmission error
[ 1249.130645] b43legacy-phy0 ERROR: PHY transmission error
[ 1249.808400] b43legacy-phy0 ERROR: PHY transmission error
[ 1251.987600] b43legacy-phy0 ERROR: PHY transmission error
[ 1252.447043] b43legacy-phy0 ERROR: PHY transmission error
[ 1252.501690] b43legacy-phy0 ERROR: PHY transmission error
[ 1259.524436] b43legacy-phy0 ERROR: PHY transmission error
[ 1259.997298] b43legacy-phy0 ERROR: PHY transmission error
[ 1261.319637] b43legacy-phy0 ERROR: PHY transmission error
[ 1261.376939] b43legacy-phy0 ERROR: PHY transmission error
[ 1263.713583] b43legacy-phy0 ERROR: PHY transmission error
[ 1264.256310] b43legacy-phy0 ERROR: PHY transmission error
[ 1304.573815] b43legacy-phy0 ERROR: PHY transmission error
[ 1305.545873] b43legacy-phy0 ERROR: PHY transmission error
[ 1336.682634] b43legacy-phy0 ERROR: PHY transmission error
[ 1344.754644] b43legacy-phy0 ERROR: PHY transmission error
[ 1344.754676] b43legacy-phy0 ERROR: PHY transmission error
[ 1373.277642] b43legacy-phy0 ERROR: PHY transmission error
[ 1407.221091] b43legacy-phy0 ERROR: PHY transmission error
[ 1497.531016] b43legacy-phy0 ERROR: PHY transmission error
[ 1498.077231] b43legacy-phy0 ERROR: PHY transmission error
[ 1499.692878] b43legacy-phy0 ERROR: PHY transmission error
[ 1500.417973] b43legacy-phy0 ERROR: PHY transmission error
[ 1501.062440] b43legacy-phy0 ERROR: PHY transmission error
[ 1502.953354] b43legacy-phy0 ERROR: PHY transmission error
[ 1503.899830] b43legacy-phy0 ERROR: PHY transmission error
[ 1504.077677] b43legacy-phy0 ERROR: PHY transmission error
[ 1505.776998] b43legacy-phy0 ERROR: PHY transmission error
[ 1506.226966] b43legacy-phy0 ERROR: PHY transmission error
[ 1507.563580] b43legacy-phy0 ERROR: PHY transmission error
[ 1507.802346] b43legacy-phy0 ERROR: PHY transmission error
[ 1511.332086] b43legacy-phy0 ERROR: PHY transmission error
[ 1511.578699] b43legacy-phy0 ERROR: PHY transmission error
[ 1511.578735] b43legacy-phy0 ERROR: PHY transmission error
[ 1515.300780] b43legacy-phy0 ERROR: PHY transmission error
[ 1515.300815] b43legacy-phy0 ERROR: PHY transmission error
[ 1515.888254] b43legacy-phy0 ERROR: PHY transmission error
[ 1515.888286] b43legacy-phy0 ERROR: PHY transmission error
[ 1518.587237] b43legacy-phy0 ERROR: PHY transmission error
[ 1518.587273] b43legacy-phy0 ERROR: PHY transmission error
[ 1518.814631] b43legacy-phy0 ERROR: PHY transmission error
[ 1518.814664] b43legacy-phy0 ERROR: PHY transmission error
[ 1531.716235] b43legacy-phy0 ERROR: PHY transmission error
[ 1532.454235] b43legacy-phy0 ERROR: PHY transmission error
[ 1534.087198] b43legacy-phy0 ERROR: PHY transmission error
[ 1534.267465] b43legacy-phy0 ERROR: PHY transmission error
[ 1535.645554] b43legacy-phy0 ERROR: PHY transmission error
[ 1536.562059] b43legacy-phy0 ERROR: PHY transmission error
[ 1537.244303] b43legacy-phy0 ERROR: PHY transmission error
[ 1538.991661] b43legacy-phy0 ERROR: PHY transmission error
[ 1539.870331] b43legacy-phy0 ERROR: PHY transmission error
[ 1540.100944] b43legacy-phy0 ERROR: PHY transmission error
[ 1541.603143] b43legacy-phy0 ERROR: PHY transmission error
[ 1542.060972] b43legacy-phy0 ERROR: PHY transmission error
[ 1543.269273] b43legacy-phy0 ERROR: PHY transmission error
[ 1543.333862] b43legacy-phy0 ERROR: PHY transmission error
[ 1544.781213] b43legacy-phy0 ERROR: PHY transmission error
[ 1544.949697] b43legacy-phy0 ERROR: PHY transmission error
[ 1549.102806] b43legacy-phy0 ERROR: PHY transmission error
[ 1549.102841] b43legacy-phy0 ERROR: PHY transmission error
[ 1549.860153] b43legacy-phy0 ERROR: PHY transmission error
[ 1549.860181] b43legacy-phy0 ERROR: PHY transmission error
[ 1552.319152] b43legacy-phy0 ERROR: PHY transmission error
[ 1552.319184] b43legacy-phy0 ERROR: PHY transmission error
[ 1552.654555] b43legacy-phy0 ERROR: PHY transmission error
[ 1554.879356] b43legacy-phy0 ERROR: PHY transmission error
[ 1554.879386] b43legacy-phy0 ERROR: PHY transmission error
[ 1555.157380] b43legacy-phy0 ERROR: PHY transmission error
[ 1555.157414] b43legacy-phy0 ERROR: PHY transmission error
[ 1557.439553] b43legacy-phy0 ERROR: PHY transmission error
[ 1557.439586] b43legacy-phy0 ERROR: PHY transmission error
[ 1557.690519] b43legacy-phy0 ERROR: PHY transmission error
[ 1557.690551] b43legacy-phy0 ERROR: PHY transmission error
[ 1567.158506] b43legacy-phy0 ERROR: PHY transmission error
[ 1570.633422] b43legacy-phy0 ERROR: PHY transmission error
[ 1571.271392] b43legacy-phy0 ERROR: PHY transmission error
[ 1573.500258] b43legacy-phy0 ERROR: PHY transmission error
[ 1574.421886] b43legacy-phy0 ERROR: PHY transmission error
[ 1574.596599] b43legacy-phy0 ERROR: PHY transmission error
[ 1576.162149] b43legacy-phy0 ERROR: PHY transmission error
[ 1576.525933] b43legacy-phy0 ERROR: PHY transmission error
[ 1577.901673] b43legacy-phy0 ERROR: PHY transmission error
[ 1578.140959] b43legacy-phy0 ERROR: PHY transmission error
[ 1579.695553] b43legacy-phy0 ERROR: PHY transmission error
[ 1579.872504] b43legacy-phy0 ERROR: PHY transmission error
[ 1582.861394] b43legacy-phy0 ERROR: PHY transmission error
[ 1583.484329] b43legacy-phy0 ERROR: PHY transmission error
[ 1585.270110] b43legacy-phy0 ERROR: PHY transmission error
[ 1585.497510] b43legacy-phy0 ERROR: PHY transmission error
[ 1586.033798] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 1587.011954] b43legacy-phy0 ERROR: PHY transmission error
[ 1587.276979] b43legacy-phy0 ERROR: PHY transmission error
[ 1588.948220] b43legacy-phy0 ERROR: PHY transmission error
[ 1588.986978] b43legacy-phy0 ERROR: PHY transmission error
[ 1590.515674] b43legacy-phy0 ERROR: PHY transmission error
[ 1591.473231] b43legacy-phy0 ERROR: PHY transmission error
[ 1592.284006] b43legacy-phy0 ERROR: PHY transmission error
[ 1594.228146] b43legacy-phy0 ERROR: PHY transmission error
[ 1594.920478] b43legacy-phy0 ERROR: PHY transmission error
[ 1614.778314] b43legacy-phy0 ERROR: PHY transmission error
[ 1632.165183] b43legacy-phy0 ERROR: PHY transmission error
[ 1694.863827] b43legacy-phy0 ERROR: PHY transmission error
```

---

