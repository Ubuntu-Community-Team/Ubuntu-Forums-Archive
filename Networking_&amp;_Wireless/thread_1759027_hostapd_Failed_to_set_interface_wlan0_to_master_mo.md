---
title: "hostapd: Failed to set interface wlan0 to master mode"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by upskuhr on 2011-05-15
Hello,

I try to set-up an Access point using ubuntu 11.04. I am using the minimal configuration file from [http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd) together with a TP-Link TL-WN422G (Atheros chipset). I've installed the linux-backports-net-natty-generic drivers. But when trying to start hostapd I always get this output:
```

# hostapd -dd -K  test.conf 
Configuration file: test.conf
Failed to set interface wlan0 to master mode.
nl80211 driver initialization failed.
wlan0: Unable to setup interface.
ELOOP: remaining socket: sock=5 eloop_data=0x9b9440 user_data=(nil) handler=0x43d980

```I have also disabled the network-manager for this device by adding this to /etc/network/interfaces:
```

iface wlan0 inet manual

```cat test.conf:
```

interface=wlan0
driver=nl80211
ssid=test
channel=1

```lsusb says:
```

...
Bus 001 Device 005: ID 0cf3:1006 Atheros Communications, Inc. TP-Link TL-WN422G v2 802.11g [Atheros AR9271]
...

```lsmo:
```

Module                  Size  Used by
binfmt_misc            17565  1 
snd_hda_codec_via      62470  1 
arc4                   12529  2 
nvidia              10709116  56 
ath9k_htc              61400  0 
snd_hda_intel          33211  4 
edac_core              53845  0 
snd_hda_codec         103804  2 snd_hda_codec_via,snd_hda_intel
mac80211              294370  1 ath9k_htc
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_intel,snd_hda_codec
ath9k_common           13851  1 ath9k_htc
ath9k_hw              323077  2 ath9k_htc,ath9k_common
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
psmouse                73535  0 
ath                    23773  2 ath9k_htc,ath9k_hw
lp                     17825  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  3 ath9k_htc,mac80211,ath
r8712u                307592  0 
ppdev                  17113  0 
serio_raw              13166  0 
edac_mce_amd           23464  0 
snd                    67382  16 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2            13058  0 
k10temp                13119  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport_pc             36959  1 
parport                46458  3 lp,ppdev,parport_pc
hid_logitech           17693  0 
ff_memless             13097  1 hid_logitech
usbhid                 46956  1 hid_logitech
hid                    91020  2 hid_logitech,usbhid
raid10                 30673  0 
raid456                62777  0 
async_pq               12995  1 raid456
async_xor              12879  2 raid456,async_pq
xor                    12890  1 async_xor
async_memcpy           12529  1 raid456
async_raid6_recov      12776  1 raid456
forcedeth              63555  0 
pata_amd               14130  0 
sata_nv                32054  6 
raid6_pq               88307  2 async_pq,async_raid6_recov
async_tx               13349  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  30596  2 
multipath              13187  0 
linear                 12966  0 
raid0                  17271  0 

```uname -a
```

Linux magnet 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by madbob on 2011-06-15
Hello, upskuhr!

See my configs:

# hardware
# 0cf3:9271 TP-WN722NC + Lucid / 10.04 + current compat-wireless
# firmware [http://wireless.kernel.org/download/htc_fw/1.3/htc_9271.fw](http://wireless.kernel.org/download/htc_fw/1.3/htc_9271.fw)

realpath /sys/class/net/wlan0/device/driver 
/sys/bus/usb/drivers/ath9k_htc

root@primus# dmesg |grep ath9k_htc
[   19.153503] usb 1-6.4.2: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   19.388584] ath9k_htc 1-6.4.2:1.0: ath9k_htc: HTC initialized with 33 credits
[   19.580311] ath9k_htc 1-6.4.2:1.0: ath9k_htc: FW Version: 1.3
[   19.581854] Registered led device: ath9k_htc-phy1
[   19.581857] usb 1-6.4.2: ath9k_htc: USB layer initialized
[   19.581875] usbcore: registered new interface driver ath9k_htc

## start easy_open_802.1G.hostapd.conf 
interface=wlan0
driver=nl80211

hw_mode=g
channel=11

country_code=NO

ssid=void

auth_algs=1
wpa=0
ignore_broadcast_ssid=0

## end easy_open_802.1G.hostapd.conf 

root@primus# ./hostapd.git_HT40  easy_open_802.1G.hostapd.conf 
Configuration file: easy_open_802.1G.hostapd.conf
Using interface wlan0 with hwaddr 74:ea:3a:90:d6:b6 and ssid 'void'
wlan0: STA 00:16:eb:2b:92:88 IEEE 802.11: authenticated
wlan0: STA 00:16:eb:2b:92:88 IEEE 802.11: associated (aid 1)
wlan0: AP-STA-CONNECTED 00:16:eb:2b:92:88
wlan0: AP-STA-DISCONNECTED 00:16:eb:2b:92:88

---

