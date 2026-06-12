---
title: "Cannot Connect to Internet Via Built-in Ethernet Port"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by emorydunn on 2011-12-21
Hi, 

I've got a relatively new install of Ubuntu 11.10 that has been running pretty well for a couple weeks. Unfortunately, the wireless cards (yes, I have two) started acting up so I decided to go for the more stable option: a wired connection. This endeavour has not gone well. 

The basic problem is I can't connect to the internet. 

When Ubuntu sets up its "Auto Ethernet" connection it seems to fail while trying to get an IP address. To remedy this I set up a manual connection which got the computer on the network but not online. 

As far as I can tell there is nothing wrong with the hardware. It shows up as eth0 under every terminal command under the sun (I'll post the output once I put the wireless card back in). I've been endlessly searching for the past several hours and have found nothing that actually has helped solve anything. 

Finally, some specs on the computer: 
It's running Ubuntu 11.10 on a BioStar NF4ST-A9. It's got an nVidia nForce ethernet controller using the Forcedeth driver.

ifconfig: 
```
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:df:77:ed  
          inet6 addr: fe80::2e0:4cff:fedf:77ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:133132 (133.1 KB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20347 (20.3 KB)  TX bytes:20347 (20.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:08:54:ae:05:7c  
          inet addr:10.0.2.46  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:feae:57c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3070871 (3.0 MB)  TX bytes:345285 (345.2 KB)

```

sudo ethtool eth0
```
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 17
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes

```

lspci
```


00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Network controller: Ralink corp. RT2800 802.11n PCI
05:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 (PCIE)]
05:00.1 Display controller: ATI Technologies Inc R430 [Radeon X800] (PCIE) (Secondary)

```

Please let me know if there are any other commands you would like the output from.


Things I have tried: 


> **praseodym said:**
> Hi,

NVIDIA-Gigabit cards often need additional module parameters:

```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```

and reboot.
This didn't help.

---

### Post by Thylex on 2011-12-21
Is the config in NM set to use DHCP? If yes, do you have a DHCP server up and running somewhere?

The output of lsmod and the section from dmesg relating to the NIC from the boot sequence would help too.

---

### Post by emorydunn on 2011-12-21
> **Thylex said:**
> Is the config in NM set to use DHCP? If yes, do you have a DHCP server up and running somewhere?

The output of lsmod and the section from dmesg relating to the NIC from the boot sequence would help too.

Yes, it is set to use DHCP in both my manual configuration and the automatic configuration. And yes, the computer is plugged directly into an Apple Airport that is set up to use DHCP. I've checked to connection by plugging my laptop in and it works fine. 

And let me get those for you. Is there a way to limit the dmesg command to just the information you're looking for? I'll post the info I find that looks relevant, but I'm not sure what the NIC is. 


lsmod
```
Module                  Size  Used by
vesafb                 13809  1 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
edac_core              53746  0 
serio_raw              13166  0 
k8temp                 13057  0 
edac_mce_amd           23709  0 
arc4                   12529  2 
rt2800pci              18715  0 
rt2800lib              54538  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              462092  3 rt2800lib,rt2x00pci,rt2x00lib
snd_intel8x0           38401  2 
snd_ac97_codec        134826  1 snd_intel8x0
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96714  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
cfg80211              199587  2 rt2x00lib,mac80211
snd_seq_midi_event     14899  1 snd_seq_midi
parport_pc             36962  1 
eeprom_93cx6           12725  1 rt2800pci
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
binfmt_misc            17540  1 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_intel8x0,snd_pcm
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
forcedeth              67563  0 
sata_nv                32305  2 
pata_amd               14121  0 
floppy                 70365  0 

```

dmesg
```

[    1.172496] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.172718] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    1.172724] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.696907] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x3f1 @ 17, addr 00:e0:4c:df:77:ed
[    1.696911] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[   19.320548] forcedeth 0000:00:0a.0: eth0: no link during initialization

```
The last time I ran dmesg there were a few lines about eth0 that don't seem to be there anymore.

---

### Post by emorydunn on 2011-12-21
Sorry for the double post, but I figured it would help break up the information. 

I noticed the ethernet cable was unplugged when I ran the commands in my last post, so I plugged it in and ran dmesg again and it only output this. lsmod doesn't appear to have changed.  

dmesg
```

[ 1033.642346] forcedeth 0000:00:0a.0: eth0: link up
[ 1033.642871] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1044.096020] eth0: no IPv6 routers present

```

---

