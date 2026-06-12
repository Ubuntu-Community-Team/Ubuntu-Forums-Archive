---
title: "Wireless internet slow in Ubuntu 11.10"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by Icedrake99 on 2011-12-23
Ever since installing Ubuntu 11.10, my wireless internet speed has been painfully slow; especially download speeds are unbearable. 

Take a look at my speedtest results (I used to always get As on this test):

[[IMG]http://www.speedtest.net/result/1665319497.png[/IMG]](http://www.speedtest.net)

This does not happen on the other Windows computers in the house that are also using this same internet/network.

Here's some additional info:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:C1:C0:9D:6A:2E   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:163  Invalid misc:12   Missed beacon:0

```

How can I fix this? I can't download even the smallest of things without it taking forever. :( I saw another thread about someone having a similar slow internet issue, but I didn't want to try the commands given in that thread, just in case they were meant specifically for that user.

---

### Post by praseodym on 2011-12-23
Hi,

what hardware is in use? Please show:

```
lspci -nnk | grep -iA2 net
lsmod
lsusb
cat /etc/resolv.conf
sudo iwlist scan
```

---

### Post by Icedrake99 on 2011-12-23
Here you go:

```
~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 9400 Laptop [1028:01cd]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Device [8086:1020]
	Kernel driver in use: iwl3945

~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
zram                   18007  2 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
binfmt_misc            17292  1 
dell_laptop            13519  0 
usbhid                 41905  0 
dcdbas                 14098  1 dell_laptop
hid                    77367  1 usbhid
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
iwl3945                73360  0 
radeon                925193  3 
iwl_legacy             71499  1 iwl3945
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              393459  2 iwl3945,iwl_legacy
r592                   17808  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
mtd                    35852  2 sm_common,nand
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
wmi                    18744  1 dell_wmi
drm                   192194  5 radeon,ttm,drm_kms_helper
video                  18908  0 
snd                    55902  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 radeon
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
b44                    31443  0 
ssb                    50682  1 b44
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 005 Device 002: ID 0461:4d0f Primax Electronics, Ltd 

cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 208.67.222.222
nameserver 208.67.220.220

~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:C1:C0:9D:6A:2E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001fb33b4451c
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 0004486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B000103104700109EB40C7AEF63DE362B7F43CC42DC1DDE102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
```

---

### Post by praseodym on 2011-12-23
There is a bug with the country code settings in 11.10, you can see it in "iwconfig" where only 15 dBm are shown. Try:

```
sudo apt-get install iw
iw reg get
sudo iw reg set DE
```
"DE" is for Germany, change it to your country

---

### Post by Icedrake99 on 2011-12-23
> **praseodym said:**
> There is a bug with the country code settings in 11.10, you can see it in "iwconfig" where only 15 dBm are shown. Try:

```
sudo apt-get install iw
iw reg get
sudo iw reg set DE
```
"DE" is for Germany, change it to your country

Was that supposed to do anything? I typed your commands, and typed sudo iw reg set US and my internet is as slow as ever. No difference in speedtest.net.

---

### Post by praseodym on 2011-12-23
Ok, check now (again):

```
iwconfig
iwlist chan
dmesg | egrep 'country|iwl'
```
and a _complete_ scan
```
sudo iwlist scan
```

---

### Post by Icedrake99 on 2011-12-23
Do you want the results from those tests or do you just want me to run them and see if they have any effect?

---

### Post by Icedrake99 on 2011-12-23
Here are the results, in case you wanted them:

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:C1:C0:9D:6A:2E   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:5   Missed beacon:0

iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     24 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)

[12994.348041] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[12994.348050] iwl3945 0000:0c:00.0: On demand firmware reload
[13050.493796] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13050.493806] iwl3945 0000:0c:00.0: On demand firmware reload
[13095.719614] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[13095.719624] iwl3945 0000:0c:00.0: On demand firmware reload
[13202.397802] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13202.397808] iwl3945 0000:0c:00.0: On demand firmware reload
[13227.573685] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[13227.573691] iwl3945 0000:0c:00.0: On demand firmware reload
[13250.796487] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13250.796493] iwl3945 0000:0c:00.0: On demand firmware reload
[13264.983088] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13264.983098] iwl3945 0000:0c:00.0: On demand firmware reload
[13268.658675] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[13268.658681] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13269.161674] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[13269.161683] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13269.660028] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[13269.660034] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[13269.660037] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13270.000073] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[13270.000084] iwl3945 0000:0c:00.0: Error setting new configuration (-110).
[13270.160132] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[13270.160142] iwl3945 0000:0c:00.0: On demand firmware reload
[13270.500073] iwl3945 0000:0c:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[13270.621357] cfg80211: Calling CRDA for country: US
[13270.637552] cfg80211: Regulatory domain changed to country: US
[13387.772126] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13387.772135] iwl3945 0000:0c:00.0: On demand firmware reload
[13394.941422] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13394.941431] iwl3945 0000:0c:00.0: On demand firmware reload
[13398.621761] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13399.120039] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13399.620705] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[13399.620715] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13400.120799] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[13400.120808] iwl3945 0000:0c:00.0: On demand firmware reload
[13445.774293] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13445.774304] iwl3945 0000:0c:00.0: On demand firmware reload
[13505.508322] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13505.508332] iwl3945 0000:0c:00.0: On demand firmware reload
[13562.478150] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[13562.478157] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[13563.100153] iwl3945 0000:0c:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[13563.712036] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[13563.712045] iwl3945 0000:0c:00.0: On demand firmware reload
[13563.900074] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[13563.900085] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[13579.080436] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[13579.080446] iwl3945 0000:0c:00.0: On demand firmware reload
[13582.689440] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[13583.191815] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[13583.191826] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[13583.191833] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13583.688492] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[13583.688503] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[13583.688509] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13584.189180] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[13584.189189] iwl3945 0000:0c:00.0: On demand firmware reload
[13610.300067] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[13610.300077] iwl3945 0000:0c:00.0: On demand firmware reload
[14522.072783] cfg80211: Calling CRDA for country: US
[14522.081122] cfg80211: Regulatory domain changed to country: US
[33238.914105] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[33238.914112] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[33239.841334] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[33239.841345] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[33240.581819] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[33240.581829] iwl3945 0000:0c:00.0: On demand firmware reload
[33240.893273] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[33240.893280] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[33496.068076] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[33496.068085] iwl3945 0000:0c:00.0: On demand firmware reload
[33785.855946] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[33785.855951] iwl3945 0000:0c:00.0: On demand firmware reload
[33811.508074] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[33811.508083] iwl3945 0000:0c:00.0: On demand firmware reload
[33824.084673] iwl3945 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000008.
[33824.084679] iwl3945 0000:0c:00.0: Loaded firmware version: 15.32.2.9
[33824.085650] iwl3945 0000:0c:00.0: Start IWL Error Log Dump:
[33824.085653] iwl3945 0000:0c:00.0: Status: 0x000202E4, count: 1
[33824.085656] iwl3945 0000:0c:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
[33824.086646] iwl3945 0000:0c:00.0: SYSASSERT     (0x5) 2429599081 0x008B6 0x00274 0x0031C 0x078F8 116
[33824.086646] iwl3945 0000:0c:00.0: Start IWL Event Log Dump: display last 20 count
[33824.086646] iwl3945 0000:0c:00.0: 2429398370	0x000007c3	0310
[33824.086646] iwl3945 0000:0c:00.0: 2429398391	0x000000d9	0106
[33824.086646] iwl3945 0000:0c:00.0: 2429398393	0x00000000	0302
[33824.086646] iwl3945 0000:0c:00.0: 2429398563	0x00000000	0308
[33824.086646] iwl3945 0000:0c:00.0: 2429398592	0x000007c3	0310
[33824.086646] iwl3945 0000:0c:00.0: 2429398613	0x000000d9	0106
[33824.086646] iwl3945 0000:0c:00.0: 2429398615	0x00000000	0302
[33824.086646] iwl3945 0000:0c:00.0: 2429398717	0x00000000	0308
[33824.086646] iwl3945 0000:0c:00.0: 2429398746	0x000007c3	0310
[33824.086646] iwl3945 0000:0c:00.0: 2429398765	0x000000d9	0106
[33824.086646] iwl3945 0000:0c:00.0: 2429398767	0x00000000	0302
[33824.086646] iwl3945 0000:0c:00.0: 2429399031	0x00000000	0308
[33824.086646] iwl3945 0000:0c:00.0: 2429399060	0x000007c3	0310
[33824.086646] iwl3945 0000:0c:00.0: 2429399081	0x000000d9	0106
[33824.086646] iwl3945 0000:0c:00.0: 2429399083	0x00000000	0302
[33824.086646] iwl3945 0000:0c:00.0: 2429399221	0x00000000	0308
[33824.086646] iwl3945 0000:0c:00.0: 2429399349	0x00000000	0310
[33824.086646] iwl3945 0000:0c:00.0: 2429399352	0x00000000	0302
[33824.086646] iwl3945 0000:0c:00.0: 2429599079	0x00000002	0123
[33824.086646] iwl3945 0000:0c:00.0: 2429599082	0x00000100	0125
[33824.086646] iwl3945 0000:0c:00.0: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x02B0 ser 0x00740000
[33824.100776] iwl3945 0000:0c:00.0: Can't stop Rx DMA.
[33881.204872] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[33881.204882] iwl3945 0000:0c:00.0: On demand firmware reload
[33886.368144] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[33886.368153] iwl3945 0000:0c:00.0: On demand firmware reload
[33912.500663] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[33912.500672] iwl3945 0000:0c:00.0: On demand firmware reload
[33931.190462] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[33931.190472] iwl3945 0000:0c:00.0: On demand firmware reload
[33941.360454] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[33941.360463] iwl3945 0000:0c:00.0: On demand firmware reload
[34088.584915] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34088.584925] iwl3945 0000:0c:00.0: On demand firmware reload
[34119.752039] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34119.752049] iwl3945 0000:0c:00.0: On demand firmware reload
[34166.377287] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34166.377293] iwl3945 0000:0c:00.0: On demand firmware reload
[34170.508112] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34170.508123] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[34170.508129] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34171.012884] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34171.012894] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[34171.012900] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34171.512127] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34171.512138] iwl3945 0000:0c:00.0: On demand firmware reload
[34171.779968] cfg80211: Calling CRDA for country: US
[34171.802886] cfg80211: Regulatory domain changed to country: US
[34186.250208] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34186.250218] iwl3945 0000:0c:00.0: On demand firmware reload
[34197.640855] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[34197.640861] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[34197.916149] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34197.916159] iwl3945 0000:0c:00.0: On demand firmware reload
[34198.266238] iwl3945 0000:0c:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[34198.266245] iwl3945 0000:0c:00.0: Error setting RXON_ASSOC configuration (-110).
[34366.592276] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34366.592286] iwl3945 0000:0c:00.0: On demand firmware reload
[34370.754255] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34370.754266] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34371.252123] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34371.252134] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34371.753343] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34371.753353] iwl3945 0000:0c:00.0: On demand firmware reload
[34384.426985] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34384.426995] iwl3945 0000:0c:00.0: On demand firmware reload
[34409.600127] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34409.600136] iwl3945 0000:0c:00.0: On demand firmware reload
[34434.783296] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34434.783306] iwl3945 0000:0c:00.0: On demand firmware reload
[34605.531688] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34605.531698] iwl3945 0000:0c:00.0: On demand firmware reload
[34644.728133] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34644.728143] iwl3945 0000:0c:00.0: On demand firmware reload
[34680.784614] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[34680.784626] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[34681.708059] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[34681.708070] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[34682.430524] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34682.430535] iwl3945 0000:0c:00.0: On demand firmware reload
[34682.632199] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[34682.632210] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[34719.742092] iwl3945 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000008.
[34719.742099] iwl3945 0000:0c:00.0: Loaded firmware version: 15.32.2.9
[34719.742583] iwl3945 0000:0c:00.0: Start IWL Error Log Dump:
[34719.742585] iwl3945 0000:0c:00.0: Status: 0x000202E4, count: 1
[34719.742588] iwl3945 0000:0c:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
[34719.744675] iwl3945 0000:0c:00.0: SYSASSERT     (0x5) 3325245989 0x008B6 0x00274 0x00320 0x07AD4 116
[34719.744810] iwl3945 0000:0c:00.0: Start IWL Event Log Dump: display last 20 count
[34719.744852] iwl3945 0000:0c:00.0: 3325044329	0x00000002	0358
[34719.744874] iwl3945 0000:0c:00.0: 3325044517	0x00000000	0301
[34719.744897] iwl3945 0000:0c:00.0: 3325044523	0x00008000	0350
[34719.744919] iwl3945 0000:0c:00.0: 3325044743	0x000000d9	0106
[34719.744942] iwl3945 0000:0c:00.0: 3325044745	0x00000000	0302
[34719.744989] iwl3945 0000:0c:00.0: 3325044820	0x00000000	0308
[34719.745012] iwl3945 0000:0c:00.0: 3325044849	0x000007c3	0310
[34719.745035] iwl3945 0000:0c:00.0: 3325044868	0x000000d9	0106
[34719.745058] iwl3945 0000:0c:00.0: 3325044870	0x00000000	0302
[34719.745081] iwl3945 0000:0c:00.0: 3325045108	0x00000003	0358
[34719.745104] iwl3945 0000:0c:00.0: 3325045458	0x000000d9	0106
[34719.745126] iwl3945 0000:0c:00.0: 3325045460	0x00000000	0302
[34719.745148] iwl3945 0000:0c:00.0: 3325045698	0x00000004	0358
[34719.745171] iwl3945 0000:0c:00.0: 3325045994	0x000000d9	0106
[34719.745193] iwl3945 0000:0c:00.0: 3325045996	0x00000000	0302
[34719.745216] iwl3945 0000:0c:00.0: 3325046248	0x00000000	0308
[34719.745238] iwl3945 0000:0c:00.0: 3325046408	0x00000000	0310
[34719.745260] iwl3945 0000:0c:00.0: 3325046411	0x00000000	0302
[34719.745283] iwl3945 0000:0c:00.0: 3325245987	0x00000002	0123
[34719.745305] iwl3945 0000:0c:00.0: 3325245990	0x00000100	0125
[34719.745320] iwl3945 0000:0c:00.0: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0291 ser 0x00740000
[34719.750521] iwl3945 0000:0c:00.0: Can't stop Rx DMA.
[34769.884048] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34769.884058] iwl3945 0000:0c:00.0: On demand firmware reload
[34905.080042] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34905.080052] iwl3945 0000:0c:00.0: On demand firmware reload
[34912.200892] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34912.200901] iwl3945 0000:0c:00.0: On demand firmware reload
[34928.878239] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34928.878249] iwl3945 0000:0c:00.0: On demand firmware reload
[34935.036033] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34935.036043] iwl3945 0000:0c:00.0: On demand firmware reload
[34943.676141] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34943.676150] iwl3945 0000:0c:00.0: On demand firmware reload
[34948.310325] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34948.310335] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34948.808147] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34948.808156] iwl3945 0000:0c:00.0: On demand firmware reload
[34957.452107] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34957.452116] iwl3945 0000:0c:00.0: On demand firmware reload
[34968.588042] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34968.588048] iwl3945 0000:0c:00.0: On demand firmware reload
[34974.742320] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34974.742330] iwl3945 0000:0c:00.0: On demand firmware reload
[34979.892248] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34979.892253] iwl3945 0000:0c:00.0: On demand firmware reload
[34984.553862] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34985.051628] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[34985.051637] iwl3945 0000:0c:00.0: On demand firmware reload
[34990.223876] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34990.223881] iwl3945 0000:0c:00.0: On demand firmware reload
[34997.892064] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[34997.892074] iwl3945 0000:0c:00.0: On demand firmware reload
[35004.060612] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35004.060622] iwl3945 0000:0c:00.0: On demand firmware reload
[35008.237600] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35008.739131] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[35008.739138] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35009.242952] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[35009.242963] iwl3945 0000:0c:00.0: On demand firmware reload
[35013.909087] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35014.408064] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35014.408073] iwl3945 0000:0c:00.0: On demand firmware reload
[35022.581744] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35022.581754] iwl3945 0000:0c:00.0: On demand firmware reload
[35031.246437] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35031.246447] iwl3945 0000:0c:00.0: On demand firmware reload
[35036.405774] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35036.405780] iwl3945 0000:0c:00.0: On demand firmware reload
[35039.622239] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[35039.622251] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[35040.548158] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[35040.548170] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[35041.498375] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[35041.498386] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[35041.547209] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35041.547215] iwl3945 0000:0c:00.0: On demand firmware reload
[35046.212037] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35046.212043] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35046.712124] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35046.712134] iwl3945 0000:0c:00.0: On demand firmware reload
[35058.372116] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35058.372125] iwl3945 0000:0c:00.0: On demand firmware reload
[35065.533275] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35065.533285] iwl3945 0000:0c:00.0: On demand firmware reload
[35070.684144] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35070.684154] iwl3945 0000:0c:00.0: On demand firmware reload
[35078.340825] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35078.340825] iwl3945 0000:0c:00.0: On demand firmware reload
[35085.024116] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35085.024126] iwl3945 0000:0c:00.0: On demand firmware reload
[35091.204963] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35091.204973] iwl3945 0000:0c:00.0: On demand firmware reload
[35097.889163] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35097.889173] iwl3945 0000:0c:00.0: On demand firmware reload
[35116.584119] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35116.584129] iwl3945 0000:0c:00.0: On demand firmware reload
[35127.276030] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35127.276039] iwl3945 0000:0c:00.0: On demand firmware reload
[35131.956052] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35132.459582] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35132.459592] iwl3945 0000:0c:00.0: On demand firmware reload
[35137.108144] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35137.610776] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35137.610786] iwl3945 0000:0c:00.0: On demand firmware reload
[35150.296035] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35150.296041] iwl3945 0000:0c:00.0: On demand firmware reload
[35166.784156] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[35166.784167] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[35167.412072] iwl3945 0000:0c:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[35168.017420] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35168.017429] iwl3945 0000:0c:00.0: On demand firmware reload
[35168.212637] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[35168.212648] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[35175.870394] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35175.870400] iwl3945 0000:0c:00.0: On demand firmware reload
[35185.040043] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35185.040052] iwl3945 0000:0c:00.0: On demand firmware reload
[35197.669516] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35197.669525] iwl3945 0000:0c:00.0: On demand firmware reload
[35208.281484] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35208.281494] iwl3945 0000:0c:00.0: On demand firmware reload
[35213.460113] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35213.460123] iwl3945 0000:0c:00.0: On demand firmware reload
[35240.129570] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35240.129576] iwl3945 0000:0c:00.0: On demand firmware reload
[35265.772136] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35265.772146] iwl3945 0000:0c:00.0: On demand firmware reload
[35271.380148] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35271.380158] iwl3945 0000:0c:00.0: On demand firmware reload
[35290.488132] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35290.488142] iwl3945 0000:0c:00.0: On demand firmware reload
[35296.150331] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35296.150341] iwl3945 0000:0c:00.0: On demand firmware reload
[35345.800160] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35345.800170] iwl3945 0000:0c:00.0: On demand firmware reload
[35353.908041] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35353.908051] iwl3945 0000:0c:00.0: On demand firmware reload
[35387.016152] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35387.016162] iwl3945 0000:0c:00.0: On demand firmware reload
[35395.128160] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35395.128170] iwl3945 0000:0c:00.0: On demand firmware reload
[35429.736147] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35429.736157] iwl3945 0000:0c:00.0: On demand firmware reload
[35445.344162] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35445.344172] iwl3945 0000:0c:00.0: On demand firmware reload
[35450.952743] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35450.952752] iwl3945 0000:0c:00.0: On demand firmware reload
[35457.561355] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35457.561364] iwl3945 0000:0c:00.0: On demand firmware reload
[35467.668163] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35467.668172] iwl3945 0000:0c:00.0: On demand firmware reload
[35480.780138] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35480.780147] iwl3945 0000:0c:00.0: On demand firmware reload
[35485.888136] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35485.888146] iwl3945 0000:0c:00.0: On demand firmware reload
[35497.496757] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35497.496767] iwl3945 0000:0c:00.0: On demand firmware reload
[35497.643186] cfg80211: Calling CRDA for country: US
[35497.651165] cfg80211: Regulatory domain changed to country: US
[35509.136149] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35509.136159] iwl3945 0000:0c:00.0: On demand firmware reload
[35518.056190] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[35518.056201] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[35518.980868] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[35518.980879] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[35519.744115] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35519.744125] iwl3945 0000:0c:00.0: On demand firmware reload
[35519.904185] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[35519.904197] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[35541.512113] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35541.512123] iwl3945 0000:0c:00.0: On demand firmware reload
[35548.120158] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35548.120168] iwl3945 0000:0c:00.0: On demand firmware reload
[35569.728161] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35569.728171] iwl3945 0000:0c:00.0: On demand firmware reload
[35585.836113] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35585.836123] iwl3945 0000:0c:00.0: On demand firmware reload
[35613.444701] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35613.444710] iwl3945 0000:0c:00.0: On demand firmware reload
[35613.559979] cfg80211: Calling CRDA for country: US
[35613.564238] cfg80211: Regulatory domain changed to country: US
[35650.052161] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35650.052170] iwl3945 0000:0c:00.0: On demand firmware reload
[35663.660147] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35663.660157] iwl3945 0000:0c:00.0: On demand firmware reload
[35671.268122] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35671.268131] iwl3945 0000:0c:00.0: On demand firmware reload
[35773.518029] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35773.518034] iwl3945 0000:0c:00.0: On demand firmware reload
[35785.676108] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35785.676117] iwl3945 0000:0c:00.0: On demand firmware reload
[35792.837219] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35792.837229] iwl3945 0000:0c:00.0: On demand firmware reload
[35797.988515] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35797.988525] iwl3945 0000:0c:00.0: On demand firmware reload
[35802.616045] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35803.117791] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35803.117801] iwl3945 0000:0c:00.0: On demand firmware reload
[35807.278850] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35807.278861] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35807.780609] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35807.780620] iwl3945 0000:0c:00.0: Queue 0 stuck for 2000 ms.
[35807.780627] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35808.280775] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35808.280785] iwl3945 0000:0c:00.0: On demand firmware reload
[35808.674017] cfg80211: Calling CRDA for country: US
[35808.683126] cfg80211: Regulatory domain changed to country: US
[35815.436735] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35815.436742] iwl3945 0000:0c:00.0: On demand firmware reload
[35824.608125] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35824.608135] iwl3945 0000:0c:00.0: On demand firmware reload
[35825.257890] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35830.260070] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35830.260079] iwl3945 0000:0c:00.0: On demand firmware reload
[35838.940073] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35838.940083] iwl3945 0000:0c:00.0: On demand firmware reload
[35848.560110] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35848.560119] iwl3945 0000:0c:00.0: On demand firmware reload
[35853.236058] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35853.737056] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35853.737066] iwl3945 0000:0c:00.0: On demand firmware reload
[35861.391703] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35861.391709] iwl3945 0000:0c:00.0: On demand firmware reload
[35861.548136] iwl3945 0000:0c:00.0: Error removing station c0:c1:c0:9d:6a:2e
[35861.596554] cfg80211: Calling CRDA for country: US
[35861.603870] cfg80211: Regulatory domain changed to country: US
[35871.050103] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35871.050112] iwl3945 0000:0c:00.0: On demand firmware reload
[35877.636095] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[35877.636106] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[35877.700764] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35877.700773] iwl3945 0000:0c:00.0: On demand firmware reload
[35882.868134] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35882.868143] iwl3945 0000:0c:00.0: On demand firmware reload
[35886.508018] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35887.008144] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35887.514766] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35888.008150] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35888.008160] iwl3945 0000:0c:00.0: On demand firmware reload
[35894.668538] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35894.668548] iwl3945 0000:0c:00.0: On demand firmware reload
[35901.844060] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35901.844069] iwl3945 0000:0c:00.0: On demand firmware reload
[35910.518289] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35910.518299] iwl3945 0000:0c:00.0: On demand firmware reload
[35915.684141] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35915.684150] iwl3945 0000:0c:00.0: On demand firmware reload
[35921.340113] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35921.340123] iwl3945 0000:0c:00.0: On demand firmware reload
[35926.495894] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35926.495903] iwl3945 0000:0c:00.0: On demand firmware reload
[35931.634001] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35931.634009] iwl3945 0000:0c:00.0: On demand firmware reload
[35936.804033] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35936.804043] iwl3945 0000:0c:00.0: On demand firmware reload
[35941.486862] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35941.984116] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35941.984126] iwl3945 0000:0c:00.0: On demand firmware reload
[35948.164488] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35948.164498] iwl3945 0000:0c:00.0: On demand firmware reload
[35954.330813] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35954.330823] iwl3945 0000:0c:00.0: On demand firmware reload
[35958.957241] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35958.957247] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35959.456956] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[35959.456967] iwl3945 0000:0c:00.0: On demand firmware reload
[35972.604203] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35972.604212] iwl3945 0000:0c:00.0: On demand firmware reload
[35987.712165] iwl3945 0000:0c:00.0: Queue 2 stuck for 2000 ms.
[35987.712174] iwl3945 0000:0c:00.0: On demand firmware reload
[36000.324181] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[36000.324192] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[36001.249073] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[36001.249085] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[36001.833296] iwl3945 0000:0c:00.0: Queue 4 stuck for 2000 ms.
[36001.833306] iwl3945 0000:0c:00.0: On demand firmware reload
[36002.172913] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[36002.172924] iwl3945 0000:0c:00.0: Error clearing ASSOC_MSK on current configuration (-110).

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:C1:C0:9D:6A:2E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000020218416056
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0004486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B000103104700109EB40C7AEF63DE362B7F43CC42DC1DDE102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:22:6B:87:70:1A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018734a79a0
                    Extra: Last beacon: 5024ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000700000000000000000000000000000000000000
                    IE: Unknown: DD820050F204104A0001101044000101103B000103104700102880288028801880A88000226B87701A1021000C4C696E6B73797320496E632E102300095752543136304E76321024000776322E302E3032104200033030381054000800060050F2040001101100114C696E6B737973205752543136304E7632100800020084103C000101
```

---

### Post by praseodym on 2011-12-24
Disable IPv6 system wide:

```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
and reboot. Set IPv6 to "Ignore" in the network-manager, and disable IPv6 in Firefox:

Type in
```
about:config
```
and change
```
network.dns.disableIPv6
```
via double click to "true". Restart FF

---

### Post by Icedrake99 on 2011-12-24
I use Chrome, so how do I disable IPv6 in chrome? But I'd like to know, what exactly will disabling IPv6 supposed to do?

---

### Post by praseodym on 2011-12-24
Edit the starter of "Chrome" and let it look like:

```
/usr/bin/chromium-browser --disable-ipv6 %U
```

---

### Post by Icedrake99 on 2011-12-24
Somehow, I don't think this is a problem with IPv6. My internet worked fine in 11.04, and I didn't do any of this then. It's just after upgrading to 11.10.

---

### Post by praseodym on 2011-12-24
Try a

```
sudo iwconfig wlan0 txpower 20
iwconfig #control
dmesg | egrep 'ipw|country'
```
Does the router send in N-mode, too?

---

### Post by Icedrake99 on 2011-12-24
```
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.
iwconfig #control
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:C1:C0:9D:6A:2E   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:84   Missed beacon:0

dmesg | egrep 'ipw|country'
[35613.559979] cfg80211: Calling CRDA for country: US
[35613.564238] cfg80211: Regulatory domain changed to country: US
[35808.674017] cfg80211: Calling CRDA for country: US
[35808.683126] cfg80211: Regulatory domain changed to country: US
[35861.596554] cfg80211: Calling CRDA for country: US
[35861.603870] cfg80211: Regulatory domain changed to country: US
[36026.690205] cfg80211: Calling CRDA for country: US
[36026.709618] cfg80211: Regulatory domain changed to country: US
[36159.577137] cfg80211: Calling CRDA for country: US
[36159.585991] cfg80211: Regulatory domain changed to country: US
[36445.713410] cfg80211: Calling CRDA for country: US
[36445.728658] cfg80211: Regulatory domain changed to country: US
[36931.639884] cfg80211: Calling CRDA for country: US
[36931.648392] cfg80211: Regulatory domain changed to country: US
[37215.551634] cfg80211: Calling CRDA for country: US
[37215.560652] cfg80211: Regulatory domain changed to country: US
[79382.685659] cfg80211: Calling CRDA for country: US
[79382.696546] cfg80211: Regulatory domain changed to country: US
[79863.572781] cfg80211: Calling CRDA for country: US
[79863.579654] cfg80211: Regulatory domain changed to country: US
[79947.597546] cfg80211: Calling CRDA for country: US
[79947.601910] cfg80211: Regulatory domain changed to country: US
[79964.573159] cfg80211: Calling CRDA for country: US
[79964.581348] cfg80211: Regulatory domain changed to country: US
[80150.402474] cfg80211: Calling CRDA for country: US
[80150.422778] cfg80211: Regulatory domain changed to country: US

```

I've also changed my dns servers to auto from using OpenDNS.

---

### Post by praseodym on 2011-12-24
Ok,

some more:

```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig wlan0
route -n
```
Check the mtu-value of your ISP and add it as a numer instead of "Automatic" in the network-manager

Edit: Update the firmware with the package "linux-firmware" and reboot

---

### Post by mboland002 on 2011-12-27
I have a similar problem with a wired connection, tried a number of fixes and none seem to work.

```
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8221]
    Kernel driver in use: forcedeth
mike@BOLAND-UBUNTU:~$ lsmod
Module                  Size  Used by
vesafb                 13489  1 
snd_usb_audio         100880  1 
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_hda_codec_hdmi     31426  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
fglrx                2788305  114 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80435  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
gspca_zc3xx            51066  0 
gspca_main             27610  1 gspca_zc3xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
videodev               85626  1 gspca_main
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  1 
snd                    55902  20 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_atk0110           17742  0 
psmouse                63474  0 
serio_raw              12990  0 
nv_tco                 13399  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35846  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_amd               13753  0 
sata_nv                23379  3 
forcedeth              58103  0 
mike@BOLAND-UBUNTU:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1532:0015 Razer USA, Ltd 
Bus 002 Device 003: ID 06a3:8020 Saitek PLC Eclipse Keyboard
Bus 002 Device 004: ID 046d:08d8 Logitech, Inc. QuickCam for Notebook Deluxe
Bus 002 Device 005: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
mike@BOLAND-UBUNTU:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.2.1
mike@BOLAND-UBUNTU:~$ sudo iwlist scan
[sudo] password for mike: 
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

```

---

### Post by praseodym on 2011-12-27
Hi mboland002,

the driver often needs two additional parameters:

```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
sudo modprobe -rfv forcedeth
sudo modprobe -v forcedeth
```

---

### Post by mboland002 on 2011-12-27
> **praseodym said:**
> Hi mboland002,

the driver often needs two additional parameters:

```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
sudo modprobe -rfv forcedeth
sudo modprobe -v forcedeth
```

Problem solved, thanks!

---

### Post by Dawnbreaker on 2012-04-13
I have the very same issue on my thinkpad t61, wireless dl speed is extremely slow and when I dl something through my torrent client the whole connection dies. I disabled the ipv6 thing as mentioned below, and there seemed to be some results, I'm reaching again the maximum DL speed like on Windows, but it's still not that stable. Anyway this almost solved the problem, thanks!

> **praseodym said:**
> Disable IPv6 system wide:

```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```and reboot. Set IPv6 to "Ignore" in the network-manager, and disable IPv6 in Firefox:

Type in
```
about:config
```and change
```
network.dns.disableIPv6
```via double click to "true". Restart FF


---
Let's hope that in 12.04 this will get fixed we won't have the same issues with slow wifi.

---

### Post by TooTechy on 2013-03-31
I am having the same issue now - actually on openSuse, but I had it before on Ubuntu. Oddly enough, and I wanted to record it somewhere it might be found, I managed to greatly reduce the problem by disabling Bluetooth in the BIOS.

Now I get the issue every half hour or so rather than several times a minute.

The implication is that perhaps one driver is stomping on another (tech speak there.. ;-) Perhaps radio interference (Less likely)?



> **Icedrake99 said:**
> Here you go:

```
~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 9400 Laptop [1028:01cd]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Device [8086:1020]
	Kernel driver in use: iwl3945

~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
zram                   18007  2 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
binfmt_misc            17292  1 
dell_laptop            13519  0 
usbhid                 41905  0 
dcdbas                 14098  1 dell_laptop
hid                    77367  1 usbhid
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
iwl3945                73360  0 
radeon                925193  3 
iwl_legacy             71499  1 iwl3945
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              393459  2 iwl3945,iwl_legacy
r592                   17808  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
mtd                    35852  2 sm_common,nand
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
wmi                    18744  1 dell_wmi
drm                   192194  5 radeon,ttm,drm_kms_helper
video                  18908  0 
snd                    55902  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 radeon
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
b44                    31443  0 
ssb                    50682  1 b44
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 005 Device 002: ID 0461:4d0f Primax Electronics, Ltd 

cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 208.67.222.222
nameserver 208.67.220.220

~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:C1:C0:9D:6A:2E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001fb33b4451c
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 0004486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B000103104700109EB40C7AEF63DE362B7F43CC42DC1DDE102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
```

---

### Post by TooTechy on 2013-03-31
I am having the same issue now - actually on openSuse, but I had it before on Ubuntu. Oddly enough, and I wanted to record it somewhere it might be found, I managed to greatly reduce the problem by disabling Bluetooth in the BIOS.

Now I get the issue every half hour or so rather than several times a minute.

The implication is that perhaps one driver is stomping on another (tech speak there.. ;-) Perhaps radio interference (Less likely)?

---

### Post by wildmanne39 on 2013-03-31
Thread closed. Please do not post in old threads.

---

