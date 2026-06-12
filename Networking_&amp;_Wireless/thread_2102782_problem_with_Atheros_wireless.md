---
title: "problem with Atheros wireless"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by MadsRC on 2013-01-08
I have an old, OLD!, Fujitsu Siemens Amilo 1720 that works fairly well with Xubuntu 12.10 out-of-the-box.

Problem is that the wireless sometimes goes crazy...

It will tell me that there's a hardware block (From RFKill), even though the laptop doesn't have a switch for it.

The solution is, wierd as it is, to do this:
```
sudo vi /etc/modprobe.d/blacklists.conf
add "blacklist acer-wmi"
reboot
```

Then it works, but every once in a while it stops working, and I have will have to remove the blacklist entry from above, reboot, add blacklist again and then reboot again.

This is lshw's info about the netcard:
```
-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap
_list
             configuration: driver=pcieport
             resources: irq:40 memory:c0100000-c01fffff
           *-network
                description: Wireless interface
                product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:c0:a8:c8:b0:e6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.5.0-21-generic firmware=N/A ip=10.128.83.234 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:c0100000-c010ffff

```

The driver I'm using is ath5k.

rfkill list gives me:
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

When it stops working, it adds "acer-wireless" to rfkill?

This is the eaxct problem, from which I found solution to reinsert the blacklist once it goes crazy: [https://bugs.launchpad.net/ubuntu/+bug/864456](https://bugs.launchpad.net/ubuntu/+bug/864456)

Does anybody have an idea for a permanent solution?

---

### Post by Us3r Unfriendly on 2013-01-08
What's the output of:  lsmod

---

### Post by MadsRC on 2013-01-08
The output is:
```
Module                  Size  Used by
ip6table_filter        12711  0 
ip6_tables             17969  1 ip6table_filter
iptable_filter         12706  0 
ip_tables              17791  1 iptable_filter
x_tables               21898  4 ip6table_filter,ip6_tables,iptable_filter,ip_tables
arc4                   12473  2 
coretemp               13168  0 
joydev                 17161  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    63493  1 
snd_hda_intel          32515  4 
snd_hda_codec         111547  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
microcode              18209  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17905  0 
sm_common              16737  1 r852
nand                   49496  2 r852,sm_common
r592                   17707  0 
ath5k                 135205  0 
nand_ids                8547  1 nand
mtd                    38602  2 sm_common,nand
nand_bch               13003  1 nand
bch                    17199  1 nand_bch
snd                    61991  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                84843  0 
ath                    19187  1 ath5k
memstick               15842  1 r592
nand_ecc               13070  1 nand
mac80211              461161  1 ath5k
soundcore              14599  1 snd
serio_raw              13031  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
i2c_piix4              12983  0 
cfg80211              175375  3 ath5k,ath,mac80211
rfcomm                 37276  4 
bnep                   17707  2 
parport_pc             31968  0 
bluetooth             183228  10 rfcomm,bnep
ppdev                  12817  0 
binfmt_misc            17260  1 
ext2                   67204  1 
mac_hid                13037  0 
shpchp                 32189  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
xts                    12723  1 
gf128mul               14503  1 xts
dm_crypt               22402  1 
firewire_ohci          35521  0 
radeon                820734  2 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
ttm                    75534  1 radeon
drm_kms_helper         47303  1 radeon
drm                   238768  4 radeon,ttm,drm_kms_helper
8139too                23071  0 
8139cp                 26619  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_atiixp            12999  2 
video                  18847  0 
i2c_algo_bit           13197  1 radeon
wmi                    18590  0 
ati_agp                13177  0
```

---

### Post by Us3r Unfriendly on 2013-01-08
What card are you using?

---

### Post by MadsRC on 2013-01-10
I'm using an AR242x / AR542x Wireless Network Adapter as stated by "lshw". I don't know if it is the AR242x or AR542x adapter though...

The problem persist, lately it's been more frequent.

Right now my rfkill list looks like:
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

Here's my ifconfig (as of right now)
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:10.129.52.93  Bcast:10.129.53.255  Mask:255.255.254.0
          inet6 addr: fe80::20a:e4ff:febd:4395/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8090660 (8.0 MB)  TX bytes:1520964 (1.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:636004 (636.0 KB)  TX bytes:636004 (636.0 KB)
```
Notice that wlan0 is missing...

Here's my iwconfig (as of right now):
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.
```

Putting my wireless card in monitor mode shows:
```
wlan0		Atheros 	ath5k - [phy0]SIOCSIFFLAGS: Operation not possible due to RF-kill

				(monitor mode enabled on mon0)

```

So phy0 is the interface, and I guess the reason that "Network Manager" cannont find any wireless networks is for the same reason that I cannot put said card in monitor mode. Due to rfkill...

and no, I have tried to disable the rfkill.

There is a physical button on the machine for wireless, which works under windows, but I've never gotten it to work under linux.

---

