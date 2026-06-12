---
title: "Slow wireless in 11.10 with Broadcom 4401"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by brohan76 on 2011-11-09
First of all, thank you for taking a look, and helping with my problem. I am new to Ubuntu, and this is my first post on these forums.  I installed Ubuntu 11.10 on my Dell Inspiron 6400. The install is dual boot with Windows Vista (Ubuntu is on separate partition).  I have been able to configure just about everything to my liking but have 2 issues the first is a slow internet connection. In windows I get about 7.5 download per speedtest.net, in Ubuntu I get .5. Here is some info on my system

```
[COLOR="Red"]bjrohan@bjrohan-MM061:~$ lspci -nnk | grep -iA2 net[/COLOR]
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 6400 [1028:01af]
	Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Device [8086:1020]
	Kernel driver in use: iwl3945
bjrohan@bjrohan-MM061:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 6400 [1028:01af]
	Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Device [8086:1020]
	Kernel driver in use: iwl3945


[COLOR="Red"]bjrohan@bjrohan-MM061:~$ lsmod[/COLOR]
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44173  0 
uas                    17699  0 
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
usbhid                 41905  0 
hid                    77367  1 usbhid
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hda_codec_idt      60049  1 
arc4                   12473  2 
iwl3945                73360  0 
iwl_legacy             71499  1 iwl3945
btusb                  18160  2 
mac80211              393459  2 iwl3945,iwl_legacy
snd_hda_intel          24262  1 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
psmouse                73673  0 
snd_hwdep              13276  1 snd_hda_codec
r852                   17901  0 
sm_common              16737  1 r852
nand                   49707  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
bluetooth             148839  23 bnep,rfcomm,btusb
serio_raw              12990  0 
mtd                    35852  2 sm_common,nand
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
radeon                925094  3 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18908  0 
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
wmi                    18744  1 dell_wmi
i2c_algo_bit           13199  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
b44                    31443  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    50682  1 b44
```




My second issue is that the any and all sounds are garbled (CD's, internet video/audio, even the speaker tests for setting up audio settings)

Again, thank you for your help.

---

### Post by praseodym on 2011-11-09
Hi,

can you show additionally:

```
dmesg | grep iwl
sudo iwlist scan
cat /etc/resolv.conf
iwconfig
ifconfig -a
```

---

### Post by brohan76 on 2011-11-09
Here is what I get, although not all of it (as you will be able to see)

[COLOR="Red"]dmesg | grep iwl:[/COLOR]

```
[85062.620056] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85062.620087] iwl3945 0000:0b:00.0: On demand firmware reload
[85126.977474] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85126.977481] iwl3945 0000:0b:00.0: On demand firmware reload
[85163.220080] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85163.220091] iwl3945 0000:0b:00.0: On demand firmware reload
[85167.411832] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85167.411845] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85167.908050] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85167.908057] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[85167.908060] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85168.408075] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85168.408084] iwl3945 0000:0b:00.0: On demand firmware reload
[85176.076389] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85176.076401] iwl3945 0000:0b:00.0: On demand firmware reload
[85199.790236] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[85199.790249] iwl3945 0000:0b:00.0: On demand firmware reload
[85232.032263] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85232.032269] iwl3945 0000:0b:00.0: On demand firmware reload
[85352.588066] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85352.588078] iwl3945 0000:0b:00.0: On demand firmware reload
[85412.344035] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85412.344041] iwl3945 0000:0b:00.0: On demand firmware reload
[85455.542070] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[85455.542077] iwl3945 0000:0b:00.0: On demand firmware reload
[85475.720022] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85475.720028] iwl3945 0000:0b:00.0: On demand firmware reload
[85481.404033] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85481.404040] iwl3945 0000:0b:00.0: On demand firmware reload
[85568.540068] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85568.540080] iwl3945 0000:0b:00.0: On demand firmware reload
[85607.668245] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85607.668252] iwl3945 0000:0b:00.0: On demand firmware reload
[85945.904057] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85945.904068] iwl3945 0000:0b:00.0: On demand firmware reload
[85950.077765] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85950.077771] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85950.576072] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85950.576085] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[85950.576093] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85951.076046] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85951.076058] iwl3945 0000:0b:00.0: On demand firmware reload
[85968.260066] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85968.260077] iwl3945 0000:0b:00.0: On demand firmware reload
[85978.896055] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85978.896066] iwl3945 0000:0b:00.0: On demand firmware reload
[85983.060007] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85983.060043] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85983.561363] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85983.561370] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[85983.561373] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[85984.060067] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85984.060079] iwl3945 0000:0b:00.0: On demand firmware reload
[85990.730619] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[85990.730631] iwl3945 0000:0b:00.0: On demand firmware reload
[86090.909022] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[86090.909034] iwl3945 0000:0b:00.0: On demand firmware reload
[86148.088963] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[86148.088974] iwl3945 0000:0b:00.0: On demand firmware reload
[86178.716066] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[86178.716073] iwl3945 0000:0b:00.0: On demand firmware reload
[90385.912069] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[90385.912080] iwl3945 0000:0b:00.0: On demand firmware reload
[90474.584058] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[90474.584070] iwl3945 0000:0b:00.0: On demand firmware reload
[90477.736077] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[90477.736090] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90478.236038] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[90478.236050] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90478.748071] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[90478.748084] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[90478.748092] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90479.253902] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[90479.253915] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[90479.253923] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90479.761788] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[90479.761800] iwl3945 0000:0b:00.0: On demand firmware reload
[90480.012411] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[90480.012424] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[90480.521729] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[90489.734274] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90489.734280] iwl3945 0000:0b:00.0: On demand firmware reload
[90492.368369] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90492.872735] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[90492.872742] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90493.381373] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[90493.381380] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90493.890502] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[90493.890524] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90494.009024] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[90494.009037] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[90494.388432] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[90494.388444] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[90494.508376] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[90494.889325] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[90494.889331] iwl3945 0000:0b:00.0: On demand firmware reload
[90495.013382] iwl3945 0000:0b:00.0: Error sending REPLY_REMOVE_STA: time out after 500ms.
[90495.013392] iwl3945 0000:0b:00.0: Error removing station 00:21:29:9c:d4:9d
[91161.912069] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91161.912082] iwl3945 0000:0b:00.0: On demand firmware reload
[91366.720087] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[91366.720098] iwl3945 0000:0b:00.0: On demand firmware reload
[91485.967839] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[91485.967851] iwl3945 0000:0b:00.0: On demand firmware reload
[91489.134234] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[91489.134243] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91489.640559] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[91489.640565] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[91489.640569] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91490.150885] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[91490.150893] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[91490.150898] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91490.650471] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[91490.650478] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[91490.650481] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91491.026073] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[91491.026086] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[91491.148028] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[91491.148034] iwl3945 0000:0b:00.0: On demand firmware reload
[91491.524070] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[91501.280848] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91501.280860] iwl3945 0000:0b:00.0: On demand firmware reload
[91505.454278] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91505.961762] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[91505.961769] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91506.460565] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[91506.460573] iwl3945 0000:0b:00.0: On demand firmware reload
[91516.204047] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91516.204058] iwl3945 0000:0b:00.0: On demand firmware reload
[91520.872031] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[91521.372031] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[91521.372038] iwl3945 0000:0b:00.0: On demand firmware reload
[91868.061673] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[91868.061684] iwl3945 0000:0b:00.0: On demand firmware reload
[91933.192820] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[91933.192832] iwl3945 0000:0b:00.0: On demand firmware reload
[91957.305067] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[91957.305079] iwl3945 0000:0b:00.0: On demand firmware reload
[92052.416086] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[92052.416098] iwl3945 0000:0b:00.0: On demand firmware reload
[92367.128085] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[92367.128096] iwl3945 0000:0b:00.0: On demand firmware reload
[92398.757352] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[92398.757364] iwl3945 0000:0b:00.0: On demand firmware reload
[92906.744041] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[92906.744053] iwl3945 0000:0b:00.0: On demand firmware reload
[93039.430597] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[93039.430609] iwl3945 0000:0b:00.0: On demand firmware reload
[103503.324327] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[103503.324339] iwl3945 0000:0b:00.0: On demand firmware reload
[103796.064060] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[103796.064072] iwl3945 0000:0b:00.0: On demand firmware reload
[103865.804047] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[103865.804059] iwl3945 0000:0b:00.0: On demand firmware reload
[104023.989830] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[104023.989836] iwl3945 0000:0b:00.0: On demand firmware reload
[104117.752029] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[104117.752036] iwl3945 0000:0b:00.0: On demand firmware reload
[104122.885321] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[104122.885331] iwl3945 0000:0b:00.0: On demand firmware reload
[104171.072633] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[104171.072644] iwl3945 0000:0b:00.0: On demand firmware reload
[104186.691669] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[104186.691681] iwl3945 0000:0b:00.0: On demand firmware reload
[104303.425366] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[104303.425373] iwl3945 0000:0b:00.0: On demand firmware reload
[104309.558449] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[104309.558456] iwl3945 0000:0b:00.0: On demand firmware reload
[104396.736087] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[104396.736099] iwl3945 0000:0b:00.0: On demand firmware reload
[105412.200087] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[105412.200098] iwl3945 0000:0b:00.0: On demand firmware reload
[105485.584092] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[105485.584105] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[105486.213789] iwl3945 0000:0b:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[105487.013145] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[105487.013159] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[105487.352065] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[105487.352075] iwl3945 0000:0b:00.0: On demand firmware reload
[105487.637588] iwl3945 0000:0b:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[105498.272324] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[105498.272336] iwl3945 0000:0b:00.0: On demand firmware reload
[105811.988263] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[105811.988268] iwl3945 0000:0b:00.0: On demand firmware reload
[106617.033569] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[106617.033580] iwl3945 0000:0b:00.0: On demand firmware reload
[106769.468049] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[106769.468055] iwl3945 0000:0b:00.0: On demand firmware reload
[106786.172032] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[106786.172040] iwl3945 0000:0b:00.0: On demand firmware reload
[106801.643752] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[106801.643766] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[106802.280418] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[106802.280433] iwl3945 0000:0b:00.0: Error setting RXON_ASSOC configuration (-110).
[106802.336047] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[106802.336059] iwl3945 0000:0b:00.0: On demand firmware reload
[106818.045462] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[106818.045474] iwl3945 0000:0b:00.0: On demand firmware reload
[106867.308447] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[106867.308459] iwl3945 0000:0b:00.0: On demand firmware reload
[106884.004161] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[106884.004168] iwl3945 0000:0b:00.0: On demand firmware reload
[106971.949494] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[106971.949501] iwl3945 0000:0b:00.0: On demand firmware reload
[106976.084041] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[106976.584081] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[106977.087819] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[106977.087831] iwl3945 0000:0b:00.0: On demand firmware reload
[106982.249240] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[106982.249251] iwl3945 0000:0b:00.0: On demand firmware reload
[106986.892031] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[106987.392100] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[106987.392112] iwl3945 0000:0b:00.0: On demand firmware reload
[106993.560780] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[106993.560792] iwl3945 0000:0b:00.0: On demand firmware reload
[106999.208137] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[106999.208143] iwl3945 0000:0b:00.0: On demand firmware reload
[107003.856034] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107004.356155] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107004.356166] iwl3945 0000:0b:00.0: On demand firmware reload
[107012.533938] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107012.533946] iwl3945 0000:0b:00.0: On demand firmware reload
[107017.708145] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107017.708157] iwl3945 0000:0b:00.0: On demand firmware reload
[107022.872867] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107022.872879] iwl3945 0000:0b:00.0: On demand firmware reload
[107027.012613] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107027.512145] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107027.512158] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107028.012080] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107028.012092] iwl3945 0000:0b:00.0: On demand firmware reload
[107032.170176] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107032.668025] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[107032.668031] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107033.168067] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[107033.168079] iwl3945 0000:0b:00.0: On demand firmware reload
[107038.340551] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107038.340558] iwl3945 0000:0b:00.0: On demand firmware reload
[107051.027896] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107051.027907] iwl3945 0000:0b:00.0: On demand firmware reload
[107132.380725] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107132.380731] iwl3945 0000:0b:00.0: On demand firmware reload
[107136.540034] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[107136.540044] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107137.041414] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[107137.041421] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107137.542041] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[107137.542050] iwl3945 0000:0b:00.0: On demand firmware reload
[107138.020041] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[107138.020049] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[107138.524102] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[107148.740032] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107148.740039] iwl3945 0000:0b:00.0: On demand firmware reload
[107357.099021] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107357.099027] iwl3945 0000:0b:00.0: On demand firmware reload
[107361.254712] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107361.753542] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[107361.753554] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107362.263828] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[107362.263840] iwl3945 0000:0b:00.0: On demand firmware reload
[107367.943397] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107367.943409] iwl3945 0000:0b:00.0: On demand firmware reload
[107386.128797] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107386.128808] iwl3945 0000:0b:00.0: On demand firmware reload
[107390.284497] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107390.784045] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107391.284041] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[107391.284048] iwl3945 0000:0b:00.0: On demand firmware reload
[107398.952348] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107398.952355] iwl3945 0000:0b:00.0: On demand firmware reload
[107401.648554] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[107401.648562] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[107402.281273] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[107402.281284] iwl3945 0000:0b:00.0: Error setting RXON_ASSOC configuration (-110).
[107403.098879] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[107403.098890] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[107403.104045] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107403.104059] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107403.609700] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107403.609707] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107403.726100] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[107403.726114] iwl3945 0000:0b:00.0: Error setting RXON_ASSOC configuration (-110).
[107404.108052] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107404.108058] iwl3945 0000:0b:00.0: On demand firmware reload
[107404.524051] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[107404.524059] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[107407.545416] iwl3945 0000:0b:00.0: Microcode SW error detected. Restarting 0x82000008.
[107407.545430] iwl3945 0000:0b:00.0: Loaded firmware version: 15.32.2.9
[107407.545469] iwl3945 0000:0b:00.0: Start IWL Error Log Dump:
[107407.545477] iwl3945 0000:0b:00.0: Status: 0x000202E4, count: 1
[107407.545484] iwl3945 0000:0b:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
[107407.545718] iwl3945 0000:0b:00.0: SYSASSERT     (0x5) 0197945637 0x008B6 0x00274 0x0031C 0x07AD4 116
[107407.545855] iwl3945 0000:0b:00.0: Start IWL Event Log Dump: display last 20 count
[107407.545902] iwl3945 0000:0b:00.0: 0197741054	0x0000027e	1053
[107407.545929] iwl3945 0000:0b:00.0: 0197741149	0x000000d9	0106
[107407.545957] iwl3945 0000:0b:00.0: 0197741151	0x00000000	0301
[107407.545985] iwl3945 0000:0b:00.0: 0197743464	0x00000000	0308
[107407.546012] iwl3945 0000:0b:00.0: 0197743616	0x000007c3	0310
[107407.546040] iwl3945 0000:0b:00.0: 0197743627	0x000000d9	0106
[107407.546067] iwl3945 0000:0b:00.0: 0197743628	0x00000000	0301
[107407.546095] iwl3945 0000:0b:00.0: 0197743702	0x00000094	0353
[107407.546122] iwl3945 0000:0b:00.0: 0197743712	0x00000000	0352
[107407.546150] iwl3945 0000:0b:00.0: 0197744380	0x000000d9	0106
[107407.546177] iwl3945 0000:0b:00.0: 0197744381	0x00000000	0301
[107407.546205] iwl3945 0000:0b:00.0: 0197744456	0x00000095	0353
[107407.546232] iwl3945 0000:0b:00.0: 0197744466	0x00000000	0352
[107407.546260] iwl3945 0000:0b:00.0: 0197745637	0x000000d9	0106
[107407.546287] iwl3945 0000:0b:00.0: 0197745639	0x00000000	0302
[107407.546315] iwl3945 0000:0b:00.0: 0197746323	0x00000000	0308
[107407.546342] iwl3945 0000:0b:00.0: 0197746528	0x00000000	0310
[107407.546369] iwl3945 0000:0b:00.0: 0197746531	0x00000000	0302
[107407.546397] iwl3945 0000:0b:00.0: 0197945635	0x00000002	0123
[107407.546424] iwl3945 0000:0b:00.0: 0197945638	0x00000100	0125
[107407.546459] iwl3945 0000:0b:00.0: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x023A ser 0x00740000
[107407.551068] iwl3945 0000:0b:00.0: Can't stop Rx DMA.
[107411.136038] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107411.136044] iwl3945 0000:0b:00.0: On demand firmware reload
[107418.788980] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107418.788991] iwl3945 0000:0b:00.0: On demand firmware reload
[107422.916344] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107422.916356] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107423.417456] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107423.417468] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107423.917717] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107423.917723] iwl3945 0000:0b:00.0: On demand firmware reload
[107429.040041] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107429.040053] iwl3945 0000:0b:00.0: On demand firmware reload
[107433.664042] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107434.164037] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107434.164044] iwl3945 0000:0b:00.0: On demand firmware reload
[107438.285514] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107438.784406] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107438.784419] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107439.284935] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107439.284947] iwl3945 0000:0b:00.0: On demand firmware reload
[107456.908038] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107456.908049] iwl3945 0000:0b:00.0: On demand firmware reload
[107696.216418] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107696.216430] iwl3945 0000:0b:00.0: On demand firmware reload
[107808.552215] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[107808.552226] iwl3945 0000:0b:00.0: On demand firmware reload
[107881.633206] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[107881.633219] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[107882.256507] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[107882.256515] iwl3945 0000:0b:00.0: Error setting RXON_ASSOC configuration (-110).
[107882.728035] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[107882.728043] iwl3945 0000:0b:00.0: On demand firmware reload
[107883.060211] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[107883.060224] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[108362.304093] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[108362.304107] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[108363.230340] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[108363.230353] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[108363.902691] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[108363.902697] iwl3945 0000:0b:00.0: On demand firmware reload
[108364.288622] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[108364.288631] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[108637.140033] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[108637.140045] iwl3945 0000:0b:00.0: On demand firmware reload
[108737.404694] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[108737.404706] iwl3945 0000:0b:00.0: On demand firmware reload
[112081.640072] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[112081.640086] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[112082.270026] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[112082.270041] iwl3945 0000:0b:00.0: Error setting RXON_ASSOC configuration (-110).
[112083.082719] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[112083.082733] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[112083.220038] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112083.220045] iwl3945 0000:0b:00.0: On demand firmware reload
[112083.704209] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[112083.704223] iwl3945 0000:0b:00.0: Error setting RXON_ASSOC configuration (-110).
[112086.860042] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112087.360027] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112087.360034] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112087.860039] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112087.860052] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112088.360034] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112088.360041] iwl3945 0000:0b:00.0: On demand firmware reload
[112088.546029] iwl3945 0000:0b:00.0: Error removing station 00:21:29:9c:d4:9d
[112102.040590] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112102.040597] iwl3945 0000:0b:00.0: On demand firmware reload
[112117.208189] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112117.208195] iwl3945 0000:0b:00.0: On demand firmware reload
[112120.373593] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112120.875735] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112120.875747] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112121.372044] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112121.372057] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112121.874294] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112121.874307] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112122.000119] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[112122.000132] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[112122.372095] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112122.372107] iwl3945 0000:0b:00.0: On demand firmware reload
[112122.500055] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[112129.676273] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112129.676285] iwl3945 0000:0b:00.0: On demand firmware reload
[112132.818223] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112133.324648] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112133.324661] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112133.830845] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112133.830857] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112133.830865] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112134.328994] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112134.329006] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112134.329014] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112134.828080] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112134.828092] iwl3945 0000:0b:00.0: On demand firmware reload
[112135.005206] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[112135.005213] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[112135.504169] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[112145.172216] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112145.172222] iwl3945 0000:0b:00.0: On demand firmware reload
[112153.305588] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112153.305599] iwl3945 0000:0b:00.0: On demand firmware reload
[112159.428072] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112159.428083] iwl3945 0000:0b:00.0: On demand firmware reload
[112168.537727] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112168.537739] iwl3945 0000:0b:00.0: On demand firmware reload
[112189.192042] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112189.192054] iwl3945 0000:0b:00.0: On demand firmware reload
[112197.328061] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112197.328068] iwl3945 0000:0b:00.0: On demand firmware reload
[112201.632064] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[112201.632071] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[112202.256077] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[112202.256091] iwl3945 0000:0b:00.0: Error setting RXON_ASSOC configuration (-110).
[112203.057703] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[112203.057710] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[112203.436070] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112203.436081] iwl3945 0000:0b:00.0: On demand firmware reload
[112203.680462] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[112203.680475] iwl3945 0000:0b:00.0: Error setting RXON_ASSOC configuration (-110).
[112211.813528] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112211.813534] iwl3945 0000:0b:00.0: On demand firmware reload
[112216.928036] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112216.928048] iwl3945 0000:0b:00.0: On demand firmware reload
[112232.056036] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112232.056042] iwl3945 0000:0b:00.0: On demand firmware reload
[112284.220111] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112284.220118] iwl3945 0000:0b:00.0: On demand firmware reload
[112287.369402] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112287.869305] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112287.869312] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112288.368031] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112288.368038] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112288.868027] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112288.868034] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112289.016725] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[112289.016732] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[112289.368023] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112289.368030] iwl3945 0000:0b:00.0: On demand firmware reload
[112289.516030] iwl3945 0000:0b:00.0: Error sending REPLY_RXON_ASSOC: time out after 500ms.
[112300.767561] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112300.767573] iwl3945 0000:0b:00.0: On demand firmware reload
[112305.944999] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[112305.945005] iwl3945 0000:0b:00.0: On demand firmware reload
[112457.770404] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112457.770410] iwl3945 0000:0b:00.0: On demand firmware reload
[112489.936030] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[112489.936036] iwl3945 0000:0b:00.0: On demand firmware reload
[112744.436039] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[112744.436046] iwl3945 0000:0b:00.0: On demand firmware reload
[113002.880906] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[113002.880912] iwl3945 0000:0b:00.0: On demand firmware reload
[113006.541637] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113007.049008] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113007.049015] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[113007.549255] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113007.549262] iwl3945 0000:0b:00.0: Queue 0 stuck for 2000 ms.
[113007.549265] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[113008.054166] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113008.054172] iwl3945 0000:0b:00.0: On demand firmware reload
[113012.680019] iwl3945 0000:0b:00.0: Queue 2 stuck for 2000 ms.
[113013.180168] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113013.180177] iwl3945 0000:0b:00.0: On demand firmware reload
[113224.408068] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113224.408079] iwl3945 0000:0b:00.0: On demand firmware reload
[113247.584026] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113247.584032] iwl3945 0000:0b:00.0: On demand firmware reload
[113263.749537] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113263.749544] iwl3945 0000:0b:00.0: On demand firmware reload
[113271.393891] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113271.393898] iwl3945 0000:0b:00.0: On demand firmware reload
[113360.212329] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113360.212335] iwl3945 0000:0b:00.0: On demand firmware reload
[113392.408023] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113392.408029] iwl3945 0000:0b:00.0: On demand firmware reload
[113422.032031] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113422.032038] iwl3945 0000:0b:00.0: On demand firmware reload
[113810.472029] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[113810.472035] iwl3945 0000:0b:00.0: On demand firmware reload
[114164.408091] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[114164.408105] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[114165.033084] iwl3945 0000:0b:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[114165.832065] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[114165.832073] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[114165.924032] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[114165.924041] iwl3945 0000:0b:00.0: On demand firmware reload
[114488.316283] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[114488.316295] iwl3945 0000:0b:00.0: On demand firmware reload
[114503.972040] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[114503.972051] iwl3945 0000:0b:00.0: On demand firmware reload
[114521.146116] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[114521.146127] iwl3945 0000:0b:00.0: On demand firmware reload
[114521.632105] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[114521.632118] iwl3945 0000:0b:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[114795.480045] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[114795.480052] iwl3945 0000:0b:00.0: On demand firmware reload
[114903.752695] iwl3945 0000:0b:00.0: Queue 4 stuck for 2000 ms.
[114903.752707] iwl3945 0000:0b:00.0: On demand firmware reload
```

[COLOR="Red"]sudo iwlist scan:[/COLOR]

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:9C:D4:9D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"Rohan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010d84b8c85
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0005526F68616E
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD090010180202F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:21:29:9C:D4:9D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010d844a183
                    Extra: Last beacon: 528ms ago
                    IE: Unknown: 00050000000000
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD090010180202F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:00:00:00:00:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010d9c1e25e
                    Extra: Last beacon: 484ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 40:4A:03:E0:D8:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"myqwest3539"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003dbe5b8a236
                    Extra: Last beacon: 12372ms ago
                    IE: Unknown: 000B6D79717765737433353339
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050C000300000000000000000000
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:24:7B:7D:A7:8E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"myqwest4893"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010d9c05249
                    Extra: Last beacon: 564ms ago
                    IE: Unknown: 000B6D79717765737434383933
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7A0050F204104A0001101044000102103B0001031047001025B47828692C7534F5F9603C87445CD7102100025449102300064150444B3731102400043731303010420007313233343332311054000800060050F20400011011001A416374696F6E7465632052656769737472617220504B3530303010080002008C
          Cell 06 - Address: 00:26:F2:8D:9D:31
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"ROBERT1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006312b3ad80
                    Extra: Last beacon: 3824ms ago
                    IE: Unknown: 0007524F4245525431
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051900000000000000000000000000000000000000
                    IE: Unknown: 3D1601051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000026F28D9D311021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103
          Cell 07 - Address: 00:24:B2:D7:46:2E
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"clarkg"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000175f91a0e
                    Extra: Last beacon: 3848ms ago
                    IE: Unknown: 0006636C61726B67
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1602051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000024B2D7462E1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103
          Cell 08 - Address: 00:1E:E5:51:29:A8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Homer Net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000aedd1b3183
                    Extra: Last beacon: 536ms ago
                    IE: Unknown: 0009486F6D6572204E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483232353835311054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: Unknown: DD090010180202F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 00:23:69:89:AD:42
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Jeff Wireless Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000eaebc0a9183
                    Extra: Last beacon: 496ms ago
                    IE: Unknown: 00124A65666620576972656C65737320486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 00:05:5D:FA:FA:F6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"annex"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000021d163cc1dd
                    Extra: Last beacon: 560ms ago
                    IE: Unknown: 0005616E6E6578
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 050401030000
          Cell 11 - Address: 00:18:39:4B:01:BE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000052f9e50186
                    Extra: Last beacon: 760ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4
          Cell 12 - Address: 00:18:F8:CA:6A:1A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"bobbi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005800370c187
                    Extra: Last beacon: 648ms ago
                    IE: Unknown: 0005626F626269
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F5000000
          Cell 13 - Address: 20:4E:7F:9B:15:80
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR17"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ede9bcc189
                    Extra: Last beacon: 672ms ago
                    IE: Unknown: 00094E4554474541523137
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1607001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010CAD19D3159FB3E35FD75AB3971C0800C1021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C000103
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: 00:24:7B:0F:45:7A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"myqwest0825"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000088a2962a24b
                    Extra: Last beacon: 2944ms ago
                    IE: Unknown: 000B6D79717765737430383235
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050C000300000000000000000000
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 15 - Address: C0:3F:0E:9F:5A:4A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"gears-Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000156bce2b147
                    Extra: Last beacon: 2928ms ago
                    IE: Unknown: 000E67656172732D576972656C657373
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD800050F204104A00011010440001021041000100103B00010310470010A6CF25F91CB58C902583D9FFE0249DD11021000D4E4554474541522C20496E632E10230008574E52333530304C10240008574E52333530304C10420004333530301054000800060050F204000110110008574E52333530304C100800020084103C000101
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 16 - Address: 00:26:F2:A0:99:9D
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Redding86"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d9ac86928
                    Extra: Last beacon: 3844ms ago
                    IE: Unknown: 000952656464696E673836
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34020D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16020D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000026F2A0999D1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103

```

[COLOR="Red"]cat /etc/resolv.conf[/COLOR]

```
# Generated by NetworkManager
nameserver 192.168.1.1

```

[COLOR="Red"]iwconfig[/COLOR]

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Rohan"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:9C:D4:9D   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:68   Missed beacon:0

```

[COLOR="Red"]ifconfig -a[/COLOR]

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"xxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:9C:D4:9D   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:68   Missed beacon:0

bjrohan@bjrohan-MM061:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:b9:7d:80:ce  
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
          RX packets:5785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:473580 (473.5 KB)  TX bytes:473580 (473.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:46:32:0b  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe46:320b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:498591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:440911874 (440.9 MB)  TX bytes:146284701 (146.2 MB)
```

I hope this helps, and is what you are looking for, it is mostly gibberish to me.

---

### Post by praseodym on 2011-11-09
The connection looks good, but there is a lot of traffic on/around channel 6, try to set the channel to "auto mode" in your router interface. For this connect via cable (because you make changes) and type 192.168.1.1 in your browser.

Another one: Add the nameservers of your ISP (or the google nameservers 8.8.8.8 and 8.8.4.4) in "IPv4-settings" in the network-manager applet.

Right-click->Edit connections->choose yours->Edit->IPv4-setings

Change there to "Automatic (DHCP), addresses only" and add the nameservers in the field "DNS-servers". Restart the network after that.

---

### Post by brohan76 on 2011-11-09
I did as you suggested, my speed test is now 6 MBPS :-) much better than before, thank you.

---

### Post by brohan76 on 2011-11-10
I regret to say that after the internet worked for me so well, after a few hours, it degraded back to where it was.  I stopped the network using $ sudo /etc/init.d/networking stop When I did this, the network stopped, but then something weird happened, all my icons changed, and as well as my taskbar up above. When I clicked the start/stop area, no menu appeared to reboot.  I then simply rebooted my machine, and everything returned to normal, with internet speeds just fine.  Interestingly enough, when my internet was working fine, my audio worked fine. As my internet speed degraded, ALL audio became garbled. If I exited all programs, then inserted a music CD, even the CD was garbled. When internet was working fine, audio was fine (CDs, youtube videos etc.)  

Please help.

---

