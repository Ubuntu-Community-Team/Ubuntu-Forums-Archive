---
title: "Wireless randomly disconnects ubuntu 12.04. LTS"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by The Gambler on 2013-01-04
Please help me, I tried some stuff but I'm just not able to cope with the problem.
Wireless disconnects randomly, sometimes it works 20 min, sometimes it works 30 sec.


lspci -nnk | grep -iA2 net 

```

01:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2800pci
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14e7]
    Kernel driver in use: alx
```lsmod

```
Module                  Size  Used by
asus_nb_wmi            16990  0 
joydev                 17693  0 
asus_wmi               24438  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_codec_via      46513  1 
snd_hda_codec_hdmi     32193  1 
snd_hda_intel          33296  5 
snd_hda_codec         134068  3 snd_hda_codec_via,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
rt2800pci              18521  0 
rt2800lib              58421  1 rt2800pci
dm_multipath           23275  0 
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14475  1 rt2800pci
rt2x00lib              54816  3 rt2800pci,rt2800lib,rt2x00pci
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
mac80211              523732  3 rt2800lib,rt2x00pci,rt2x00lib
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17128  1 videodev
rfcomm                 46621  0 
psmouse                97485  0 
bnep                   18139  2 
bluetooth             209171  10 rfcomm,bnep
parport_pc             32866  0 
serio_raw              13211  0 
ppdev                  17113  0 
i2c_piix4              13301  0 
k10temp                13166  0 
fglrx                3264017  115 
snd                    79041  20 snd_hda_codec_via,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              209911  2 rt2x00lib,mac80211
eeprom_93cx6           13344  1 rt2800pci
alx                    81350  0 
compat                 13447  7 rt2800pci,mac80211,rfcomm,bnep,bluetooth,cfg80211,alx
soundcore              15091  1 snd
nls_iso8859_1          12713  1 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
video                  19596  0 
wmi                    19256  1 asus_wmi
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 653005  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
```ifconfig

```
eth0      Link encap:Ethernet  HWaddr 50:46:5d:4b:30:eb  
          inet addr:192.168.178.31  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::5246:5dff:fe4b:30eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2411 errors:0 dropped:483 overruns:483 frame:483
          TX packets:2395 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:1987262 (1.9 MB)  TX bytes:401664 (401.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:278775 (278.7 KB)  TX bytes:278775 (278.7 KB)

wlan0     Link encap:Ethernet  HWaddr 84:4b:f5:70:0d:5d  
          inet addr:192.168.178.30  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::864b:f5ff:fe70:d5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7808592 (7.8 MB)  TX bytes:1641720 (1.6 MB)
```

---

### Post by dannyboy79 on 2013-01-04
can you post back dmesg output after it stops working please? also, do you have a lot of devices that would interfere like baby monitors, cordless phones, etc etc

---

### Post by The Gambler on 2013-01-04
At the moment the connection is just very slow and the speed goes up and down randomly. I have a cordless phone and a mobile phone. I'm in a room where the Wlan signal is not 100% percent but my phone connects without any problem.

if it helps I post my dmesg anyway

```
[ 1273.852318] wlan0: send auth to 24:65:11:73:5d:68 (try 1/3)
[ 1273.854834] wlan0: authenticated
[ 1273.864088] wlan0: associate with 24:65:11:73:5d:68 (try 1/3)
[ 1273.869319] wlan0: RX AssocResp from 24:65:11:73:5d:68 (capab=0x431 status=0 aid=1)
[ 1273.869331] wlan0: associated
[ 1273.877525] cfg80211: Calling CRDA for country: DE
[ 1273.888868] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.888882] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.888890] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.888898] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.888904] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.888912] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.888918] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.888926] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.888932] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.888939] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.888945] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.888953] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.888959] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.888966] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.888972] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.888980] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.888986] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.888993] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.888999] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.889006] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.889012] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.889020] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.889026] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.889033] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.889039] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1273.889047] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1273.889052] cfg80211: Disabling freq 2484 MHz
[ 1273.889060] cfg80211: Regulatory domain changed to country: DE
[ 1273.889065] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1273.889072] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1273.889078] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1273.889085] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1273.889091] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[ 1284.616047] wlan0: no IPv6 routers present
[ 1660.958818] wlan0: deauthenticating from 24:65:11:73:5d:68 by local choice (reason=3)
[ 1661.001639] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1661.001658] cfg80211: Restoring regulatory settings
[ 1661.001670] cfg80211: Calling CRDA to update world regulatory domain
[ 1661.024780] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024792] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024798] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024804] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024809] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024814] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024819] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024825] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024830] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024835] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024840] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024845] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024850] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024855] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024860] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024866] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024870] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024876] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024880] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024886] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024890] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024896] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024901] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024906] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1661.024911] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024916] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1661.024921] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1661.024926] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1661.024933] cfg80211: World regulatory domain updated:
[ 1661.024937] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1661.024942] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024947] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1661.024952] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1661.024957] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1661.024962] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1662.457268] wlan0: authenticate with 24:65:11:73:5d:68
[ 1662.468247] wlan0: send auth to 24:65:11:73:5d:68 (try 1/3)
[ 1662.470015] wlan0: authenticated
[ 1662.480269] wlan0: associate with 24:65:11:73:5d:68 (try 1/3)
[ 1662.484240] wlan0: RX AssocResp from 24:65:11:73:5d:68 (capab=0x431 status=0 aid=1)
[ 1662.484254] wlan0: associated
[ 1662.493694] cfg80211: Calling CRDA for country: DE
[ 1662.507898] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.507915] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.507925] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.507935] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.507943] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.507952] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.507960] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.507970] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.507977] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.507987] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.507994] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.508090] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.508098] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.508108] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.508115] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.508126] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.508143] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.508164] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.508180] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.508200] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.508216] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.508235] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.508251] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.508270] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.508286] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1662.508306] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1662.508323] cfg80211: Disabling freq 2484 MHz
[ 1662.508339] cfg80211: Regulatory domain changed to country: DE
[ 1662.508353] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1662.508371] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1662.508388] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1662.508404] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1662.508421] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[ 1670.360332] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1670.360352] cfg80211: Restoring regulatory settings
[ 1670.360404] cfg80211: Calling CRDA to update world regulatory domain
[ 1670.375501] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375518] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375527] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375537] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375546] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375555] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375563] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375573] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375580] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375590] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375597] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375606] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375614] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375623] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375631] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375640] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375648] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375657] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375665] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375674] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375697] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375706] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375714] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375723] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1670.375731] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375740] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1670.375748] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1670.375757] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1670.375768] cfg80211: World regulatory domain updated:
[ 1670.375774] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1670.375783] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375791] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1670.375799] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1670.375807] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1670.375815] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1671.577810] wlan0: authenticate with 24:65:11:73:5d:68
[ 1671.592212] wlan0: send auth to 24:65:11:73:5d:68 (try 1/3)
[ 1671.598843] wlan0: authenticated
[ 1671.608191] wlan0: associate with 24:65:11:73:5d:68 (try 1/3)
[ 1671.612130] wlan0: RX AssocResp from 24:65:11:73:5d:68 (capab=0x431 status=0 aid=1)
[ 1671.612146] wlan0: associated
[ 1671.622253] cfg80211: Calling CRDA for country: DE
[ 1671.635210] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635225] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635232] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635240] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635247] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635254] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635261] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635268] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635275] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635282] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635288] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635325] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635331] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635338] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635344] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635351] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635357] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635365] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635371] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635378] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635384] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635391] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635397] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635405] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635411] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1671.635418] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1671.635424] cfg80211: Disabling freq 2484 MHz
[ 1671.635432] cfg80211: Regulatory domain changed to country: DE
[ 1671.635437] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1671.635444] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1671.635450] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1671.635456] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1671.635462] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[ 1673.776210] wlan0: no IPv6 routers present
[ 1674.628190] wlan0: deauthenticated from 24:65:11:73:5d:68 (Reason: 6)
[ 1674.648549] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1674.648564] cfg80211: Restoring regulatory settings
[ 1674.648573] cfg80211: Calling CRDA to update world regulatory domain
[ 1674.661493] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661509] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661519] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661529] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661537] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661546] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661554] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661563] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661571] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661580] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661588] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661597] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661605] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661614] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661621] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661630] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661638] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661647] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661654] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661663] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661671] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661680] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661688] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661697] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1674.661704] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661713] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1674.661721] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1674.661730] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1674.661741] cfg80211: World regulatory domain updated:
[ 1674.661747] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1674.661756] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661764] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1674.661772] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1674.661780] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.661788] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1675.854053] wlan0: authenticate with 24:65:11:73:5d:68
[ 1675.868461] wlan0: send auth to 24:65:11:73:5d:68 (try 1/3)
[ 1675.870295] wlan0: authenticated
[ 1675.880187] wlan0: associate with 24:65:11:73:5d:68 (try 1/3)
[ 1675.884477] wlan0: RX AssocResp from 24:65:11:73:5d:68 (capab=0x431 status=0 aid=1)
[ 1675.884502] wlan0: associated
[ 1675.894257] cfg80211: Calling CRDA for country: DE
[ 1675.908694] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908711] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908720] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908730] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908738] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908748] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908756] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908765] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908773] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908782] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908790] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908799] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908806] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908815] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908823] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908832] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908840] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908849] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908856] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908865] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908873] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908882] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908890] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908899] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908906] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1675.908915] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1675.908922] cfg80211: Disabling freq 2484 MHz
[ 1675.908932] cfg80211: Regulatory domain changed to country: DE
[ 1675.908939] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1675.908947] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1675.908955] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1675.908963] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1675.908970] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
```

---

### Post by dannyboy79 on 2013-01-04
wow, not sure what all that mess is. You'll have to wait for someone more knowledgable to help you out.

---

### Post by The Gambler on 2013-01-04
ok, thanks anyway, could you show my what a "normal" dmesg output should look like?

---

### Post by dotpc on 2013-01-11
You should find chili555, he seems to know everything there is to know about fixing wifi.

---

### Post by ikem.krueger on 2013-01-28
This tutorial fixed it for me:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

---

