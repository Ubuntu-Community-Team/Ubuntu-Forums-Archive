---
title: "my huawei usb modem disconnects randomly"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by braakwaku on 2013-03-06
My huawei usb modem disconnects randomly a lot. I am running ubuntu 11.10. I have searched and searched  for solutions and all i get are temporary fixes that never even work for me. 

Using ubuntu requires the use of the internet a lot and my usb modem is my only source of internet.

---

### Post by praseodym on 2013-03-06
Please show the outputs of
```

lsusb
lsmod
usb-devices
ifconfig -a
```
Did you install "usb-modeswitch"? Please also have a look at this:

[http://ubuntuforums.org/showthread.php?t=1831649](http://ubuntuforums.org/showthread.php?t=1831649)

---

### Post by braakwaku on 2013-03-06
thank you very much for replying.. i am a complete noob.. but i think i have the usb modeswitch thing. and here is the output for those commands u gave me

```
braakwaku@braakwaku-Latitude-110L:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 04f3:00a3 Elan Microelectronics Corp. 
Bus 001 Device 004: ID 046d:09c1 Logitech, Inc. QuickCam Deluxe for Notebooks
Bus 001 Device 007: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

```
```

braakwaku@braakwaku-Latitude-110L:~$ lsmod
Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12595  1 ppp_async
option                 21205  2 
usb_wwan               19779  1 option
usbserial              37203  7 option,usb_wwan
parport_pc             32114  0 
bnep                   17923  2 
ppdev                  12849  0 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
snd_usb_audio         100880  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_hwdep              13276  1 snd_usb_audio
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_pcm                80468  3 snd_usb_audio,snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            13519  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dcdbas                 14098  1 dell_laptop
pcmcia                 39822  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146148  0 
libipw                 46701  1 ipw2200
psmouse                73673  0 
serio_raw              12990  0 
cfg80211              172392  2 ipw2200,libipw
snd                    55902  16 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
lib80211               14570  2 ipw2200,libipw
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
binfmt_misc            17292  1 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
e100                   36289  0 

```
```

braakwaku@braakwaku-Latitude-110L:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0608 Rev=77.64
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=03 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=046d ProdID=09c1 Rev=00.05
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 3 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio

T:  Bus=01 Lev=02 Prnt=03 Port=02 Cnt=02 Dev#=  7 Spd=480 MxCh= 0
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

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04f3 ProdID=00a3 Rev=10.23
S:  Product=2.4GRF Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```
```

braakwaku@braakwaku-Latitude-110L:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:3f:0e:5d:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:12:f0:8f:5e:b5  
          inet6 addr: fe80::212:f0ff:fe8f:5eb5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5217 (5.2 KB)
          Interrupt:19 Base address:0x8000 Memory:dfdfe000-dfdfefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43728 (43.7 KB)  TX bytes:43728 (43.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.15.130.130  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:178799 (178.7 KB)  TX bytes:45114 (45.1 KB)

```

---

### Post by varunendra on 2013-03-09
Welcome to the forums braakwaku :)

Please always use 'Code' tags whenever posting terminal outputs. It makes the post look clean and more readable. Follow the 'Code Tags example' link in my signature to see  an example of how to do it.

Regarding your issue, you seem to be already in good hands (thanks praseodym for the exhaustive checklist. Think I'll refer to it often now ;))
Just a personal experience I'd like to share -

Do you have an option to try a different service provider ?
I use a 3G modem (using a 2G connection) myself, and of the four services I have tried so far (namely BSNL, Airtel, Tata Docomo and Idea), only one (Airtel) is able to give me a stable and relatively fast connection.

One (BSNL) gives a speed that is practically unusable, and the remaining two disconnect every few minutes or an approximately fixed amount of data. I'm not sure if it is some technical issue or some kind of 'under the hood' policy they have, but it happens both on Ubuntu and Windows (both in XP/7).

And given the way the Docomo service behaves (tried in three different cities), I can say with confidence that certain service providers definitely have some black policies to keep users from using too much data, thus squeezing profit.

So if you have an option, consider switching to a different service provider who is known to provide stable service in your area.

Just my 2c

---

