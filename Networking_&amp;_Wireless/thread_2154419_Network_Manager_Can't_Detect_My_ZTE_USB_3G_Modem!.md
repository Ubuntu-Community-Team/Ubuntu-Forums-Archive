---
title: "Network Manager Can't Detect My ZTE USB 3G Modem!"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by Ashfaqur Rahman on 2013-06-14
Hello, I am using ubuntu 12.10.
I use a ZTE USB 3G Modem to connect to internet. I connect that modem through a driver software which was provided with the modem. This modem works fine. I can browse , use apt-get through terminal.
But the problem is network-manager cant detect my modem. It shows nothing in the top bar. Because of this I -  

1. Can't use Ubuntu Software Center
2. Can't use VPN services
3. Can't create wifi hotspot 

First of all i am telling what i have noticed about this modem:

1. When I connect this modem first time that driver software can't detect it. This time ' lsusb ' command give this [http://paste.ubuntu.com/5691060/](http://paste.ubuntu.com/5691060/) (I cant understand how to add link with text here!). After unplugging and plugging for 2-3 times that software can detect modem and output of lsusb changed to [http://paste.ubuntu.com/5691067/](http://paste.ubuntu.com/5691067/) . But if i connect modem before starting Ubuntu that driver software can detect modem at first time!!
2. I have tried to connect this modem through ' Mobile Broadband ' option but unfortunately this option can't detect my modem under ' create a connection for this mobile broadband device ' option.
3. I think that driver software use wvdial to connect to the internet as I have to install wvdial before installing that software.
4. Also used sakis3g. sakis3g can connect my modem but this also can't solve the network-manager problem.

Now I am telling what I have done till now to solve that network-manager problem:

I have tried this code with root privilege:
```
echo vendor productID > /sys/bus/usb-serial/drivers/option1/new_id
```

It didn't work. Actually it shouldn't. Its clearly saying to edit **new_id** file with **vendor and product id** in **/sys/bus/usb-serial/drivers/option1** directory. **But i have no option1 folder in /sys/bus/usb-serial/drivers directory! **I have only a folder named **generic **in that directory. And **new_id** is also present there.

so i have tried this code with root privilege: 
```
echo vendor productID > /sys/bus/usb-serial/drivers/generic/new_id
```

it didn't work too. One more thing its confusing what will be my productID for this code **0154**(which lsusb finds before modem gets detected by driver software)? or **2003**(which lsusb finds after modem gets detected by driver software)?

As option1 folder is not present in the /sys/bus/usb-serial/drivers directory I have tried to create this folder manually with root privilege:
```
mkdir /sys/bus/usb-serial/drivers/option1
```
but it gives this error message **"****mkdir: cannot create directory `/sys/bus/usb-serial/drivers/option1': No such file or directory"**.

Thats all. Now my question is whats wrong? Is there any solution to **get my modem detected by network-manager? **&#8203;

---

### Post by praseodym on 2013-06-14
Please show the terminal outputs of
```

uname -a
dpkg -l usb-modeswitch
lsmod
usb-devices
```

---

### Post by Ashfaqur Rahman on 2013-06-14
**uname -a** gives:

```
Linux MULTIVAC 3.5.0-30-generic #51-Ubuntu SMP Tue May 14 18:49:52 UTC 2013 i686 i686 i686 GNU/Linux
```

**dpkg -l usb-modeswitch** gives:

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  usb-modeswitch 1.2.3+repack i386         mode switching tool for controlli

```

**lsmod** gives:

```

Module                  Size  Used by
ppp_async              17206  1 
crc_ccitt              12628  1 ppp_async
isofs                  39211  0 
usb_storage            39351  0 
usbserial              36684  11 
parport_pc             31969  0 
ppdev                  12818  0 
bnep                   17708  2 
rfcomm                 37277  12 
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_realtek    63579  1 
joydev                 17162  0 
coretemp               13169  0 
kvm_intel             126746  0 
kvm                   357807  1 kvm_intel
dell_wmi               12602  0 
sparse_keymap          13659  1 dell_wmi
snd_hda_intel          32516  3 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
dell_laptop            17162  0 
dcdbas                 14055  1 dell_laptop
rts5139               281401  0 
microcode              18210  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
arc4                   12474  2 
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
psmouse                84878  0 
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13032  0 
lpc_ich                16926  0 
ath3k                  12791  0 
btusb                  17987  0 
ath9k                 116558  0 
bluetooth             183270  23 bnep,rfcomm,ath3k,btusb
mac80211              461261  1 ath9k
ath9k_common           13784  1 ath9k
ath9k_hw              376270  2 ath9k,ath9k_common
ath                    19188  3 ath9k,ath9k_common,ath9k_hw
snd                    62146  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              175574  3 ath9k,mac80211,ath
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
mei                    35797  0 
i915                  457241  4 
drm_kms_helper         47304  1 i915
drm                   238811  5 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
wmi                    18591  1 dell_wmi
video                  18895  1 i915
mac_hid                13038  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
r8169                  55977  0 
ahci                   25497  6 
libahci                25938  1 ahci

```

**usb-devices** gives:

```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-30-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  8 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0cf3 ProdID=e004 Rev=00.02
S:  Manufacturer=Atheros Communications
S:  Product=Bluetooth USB Host Controller
S:  SerialNumber=Alaska Day 2006
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb


T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=0129 Rev=39.60
S:  Manufacturer=Generic
S:  Product=USB2.0-CRW
S:  SerialNumber=20100201396000000
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=06 Prot=50 Driver=rts5139


T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=64ad Rev=29.25
S:  Manufacturer=CN0Y3PX8724872B2ADJ0A00
S:  Product=Laptop_Integrated_Webcam_HD
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-30-generic ehci_hcd
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
S:  Manufacturer=Linux 3.5.0-30-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=2003 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=MF1900ZTED010000
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usbserial_generic


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.05
S:  Manufacturer=Linux 3.5.0-30-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub



```

NB: This output was taken when my modem was connected

---

### Post by ilianko on 2013-12-18
I had to disable usb3.0 in BIOS in order for the 3g dongle to be detected without trouble

---

