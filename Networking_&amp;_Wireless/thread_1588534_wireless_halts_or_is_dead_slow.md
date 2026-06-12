---
title: "wireless halts or is dead slow"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by Arnoldijzermans on 2010-10-05
Hi all

I have a problem that's driving me nuts. 
My wireless card (linksys wusb54GR) connects to the network out of the box, but at a certain point just halts. I'm not sure if it just stops, or if it is dead slow, but disconnecting and reconnecting usually does the trick for some time (varrying in 2 - 5 minutes).

any help is much appreciacted since it starts to become unworkable.

Below is the information on my config.
OS: Ubuntu 10.04.1 LTS 2.6.32-25-generic
Wireless adapter: Linksys WUSB54GR (with rangebooster that is)

lsusb:
Bus 001 Device 003: ID 13b1:0023 Linksys WUSB54GR

ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:1a:70:a9:35:ba  
          inet addr:192.168.1.76  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:70ff:fea9:35ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9423619 (9.4 MB)  TX bytes:3820039 (3.8 MB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SpeedTouchAC69C2"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:18:F6:01:2A:CA   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_emu10k1x           13213  3 
snd_ac97_codec        100646  1 snd_emu10k1x
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_emu10k1x,snd_ac97_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
nfsd                  238967  13 
exportfs                3437  1 nfsd
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
nfs                   264918  0 
snd_rawmidi            19056  2 snd_emu10k1x,snd_seq_midi
lockd                  64849  2 nfsd,nfs
nfs_acl                 2245  2 nfsd,nfs
auth_rpcgss            33735  2 nfsd,nfs
rt73usb                21938  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
sunrpc                193085  12 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
crc_itu_t               1371  1 rt73usb
rt2x00usb               9694  1 rt73usb
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00lib              26858  2 rt73usb,rt2x00usb
snd_timer              19098  2 snd_pcm,snd_seq
led_class               2864  1 rt2x00lib
compat_firmware_class     6554  1 rt2x00lib
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
radeon                675160  2 
ttm                    49943  1 radeon
snd                    54148  16 snd_emu10k1x,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 radeon
dell_wmi                1793  0 
mac80211              225491  2 rt2x00usb,rt2x00lib
joydev                  8708  0 
emu10k1_gp              1492  0 
soundcore               6620  1 snd
ac97_bus                1002  1 snd_ac97_codec
ppdev                   5259  0 
dcdbas                  5422  0 
drm                   162409  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
snd_page_alloc          7076  2 snd_emu10k1x,snd_pcm
gameport                9089  2 emu10k1_gp
cfg80211              144650  2 rt2x00lib,mac80211
usbhid                 36110  0 
parport_pc             25962  1 
psmouse                63245  0 
serio_raw               3978  0 
intel_agp              24119  1 
hid                    67032  1 usbhid
lp                      7060  0 
agpgart                31724  3 ttm,drm,intel_agp
shpchp                 28820  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39553  1 
e100                   28211  0 
mii                     4381  1 e100
floppy                 53016  0

dmesg
[ 1248.770194] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1248.770202] cfg80211: Restoring regulatory settings
[ 1248.770207] cfg80211: Calling CRDA to update world regulatory domain
[ 1248.786586] cfg80211: World regulatory domain updated:
[ 1248.786592]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1248.786597]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1248.786601]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1248.786605]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1248.786608]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1248.786612]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1248.870079] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1249.775229] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1249.890199] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1249.957989] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1250.138763] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1252.625262] wlan0: authenticate with 00:18:f6:01:2a:ca (try 1)
[ 1252.627040] wlan0: authenticated
[ 1252.628625] wlan0: associate with 00:18:f6:01:2a:ca (try 1)
[ 1252.632451] wlan0: RX AssocResp from 00:18:f6:01:2a:ca (capab=0x431 status=0 aid=3)
[ 1252.632458] wlan0: associated
[ 1252.638606] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1263.500026] wlan0: no IPv6 routers present
[ 2574.754250] wlan0: deauthenticating from 00:18:f6:01:2a:ca by local choice (reason=3)
[ 2574.763665] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2574.763672] cfg80211: Restoring regulatory settings
[ 2574.763676] cfg80211: Calling CRDA to update world regulatory domain
[ 2574.793370] cfg80211: World regulatory domain updated:
[ 2574.793378]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2574.793382]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2574.793386]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2574.793390]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2574.793394]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2574.793398]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2574.879948] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2577.327362] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2577.461327] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2577.538015] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2577.723582] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2580.226372] wlan0: authenticate with 00:18:f6:01:2a:ca (try 1)
[ 2580.227984] wlan0: authenticated
[ 2580.229609] wlan0: associate with 00:18:f6:01:2a:ca (try 1)
[ 2580.232200] wlan0: RX AssocResp from 00:18:f6:01:2a:ca (capab=0x431 status=0 aid=3)
[ 2580.232205] wlan0: associated
[ 2580.250525] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2590.996022] wlan0: no IPv6 routers present
[ 2652.355711] wlan0: deauthenticating from 00:18:f6:01:2a:ca by local choice (reason=3)
[ 2652.366383] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2652.366392] cfg80211: Restoring regulatory settings
[ 2652.366397] cfg80211: Calling CRDA to update world regulatory domain
[ 2652.384072] cfg80211: World regulatory domain updated:
[ 2652.384079]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2652.384084]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2652.384088]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2652.384092]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2652.384096]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2652.384100]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2652.470671] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2653.523811] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2653.642017] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2653.735239] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2653.898683] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2656.386820] wlan0: authenticate with 00:18:f6:01:2a:ca (try 1)
[ 2656.388595] wlan0: authenticated
[ 2656.390189] wlan0: associate with 00:18:f6:01:2a:ca (try 1)
[ 2656.393103] wlan0: RX AssocResp from 00:18:f6:01:2a:ca (capab=0x431 status=0 aid=3)
[ 2656.393110] wlan0: associated
[ 2656.409285] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2666.616016] wlan0: no IPv6 routers present
[ 2750.613436] wlan0: deauthenticating from 00:18:f6:01:2a:ca by local choice (reason=3)
[ 2750.622532] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2750.622541] cfg80211: Restoring regulatory settings
[ 2750.622546] cfg80211: Calling CRDA to update world regulatory domain
[ 2750.644382] cfg80211: World regulatory domain updated:
[ 2750.644388]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2750.644393]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2750.644397]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2750.644401]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2750.644405]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2750.644409]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2750.736255] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2752.703654] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2752.824503] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2752.889969] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2753.083077] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2755.590804] wlan0: authenticate with 00:18:f6:01:2a:ca (try 1)
[ 2755.592571] wlan0: authenticated
[ 2755.594164] wlan0: associate with 00:18:f6:01:2a:ca (try 1)
[ 2755.597871] wlan0: RX AssocResp from 00:18:f6:01:2a:ca (capab=0x431 status=0 aid=3)
[ 2755.597878] wlan0: associated
[ 2755.615010] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2766.060017] wlan0: no IPv6 routers present

iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F6:01:2A:CA
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SpeedTouchAC69C2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014487123e8
                    Extra: Last beacon: 101956ms ago
                    IE: Unknown: 00105370656564546F756368414336394332
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00

---

### Post by Scrapper89 on 2010-10-05
"Link Quality=32/70  Signal level=-78 dBm"

Well - this shows that the wifi connection is of quite bad quality. @ -90dBm is the noise level... good connection always has ~-20 to -60 dBm.

It should be still working with -78, but if you have power fluctuations at home, and for some reason the signal strength from either router or your laptop get weaker for a split second (they always deviate +-10dBm, +-5 in good router case) - you get close to noise level and get disconnected...

Try using wicd for wireless network manager - it is a bit more stable in case of these things.

Otherwise - do you have another laptop to try if this is really not a router problem?

---

### Post by Arnoldijzermans on 2010-10-05
Hi

noticed the poor connection as well. I'm already using WICD as manager by the way.
I'll see if I can improve the connection.

I do have another laptop (2 in fact).
One is running ubuntu netbook version and doesn't have any problems. The other one is the XP laptop from work that runs fine.
In that respect the XP partition on my desktop doesn't have the problem either. Which makes me wonder if running the XP driver with NDISWRAPPER would solve the problem.

Thing is that I'm not comfortable to try that and only want to if  I know it could make a difference.

---

