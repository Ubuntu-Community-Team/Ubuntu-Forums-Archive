---
title: "WiFi [Asus USB-N53] not working after a failed suspend"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by benkomalo on 2012-01-13
I tried to put my desktop into suspend earlier and it seemed to hang doing so. I had to power cycle the machine and when it came back up, it doesn't seem to be able to connect to wifi. Tried to search for solutions, but to no avail, but please point me to a thread if this has been answered before (and I apologize if so).

Any help would be really appreciated.

Info
- this USB wifi adapter was working before on this machine, prior to the failed suspend and I made no system config changes since
- this is a dual boot machine, and the same device works in Win7

```
$ uname -a
Linux boxname 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr f4:6d:04:5d:a2:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

dmesg output after I tried to unplug and re-plug the device:

```

[  646.471693] usb 1-4: USB disconnect, device number 2
[  649.888420] usb 1-4: new high speed USB device number 7 using ehci_hcd
[  650.055327] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  650.055332] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055335] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  650.055338] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055341] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  650.055344] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055347] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  650.055350] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055353] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  650.055356] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055358] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  650.055362] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055364] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  650.055367] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055370] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  650.055373] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055376] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  650.055379] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055381] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  650.055385] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055387] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  650.055390] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055393] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  650.055396] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055399] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  650.055402] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055405] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  650.055408] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055410] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  650.055414] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055416] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[  650.055420] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055422] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  650.055425] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055428] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  650.055431] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055434] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[  650.055437] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055439] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  650.055443] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055445] cfg80211: Disabling freq 5260 MHz
[  650.055447] cfg80211: Disabling freq 5270 MHz
[  650.055449] cfg80211: Disabling freq 5280 MHz
[  650.055453] cfg80211: Disabling freq 5300 MHz
[  650.055454] cfg80211: Disabling freq 5310 MHz
[  650.055455] cfg80211: Disabling freq 5320 MHz
[  650.055456] cfg80211: Disabling freq 5500 MHz
[  650.055457] cfg80211: Disabling freq 5510 MHz
[  650.055459] cfg80211: Disabling freq 5520 MHz
[  650.055460] cfg80211: Disabling freq 5540 MHz
[  650.055461] cfg80211: Disabling freq 5550 MHz
[  650.055462] cfg80211: Disabling freq 5560 MHz
[  650.055463] cfg80211: Disabling freq 5580 MHz
[  650.055465] cfg80211: Disabling freq 5590 MHz
[  650.055466] cfg80211: Disabling freq 5600 MHz
[  650.055467] cfg80211: Disabling freq 5620 MHz
[  650.055468] cfg80211: Disabling freq 5630 MHz
[  650.055469] cfg80211: Disabling freq 5640 MHz
[  650.055470] cfg80211: Disabling freq 5660 MHz
[  650.055472] cfg80211: Disabling freq 5670 MHz
[  650.055473] cfg80211: Disabling freq 5680 MHz
[  650.055474] cfg80211: Disabling freq 5700 MHz
[  650.055475] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  650.055478] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055479] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[  650.055481] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055483] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  650.055485] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055487] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  650.055489] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055491] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[  650.055493] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055495] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  650.055497] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055499] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  650.055501] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 2000 mBm)
[  650.055502] cfg80211: Disabling freq 5835 MHz
[  650.055503] cfg80211: Disabling freq 5845 MHz
[  650.055505] cfg80211: Disabling freq 5855 MHz
[  650.055506] cfg80211: Disabling freq 5865 MHz
[  650.055586] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[  650.056202] Registered led device: rt2800usb-phy1::radio
[  650.056218] Registered led device: rt2800usb-phy1::assoc
[  650.056234] Registered led device: rt2800usb-phy1::quality
[  650.513501] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

```

$ lsmod
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
snd_hda_codec_analog    93522  1 
arc4                   12529  2 
binfmt_misc            17540  1 
rt2800usb              22590  0 
rt2800lib              54538  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20830  1 rt2800usb
rt2x00lib              50325  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              462092  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
dell_wmi               12681  0 
ppdev                  17113  0 
sparse_keymap          13890  1 dell_wmi
psmouse                73882  0 
dcdbas                 14490  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
nouveau               728662  3 
serio_raw              13166  0 
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
drm                   236290  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
i7core_edac            27942  0 
snd_timer              29991  2 snd_pcm,snd_seq
wmi                    19256  2 dell_wmi,mxm_wmi
parport_pc             36962  1 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              53746  3 i7core_edac
video                  19412  1 nouveau
snd                    68266  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
tg3                   147729  0 
ahci                   26002  2 
libahci                26861  1 ahci

```

---

