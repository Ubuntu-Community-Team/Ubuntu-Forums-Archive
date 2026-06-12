---
title: "USB modem stopped working"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by enceladus47 on 2012-04-11
I have a ZTE USB modem that was working normally until yesterday when it  stopped appearing it in networks, and I can't even see its internal storage...

Still works normally on other systems.

---

### Post by praseodym on 2012-04-11
Hi,

please show:
```

lsusb
lsmod
usb-devices
ifconfig -a
```

---

### Post by enceladus47 on 2012-04-15
Thanks for the answer, and sorry for being late

```
omar@omar-V:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 064e:a213 Suyin Corp. 
Bus 001 Device 005: ID 0489:e00f Foxconn / Hon Hai Foxconn T77H114 BCM2070 [Single-Chip Bluetooth 2.1 + EDR Adapter]
Bus 002 Device 006: ID 19d2:0117 ZTE WCDMA Technologies MSM 
omar@omar-V:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40257  1 
option                 25849  0 
usb_wwan               20491  1 option
usbserial              47077  2 option,usb_wwan
uas                    18027  0 
usb_storage            49198  1 
snd_hrtimer            12744  1 
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12529  2 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17693  0 
iwlwifi               328352  0 
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
btusb                  18288  2 
mac80211              506816  1 iwlwifi
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
bluetooth             180104  23 bnep,rfcomm,btusb
i915                  468651  8 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87603  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205544  2 iwlwifi,mac80211
mac_hid                13253  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
intel_ips              18089  0 
video                  19596  1 i915
mei                    41616  0 
serio_raw              13211  0 
sony_laptop            45393  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sky2                   59043  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
omar@omar-V:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=064e ProdID=a213 Rev=05.51
S:  Manufacturer=SuYin 
S:  Product=USB 2.0 Camera
S:  SerialNumber=CN0319-S33B-OV022-VS-R05.05.01
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=02 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e00f Rev=05.96
S:  Manufacturer=Broadcom Corp
S:  Product=Broadcom Bluetooth Device
S:  SerialNumber=C0CB38FB18C4
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0117 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=MF1900ZTED010000
C:  #Ifs= 4 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


```

---

