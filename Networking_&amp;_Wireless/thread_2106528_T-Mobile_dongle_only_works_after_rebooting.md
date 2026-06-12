---
title: "T-Mobile dongle only works after rebooting"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by dreamkatcha on 2013-01-19
Hi,

When I first turn my computer on, the light on my dongle remains red indicating that it has no signal. If I reboot, the light turns blue allowing me to connect to the internet. Unplugging and re-inserting it doesn't do the trick, it has to be a reboot every time.

Any idea what that's about or how to fix it?

---

### Post by praseodym on 2013-01-19
What kind of dongle is it? Please show the terminal outputs of:
```

lsusb
lsmod
usb-devices
```

---

### Post by dreamkatcha on 2013-01-19
It's one of [these]("http://support.t-mobile.co.uk/help-and-support/index?page=support&cat=USB_STICK_615"). Hey, why can't I have a pink one? ;)

I'm using a USB hub but the dongle is connected directly to my laptop.

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 007: ID 19d2:1515 ZTE WCDMA Technologies MSM 
Bus 003 Device 003: ID 050d:0304 Belkin Components FSU304 USB 2.0 - 4 Ports Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 2232:1029  
Bus 003 Device 004: ID 03f0:8207 Hewlett-Packard FHA-3510 2.4GHz Wireless Optical Mobile Mouse
Bus 003 Device 005: ID 3292:8001  
Bus 003 Device 006: ID 0fd9:0021 Elgato Systems GmbH EyeTV DTT

Module                  Size  Used by
ppp_deflate            12950  0 
zlib_deflate           26914  1 ppp_deflate
bsd_comp               12921  0 
ppp_async              17413  1 
crc_ccitt              12667  1 ppp_async
cdc_acm                26935  5 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
rfcomm                 46619  0 
bnep                   18140  2 
parport_pc             32688  0 
ppdev                  17073  0 
binfmt_misc            17500  1 
rc_dib0700_rc5         12508  0 
nls_iso8859_1          12713  1 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
ghash_clmulni_intel    13180  0 
cryptd                 20403  1 ghash_clmulni_intel
joydev                 17457  0 
hid_generic            12493  0 
samsung_laptop         14532  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
microcode              22803  0 
arc4                   12529  2 
lpc_ich                17061  0 
snd_seq_midi           13324  0 
ath9k                 131308  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
snd_rawmidi            30512  1 snd_seq_midi
mac80211              539908  1 ath9k
rts5139               356158  0 
ath9k_common           14055  1 ath9k
psmouse                95552  0 
serio_raw              13215  0 
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
ath9k_hw              395218  2 ath9k,ath9k_common
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
videobuf2_memops       13368  1 videobuf2_vmalloc
cfg80211              206566  3 ath9k,mac80211,ath
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
ath3k                  12918  0 
btusb                  18334  0 
bluetooth             209199  12 rfcomm,bnep,ath3k,btusb
dvb_usb_dib0700       148701  5 
dib0090                38608  1 dvb_usb_dib0700
dib7000p               38381  2 dvb_usb_dib0700
dib7000m               22984  1 dvb_usb_dib0700
dib0070                18232  2 dvb_usb_dib0700
dvb_usb                24222  1 dvb_usb_dib0700
dib8000                52678  1 dvb_usb_dib0700
dvb_core              110323  3 dib7000p,dvb_usb,dib8000
dib3000mc              23239  1 dvb_usb_dib0700
snd_timer              29425  2 snd_pcm,snd_seq
rc_core                22330  4 rc_dib0700_rc5,dvb_usb_dib0700,dvb_usb
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
dibx000_common         18706  5 dvb_usb_dib0700,dib7000p,dib7000m,dib8000,dib3000mc
snd                    78734  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    40690  0 
usbhid                 46947  0 
soundcore              15047  1 snd
hid                   100366  2 hid_generic,usbhid
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i915                  520519  2 
mac_hid                13205  0 
wmi                    19070  0 
drm_kms_helper         46784  1 i915
drm                   275528  3 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
video                  19335  2 samsung_laptop,i915
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
uas                    17844  0 
usb_storage            48838  0 
r8169                  61650  0 

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-17-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=0129 Rev=39.60
S:  Manufacturer=Generic
S:  Product=USB2.0-CRW
S:  SerialNumber=20100201396000000
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=06 Prot=50 Driver=rts5139

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=2232 ProdID=1029 Rev=00.25
S:  Manufacturer=Generic
S:  Product=WebCam SC-13HDL11939N
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-17-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-17-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1515 Rev=00.01
S:  Manufacturer=ZTE
S:  Product=MF192
S:  SerialNumber=74B351CA55714F082A7F7A1654867280B028ECA6
C:  #Ifs= 7 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 6 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  3 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=050d ProdID=0304 Rev=07.02
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=02 Prnt=03 Port=00 Cnt=01 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=8207 Rev=00.01
S:  Manufacturer=HP
S:  Product=Wireless Optical Mobile Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=03 Lev=02 Prnt=03 Port=02 Cnt=02 Dev#=  5 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=3292 ProdID=8001 Rev=01.02
S:  Manufacturer=FOG (c) 2012
S:  Product=Retro Joystick interface v1.2 
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=160mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=03 Lev=02 Prnt=03 Port=03 Cnt=03 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0fd9 ProdID=0021 Rev=01.00
S:  Manufacturer=Elgato
S:  Product=EyeTV DTT
S:  SerialNumber=005
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=dvb_usb_dib0700

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.05
S:  Manufacturer=Linux 3.5.0-17-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by praseodym on 2013-01-19
Did you install usb-modeswitch?

Please check also here:

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=876](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=876)

---

### Post by dreamkatcha on 2013-01-21
No, not manually. I wouldn't know if it's already included in 12.10 either. What I noticed though is that my dongle works first time whenever my iPod Shuffle isn't connected to my laptop when it boots up. Probably just another example of USB flakiness, as you get on any platform.

---

