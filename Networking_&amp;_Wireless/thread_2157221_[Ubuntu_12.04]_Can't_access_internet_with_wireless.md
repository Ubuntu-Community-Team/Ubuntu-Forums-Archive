---
title: "[Ubuntu 12.04] Can't access internet with wireless or Vodafone Mobile Broadband Modem"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by Crystal1989 on 2013-06-24
Hey potential saviors,

I'm a newbie to Ubuntu.  I replaced my **Windows Vista **with **Ubuntu 12.04 **two days ago.  The only way for me to get online is by using a **Vodafone Mobile Broadband Modem (ZTE) (Model: K3565-Z).  **I have been trying to get Ubuntu online since it's been installed.  I messed up the first time, so I re-installed all over again.  I have been browsing the internet (on my Win7 laptop) before asking this question and basically all of the links are now purple and I still haven't managed to get my Ubuntu online.  I've tried everything, or at least everything that I've found.

I've tried getting online in many different ways.

1. Hooking the stick directly to the PC with Ubuntu 12.04.  Turns out that there is apparently a bug.  Tried to create the Mobile Broadband.  It didn't show up in the list unless I restarted the computer.  I did.  I tried to access it, but it won't work.

2. I moved on to add a bash text file to make sure that it refreshed whenever it went offline.  It teased me by making it seem like it will go online, but it never did and it had the gall to say that I went offline even though I was never on (my mobile broadband says it's never been used).

3. I tried to create a home network with my laptop as host.  I made sure that everything can be shared.  The wireless popped up on the list on Ubuntu, but yet again, it never connected.

4. I tried to make a computer-to-computer connection with  a crossover, which is apparently super easy, but somehow that still didn't work.  It teased me again.

5. I tried static ip addresses for both and released/renewed/up/down.  Nothing.

I refreshed everything, I did everything that was available.  I can't download or upgrade anything on Ubuntu because there is **no Internet connection**.  I tried to download everything on my laptop, but there is always something missing and it won't install on Ubuntu.  I tried the **wvdial **thing, but it didn't install.

I would be forever grateful to anyone who can take my hand and walk me to the land of the internet on Ubuntu.  I am ready to follow anyone's wise words.

---

### Post by praseodym on 2013-06-24
Hi,

please open a terminal and show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
usb-devices
lsmod
ifconfig -a
iwconfig
rfkill list
```

---

### Post by Crystal1989 on 2013-06-27
@praseodym thank you so much for replying.  I guess I must be a noob at  forums as well because for the past 2 days I've been refreshing and  seeing no replies for some reason.

Here are the results while the Vodafone stick was in plugged directly into the computer with Ubuntu 12.04:

```

user1@user1-NC700AA-ABA-IQ526:~$ uname -a
Linux user1-NC700AA-ABA-IQ526 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux

```

```

user1@user1-NC700AA-ABA-IQ526:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:2a82]
    Kernel driver in use: r8169
--
05:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
    Subsystem: Ralink corp. Device [1814:2790]
    Kernel driver in use: rt2800pci

```

```

user1@user1-NC700AA-ABA-IQ526:~$ lsusb
Bus 001 Device 003: ID 0a48:3274 I/O Interconnect 
Bus 001 Device 005: ID 0424:2507 Standard Microsystems Corp. 
Bus 002 Device 003: ID 04f2:b056 Chicony Electronics Co., Ltd 
Bus 002 Device 006: ID 19d2:0063 ZTE WCDMA Technologies MSM K3565-Z HSDPA
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 004 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 006 Device 002: ID 1926:0003 NextWindow 1900 HID Touchscreen
Bus 007 Device 002: ID 03f0:140c Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1934:0702 Feature Integration Technology Inc. (Fintek) Integrated Consumer Infrared Receiver/Transceiver

```

```

user1@user1-NC700AA-ABA-IQ526:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0a48 ProdID=3274 Rev=58.87
S:  Manufacturer=Generic
S:  Product=USB 2.0 Reader
S:  SerialNumber=00000001
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  5 Spd=480 MxCh= 7
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=2507 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub

T:  Bus=01 Lev=02 Prnt=05 Port=02 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=1934 ProdID=0702 Rev=00.01
S:  Manufacturer=FINTEK
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=88636562727801
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=mceusb

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b056 Rev=67.51
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=CNF7042
S:  SerialNumber=SN0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0063 Rev=00.00
S:  Manufacturer=Vodafone (ZTE)
S:  Product=Vodafone Mobile Broadband K3565-Z
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qmi_wwan
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=03f0 ProdID=171d Rev=01.00
S:  Manufacturer=Broadcom Corp
S:  Product=HP Integrated Module
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c315 Rev=28.00
S:  Manufacturer=Logitech
S:  Product=Logitech USB Keyboard
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1926 ProdID=0003 Rev=02.00
S:  Manufacturer=NextWindow
S:  Product=Touchscreen
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=usbhid

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=140c Rev=00.01
S:  Manufacturer=HP
S:  Product=HP Wireless Keyboard Kit
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

```

user1@user1-NC700AA-ABA-IQ526:~$ lsmod
Module                  Size  Used by
option                 25700  0 
usb_wwan               19532  1 option
usbserial              36882  2 option,usb_wwan
qmi_wwan               13022  0 
usbnet                 25247  1 qmi_wwan
cdc_wdm                17664  1 qmi_wwan
coretemp               13362  0 
joydev                 17394  0 
hid_generic            12485  0 
snd_hda_codec_analog    75324  1 
parport_pc             32115  0 
ppdev                  12850  0 
psmouse                91022  0 
microcode              18396  0 
rfcomm                 38104  12 
bnep                   17791  2 
serio_raw              13032  0 
ir_lirc_codec          12740  0 
lirc_dev               18701  1 ir_lirc_codec
ir_mce_kbd_decoder     12682  0 
ir_sanyo_decoder       12466  0 
ir_sony_decoder        12463  0 
ir_jvc_decoder         12460  0 
ir_rc6_decoder         12460  0 
ir_rc5_decoder         12460  0 
ir_nec_decoder         12460  0 
snd_hda_intel          33029  2 
snd_hda_codec         116477  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
rc_rc6_mce             12455  0 
snd_rawmidi            25426  1 snd_seq_midi
mceusb                 17800  0 
rc_core                21295  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,mceusb
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 46054  0 
arc4                   12474  2 
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
rt2800pci              18368  0 
rt2800lib              57759  1 rt2800pci
crc_ccitt              12628  1 rt2800lib
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
mac_hid                13078  0 
nouveau               855013  3 
hid                    82511  2 hid_generic,usbhid
snd                    62675  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2x00pci              14203  1 rt2800pci
videobuf2_memops       13213  1 videobuf2_vmalloc
rt2x00lib              49084  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              475488  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              181041  2 rt2x00lib,mac80211
lpc_ich                16993  0 
eeprom_93cx6           13169  1 rt2800pci
ttm                    76326  1 nouveau
drm_kms_helper         47459  1 nouveau
drm                   240232  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13317  1 nouveau
mxm_wmi                12894  1 nouveau
btusb                  17952  0 
bluetooth             189585  24 rfcomm,bnep,btusb
video                  19070  1 nouveau
wmi                    18745  2 nouveau,mxm_wmi
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
firewire_ohci          36110  0 
r8169                  56853  0 
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
usb_storage            39720  0 

```

```

user1@user1-NC700AA-ABA-IQ526:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:8c:21:d5:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10208 (10.2 KB)  TX bytes:10208 (10.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:60:86:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wwan0     Link encap:Ethernet  HWaddr 1a:05:e5:1a:62:e2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

user1@user1-NC700AA-ABA-IQ526:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wwan0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

```

```

user1@user1-NC700AA-ABA-IQ526:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

If you have time, it would be great if you could let me know what you are looking for so that I could learn a bit more about Ubuntu.

---

### Post by rrich1974 on 2013-06-27
Bus 002 Device 006: ID 19d2:0063 ZTE WCDMA Technologies MSM K3565-Z HSDPA

this is what we are looking for. i have had the exact same modem and it works like a charm in ubuntu. normally, if you insert the modem in the usb port, wait about a minute, maybe less, the "new mobile broadband connection" or something like this should appear and you can setup your connection. other option is wvdial, but is not installed by default.

---

### Post by Crystal1989 on 2013-06-27
@rrich1974 I realize that it should do that, but it doesn't show up at all.  The only pop-up I get is that I am offline.  The stick doesn't show up at all.  I tried to download wvdial from my Win7 laptop because there is no way to download it without internet on Ubuntu, but every time I tried to install there was always something missing and whenever I would get that next file, yet another one would be missing, so I couldn't install.

---

### Post by rrich1974 on 2013-06-27
pretty strange, in my case, it appears as "new mobile broadband" but after some time, one minute or so...
maybe it appears as a storage device, if so, unmount it. 
i found a deb file of wvdial, you can try.

 [http://ftp.debian.org/debian/pool/main/w/wvdial/](http://ftp.debian.org/debian/pool/main/w/wvdial/)
[TABLE]
[TR]
[TD][wvdial_1.61-4.1_i386.deb]("http://ftp.debian.org/debian/pool/main/w/wvdial/wvdial_1.61-4.1_i386.deb")[/TD]
[TD="align: right"]13-Mar-2012 21:55[/TD]
[TD="align: right"]102K[/TD]
[/TR]
[/TABLE]

but read the instruction before setup the connection. 


[h=2][https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)[/h][h=2]Alternative Way 1 (using wvdialconf & wvdial)[/h]

---

### Post by praseodym on 2013-06-27
You may want to have a look at here:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

