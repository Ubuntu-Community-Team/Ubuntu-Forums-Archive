---
title: "Lucid (and Precise) networking broken"
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by CatKiller on 2013-08-23
I've just upgraded a computer from Hardy (where the network was fine) to Lucid (where the network is non-existent). This makes the next step up to Precise somewhat problematic.

I've tried DHCP and static addresses and, remembering that Network Manager was something of a pain in the **** in that era, I've tried purging Network Manager and specifying the connection directly in interfaces. No joy.

ifconfig appears to be showing the interface as up, but the only traffic is on the loopback device. I'm stumped.

---

### Post by praseodym on 2013-08-24
Please show:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
rfkill list
sudo iwlist scan
```

---

### Post by CatKiller on 2013-08-24
You know there's no Internet connection on that computer, right?

I'll have a look at those files when I'm back there next week, but I'm unlikely to post them from my phone.

---

### Post by CatKiller on 2013-08-24
I can tell you straight off that the kernel is whatever you get with a fresh upgrade to Lucid, USB is irrelevant because it's not a USB device - I believe it's on-board on an nForce chipset, but I'll check - and although hardware support is always a potential suspect it was working fine in Hardy so a regression of that scale should have been fixed in the significant time between Lucid's release and now.

---

### Post by praseodym on 2013-08-24
You can copy the outputs into a text file and paste the content herein.

---

### Post by CatKiller on 2013-08-27
Thanks to your pointers, I re-purged NetworkManager, blew resolv.conf away and replaced it with entries to Google's DNS servers, deleted the default route and rebooted. All seems to be working OK now. Thank you.

---

### Post by CatKiller on 2013-08-27
I've now done the upgrade to Precise and got the same problem. The trick didn't work this time.

Boot is taking a long time, so I checked dmesg and saw messages about "eth1: link is not ready." That's probably relevant.

---

### Post by praseodym on 2013-08-27
Please show the outputs from #3

---

### Post by CatKiller on 2013-08-27
I'll take in a USB cable to that end tomorrow. The bits that aren't relevant still aren't relevant. I did establish today that it's using forcedeth that has caused other people problems. I'll also take in a spare ethernet cable, just in case.

---

### Post by CatKiller on 2013-08-28
lspci -nnk | grep -iA2 net

```
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
	Kernel driver in use: forcedeth
```

lsmod

```
Module                  Size  Used by
dm_crypt               22528  0 
snd_hda_codec_via      46198  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
nvidia              10286823  40 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
rfcomm                 38139  0 
bnep                   17830  2 
snd_seq_midi           13132  0 
ppdev                  12849  0 
bluetooth             158447  10 rfcomm,bnep
snd_rawmidi            25424  1 snd_seq_midi
binfmt_misc            17292  1 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13027  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
k10temp                12990  0 
parport_pc             32114  1 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    62218  15 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
i2c_nforce2            12906  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
sata_nv                23360  3 
forcedeth              58096  0 
pata_amd               13750  0 
```

ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:25:22:5d:94:84  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2555 (2.5 KB)  TX bytes:2555 (2.5 KB)
```

cat /etc/network/interfaces 

```
auto lo
iface lo inet loopback

auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
	address	192.168.1.1
	netmask	255.255.255.0
	gateway	192.168.1.254
```

cat /etc/resolv.conf 

```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# OpenDNS
nameserver	208.67.222.222

# Google DNS
nameserver 	8.8.8.8
nameserver 	8.8.4.4
```

route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

Potentially significant bit of dmesg.

```
[  264.269375] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  886.908217] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[  886.908633] forcedeth 0000:00:07.0: eth0: no link during initialization
[  886.910035] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by CatKiller on 2013-08-28
OK, I've managed to get it running by giving it a ```
sudo ethtool -s eth0 autoneg off speed 100 duplex full
```

I have no idea why that worked, or if it will survive a reboot.

EDIT: It didn't survive a reboot. That line did bring it up again, though.

---

### Post by CatKiller on 2013-08-28
modprobing gets me ```
[  332.973830] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[  332.973851] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[  332.973856] forcedeth 0000:00:07.0: setting latency timer to 64
[  333.496073] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:25:22:5d:94:84
[  333.496086] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[  333.523813] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[  333.523999] forcedeth 0000:00:07.0: eth0: no link during initialization
[  333.525632] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

and the ethtool line gets me an extra

```
[  409.460707] forcedeth 0000:00:07.0: eth0: link up
[  409.461017] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```

Sometimes it takes two goes, which is annoying in terms of just adding that line to some bootup script somewhere.

---

### Post by praseodym on 2013-08-28
Is the network-manager installed? If yes, change "false" to "true" in /etc/NetworkManager/NetworkManager.conf, otherwise the NM can not handle the manual configuration. Or remove the manual congif from the interfaces again and reboot.

The forcedeth driver needs additional module parameters:
```

echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
sudo modprobe -rfv forcedeth
sudo modprobe -v forcedeth
```

---

### Post by CatKiller on 2013-08-28
Already tried those; didn't help. Didn't seem to hurt, either.

At the moment, Network Manager is not installed. There seems to be something hinky with the autoneg code in forcedeth, though. Currently there's a massive delay on boot as it tries and fails to set up networking and then the ethtool command gets run by rc.local. It's a passable but distinctly sub-optimal solution and there's every chance that it will occasionally not work, which will get me panicked calls from my employer.

---

### Post by CatKiller on 2013-08-29
I've tried all the options I can find with modinfo, and nothing works other than turning off autoneg. Which you can't do as a module option, as far as I can see.

---

