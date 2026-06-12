---
title: "Problems with Huawei E1750 - discovery issues on system load"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by tommo1982 on 2011-10-18
I am having problems with the E1750 modem discovery when I turn the computer on, with it plugged in, and let the system load. It seems it is discovered but Network Manager acts like it doesn't see it. Meaning, my default mobile internet connection won't show up on the list and I can't connect. If my memory serves me well, when I had 11.04 soon after it came out I had no problems, but after one of the updates it started to behave like that. Now I have 11.10 and the problem persists. When I unplug and plug it in everything is fine, but I don't want to do it everytime I load the system.

I'm new to ubuntu and linux generally and I don't know enough to solve it myself. I'd be grateful if anyone could help find a solution.

PS.
I searched through the forum, but nothing is really similar to what I experienced.

---

### Post by praseodym on 2011-10-18
Hi,

please show the terminal outputs of:

```
lsusb
lsmod
usb-devices
```
in non-connected _and_ connected state

---

### Post by tommo1982 on 2011-10-19
Here's connected state:

```

**lsusb connected**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 090c:37b3 Feiya Technology Corp. 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 006: ID 1020:030a Labtec 
Bus 002 Device 009: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 010: ID 4971:ce21 SimpleTech 

**lsmod connected**
Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
option                 21205  2 
usb_wwan               19779  1 option
usbserial              37203  7 option,usb_wwan
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  4 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
snd_seq_midi           13132  0 
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10390874  43 
snd_timer              28932  2 snd_pcm,snd_seq
psmouse                73673  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              272785  1 brcmsmac
video                  18908  0 
wmi                    18744  0 
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  2 ppp_async,brcmsmac
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ums_realtek            13096  0 
usb_storage            44173  5 ums_realtek
uas                    17699  0 
r8169                  43104  0 
ahci                   21634  3 
libahci                25727  1 ahci

**usb-devices connected**
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=4971 ProdID=ce21 Rev=00.00
S:  Manufacturer=Hitachi GST
S:  Product=SimpleDrive mini
S:  SerialNumber=25120101020301BF
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  9 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=03 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=090c ProdID=37b3 Rev=08.16
S:  Manufacturer=Image Processor
S:  Product=Lenovo EasyCamera
S:  SerialNumber=Integrated Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=04 Dev#=  4 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0608 Rev=77.61
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=03 Prnt=04 Port=03 Cnt=01 Dev#=  6 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1020 ProdID=030a Rev=01.04
S:  Manufacturer=PATEN
S:  Product=USB HID Device        
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
```


Not-connected state:

```
[B]
lsusb not connected[/B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 090c:37b3 Feiya Technology Corp. 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 006: ID 1020:030a Labtec 
Bus 002 Device 010: ID 4971:ce21 SimpleTech 

**lsmod not connected**
Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  0 
option                 21205  0 
usb_wwan               19779  1 option
usbserial              37203  2 option,usb_wwan
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  4 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
snd_seq_midi           13132  0 
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10390874  43 
snd_timer              28932  2 snd_pcm,snd_seq
psmouse                73673  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              272785  1 brcmsmac
video                  18908  0 
wmi                    18744  0 
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  2 ppp_async,brcmsmac
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ums_realtek            13096  0 
usb_storage            44173  5 ums_realtek
uas                    17699  0 
r8169                  43104  0 
ahci                   21634  3 
libahci                25727  1 ahci

**usb-devices not connected**
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=4971 ProdID=ce21 Rev=00.00
S:  Manufacturer=Hitachi GST
S:  Product=SimpleDrive mini
S:  SerialNumber=25120101020301BF
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=090c ProdID=37b3 Rev=08.16
S:  Manufacturer=Image Processor
S:  Product=Lenovo EasyCamera
S:  SerialNumber=Integrated Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#=  4 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0608 Rev=77.61
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=03 Prnt=04 Port=03 Cnt=01 Dev#=  6 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1020 ProdID=030a Rev=01.04
S:  Manufacturer=PATEN
S:  Product=USB HID Device        
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
```

---

### Post by praseodym on 2011-10-19
Did you install **usb-modeswitch**?

---

### Post by tommo1982 on 2011-10-20
Yes, it's installed.

By the way. Last time I didn't use those commands after boot. Here is what you requested right after the system started. Also I forgot about one thing. The modem won't start flashing blue sometimes. After I plug it in the diode is flashing green twice every few seconds then it settles on single blue flash now and then. Today I had to plug it into a different USB slot to make it work.

Connected after boot:
```

**lsusb connected after boot**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 090c:37b3 Feiya Technology Corp. 
Bus 002 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552 (HSPA modem)

**lsmod connected after boot**
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
snd_hda_codec_hdmi     31426  4 
nvidia              10390874  43 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
wl                   2646601  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211               14570  1 wl
bcma                   19571  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              591864  0 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
psmouse                73673  0 
serio_raw              12990  0 
brcmutil               16885  1 brcmsmac
mei                    36466  0 
soundcore              12600  1 snd
mac80211              272785  1 brcmsmac
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  1 brcmsmac
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  0 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
r8169                  43104  0 
ahci                   21634  3 
libahci                25727  1 ahci

**usb-devices after boot**
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1446 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=090c ProdID=37b3 Rev=08.16
S:  Manufacturer=Image Processor
S:  Product=Lenovo EasyCamera
S:  SerialNumber=Integrated Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

```

I noticed it's not recognised properly and I think it's not recognised as a modem but a pen drive? Someone mentioned this is a common issue.

---

### Post by praseodym on 2011-10-20
Setup an udev-rule:

```
gksudo gedit /lib/udev/rules.d/61-option-modem-modeswitch.rules
```
Insert:

```
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"
```
save, close, and:

```
sudo service udev reload
```

---

### Post by tommo1982 on 2011-10-21
Done. I'll see next time I turn on my laptop if it worked. By the way, could you explain what I just did? I'd like to know what caused the problem.

Uhm, is idProduct=1446 correct? 'lsusb' shows it this way when everything is working:
*ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem*

---

### Post by praseodym on 2011-10-21
1446 is for the storage device. The udev-rule throws out the storage device automatically, after that it should show 1001 and it should work.

---

### Post by tommo1982 on 2011-10-22
Yes, everything is working now. I turned on the laptop, the system loaded, with modem being properly recognised and I just had to enable modem connection and it connected :). Thank you for your help!

---

### Post by tommo1982 on 2011-10-23
I was too fast. It turned out it wasn't working as it should be. It was because the command modem-modeswitch doesn't exist in 11.10. Instead it's name is 'usb_modeswitch'.

---

### Post by tommo1982 on 2011-11-03
It won't work. Bloody devs changed name of the program and its options. I can't make it work and if that wasn't bad enough, there are other problems with the modem. It's detected, but that bloody nerwork manager just won't see it.

lsusb, usb-devices, I even ran udevadm info to see if it's there (yeah, I don't really know what I am doing, just trying to get some info) ... and the modem is there. It's just like ... the system knows it's there ... but it's not ... or whatever.

The problem is I have to plug it to other USB port to make that bloody modem work. That's not bad, today even that didn't work. Re-logging didn't work, reboot did. I noticed something saying [failed] and 'modem' during startup (and that bloody canonical wants to do no-text system boot?!). I don't know what it was, cuz it vanished before I could read it properly.

The thing is ... can anyone help me? It's soo bloody aggreviating that I want to switch back to Win7 and I don't want to be doing that.

The modem is Huaweii E1750c running on Lenovo G560 laptop, Intel P6200, GeForce 310M.

---

### Post by pdc on 2011-11-03
if you copy and paste 

> dmesg | grep tty

.......the vertical line is a pipe command: SHIFT-\ if you can't copy and paste.......

looking for ttyUSB0 .......

.....if you see that, your device is recognised as a modem;

help me understand; is usb_modeswitch already installed on your computer?

---

### Post by tommo1982 on 2011-11-05
```

[    0.000000] console [tty0] enabled
[   26.536698] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[   26.536812] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[   26.536924] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB2

```

That's what I got when the modem was working properly. I'll try it again when it won't.

Yes, I have usb_modeswitch installed. I just don't know how to use it.

---

### Post by pdc on 2011-11-05
> GSM modem (1-port) converter now attached to ttyUSB0

so when you see that, the device should be recognised as a modem

> *Yes, I have usb_modeswitch installed. I just don't know how to use it*. 

If you have it installed; and the ID of your device is in its data file, it should work in the background without you needing to do anything

---

### Post by tommo1982 on 2011-11-05
You're right. I read through logs and it works just fine. However I found something else as well. Here are parts of my syslog file:

```

**During boot:**
Nov  5 21:27:33 Lenovo-G560 kernel: [    5.688877] usb 2-1.2: new high speed USB device number 7 using ehci_hcd
Nov  5 21:27:33 Lenovo-G560 kernel: [    5.785431] scsi6 : usb-storage 2-1.2:1.0
Nov  5 21:27:33 Lenovo-G560 kernel: [    5.785812] scsi7 : usb-storage 2-1.2:1.1
Nov  5 21:27:33 Lenovo-G560 kernel: [    6.785974] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Nov  5 21:27:33 Lenovo-G560 kernel: [    6.786581] scsi 7:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Nov  5 21:27:33 Lenovo-G560 kernel: [    6.895653] sr1: scsi-1 drive
Nov  5 21:27:33 Lenovo-G560 kernel: [    6.895829] sr 6:0:0:0: Attached scsi CD-ROM sr1
Nov  5 21:27:33 Lenovo-G560 kernel: [    6.895911] sr 6:0:0:0: Attached scsi generic sg2 type 5
Nov  5 21:27:33 Lenovo-G560 kernel: [    6.900445] sd 7:0:0:0: Attached scsi generic sg3 type 0
Nov  5 21:27:33 Lenovo-G560 kernel: [    6.902903] sd 7:0:0:0: [sdb] Attached SCSI removable disk

Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Sierra
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> NetworkManager (version 0.9.1.90) is starting...
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Option High-Speed
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Samsung
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin ZTE
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Nokia
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Novatel
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Ericsson MBM
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Wavecom
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin AnyData
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Option
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Linktop
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin SimTech
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Huawei
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Generic
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Longcheer
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin Gobi
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin X22X
Nov  5 21:27:33 Lenovo-G560 modem-manager[1006]: <info>  Loaded plugin MotoC

Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: init!
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: update_system_hostname
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPluginIfupdown: management mode: unmanaged
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0)
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:07:00.0/net/eth0, iface: eth0)
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:07:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: end _init.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    Ifupdown: get unmanaged devices count: 0
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: (150916376) ... get_connections.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    SCPlugin-Ifupdown: (150916376) ... get_connections (managed=false): return empty list.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    keyfile: parsing Play Online ... 
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    keyfile:     read connection 'Play Online'
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    keyfile: parsing Wired connection 1 ... 
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    keyfile:     read connection 'Wired connection 1'
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]:    Ifupdown: get unmanaged devices count: 0
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> modem-manager is now available
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/PNP0C09:00/VPC2004:00/rfkill/rfkill0) (driver ideapad_acpi)
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/ieee80211/phy0/rfkill2) (driver (unknown))
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> WiFi disabled by radio killswitch; disabled by state file
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> Networking is enabled by state file
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (wlan0): new 802.11 WiFi device (driver: 'brcmsmac' ifindex: 3)
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (wlan0): now managed
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (wlan0): bringing up device.
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (eth0): carrier is OFF
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (eth0): now managed
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov  5 21:27:33 Lenovo-G560 NetworkManager[1014]: <info> (eth0): bringing up device.

**This is after system started and 'again' I had to remove and plug-in the modem:**
Nov  5 21:29:07 Lenovo-G560 kernel: [  116.614748] usb 2-1.2: USB disconnect, device number 7
Nov  5 21:29:22 Lenovo-G560 kernel: [  131.587703] usb 2-1.2: new high speed USB device number 8 using ehci_hcd
Nov  5 21:29:22 Lenovo-G560 mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Nov  5 21:29:22 Lenovo-G560 kernel: [  131.684334] scsi8 : usb-storage 2-1.2:1.0
Nov  5 21:29:22 Lenovo-G560 kernel: [  131.684689] scsi9 : usb-storage 2-1.2:1.1
Nov  5 21:29:22 Lenovo-G560 mtp-probe: bus: 2, device: 8 was not an MTP device
Nov  5 21:29:23 Lenovo-G560 usb_modeswitch: switching 12d1:1446 (HUAWEI Technology: HUAWEI Mobile)
Nov  5 21:29:23 Lenovo-G560 kernel: [  132.413233] usb 2-1.2: USB disconnect, device number 8
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.449662] usb 2-1.2: new high speed USB device number 9 using ehci_hcd
Nov  5 21:29:27 Lenovo-G560 mtp-probe: checking bus 2, device 9: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.547682] scsi13 : usb-storage 2-1.2:1.3
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.548420] scsi14 : usb-storage 2-1.2:1.4
Nov  5 21:29:27 Lenovo-G560 mtp-probe: bus: 2, device: 9 was not an MTP device
Nov  5 21:29:27 Lenovo-G560 usb_modeswitch: switched to 12d1:1001 (HUAWEI Technology: HUAWEI Mobile)
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.580988] usbcore: registered new interface driver usbserial
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.581006] USB Serial support registered for generic
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.582084] usbcore: registered new interface driver usbserial_generic
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.582087] usbserial: USB Serial Driver core
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.585368] USB Serial support registered for GSM modem (1-port)
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.586214] option 2-1.2:1.0: GSM modem (1-port) converter detected
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.586388] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.586401] option 2-1.2:1.1: GSM modem (1-port) converter detected
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.586503] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.586515] option 2-1.2:1.2: GSM modem (1-port) converter detected
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.586613] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB2
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.587953] usbcore: registered new interface driver option
Nov  5 21:29:27 Lenovo-G560 kernel: [  136.587956] option: v0.7.2:USB Driver for GSM modems
Nov  5 21:29:27 Lenovo-G560 modem-manager[1006]: <info>  (ttyUSB0) opening serial port...
Nov  5 21:29:27 Lenovo-G560 usb_modeswitch[1999]: usb_modeswitch: adding device ID 12d1:1001 to driver option
Nov  5 21:29:28 Lenovo-G560 kernel: [  137.546452] scsi 13:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Nov  5 21:29:28 Lenovo-G560 kernel: [  137.546941] scsi 14:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
Nov  5 21:29:28 Lenovo-G560 kernel: [  137.671379] sr1: scsi-1 drive
Nov  5 21:29:28 Lenovo-G560 kernel: [  137.671504] sr 13:0:0:0: Attached scsi CD-ROM sr1
Nov  5 21:29:28 Lenovo-G560 kernel: [  137.671576] sr 13:0:0:0: Attached scsi generic sg2 type 5
Nov  5 21:29:28 Lenovo-G560 kernel: [  137.671783] sd 14:0:0:0: Attached scsi generic sg3 type 0
Nov  5 21:29:28 Lenovo-G560 kernel: [  137.674477] sd 14:0:0:0: [sdb] Attached SCSI removable disk

```

These are only parts I thought might be relevant. If you want I can post a whole file here.
Sorry to be a pain btw. I'm just not giving up until it's working the way it is supposed to.

---

### Post by pdc on 2011-11-05
..........so I am sensing that your experience is that if you turn the computer on first; and then plug in the Huawei, it is recognised as a modem; as usb_modeswitch does the switching.

......whereas if you start the computer with the Huawei plugged in, it is not recognised....

..am I inferring correctly.......?

---

### Post by tommo1982 on 2011-11-06
Yes, you are right. However the thing is, it's not a rule. Sometimes I turn the laptop with the modem plugged in and everything is okay. The other time it is not. I am suspecting the modem itself might be malfunctioning, but I want to be sure before I buy a new one. I hope I am communicating my thoughts clearly, if not ... just say and I'll try to do better :)

Btw, are there modems on sale which don't include drivers provided on built-in flash memory?

---

### Post by pdc on 2011-11-06
> Yes, you are right

..glad I inferred correctly....

> I hope I am communicating my thoughts clearly

.you are very clear........

> Btw, are there modems on sale which don't include drivers provided on built-in flash memory


there are a couple of ideas contained in this phrase..

...one I think is........what about a new modem? ..well you could just try one in a telephone shop.......because they might let you put your simcard in one of their other modems and try it out..but you would need to reboo your laptop repeatedly to be happy....!!

the other idea is "which don't include drivers provided on built-in flash memory"

...not sure what your imagery is there...

on linux......you don't need modem-specific drivers..

....all these device have dual-identity; first seen as virtual CD-ROM storage devices (loaded with windows drivers)....

...and when their ID is flipped......they are "unmasked" as modems........

I think you may just have to live with the vagarities of its behaviour on 11.10 ... on balance..I am still running our MF636 stick (a ZTE one) on a 2.6.32 kernel........as it works......and that is good enough for me !!

(we just use the MF636 on weekend trips away)

---

### Post by tommo1982 on 2011-11-10
I returned to 2.6.38 kernel and the modem is working better. Sometimes it won't switch properly when I turn on the laptop, but it's better than before still. I guess the newest kernel is not the best ... yet, so I'll stick with the old one and I think I'll look for older usb-modem switch package, see what happens.

---

