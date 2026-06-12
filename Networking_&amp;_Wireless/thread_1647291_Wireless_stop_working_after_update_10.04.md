---
title: "Wireless stop working after update 10.04"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by Zwendel on 2010-12-17
Hi everybody, yesterday I let the update manager install a whole bunch of updates for my 10.04 install on my MSI Notebook ER710. My wireless was just working peachy until then (with the madwifi drivers), but after the update, no more... I checked the madwifi, tried a new make, but nothing worked.

So, after reading somewhere that 10.10 had less issues with wireless I decided to upgrade to 10.10 in the hope that that would solve my problem.

Well, partly it did, as in, according to my system I've got a wireless again and this morning even, it was able to see wireless networks! Unfortunately I couldn't connect to mine, although the key was correct. At some point I lost the ability to see wireless networks again. I tried wicd too, but no luck their either. It recognizes my card but can't see any networks.

Any help would be appreciated, here is all the info:

**Machine Brand and Model (PC/Laptop):** MSI ER710

**lspci**
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:21:85:4d:82:78  
          inet addr:192.168.2.108  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe4d:8278/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7608720 (7.6 MB)  TX bytes:796091 (796.0 KB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5198 (5.1 KB)  TX bytes:5198 (5.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:cf:e2:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
[B]
iwconfig[/B]
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
**lsmod**
```
Module                  Size  Used by
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_atihdmi     2411  1 
joydev                  8735  0 
arc4                    1165  2 
snd_hda_codec_realtek   217971  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
radeon                827837  3 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
ttm                    56633  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 35973  0 
ath5k                 130083  0 
drm_kms_helper         30168  1 radeon
mac80211              231541  1 ath5k
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ati_agp                 5202  0 
drm                   168054  5 radeon,ttm,drm_kms_helper
ath                     8153  1 ath5k
btusb                  10969  2 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              144470  3 ath5k,mac80211,ath
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
i2c_algo_bit            5168  1 radeon
soundcore                880  1 snd
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                59033  0 
shpchp                 29886  0 
agpgart                32011  3 ttm,ati_agp,drm
serio_raw               4022  0 
k8temp                  3228  0 
i2c_piix4               8635  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
video                  18712  0 
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
firewire_ohci          21106  0 
r8169                  36489  0 
firewire_core          46643  1 firewire_ohci
ahci                   19013  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
led_class               2633  2 ath5k,sdhci
libahci                21667  3 ahci
pata_atiixp             3288  0 
crc_itu_t               1383  1 firewire_core
mii                     4425  1 r8169
```

**dmesg (I guess this one is useful? It's very long but keeps repeating this:)**
```
[ 2209.365408] net_ratelimit: 4 callbacks suppressed
[ 2209.365421] ath5k phy0: gain calibration timeout (2412MHz)
[ 2263.732835] ath5k phy0: gain calibration timeout (2412MHz)
[ 2264.118022] ath5k phy0: gain calibration timeout (2417MHz)
[ 2264.501942] ath5k phy0: gain calibration timeout (2422MHz)
[ 2264.886044] ath5k phy0: gain calibration timeout (2427MHz)
[ 2265.278348] ath5k phy0: gain calibration timeout (2432MHz)
[ 2265.670140] ath5k phy0: gain calibration timeout (2437MHz)
[ 2266.053989] ath5k phy0: gain calibration timeout (2442MHz)
[ 2266.437940] ath5k phy0: gain calibration timeout (2447MHz)
[ 2266.830135] ath5k phy0: gain calibration timeout (2452MHz)
[ 2268.898145] net_ratelimit: 4 callbacks suppressed
[ 2268.898152] ath5k phy0: gain calibration timeout (2484MHz)
[ 2269.353455] ath5k phy0: gain calibration timeout (2412MHz)
[ 2323.732123] ath5k phy0: gain calibration timeout (2412MHz)
[ 2324.115170] ath5k phy0: gain calibration timeout (2417MHz)
[ 2324.498078] ath5k phy0: gain calibration timeout (2422MHz)
```
[B]
sudo lshw -C network[/B]
```
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:cf:e2:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fd7f0000-fd7fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:21:85:4d:82:78
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.108 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:c800(size=256) memory:fe2ff000-fe2fffff memory:fe2c0000-fe2dffff
```

**iwlist scan**
```
wlan0     No scan results
```

**lsb_release -d**
> Ubuntu 10.10

**uname -mr**
```
2.6.35-23-generic i686
```

**sudo /etc/init.d/networking restart**
```
 * Reconfiguring network interfaces...                                                          Ignoring unknown interface eth0=eth0.
                                                                                         [ OK ]
```

---

### Post by Zwendel on 2010-12-17
Ok, managed to get the madwifi drivers back up and running thanks to these detailed instructions:
[URL="http://art.ubuntuforums.org/showthread.php?t=1163380"]
art.ubuntuforums.org/showthread.php?t=1163380[/URL]

---

