---
title: "No Internet with ASUS USB-N13"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by greekor on 2012-10-07
Hi you all!

I am having trouble connecting to my wifi with ASUS USB-N13 adapter.
I already read a few threads about my specific wifi adapter but nothing fixed my problem so far.

Sometimes I can connect to my router but then I can't ping either a server or my router.
Most of the time, my pc doesn't even connect to the network at all.

Maybe there is something useful here:


```
user@desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. 
```
```
user@desktop:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:80:ad:71:e3:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:17249 (17.2 KB)  TX-Bytes:18270 (18.2 KB)
          Interrupt:17 Basisadresse:0xd000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:17238 (17.2 KB)  TX-Bytes:17238 (17.2 KB)

wlan1     Link encap:Ethernet  Hardware Adresse 30:85:a9:37:0b:c0  
          inet Adresse:192.168.2.108  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: fe80::3285:a9ff:fe37:bc0/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:14788 (14.7 KB)  TX-Bytes:21650 (21.6 KB)

```
```
user@desktop:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"WLAN-6B6542"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 88:25:2C:6B:65:C4   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

eth0      no wireless extensions.

```
```
user@desktop:~$ lsmod
Module                  Size  Used by
rtl8192cu              67616  0 
rtl8192c_common        48369  1 rtl8192cu
rtlwifi                74676  1 rtl8192cu
mac80211              558355  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              219867  2 rtlwifi,mac80211
nls_utf8               12557  1 
isofs                  40257  1 
bnep                   18176  2 
rfcomm                 46747  0 
bluetooth             210297  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  5 
snd_hda_codec_via      51398  1 
arc4                   12529  2 
compat                 20099  7 rtl8192cu,rtlwifi,mac80211,cfg80211,bnep,rfcomm,bluetooth
joydev                 17693  0 
nvidia              12319300  43 
hid_logitech           26520  0 
ff_memless             13097  1 hid_logitech
usbhid                 47199  1 hid_logitech
hid                    99559  2 hid_logitech,usbhid
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                97362  0 
serio_raw              13211  0 
mac_hid                13253  0 
video                  19596  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
vhba                   17397  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dmfe                   27718  0 
```
```
user@desktop:~$ dmesg | grep rtl
[    2.140668] rtl8192cu: Chip version 0x11
[    2.225637] rtl8192cu: MAC address: 30:85:a9:37:0b:c0
[    2.225639] rtl8192cu: Board Type 0
[    2.225886] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    2.225930] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[    2.226149] usbcore: registered new interface driver rtl8192cu
[    2.231757] Error: Driver 'rtl8192cu' is already registered, aborting...
[    2.233506] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.234008] rtlwifi: wireless switch is on
[    2.688407] rtl8192cu: MAC auto ON okay!
[    2.721035] rtl8192cu: Tx queue select: 0x05
[  356.173634] usbcore: deregistering interface driver rtl8192cu
[  380.547484] rtl8192cu: Chip version 0x11
[  380.632091] rtl8192cu: MAC address: 30:85:a9:37:0b:c0
[  380.632096] rtl8192cu: Board Type 0
[  380.632338] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  380.632427] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  380.632537] usbcore: registered new interface driver rtl8192cu
[  380.634493] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  380.635214] rtlwifi: wireless switch is on
[  380.669605] rtl8192cu: MAC auto ON okay!
[  380.702709] rtl8192cu: Tx queue select: 0x05
[  534.968784] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x380e
[  534.968792] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xf0002ace
[  534.968797] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1a
[  534.968803] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[  538.600947] rtl8192cu: Chip version 0x11
[  538.685650] rtl8192cu: MAC address: 30:85:a9:37:0b:c0
[  538.685654] rtl8192cu: Board Type 0
[  538.685897] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  538.685992] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  538.688022] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  538.688903] rtlwifi: wireless switch is on
[  538.723888] rtl8192cu: MAC auto ON okay!
[  538.757891] rtl8192cu: Tx queue select: 0x05
[  686.019938] usbcore: deregistering interface driver rtl8192cu
[ 1230.798583] rtl8192cu: Chip version 0x11
[ 1230.883620] rtl8192cu: MAC address: 30:85:a9:37:0b:c0
[ 1230.883624] rtl8192cu: Board Type 0
[ 1230.883867] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 1230.883957] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[ 1230.884063] usbcore: registered new interface driver rtl8192cu
[ 1230.886416] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 1230.887274] rtlwifi: wireless switch is on
[ 1230.918110] rtl8192cu: MAC auto ON okay!
[ 1230.954239] rtl8192cu: Tx queue select: 0x05

```
```
user@desktop:~$ sudo lshw -C network
  *-network               
       Beschreibung: Ethernet interface
       Produkt: 21x4x DEC-Tulip compatible 10/100 Ethernet
       Hersteller: Davicom Semiconductor, Inc.
       Physische ID: 0
       Bus-Informationen: pci@0000:04:00.0
       Logischer Name: eth0
       Version: 31
       Seriennummer: 00:80:ad:71:e3:b2
       Breite: 32 bits
       Uhr: 33MHz
       Fähigkeiten: pm bus_master cap_list rom ethernet physical
       Konfiguration: broadcast=yes driver=dmfe driverversion=1.36.4 latency=32 link=no maxlatency=40 mingnt=20 multicast=yes
       Ressourcen: irq:17 ioport:d000(Größe=256) memory:f6340000-f63400ff memory:f6300000-f633ffff
  *-network
       Beschreibung: Kabellose Verbindung
       Physische ID: 2
       Bus-Informationen: usb@2:1.1
       Logischer Name: wlan1
       Seriennummer: 30:85:a9:37:0b:c0
       Fähigkeiten: ethernet physical wireless
       Konfiguration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-31-generic firmware=N/A ip=192.168.2.108 link=yes multicast=yes wireless=IEEE 802.11bgn

```
```
user@desktop:~$ lsb_release -d
Description:	Ubuntu 12.04.1 LTS
user@desktop:~$ uname -mr
3.2.0-31-generic x86_64
```

Does anybody have an idea what might cause the problem?

---

### Post by greekor on 2012-10-09
No one?

---

