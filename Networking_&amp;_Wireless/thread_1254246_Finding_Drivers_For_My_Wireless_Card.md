---
title: "Finding Drivers For My Wireless Card"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by JKeeb on 2009-08-31
Hello! 
I am trying to figure out how to install the drivers for my new USB wireless LAN card i bought.
I have tried updating unbuntu and everything is up to date yet my card still wont pick up any connections.
(I can pick up connections fine on my windows xp partition.)
I am running Unbuntu 9.04 Jaunty Jackalope
My Card is a Rosewill RNX-G1  IEEE 802.11/g Wireless USB Adapter

If anybody could assist me by explaining to me how to get this running i would be greatly appreciative. 

Thanks for your time.

---

### Post by mikewhatever on 2009-08-31
Google has reports saying the device works out of the box with 9.04. Can you post the outputs of the following commands with the device connected:

sudo lshw -C network

ifconfig

---

### Post by JKeeb on 2009-08-31
jon@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1b:45:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.100 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:68:84:67:74:01
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan2
       serial: 00:1a:ef:05:d0:66
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.11.7 multicast=yes wireless=IEEE 802.11bg


-----------------------------------------------------------------

jon@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:1b:45:9e  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe1b:459e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1761977 (1.7 MB)  TX bytes:168870 (168.8 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan2     Link encap:Ethernet  HWaddr 00:1a:ef:05:d0:66  
          inet addr:192.168.11.7  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:efff:fe05:d066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8974 (8.9 KB)  TX bytes:5019 (5.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-EF-05-D0-66-30-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



Thanks for the help!

---

### Post by uylug on 2009-08-31
Everything seems to be alright.

Can you ping google?

```
ping google.com
```

What happens if you run this command?

```
sudo dhclient wlan2
```

---

### Post by JKeeb on 2009-08-31
jon@ubuntu:~$ ping google.com
ping: unknown host google.com


---------------------------------

jon@ubuntu:~$ sudo dhclient wlan2
There is already a pid file /var/run/dhclient.pid with pid 5676
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan2/00:1a:ef:05:d0:66
Sending on   LPF/wlan2/00:1a:ef:05:d0:66
Sending on   Socket/fallback
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 13


Thanks for the help!

---

### Post by JKeeb on 2009-09-05
Still Looking for a sollution, does anybody have any advice?

Thanks!

---

### Post by Cuba71 on 2009-09-06
It looks like you have two wireless adapters connected to your machine.
A PCI Ahteros AR242x wireless adapter, that by the way, should work with Ubuntu's native ath5k (that's the card I have in my Toshiba laptop)

And the Rosewill USB wireless adapters.

Probably there's a conflict between both adapters.  What I'd do to begin with is disconnect the USB adapter, reboot the machine and see if Ubuntu recognizes de Atheros PCI card (it should).

Let us know

---

### Post by JKeeb on 2009-09-19
I have unplugged my usb wireless card.
Restarting my computer...


typed 
sudo dhclinet wlan2

SIOCSIFADDR: No such Device
wlan2: Error while getting interface flags: no such device
Bind socket to interface: no such device

---

### Post by JKeeb on 2009-09-23
Still trying to find a solution to this problem.

Any assistance is appreciated!

---

### Post by Cuba71 on 2009-09-25
The Atheros AR242x is supported in native mode by Ubuntu, that's the adapter in my Toshiba Laptop.  It uses the ath5k driver. 

Reboot your computer without the USB adapter and please post the output of 

lshw -C network
lsmod

---

### Post by JKeeb on 2009-09-25
jon@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1b:45:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:66:a6:16:39:2b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jon@ubuntu:~$ 
jon@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
joydev                 18496  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
pcmcia                 44748  0 
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
tifm_7xx1              13824  0 
ati_agp                14988  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
tifm_core              15900  1 tifm_7xx1
i2c_piix4              18448  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
psmouse                61972  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 40212  0 
agpgart                42696  2 drm,ati_agp
pcspkr                 10496  0 
k8temp                 12416  0 
ath_pci                99224  0 
serio_raw              13444  0 
video                  25360  0 
wlan                  210544  1 ath_pci
ath_hal               198864  1 ath_pci
input_polldev          11912  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
jon@ubuntu:~$

---

