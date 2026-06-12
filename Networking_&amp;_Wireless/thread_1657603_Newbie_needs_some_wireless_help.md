---
title: "Newbie needs some wireless help"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by ubuntoad on 2011-01-01
Howdy folks. 
Running ubuntu 10.10 here, brand new install/machine.USB wireless based on a realtek chipset. I spent a few days trying ndiswrapper, and now have the native driver up and running. I can see the network(s) but can't connect.
If I encrypt the network, i get a bad password error from wicd network manager (All encypt. methods- Weps, WPA etc)
If I open my wireless up with no encryption, i receive a "can't obtain IP" error.

I'm at a loss. 
Thanks.

---

### Post by ubuntoad on 2011-01-01
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root 
```

```
wlan0     Link encap:Ethernet  HWaddr 00:21:79:c2:a2:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:3956 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9382 (9.3 KB)  TX bytes:0 (0.0 B)

```

```
wlan0     802.11b/g  Mode:Managed  Frequency=2.417 GHz  
          Access Point: Not-Associated   Bit Rate:55 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
Module                  Size  Used by
arc4                    1165  0 
binfmt_misc             6599  1 
fglrx                2252898  33 
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_via      51755  1 
snd_hda_intel          22203  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
r8192s_usb            287308  0 
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
psmouse                59033  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
eeprom_93cx6            1345  1 r8192s_usb
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
agpgart                32075  1 fglrx
snd                    49038  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 29982  0 
soundcore                880  1 snd
asus_atk0110           11423  0 
joydev                  8767  0 
i2c_piix4               8795  0 
serio_raw               4022  0 
k10temp                 2607  0 
parport_pc             26378  1 
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
ndiswrapper           184352  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
pata_atiixp             3288  0 
ahci                   19198  2 
r8169                  36777  0 
mii                     4425  1 r8169
libahci                21728  1 ahci

```

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 20:cf:30:5e:61:bb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:41 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febf0000-febfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:21:79:c2:a2:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
```

---

