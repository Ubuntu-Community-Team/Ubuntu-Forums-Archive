---
title: "Aspire one 9.04 wireless (still) not working"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by swift826 on 2009-05-12
Hello,

The wireless on my Acer is currently broken. After upgrading to 9.04, I blacklisted acer-wmi and used ath5k with no problems for a week. Today, it just stopped working for no apparent reason. I've read through the page at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne), and tried using ath_pci, ath_5k, and madwifi-hal. None of these work. I've also tried using an older kernel. 

Any help/ideas would be appreciated!

Here's some system info:

Acer Aspire One, running 9.04 kernel 2.6.28-11.

lspci:
```
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

ifconfig:
```

ath0      Link encap:Ethernet  HWaddr 00:23:4e:2f:07:73  
          inet6 addr: fe80::223:4eff:fe2f:773/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:23:8b:1f:9b:90  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe1f:9b90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:299118 (299.1 KB)  TX bytes:36640 (36.6 KB)
          Interrupt:251 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-23-4E-2F-07-73-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:13340 (13.3 KB)
          Interrupt:18 

```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.447GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s  Tx-Power:16 dBm  Sensitivity=1/1
          Retry:off  RTS thr:off  Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0

pan0      no wireless extensions.

```

dmesg | grep ath[0_]:
```

[   16.696833] ath_hal: module license 'Proprietary' taints kernel.
[   16.776192] ath_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.776231] ath_pci 0000:03:00.0: setting latency timer to 64
[   17.275821] MadWifi: ath_attach: Switching rfkill capability off.
[   17.547623] ath_pci: wifi0: Atheros 5424/2424: mem=0x55200000, irq=18
[   56.888085] ath0: no IPv6 routers present

```

lsmod:
```

Module                  Size  Used by
vboxdrv               117544  0 
i915                   65540  2 
drm                    96296  3 i915
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
binfmt_misc            16776  1 
input_polldev          11912  0 
joydev                 18368  0 
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
uvcvideo               63240  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          9344  1 uvcvideo
acer_wmi               24260  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
videodev               41600  1 uvcvideo
psmouse                61972  0 
led_class              12036  1 acer_wmi
pcspkr                 10496  0 
v4l1_compat            21764  2 uvcvideo,videodev
serio_raw              13316  0 
intel_agp              34108  1 
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42696  3 drm,intel_agp
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
video                  25360  0 
output                 11008  1 video
wlan_scan_sta          21376  1 
ath_rate_sample        20608  1 
ath_pci               217784  0 
wlan                  238064  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312160  3 ath_rate_sample,ath_pci
lp                     17156  0 
parport                42220  2 ppdev,lp
r8169                  40836  0 
mii                    13312  1 r8169
raid10                 30336  0 
raid456               134928  0 
async_xor              11392  1 raid456
async_memcpy           10112  1 raid456
async_tx               15184  3 raid456,async_xor,async_memcpy
xor                    24072  2 raid456,async_xor
raid1                  29952  0 
raid0                  15360  0 
multipath              15232  0 
linear                 13312  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Let me know if there's any other info I can provide.

Thanks!

---

### Post by Peter09 on 2009-05-12
Can you provide output of

```
lshw -C network
```

---

### Post by swift826 on 2009-05-12
Here it is.

lshw -C network:
```

  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:1f:9b:90
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.9 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:23:4e:2f:07:73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:ca:c2:54:1a:d3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by Aearenda on 2009-05-12
Are you sure you haven't accidentally turned the hardware off by knocking the wifi toggle switch on the front, under the LEDs?

---

### Post by swift826 on 2009-05-12
Yes, I tried that. It didn't seem to do anything.

---

### Post by SpoonerPS3 on 2009-05-12
I´m having exactly the same problem. It stopped working today for no reason. I have 2 partitions, Xubuntu and Ubuntu and both stopped working today.

---

### Post by Peter09 on 2009-05-13
can you show /etc/network/interfaces

---

### Post by Chiapo on 2009-05-13
{how do I delete my post?}

---

### Post by Peter09 on 2009-05-13
Hi - start a new thread for this one. Otherwise trying to answer two questions at the same time gets confusing.

Start a new thread with the outpust from

```
ifconfig
```

and

```
lshw -C network
```

---

### Post by Chiapo on 2009-05-13
Thanks Peter09 :)

---

### Post by swift826 on 2009-05-13
Here's /etc/network/interfaces:

```

auto lo
iface lo inet loopback

```

---

### Post by Peter09 on 2009-05-13
Have a look at the following forum - and a thread for starter.

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=13627&sid=ee2b3effc0bef619e3d0eabf728a7d53](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=13627&sid=ee2b3effc0bef619e3d0eabf728a7d53)

---

### Post by tdr112 on 2009-06-06
I had the same thing with my Aspire one , I tried the live cd netbook remix, on two different Aspire one's same model and spec , one the wifi work and one it didn't.

After lots of time on google I found this and it has worked for me.

```
sudo gedit /etc/modprobe.d/blacklist

```  
and then add

```
blacklist acer_wmi
```

let me know if it works for you

---

### Post by worldsayshi on 2009-09-11
I'm having trouble with this aswell. Tried blacklisting acer_wmi. This doesn't seem to help.:

dmesg:
```
[   14.765834] ath_hal: module license 'Proprietary' taints kernel.
[   14.770087] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   14.848826] ath_pci: 0.9.4
[   14.848941] ath_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.848983] ath_pci 0000:03:00.0: setting latency timer to 64
[   14.897689] ath_pci 0000:03:00.0: PCI INT A disabled
```

lshw:
```
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:b6:1a:9b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:ff:4c:61:7d:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

lshw doesn't seem to find anything wireless at all..

lsmod:
```
Module                  Size  Used by
binfmt_misc            16776  1 
i915                   67844  3 
drm                    96424  4 i915
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18496  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
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
uvcvideo               63368  0 
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              34108  1 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
psmouse                61972  0 
soundcore              15200  1 snd
video                  25360  0 
pcspkr                 10496  0 
v4l1_compat            21764  2 uvcvideo,videodev
serio_raw              13444  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
agpgart                42696  3 drm,intel_agp
ath_pci                99224  0 
wlan                  210544  1 ath_pci
ath_hal               198864  1 ath_pci
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

lspci:
```
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

Wireless has always been rather unstable but currently it doesn't work at all. I actually had it working perfectly before Jaunty but that was after switching to a non kernel driver, can't remember which one it was.

Using the switch below the leds doesn't seem to work at all. Although I'm not sure. I tend to avoid it as much as possible, the connection being so unstable. :)
It fails to bring it back to life anyway.

---

