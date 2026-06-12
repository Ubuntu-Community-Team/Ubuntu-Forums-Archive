---
title: "Network Manager RT2800 Linksys WMP600N PCI Wirless NIC"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by rockrhino27 on 2012-01-16
Anybody having trouble managing their wireless NIC with Network Manager in Ubuntu 11.10 and a Linksys WMP600N PCI NIC?  It has the RaLink RT2800 chipset.  I am using the rt2800pci driver.  

For some reason Network Manager will not manage this connection under wireless connections.  It is consistently greyed out.  I manually edited /etc/network/interfaces and /etc/resolv.conf and the NIC is working fine.  However Network Manager thinks i'm not connected to the inet.  I don't know if it is something with network manager or something else.  Any assistance would be appreciated.  

Rich

---

### Post by rockrhino27 on 2012-01-17
I see I got 21 views and no responses.  :)  Here is some further information.  

Output from lspci:
00:0b.0 Network controller: Ralink corp. RT2800 802.11n PCI

output from lsmod:
rich@lakewood:~$ lsmod 
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vesafb                 13489  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_usb_audio         100880  1 
ppdev                  12849  0 
snd_pcm                80435  3 snd_intel8x0,snd_ac97_codec,snd_usb_audio
binfmt_misc            17292  1 
nvidia               7098131  34 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hwdep              13276  1 snd_usb_audio
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
parport_pc             32114  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
snd_timer              28932  2 snd_pcm,snd_seq
mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
snd                    55902  16 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
sis_agp                13165  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  1 
uas                    17699  0 
floppy                 60310  0 
sis900                 22729  0 
sata_sis               12703  2 

output from lshw -C network:
rich@lakewood:~$ sudo lshw -C network
[sudo] password for rich: 
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:50:8d:cf:0c:5a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:d800(size=256) memory:ec012000-ec012fff memory:80000000-8001ffff
  *-network:1
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: Ralink corp.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 00
       serial: 00:25:9c:b9:0f:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-14-generic firmware=0.34 ip=192.168.1.2 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:ec000000-ec00ffff


I was doing some reading and many people talk about conflicting drivers with this NIC.  Maybe somebody can assist me in reading the lshw, because i'm unsure if I have a conflicting driver.  

As always any assistance would be appreciated.  

Rich

---

### Post by rockrhino27 on 2012-01-20
***Bump***

I doubt that i'm the only person with this problem.  

Any ideas?  

Rich

---

### Post by GMS1 on 2012-02-13
I am have a similar issue except my Ubuntu 11.10 recognizes the card and says the drivers are installed but it just will not connect to the network. My wireless network is not greyed out so I think your issue may be worse. But I have found several issues like this with this card for the 11.10 but not many solutions have been posted yet especially solutions that do not require the apt-get. It seems though that I am going to have to drag the tower upstairs and hardwire it into the internet so I can do such a thing.

---

### Post by bigoldgeek on 2012-02-21
Having the same problem as GMS1 above.  It seems to see the SSID's, but won't connect. I think it connected once, but it disco'd immediately.

---

### Post by wsilk on 2012-03-11
I've got the same problem, have a no-name wireless card, which shows up as a Ralink RT2800.  The card is detected and can see my wireless network, but it won't connect. 

lspci shows:
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 Network controller: Ralink corp. Device 3062

```

lsmod
```
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              393421  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              172427  2 rt2x00lib,mac80211
emu10k1_gp             12570  0 
gameport               15060  2 emu10k1_gp
eeprom_93cx6           12653  1 rt2800pci
psmouse                73673  0 
soundcore              12600  1 snd
snd_page_alloc         14115  3 snd_hda_intel,snd_emu10k1,snd_pcm
serio_raw              12990  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
r8169                  43104  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


```

lspci -nnk | grep -iA2 net shows:
```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Ralink corp. Device [1814:3062]
	Kernel driver in use: rt2800pci
 
```

lshw -C network shows:
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:d0:87:2b:1e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:c000(size=256) memory:f7000000-f7000fff memory:7ff00000-7ff1ffff
  *-network
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: c8:3a:35:cd:da:78
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-16-generic firmware=0.34 latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:f8000000-f800ffff

```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

Any help getting the wireless connected would be great!

---

### Post by wsilk on 2012-03-11
Found a thread with instructions for a working solution. 

[http://ubuntuforums.org/showthread.php?t=1608095&page=2]("http://ubuntuforums.org/showthread.php?t=1608095&page=2")

Followed the first post, then had to blackist the RT2800 driver and reboot.

---

