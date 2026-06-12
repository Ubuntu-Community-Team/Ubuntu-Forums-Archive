---
title: "wifi keeps disconnecting"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by protonpusher on 2012-08-15
I am looking for help to get the wifi on my laptop to connect with my college wifi system. The wifi on my laptop keeps disconnecting when trying to access the wifi at my college. It will only briefly connect (the wifi icon steady on), and then after about 30 seconds it disconnects. This cycle keeps repeating, but I never get a usable connection. I have verified that I am using the correct password. The machine,with ubuntu, will connect to the wifi at my house, and I can connect to the college wifi using windows 7 on the same machine (its dual boot).

Here are the details: 

1 ) Machine Brand and Model (PC/Laptop):
```
Thinkpad Edge E520 Laptop
```

2 ) Wireless Brand, Model and Wireless Chipset:
```
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

```

3 ) check interface:
```
wlan0     Link encap:Ethernet  HWaddr 60:d8:19:d1:26:00  
          inet addr:147.144.196.150  Bcast:147.144.207.255  Mask:255.255.240.0
          inet6 addr: fe80::62d8:19ff:fed1:2600/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64006 (64.0 KB)  TX bytes:30889 (30.8 KB)

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

```

4 ) Check for modules:
```
Module                  Size  Used by
usbhid                 41906  0 
hid                    77367  1 usbhid
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  1 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
snd_hda_codec_hdmi     31775  1 
ppdev                  12849  0 
snd_hda_codec_conexant    52554  1 
arc4                   12473  2 
joydev                 17393  0 
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
snd_hda_intel          32765  3 
snd_rawmidi            25424  1 snd_seq_midi
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
rtl8192ce              75491  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95804  1 rtl8192ce
mac80211              436455  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
cfg80211              178679  2 rtlwifi,mac80211
mei                    36570  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
psmouse                72919  0 
snd                    62064  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
mac_hid                13077  0 
soundcore              14635  1 snd
binfmt_misc            17292  1 
nvram                  14029  1 thinkpad_acpi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  414739  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
sdhci_pci              18324  0 
video                  19068  1 i915
sdhci                  28241  1 sdhci_pci
r8169                  56321  0 

```

5 ) Kernel boot messages
```
[25213.668370] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[25213.668376] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25213.668381] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[25213.668388] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25213.668393] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[25213.668400] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25213.668405] cfg80211: Disabling freq 2467 MHz
[25213.668409] cfg80211: Disabling freq 2472 MHz
[25213.668412] cfg80211: Disabling freq 2484 MHz
[25213.668423] cfg80211: Regulatory domain changed to country: US
[25213.668427] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[25213.668434] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25213.668440] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[25213.668446] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25213.668451] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25213.668457] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25213.668463] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[25216.644504] wlan0: deauthenticated from 00:18:0a:30:2d:9b (Reason: 2)
[25216.679940] cfg80211: All devices are disconnected, going to restore regulatory settings
[25216.679954] cfg80211: Restoring regulatory settings
[25216.679964] cfg80211: Calling CRDA to update world regulatory domain
[25216.688657] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[25216.688667] cfg80211: World regulatory domain updated:
[25216.688672] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[25216.688679] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25216.688686] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[25216.688692] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[25216.688697] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25216.688703] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25216.783419] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[25217.862715] wlan0: authenticate with 00:18:0a:30:2d:94 (try 1)
[25217.871462] wlan0: authenticated
[25217.891914] wlan0: associate with 00:18:0a:30:2d:94 (try 1)
[25217.908431] wlan0: RX ReassocResp from 00:18:0a:30:2d:94 (capab=0x431 status=18 aid=0)
[25217.908435] wlan0: 00:18:0a:30:2d:94 denied association (code=18)
[25217.918848] wlan0: deauthenticating from 00:18:0a:30:2d:94 by local choice (reason=3)
[25218.022570] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[25219.087979] wlan0: authenticate with 00:18:0a:30:2d:9b (try 1)
[25219.097283] wlan0: authenticated
[25219.097822] wlan0: associate with 00:18:0a:30:2d:9b (try 1)
[25219.128880] wlan0: RX AssocResp from 00:18:0a:30:2d:9b (capab=0x431 status=0 aid=1)
[25219.128890] wlan0: associated
[25219.139905] cfg80211: Calling CRDA for country: US
[25219.150965] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[25219.150970] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.150972] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[25219.150975] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.150977] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[25219.150981] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.150983] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[25219.150986] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.150988] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[25219.150991] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.150994] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[25219.150997] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.151000] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[25219.151003] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.151006] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[25219.151009] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.151012] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[25219.151015] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.151018] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[25219.151021] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.151023] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[25219.151027] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.151029] cfg80211: Disabling freq 2467 MHz
[25219.151030] cfg80211: Disabling freq 2472 MHz
[25219.151032] cfg80211: Disabling freq 2484 MHz
[25219.151037] cfg80211: Regulatory domain changed to country: US
[25219.151039] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[25219.151042] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25219.151046] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[25219.151049] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25219.151051] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25219.151054] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25219.151057] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[25222.134872] wlan0: deauthenticated from 00:18:0a:30:2d:9b (Reason: 2)
[25222.159973] cfg80211: All devices are disconnected, going to restore regulatory settings
[25222.159980] cfg80211: Restoring regulatory settings
[25222.159985] cfg80211: Calling CRDA to update world regulatory domain
[25222.169512] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[25222.169516] cfg80211: World regulatory domain updated:
[25222.169517] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[25222.169520] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25222.169522] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[25222.169524] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[25222.169526] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25222.169528] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[25222.347021] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[25223.335971] wlan0: authenticate with 00:18:0a:30:2d:94 (try 1)
[25223.347843] wlan0: authenticated
[25223.368331] wlan0: associate with 00:18:0a:30:2d:94 (try 1)
[25223.393168] wlan0: RX ReassocResp from 00:18:0a:30:2d:94 (capab=0x431 status=18 aid=0)
[25223.393178] wlan0: 00:18:0a:30:2d:94 denied association (code=18)
[25223.428548] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[25223.768079] wlan0: deauthenticating from 00:18:0a:30:2d:94 by local choice (reason=3)
[25223.871814] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[25224.941030] wlan0: authenticate with 00:18:0a:30:2d:9b (try 1)
[25224.950349] wlan0: authenticated
[25224.950918] wlan0: associate with 00:18:0a:30:2d:9b (try 1)
[25224.981822] wlan0: RX AssocResp from 00:18:0a:30:2d:9b (capab=0x431 status=0 aid=1)
[25224.981835] wlan0: associated
[25224.993018] cfg80211: Calling CRDA for country: US
[25224.999396] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[25224.999405] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25224.999408] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[25224.999411] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25224.999414] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[25224.999417] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25224.999419] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[25224.999422] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25224.999424] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[25224.999427] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25224.999430] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[25224.999433] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25224.999436] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[25224.999438] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25224.999440] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[25224.999443] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[25224.999446] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[25224.999448] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)

```

Keeps repeating

6 ) Network configuration
```
 *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 60:d8:19:d1:26:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-29-generic-pae firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:3000(size=256) memory:d1d00000-d1d03fff

```

7 ) Scan for networks:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:0A:30:2D:9B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"CCSF Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000684d9180
                    Extra: Last beacon: 5460ms ago
                    IE: Unknown: 000D4343534620576972656C657373
                    IE: Unknown: 010882848B9618243048
                    IE: Unknown: 030101
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0103
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0D00180A071600000001005C8C95
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:18:0A:30:2D:94
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"CCSF Wireless"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000031c3d8180
                    Extra: Last beacon: 5800ms ago
                    IE: Unknown: 000D4343534620576972656C657373
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0103
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101080002A4400027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0D00180A071600000001005C8C95
                    IE: Unknown: DD0A00037F04010000000000

```

8 ) Ubuntu Version: 
```
Description:	Ubuntu 12.04.1 LTS

```

9 ) Kernel/architecture (including 32 vs. 64 bit): 
```
3.2.0-29-generic-pae i686
```

10 ) Restarting the network:
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...   
```

---

