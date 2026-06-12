---
title: "installing the rtl 8188cu card?"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by Akita1990 on 2013-03-05
i have a wireless card here ive been trying to get working for days now. ive tried numerous things, downloading drivers, downloading everything i can but i just does not work.

the wifi will stay connected for a few minutes at best the i get no connection. so i have to unplug my wifi card and reinsert it.

ios this device supported on 12.04? what do i have to do to keep it connected?

---

### Post by praseodym on 2013-03-05
Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Akita1990 on 2013-03-05
> **praseodym said:**
> Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```


02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2a24]
    Kernel driver in use: 8139too


Bus 001 Device 009: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 001 Device 008: ID eb1a:2861 eMPIA Technology, Inc. 
Bus 002 Device 002: ID 04d9:2517 Holtek Semiconductor, Inc. 
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



Module                  Size  Used by
snd_seq_dummy          12687  0 
snd_usb_audio         106622  1 
snd_hwdep              13277  1 snd_usb_audio
snd_usbmidi_lib        24590  1 snd_usb_audio
arc4                   12474  2 
snd_atiixp             19342  2 
snd_ac97_codec        106118  1 snd_atiixp
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                81124  3 snd_usb_audio,snd_atiixp,snd_ac97_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  2 snd_usbmidi_lib,snd_seq_midi
saa7115                22551  1 
snd_seq_midi_event     14476  1 snd_seq_midi
rtl8192cu              67489  0 
rtl8192c_common        47696  1 rtl8192cu
snd_seq                51594  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
rtlwifi                65273  1 rtl8192cu
snd_timer              28932  2 snd_pcm,snd_seq
mac80211              475546  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_seq_device         14138  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
em28xx                 85852  0 
v4l2_common            15794  2 saa7115,em28xx
snd                    62675  16 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 38104  0 
cfg80211              181041  2 rtlwifi,mac80211
bnep                   17791  2 
videodev              100265  3 saa7115,em28xx,v4l2_common
videobuf_vmalloc       13337  1 em28xx
videobuf_core          25410  2 em28xx,videobuf_vmalloc
soundcore              14636  1 snd
serio_raw              13032  0 
tveeprom               17010  1 em28xx
k8temp                 12913  0 
ppdev                  12850  0 
bluetooth             189585  10 rfcomm,bnep
snd_page_alloc         14109  2 snd_atiixp,snd_pcm
binfmt_misc            17293  1 
i2c_piix4              13094  0 
radeon                832167  3 
joydev                 17394  0 
ttm                    76326  1 radeon
drm_kms_helper         47459  1 radeon
drm                   240232  5 radeon,ttm,drm_kms_helper
parport_pc             32115  1 
i2c_algo_bit           13317  1 radeon
mac_hid                13078  0 
shpchp                 32326  0 
ati_agp                13243  0 
lp                     17456  0 
parport                40931  3 ppdev,parport_pc,lp
usb_storage            39720  0 
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
firewire_ohci          36110  0 
firewire_core          61957  1 firewire_ohci
8139too                23312  0 
crc_itu_t              12628  1 firewire_core
8139cp                 26760  0 
pata_atiixp            13000  0 
sata_sil               13276  2 

wlan0     IEEE 802.11bgn  ESSID:"SKYD6501"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 7C:4C:A5:46:22:E9   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.





in the order you asked

---

### Post by praseodym on 2013-03-06
You can update th driver according to this:

[http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#Version-3-4-2-3727](http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#Version-3-4-2-3727)

Version 3.4.2-3727

---

### Post by Akita1990 on 2013-03-06
is there a simplar tutorial?

---

### Post by praseodym on 2013-03-06
Just copy/paste the lines one after another into the terminal using a cable connection.

---

