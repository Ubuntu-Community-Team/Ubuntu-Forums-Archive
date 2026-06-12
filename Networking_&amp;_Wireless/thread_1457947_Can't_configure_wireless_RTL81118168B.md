---
title: "Can't configure wireless RTL8111/8168B"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by magtrask on 2010-04-19
I am new to Ubuntu, but I liked it so much I wiped XP entirely. 

I have an MSI Megabook M662.
 Can't get my wireless working.  I have "enabled" checked, but can't view any connections.  I don't have wireless at home, I'm trying to make this work for free connections at the library, etc.

 Have been trying to follow advice here. From the Help Menu troubleshooting I tried:


mag@MSIubuntu:~$ sudo lshw -C network
[sudo] password for mag: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:eb:51:99
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=24.142.48.224 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:d800(size=256) memory:fe2ff000-fe2fffff memory:fe2c0000-fe2dffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:9d:85:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


This reports Disabled, and the advice is to check that device is on.  But I just want to roam for service, I don't have my own wireless at home.





I thought I might need to use ndiswrapper but I cannot locate a driver for this card info:
lspci -nn 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. **RTL8111/8168B** PCI Express Gigabit Ethernet controller [**10ec:8168**] (rev 01) 



What should I try now?
Thanks in advance, Mag

---

### Post by bkratz on 2010-04-19
> **magtrask said:**
> I am new to Ubuntu, but I liked it so much I wiped XP entirely. 

I have an MSI Megabook M662.
 Can't get my wireless working.  I have "enabled" checked, but can't view any connections.  I don't have wireless at home, I'm trying to make this work for free connections at the library, etc.

 Have been trying to follow advice here. From the Help Menu troubleshooting I tried:


mag@MSIubuntu:~$ sudo lshw -C network
[sudo] password for mag: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:eb:51:99
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=24.142.48.224 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:d800(size=256) memory:fe2ff000-fe2fffff memory:fe2c0000-fe2dffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:9d:85:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


This reports Disabled, and the advice is to check that device is on.  But I just want to roam for service, I don't have my own wireless at home.





I thought I might need to use ndiswrapper but I cannot locate a driver for this card info:
lspci -nn 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. **RTL8111/8168B** PCI Express Gigabit Ethernet controller [**10ec:8168**] (rev 01) 



What should I try now?
Thanks in advance, Mag

The number you are mentioning is listed as the ethernet card, not the wireless card. If you go back to the terminal and enter

```
lspci | grep Wireless
```

it should tell us what your wireless card is, or just look for something with the word network in that earlier listing.

---

### Post by chili555 on 2010-04-19
The RTL8111/8168B is your wired ethernet  interface and is it working fine. You have a driver and an IP address and are connected.

Please run lspci -nn again and find your wireless device:> *-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:19:db:9d:85:50
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
Also, please run and post:```
rfkill list
```Thanks.

Oops, my pal bkratz beat me to it. Please continue in his good care.

---

### Post by magtrask on 2010-04-19
I first followed your suggestion bkratz, nothing happened.

mag@MSIubuntu:~$ lspci | grep Wireless
mag@MSIubuntu:~$ 

Next, I tried your suggestion chili555.

mag@MSIubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
04:04.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller [1217:7134] (rev 21)
04:04.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 01)
04:04.3 Bridge [0680]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
04:04.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
mag@MSIubuntu:~$ 

and also
mag@MSIubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

Thanks for the help, I await your further instructions....

---

### Post by bkratz on 2010-04-19
Still don't see it:


Even if it is internal, it still could be a usb device-- so post the output of 

lsusb

that is LSUSB in lowercase

---

### Post by magtrask on 2010-04-19
Yeah, I can't see it either.  But I know I have one as it worked with XP a month ago.

mag@MSIubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by bkratz on 2010-04-19
> **magtrask said:**
> Yeah, I can't see it either.  But I know I have one as it worked with XP a month ago.

mag@MSIubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I will spend some time googling the notebook part number and see if I can find anything. Could you check the bios and make sure it is enabled there, if not, will see what I can find.

---

### Post by magtrask on 2010-04-19
To illustrate my ignorance I confess I don't know what "check the bios" means.  I'll try to figure that out though.

---

### Post by bkratz on 2010-04-19
did find this site

[http://www.linlap.com/wiki/msi+megabook+m662](http://www.linlap.com/wiki/msi+megabook+m662)

Where it specifically mentions the driver as 

"Use the ipw3945 module" .  Dr. Chili is the true expert on that one, but I will see what I can find out.

---

### Post by bkratz on 2010-04-19
> **magtrask said:**
> To illustrate my ignorance I confess I don't know what "check the bios" means.  I'll try to figure that out though.

Usually there is some method like pressing del or F12 or F2 or something during the intial boot where it gives you the internal options for setup--like boot order. Did you install from a CD originally? If so you probably had to go there and set the CD as the first boot device. There may not be anything there about the wireless though, so I will still look some more.

---

### Post by magtrask on 2010-04-19
Right, I did know about this, just forgot.  I rebooted and entered bios.  No reference there to wireless.

---

### Post by bwallum on 2010-04-19
I have a similar problem with a pc wireless card by Belkin using the RTL8185L chip. Lucid just does not see it. Not got to the bottom of it yet so can only offer empathy at the moment...

If you open a terminal Applications>Accessories>Terminal and enter ```
sudo iwconfig
```what do you get returned?

---

### Post by magtrask on 2010-04-19
> **bwallum said:**
> I have a similar problem with a pc wireless card by Belkin using the RTL8185L chip. Lucid just does not see it. Not got to the bottom of it yet so can only offer empathy at the moment...

If you open a terminal Applications>Accessories>Terminal and enter ```
sudo iwconfig
```what do you get returned?

```
mag@MSIubuntu:~$ sudo iwconfig
[sudo] password for mag: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I don't know why those little faces are there in the reply.  Unintentional.

---

### Post by bkratz on 2010-04-19
> **magtrask said:**
> I don't know why those little faces are there in the reply.  Unintentional.

there is a box below to turn off those faces! Anyway, it seems something has "managed" the wireless connection!

wlan0 IEEE 802.11bg ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=off 


It might be interesting to try the following!

```
lsmod
```
to try and see what modules are loaded

and 

```
sudo iwconfig wlan0 txpower 15
```

since it says that the transmit power is off. Neither of these may help, but could.

---

### Post by magtrask on 2010-04-19
ok bkratz, here is the first:

mag@MSIubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
iptable_filter          3100  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
ip_tables              11692  1 iptable_filter
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
pcmcia                 36808  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
x_tables               16544  1 ip_tables
arc4                    1660  2 
ecb                     2524  2 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           24296  1 
soundcore               7264  1 snd
rt73usb                26336  0 
crc_itu_t               1852  1 rt73usb
rt2x00usb              11548  1 rt73usb
rt2x00lib              29756  2 rt73usb,rt2x00usb
rsrc_nonstatic         11644  1 yenta_socket
input_polldev           3716  1 rt2x00lib
joydev                 10240  0 
mac80211              181140  2 rt2x00usb,rt2x00lib
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211               93052  2 rt2x00lib,mac80211
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  2 rt2x00lib,sdhci
psmouse                56500  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
r8169                  32064  0 
usbhid                 38208  0 
mii                     5212  1 r8169
ieee1394               86596  1 ohci1394
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


and the second:
mag@MSIubuntu:~$ sudo iwconfig wlan0 txpower 15
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.

Does that mean anything to you?
thanks for all the effort folks.

---

### Post by bkratz on 2010-04-19
Sure seems to have a lot of drivers! None of them are the one I expected to see--it looks like this must be a Ralink chipset. Perhaps we can clean this up to look at by

lsmod | grep -e rt2 -e rt3


and see if it makes more sense, trying to find the right card still.

---

### Post by bwallum on 2010-04-19
Try this

At the top right of the panel find the network icon. Right click and go to Edit Connections.

Delete all wireless connections listed under the wireless tab.

Reboot

When the Desktop comes up, wait for a message. Eventually you will get one even if it is ...'not connected.

Sometimes Ubuntu gets confused if it already has a connection for the same physical device but no driver. Deleting all the entries will force it to take a fresh look.

---

### Post by bkratz on 2010-04-19
Still bothered about the lack of your card showing up, could you try 

sudo update-pciids

and then do a

lspci | grep Network

Just curious, not really necessary, this just updates the pci list.

---

### Post by magtrask on 2010-04-19
Hi, I stepped out for a few minutes.  I'll answer suggestions in sequence.

```
mag@MSIubuntu:~$ lsmod | grep -e rt2 -e rt3
rt2x00usb              11548  1 rt73usb
rt2x00lib              29756  2 rt73usb,rt2x00usb
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
led_class               4096  2 rt2x00lib,sdhci
```

Hi bwallum
As per your suggestion, I went to edit connections.
There are no wireless connections listed under the wireless tab, nothing to delete.

and thirdly, for bkratz:

```
mag@MSIubuntu:~$ sudo update-pciids
[sudo] password for mag: 
Downloaded daily snapshot dated     2010-04-09 03:15:02
mag@MSIubuntu:~$ lspci | grep Network
mag@MSIubuntu:~$ 
```

is anything supposed to show when I "lspci | grep Network"?

---

### Post by bwallum on 2010-04-19
I presume you can't make connection with the machine then... I presume you are not connected by 'wired connection'?

And... in System>Administration>Hardware Drivers is there a suggested wireless driver? If there is, is it activated?

---

### Post by magtrask on 2010-04-19
Yes, I am connected by wired connection.  I didn't do anything but plug in the cable, and a connection was established calling itself "Auto eth0".  But under the other "Edit Connection" tabs: Wireless, Mobile Broadband, VPN, and DSL, there is nothing listed.

I followed System>Administration>Hardware Drivers
the result is "no proprietary drivers are in use on this system"

---

### Post by bkratz on 2010-04-19
> **magtrask said:**
> and thirdly, for bkratz:

mag@MSIubuntu:~$ sudo update-pciids
[sudo] password for mag: 
Downloaded daily snapshot dated     2010-04-09 03:15:02
mag@MSIubuntu:~$ lspci | grep Network
mag@MSIubuntu:~$ 

is anything supposed to show when I "lspci | grep Network"?

Well, I was hoping that updating the pci id's would show up the device, obviously it didn't help. You might just try ```
lspci -nn
``` and look anyway for the network controller, but I doubt it will show up there if it didn't show up when tried earlier.  Running out of ideas, but still googling.  You might also try

```
sudo ifconfig wlan0 down && sudo ifconfig wlan0 up
```

to see if it comes up.

---

### Post by bwallum on 2010-04-19
ESSID refers to the network name which is, by default, the network name given by your router. The iwconfig report says that ESSID is "" or has no name. Is this true?

To find out You need to query the router (or cable modem). To do this you open a browser and then type in an address for the router, a common one is 192.168.1.1 or 192.168.0.1 or 10.0.0.1 or something similar. You can get a good idea of what it is by typing ```
ifconfig
```and looking for eth0 entry, find the inet address. Your router will be on the same network, typically with an address that has 1 or 254 as the last number set. Can you find out your WIRELESS network name from the router/modem?

---

### Post by magtrask on 2010-04-19
Hi bkratz.

```
mag@MSIubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
04:04.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller [1217:7134] (rev 21)
04:04.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 01)
04:04.3 Bridge [0680]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
04:04.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
mag@MSIubuntu:~$ 
```

and the second seems to do nothing:
```
mag@MSIubuntu:~$ sudo ifconfig wlan0 down && sudo ifconfig wlan0 up
mag@MSIubuntu:~$
```

Hi bwallum, here's what I have so far.

```
mag@MSIubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:db:eb:51:99  
          inet addr:24.142.48.224  Bcast:24.142.51.255  Mask:255.255.252.0
          inet6 addr: fe80::219:dbff:feeb:5199/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:576080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49469697 (49.4 MB)  TX bytes:2879947 (2.8 MB)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:db:9d:85:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-DB-9D-85-50-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by bwallum on 2010-04-19
inet addr:24.142.48.224 Bcast:24.142.51.255 Mask:255.255.252.0 indicates you are running on quite a big network. Do you have a network administrator? You could be on a sub net proxy router linked to a main network. That might mean you need some help with the specifics of your network. One of the wireless security measures is to limit connections to certain MAC addresses, you may need to get to the router to change this.

You could try putting 24.142.48.1 (or 254) into your browser and see if the router pops up. Then just try accessing the menus. Look at the wireless options and see if there are any security measures such as WEP or WPA code/password requirement. If the router is password protected you will soon discover that.

EDIT
> ..I don't have my own wireless at home Sorry I should have read this bit right at the beginning. You won't find any wireless menu if you are at home of course. Do you know of any open wireless services within range of your card that you can connect to?

An old thread but interesting [http://ubuntuforums.org/showthread.php?t=582453]("http://ubuntuforums.org/showthread.php?t=582453")

---

### Post by magtrask on 2010-04-19
There are none from here that I can connect to, but on XP I used to get a list of networks in range belonging to my neighbours (which required passwords of course).  Does Ubuntu have an equivalent display of networks in range when one's wireless card is working?

Beginning Wednesday evening of this week I will be staying at a house with wireless.  So if we can't resolve this now, maybe we can try again then.  I can hook up directly to their wired and search for their wireless.  Although I tried this from there last week which is how I discovered my wireless was not working.

---

### Post by bkratz on 2010-04-19
> **magtrask said:**
> There are none from here that I can connect to, but on XP I used to get a list of networks in range belonging to my neighbours (which required passwords of course).  Does Ubuntu have an equivalent display of networks in range when one's wireless card is working?

Beginning Wednesday evening of this week I will be staying at a house with wireless.  So if we can't resolve this now, maybe we can try again then.  I can hook up directly to their wired and search for their wireless.  Although I tried this from there last week which is how I discovered my wireless was not working.

Yes,

```
sudo iwlist scan
```

---

### Post by bwallum on 2010-04-19
I'm in, just keep to the same thread, if it's ok with you bkratz, I'll let you lead with it and comment in if something can be usefully added.

As far as I can tell the card is being detected by the machine and appears serviceable. It may still need a driver but it definitely needs a wireless network to be able to detect and trigger a connection. If a driver is required then it would be useful to link by wired connection at first in order to download the driver.

See you later, Bob

---

### Post by bkratz on 2010-04-19
> **bwallum said:**
> I'm in, just keep to the same thread, if it's ok with you bkratz, I'll let you lead with it and comment in if something can be usefully added.

As far as I can tell the card is being detected by the machine and appears serviceable. It may still need a driver but it definitely needs a wireless network to be able to detect and trigger a connection. If a driver is required then it would be useful to link by wired connection at first in order to download the driver.

See you later, Bob

From the module listing it appears that it is probably a device with a ralink chipset, but since it doesn't show up anywhere, it makes it hard to even make a plan.  Anyway, I appreciate any help given since I am running out of ideas.  I agree since it says it is managed, something must be doing it, but it doesn't even list the driver used.  Maybe you are right and it will associate with an A/P without knowing what we are doing! I hope.

---

### Post by magtrask on 2010-04-21
Hi there again, I'm in a house now connected to the wire, and they do have wireless.  I'll check back periodically until I hear from one of you.

Hi.  I redid our whole thread thus far to see if anything has changed.  The very last command now shows the network called "100 acre wood" I'm sitting beside.  This is a VERY rural place, so there is no security or password required.

```
mag@MSIubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:D1:34:01:87
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"100 acre wood"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000017ae6f8c9
                    Extra: Last beacon: 716ms ago
                    IE: Unknown: 000D313030206163726520776F6F64
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 32080C1218243048606C
```

(sorry about the faces, haven't found the buttton to turn them off yet)

Although it now shows up, still not connecting.  When I left click my Network Connections icon up top, it shows 'Wireless Networks: Device not ready".
Does the list I just posted contain everything I need to create new connection manually via Network Connections>Edit Connections>Wireless>Add?  
Thanks in advance.

---

### Post by bkratz on 2010-04-21
> **magtrask said:**
> Although it now shows up, still not connecting.  When I left click my Network Connections icon up top, it shows 'Wireless Networks: Device not ready".
Does the list I just posted contain everything I need to create new connection manually via Network Connections>Edit Connections>Wireless>Add?  
Thanks in advance.

The smiley thing is under additional options. Is the network ESSID:"100 acre wood" the one you want to connect to? It is not encrypted and everything in the last listing seems ok. Have you right clicked on the network icon and told it to setup (added (edited)) a connection for it?  You should just have to name the connection--set the SSID to "100 acre wood" (you will need the "s" since there are spaces) and go. It still bothers me that we don't see the name anywhere, but if it works, what the heck!

---

### Post by magtrask on 2010-04-21
> **bkratz said:**
> The smiley thing is under additional options. Is the network ESSID:"100 acre wood" the one you want to connect to? It is not encrypted and everything in the last listing seems ok. Have you right clicked on the network icon and told it to setup (added (edited)) a connection for it?  You should just have to name the connection--set the SSID to "100 acre wood" (you will need the "s" since there are spaces) and go. It still bothers me that we don't see the name anywhere, but if it works, what the heck!

We have success!  I am sending this wireless.  I was trying to add "100 acre wood" and thought I needed to fill in all the parameters. But, no, just the name and it did the rest automatically.
Thanks so much.  

So when I am somewhere else, like the library tomorrow, do I find the available networks via terminal> sudo iwlist scan
and add whatever SSID name it gives me?
Thanks for all the help, I'm now a happy camper again.

---

### Post by bkratz on 2010-04-21
Sure am glad to hear that!  That method would certainly work and it would tell you if it was encrypted also. Anyway, did you see the disable smiley faces checkbox, and if you would please mark the thread as solved under the thread tools, it just might help someone else sometime.

---

### Post by magtrask on 2010-04-21
I think the smiley problem comes from using quick reply, there are fewer options.  I think I may have figured it out finally, reply using "reply with quote".
Cheers, Mag.

---

### Post by bwallum on 2010-04-22
Well done magtrask, pleased you got your wireless up.:):P:guitar:

---

### Post by magtrask on 2010-04-22
Hi guys, I decided to keep this in the same thread although it turns out to be poorly titled since RTL8111/8168B is my ethernet and not my wireless.

Anyhow, I'm returning to unsolved status.  Today is a new day, and I was hoping the wireless would be easier to set up this second time since we know it can.  Unfortunately it wasn't that easy.

Like you mentioned in an earlier post bwallum:

> **bwallum said:**
> I have a similar problem with a pc wireless card by Belkin using the RTL8185L chip. Lucid just does not see it. Not got to the bottom of it yet so can only offer empathy at the moment...  

Under networking>wireless it claimed "device not ready".
So I retraced a few steps from yesterday.  When I started here I got an error:
```
mag@MSIubuntu:~$ sudo iwconfig wlan0 txpower 15
[sudo] password for mag: 
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.
```I don't really know what most of these codes mean, so maybe there is a logical place to begin? I randomly picked "sudo iwconfig wlan0 txpower 15". Random isn't a good method apparently.
So I started at the very beginning of our thread, and it did come up at finding 100 acre wood.  But that is a long set of instructions:

```
sudo lshw -C network
lspci | grep Wireless
lspci -nn
rfkill list
lsusb
sudo iwconfig
lsmod
sudo iwconfig wlan0 txpower 15
lsmod | grep -e rt2 -e rt3
sudo update-pciids
lspci | grep Network
lspci -nn
sudo ifconfig wlan0 down && sudo ifconfig wlan0 up
ifconfig
sudo iwlist scan
```Here where I know the SSID name already its not such a big deal.  I can just Disable Wireless, delete the entry under Network Connections, rename it, and Enable.  
But at the library or on the road where I may not know the name there must be an easier way than that long string of commands.

I do know one more piece of the puzzle than at the beginning.  My driver is called "rt73usb".  I know this from Connection Information now that I am on.  It turns out this did come up for us in one of our earlier searches but we didn't recognize it.  Does knowing this change anything?  
```
mag@MSIubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
ecb                     2524  2 
joydev                 10240  0 
**rt73usb                26336  0 **
crc_itu_t               1852  1 rt73usb
rt2x00usb              11548  1 rt73usb
rt2x00lib              29756  2 rt73usb,rt2x00usb
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
pcmcia                 36808  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  2 rt2x00lib,sdhci
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                56500  0 
serio_raw               5280  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
usbhid                 38208  0 
ieee1394               86596  1 ohci1394
r8169                  32064  0 
mii                     5212  1 r8169
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
```If this is the best we can do I will mark it solved again.  But if there are any new ideas on how to make it simpler, please let me know.
Thanks again, Mag.

---

### Post by bkratz on 2010-04-22
> **magtrask said:**
> Hi guys, I decided to keep this in the same thread although it turns out to be poorly titled since RTL8111/8168B is my ethernet and not my wireless.

Anyhow, I'm returning to unsolved status.  Today is a new day, and I was hoping the wireless would be easier to set up this second time since we know it can.  Unfortunately it wasn't that easy.

```

sudo iwconfig wlan0 txpower 15
sudo update-pciids
sudo ifconfig wlan0 down && sudo ifconfig wlan0 up


```If this is the best we can do I will mark it solved again.  But if there are any new ideas on how to make it simpler, please let me know.
Thanks again, Mag.

Sorry it was temporary.  I removed the commands that you had listed which were just informative only and left the commands which actually caused something to happen. The second one does update a list, but should have no other effect, but I left it anyway.
The first command should set the tx power (it originally said 0)--it could be too big so try changing the 15 to a 10, it may still error out, if so try a smaller number, but if you see no difference in response (the error message) go back to 15.  The last command should take the wireless interface up and down or down and up, which seems the more likely. 

I will go back through the thread and see if I can find anything and make a new list of what we should look at.

---

### Post by bkratz on 2010-04-22
It might be interesting to see the output of the following command:

dmesg | grep rt73

Hopefully, there might be something useful there.

---

### Post by magtrask on 2010-04-22
Hi bkratz.  Well that shorter list of commands seems like much less of a hassle.
As for the dmesg | grep rt73

mag@MSIubuntu:~$ dmesg | grep rt73
[   19.655128] Registered led device: rt73usb-phy0::radio
[   19.655148] Registered led device: rt73usb-phy0::assoc
[   19.655168] Registered led device: rt73usb-phy0::quality
[   19.655751] usbcore: registered new interface driver rt73usb
[   19.668783] rt73usb 1-6:1.0: firmware: requesting rt73.bin
[   19.729120] input: rt73usb as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input10

---

### Post by bwallum on 2010-04-22
What I found invariably works (if there is a network available and the wireless driver is installed) is simply to delete the wireless connections and force Network Manager to search for a network. It takes time so allow a minute or two. That is how you found a network earlier (no wireless entries when you started).

A cleaner way would be to add an enforced scan to Edit Connections but I don't know if the devs are doing anything along those lines.

Once you have the driver installed (which you have) then it is good for all connections.

---

### Post by bkratz on 2010-04-22
> **magtrask said:**
> Hi bkratz.  Well that shorter list of commands seems like much less of a hassle.
As for the dmesg | grep rt73

mag@MSIubuntu:~$ dmesg | grep rt73
[   19.655128] Registered led device: rt73usb-phy0::radio
[   19.655148] Registered led device: rt73usb-phy0::assoc
[   19.655168] Registered led device: rt73usb-phy0::quality
[   19.655751] usbcore: registered new interface driver rt73usb
[   19.668783] rt73usb 1-6:1.0: firmware: requesting rt73.bin
[   19.729120] input: rt73usb as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input10

Well, that all looks normal-- how about the following:

```
rfkill list
sudo lshw -C network
sudo iwconfig
sudo iwlist wlan0 scan

```

We will find something wrong, somewhere!

---

### Post by magtrask on 2010-04-22
> **bkratz said:**
> Well, that all looks normal-- how about the following:

```
rfkill list
sudo lshw -C network
sudo iwconfig
sudo iwlist wlan0 scan

```We will find something wrong, somewhere!
```
mag@MSIubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
mag@MSIubuntu:~$ sudo lshw -C network
[sudo] password for mag: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:eb:51:99
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:d800(size=256) memory:fe2ff000-fe2fffff memory:fe2c0000-fe2dffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:9d:85:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.11 multicast=yes wireless=IEEE 802.11bg
mag@MSIubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"100 acre wood"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:D1:34:01:87   
          Bit Rate=54 Mb/s   Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mag@MSIubuntu:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Device or resource busy
```I notice a different answer from "rfkill list". What does that command mean?  And for future reference, can you suggest the best source for learning terminal commands?

---

### Post by bkratz on 2010-04-22
Just for reference these are pretty good

[http://gd.tuwien.ac.at/linuxcommand.org/tlcl.php](http://gd.tuwien.ac.at/linuxcommand.org/tlcl.php)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Downloadable!

---

### Post by bkratz on 2010-04-22
> **magtrask said:**
> ```
mag@MSIubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

mag@MSIubuntu:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Device or resource busy
```I notice a different answer from "rfkill list". What does that command mean?  And for future reference, can you suggest the best source for learning terminal commands?

Well it is my understanding that the soft block is referencing some software issue that is preventing it from working, while the hard block refers to the switch itself ( but I could be wrong, often am!) Both look good, and it seems we have corected the tx power also. I don't understand why the scan of wlan0 acted like it did though. Have to do some looking up.

---

### Post by magtrask on 2010-04-23
> **bwallum said:**
> What I found invariably works (if there is a network available and the wireless driver is installed) is simply to delete the wireless connections and force Network Manager to search for a network. It takes time so allow a minute or two. That is how you found a network earlier (no wireless entries when you started).

A cleaner way would be to add an enforced scan to Edit Connections but I don't know if the devs are doing anything along those lines.

Once you have the driver installed (which you have) then it is good for all connections.
Whenever I restart the computer, I have to go through a process to get the wireless running.  The fastest method I've found is at terminal:
```
mag@MSIubuntu:~$ sudo iwconfig wlan0 txpower 15
[sudo] password for mag: 
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.
mag@MSIubuntu:~$ sudo update-pciids
mag@MSIubuntu:~$ sudo ifconfig wlan0 down && sudo ifconfig wlan0 up

```followed by Network Manager icon:
Disable wireless
Disable networking
Enable Networking
Enable wireless
It will then begin to establish the connection, without delete and re-adding name via Edit Connections.  That method seems not to work for me.

---

### Post by magtrask on 2010-12-09
The fix had been working for months, and I had streamlined it to only typing:
mag@MSIubuntu:~$ sudo iwconfig wlan0 txpower 5
[FONT=monospace][FONT=Verdana]followed by [/FONT][/FONT]by Network Manager icon:
Disable wireless
Disable networking
Enable Networking
Enable wireless

Two weeks ago I upgraded to 10.10 and am again without wireless.  I tried the previous fix, but I have no option via the Network Manager icon to enable or disable wireless.  It is there in light shade grey, un-selectable.

I also convinced my partner to get rid of windows, and installed 10.10 on our home ASUS desktop, and we lost wireless there that had worked on XP.  I began another thread about this in October, but so far no response.  (If you'd really like to help you could check threads started by me and work on the ASUS too!)

Any ideas?
Thank you.

---

### Post by magtrask on 2010-12-11
Would just like to report that the problem is solved.  Bkratz offered the suggestion to try:
 
 [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)
 
 The response:

>    The following Terminal output (that you sent us) shows the issue that your wireless card is
having:
    "
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
    0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
    [main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
"
    So your wireless card is currently disabled by a hardware switch, a
special key combination (Fn-F2, etc...), by incorrect BIOS settings for
wireless, or a combination of these factors...
    There might also be a BIOS option that allows you to have the wireless
functionality controlled "By application"
    Search for the "by application" option in the BIOS and select it (if
possible)....
    Also run the following 2 Terminal commands to try to change the rfkill
state of your wireless chipset:
    rfkill unblock all
    sudo rfkill unblock all
    Then retest wireless.
 Nothing in the BIOS, rfkill no effect, but then I tried every key on the  keyboard. Yes, there is a key for enable/disable wireless.  So after  all this time, the laptop driver was not the problem, it was a button  specific to the MSI Megabook M662. So the problem all along was my unfamiliarity with my own machine. There is a bizarre key in the upper right that I'd never tried.

Thanks Bkratz for your effort.

---

