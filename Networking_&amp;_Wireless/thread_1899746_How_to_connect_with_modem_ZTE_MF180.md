---
title: "How to connect with modem ZTE MF180"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by ekaituaku on 2011-12-24
Hi i have something problem with my connection. i cant use My modem zte mf180 if i connect with my modem in 2 or 3 minuts my connection lost :P so how to fix my problem please help me

---

### Post by praseodym on 2011-12-24
Hi,

please show

```
lsusb
lsmod
usb-devices
```

---

### Post by ekaituaku on 2011-12-24
ok i am after enter this code. but after i am use code my modem still lost connection after 2/3 minutes.......:(

---

### Post by praseodym on 2011-12-24
Please show the the outputs as "diagnosis" of the problem

---

### Post by ekaituaku on 2011-12-24
its diagnosis my problem

Bus 002 Device 004: ID 064e:f203 Suyin Corp. 
Bus 002 Device 003: ID 2188:0ae1  
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 19d2:0117 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Module                  Size  Used by
snd_hda_codec_hdmi     21630  1 
snd_hda_codec_realtek   248710  1 
joydev                  8649  0 
snd_hda_intel          21661  2 
snd_hda_codec          80498  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                    1141  2 
snd_hwdep               5424  1 snd_hda_codec
ath9k                  76473  0 
snd_pcm_oss            36427  0 
snd_mixer_oss          13581  1 snd_pcm_oss
mac80211              255996  1 ath9k
snd_pcm                68662  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_pcm_oss
ath9k_common            2466  1 ath9k
ath9k_hw              305324  2 ath9k,ath9k_common
snd_seq_dummy           1358  0 
snd_seq_oss            26216  0 
ath                    13577  2 ath9k,ath9k_hw
snd_seq_midi            4460  0 
snd_rawmidi            18745  1 snd_seq_midi
snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi
snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               60284  0 
snd_timer              17803  2 snd_pcm,snd_seq
cfg80211              153414  3 ath9k,mac80211,ath
option                 13973  0 
snd_seq_device          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               75797  1 uvcvideo
hp_wmi                  7748  0 
sparse_keymap           3194  1 hp_wmi
rfkill                 14987  3 cfg80211,hp_wmi
psmouse                52655  0 
usb_wwan               10291  1 option
serio_raw               3744  0 
usbserial              31392  2 option,usb_wwan
snd                    50697  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6048  1 snd
snd_page_alloc          6801  2 snd_hda_intel,snd_pcm
lp                      7373  0 
mac_hid                 3029  0 
intel_ips              10492  0 
wmi                     8772  1 hp_wmi
parport                29468  1 lp
usbhid                 35443  0 
hid                    69090  1 usbhid
i915                  476096  3 
drm_kms_helper         31085  1 i915
ums_realtek             4307  0 
usb_storage            40902  1 ums_realtek
drm                   178158  4 i915,drm_kms_helper
uas                     7524  0 
intel_agp               9614  1 i915
ahci                   18634  2 
i2c_algo_bit            4916  1 i915
intel_gtt              13296  3 i915,intel_agp
r8169                  36663  0 
libahci                19920  1 ahci
mii                     4091  1 r8169
agpgart                27414  3 drm,intel_agp,intel_gtt
video                  10930  1 i915

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.39.4 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0117 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=MF1800BLND010000
C:  #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.39.4 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=2188 ProdID=0ae1 Rev=01.00
S:  Product= USB OPTICAL MOUSE
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=04 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=064e ProdID=f203 Rev=02.11
S:  Manufacturer=SuYin
S:  Product=HP Webcam-101
S:  SerialNumber=HF0317-J311-SE01-VH-R02.01.01
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=150mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

---

### Post by praseodym on 2011-12-25
Have a look at here:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by ekaituaku on 2011-12-25
so what should I do? everything on the thread I have tried the same thing but no result what my modem is still keep it that way](*,)

---

### Post by praseodym on 2011-12-25
What computer is that?

---

