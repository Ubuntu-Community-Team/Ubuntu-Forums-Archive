---
title: "How to install Sony Ericsson GC89 GPRS/EDGE &amp; Wi-Fi Laptop PC Card ?"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by haasibs on 2011-12-23
I use broadband connection. Now I need to use mobile broadband connection for outside use. But I can't install Sony Ericsson GC89 GPRS/EDGE & Wi-Fi Laptop PC Card. But it works perfectly on Windows XP. Need help to install & run it. I searched online for 6 hours , found many solution , but thats did not work. :confused:

---

### Post by praseodym on 2011-12-23
Hi,

please show the outputs of the following commands:

```
lspci -nnk
lsusb
usb-devices
lsmod
ifconfig -a
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by haasibs on 2011-12-24
Here is all information, 

```
lspci -nnk
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel modules: iTCO_wdt, intel-rng
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: ata_piix
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel modules: i2c-i801
06:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
06:09.0 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
06:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller [104c:802e]
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
06:09.3 Mass storage controller [0180]: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller [104c:ac8f]
    Subsystem: Sony Corporation Device [104d:81f1]
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1
06:0a.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Device [8086:2753]
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200
07:00.0 Network controller [0280]: Broadcom Corporation BCM43xG 802.11b/g [14e4:4325] (rev 03)
    Subsystem: Device [18de:0003]
    Kernel modules: ssb
07:00.1 Serial controller [0700]: Broadcom Corporation EDGE/GPRS data and 802.11b/g combo cardbus [GC89] [14e4:4344] (rev 03)
    Subsystem: Device [18de:0003]
    Kernel driver in use: serial



```
lsusb
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
usb-device
```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-13-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0ac8 ProdID=c002 Rev=01.00
S:  Manufacturer=Vimicro Corp.
S:  Product=USB2.0 Web Camera
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=vc032x

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-13-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-13-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=093a ProdID=2510 Rev=01.00
S:  Manufacturer=PIXART
S:  Product=USB OPTICAL MOUSE
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-13-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-13-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


```
lsmod
```

Module                  Size  Used by
usbhid                 41704  0 
hid                    77084  1 usbhid
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
ndiswrapper           192828  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
i915                  451053  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
ipw2200               145664  0 
tifm_sd                17415  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
drm_kms_helper         40971  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
libipw                 46641  1 ipw2200
gspca_vc032x           32072  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 i915,drm_kms_helper
cfg80211              156212  2 ipw2200,libipw
gspca_main             27894  1 gspca_vc032x
tifm_7xx1              12898  0 
videodev               75143  1 gspca_main
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
tifm_core              15040  2 tifm_sd,tifm_7xx1
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
sony_laptop            34432  0 
soundcore              12600  1 snd
serio_raw              12990  0 
lib80211               14570  2 ipw2200,libipw
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
8139too                23208  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core


```
ifconfig -a
```


eth0      Link encap:Ethernet  HWaddr 00:13:a9:45:3c:23  
          inet addr:192.168.78.49  Bcast:192.168.78.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe45:3c23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4401 errors:2 dropped:11 overruns:2 frame:0
          TX packets:1654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1521816 (1.5 MB)  TX bytes:282521 (282.5 KB)
          Interrupt:17 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:a2:3d:32  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Memory:b0107000-b0107fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4973 (4.9 KB)  TX bytes:4973 (4.9 KB)


```
rfkill list
```


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```
cat /var/lib/NetworkManager/NetworkManager.state
```


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

> Here are all info. and this device uses PCI slot, not usb device. Thanks

---

### Post by praseodym on 2011-12-24
Why is ndiswrapper installed? Did you try sth. with windows WLAN drivers?

---

### Post by haasibs on 2011-12-24
So what should I do now? Need immediate solution. Thanks

---

### Post by praseodym on 2011-12-24
Remove it completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
and reboot. Check:
```
lsmod
```

---

### Post by haasibs on 2011-12-25
I used all code above to remove, but some code did not work properly.  Here are information: 

```
lsmod
```

> 
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
i915                  451053  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
ipw2200               145664  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
tifm_sd                17415  0 
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia                 39671  0 
drm_kms_helper         40971  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
gspca_vc032x           32072  0 
gspca_main             27894  1 gspca_vc032x
libipw                 46641  1 ipw2200
drm                   184164  4 i915,drm_kms_helper
cfg80211              156212  2 ipw2200,libipw
tifm_7xx1              12898  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
videodev               75143  1 gspca_main
psmouse                73312  0 
tifm_core              15040  2 tifm_sd,tifm_7xx1
sony_laptop            34432  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
serio_raw              12990  0 
video                  18951  1 i915
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  2 ipw2200,libipw
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
8139too                23208  0 
8139cp                 22497  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


What to do now?  :confused:

---

### Post by praseodym on 2011-12-25
Try to load the module which is not "in use":

> sudo modprobe -v ssb

---

### Post by haasibs on 2011-12-25
I loaded the module , but it shows below information. My device pci card , not USB device.

[HTML]sudo modprobe -v ssb 			 		[/HTML]

> insmod /lib/modules/2.6.38-13-generic/kernel/drivers/ssb/ssb.ko 

---

### Post by haasibs on 2011-12-25
Now what to do? I removed everything. How to install and run the device  ? Need Help.

---

