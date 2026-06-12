---
title: "DlinkDWA-140 range booster connection problem"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by parcdulas on 2012-08-26
Hello,
On an Asus X50RL laptop that the wireless network works ok with windows, under Ubuntu 12.04 although the NM indicates that I am connected to my home network Firefox cannot find the Ubuntu start page nor can Thunderbird find its server. Connection information says speed unknown but otherwise looks normal.

It looks like the wireless USB dongle is on bus 001 at device 003

```

martin@martin-F5RL:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT3072]
martin@martin-F5RL:~$ 


```

But I don't know what the Realtek mass storage device is unless it is part of the wireless dongle. There are no other things plugged into the USB ports.

There is an Atheros wireless card internally in the laptop but it will not work under windows hence the Dlink dongle. It was "blacklisted" in an attempt to get an O2 Mobile dongle to work. I don't know if this is having any effect or how to undo the blacklisting.

```
martin@martin-F5RL:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Device 5a31 (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Atheros Communications Inc. L2 Fast Ethernet (rev a0)
martin@martin-F5RL:~$ 

```

Typing lspci -nn | grep 'wireless brand' responded with nothing.

The ifconfig command gives:

```
martin@martin-F5RL:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:3f:49:3a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:feac0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131224 (131.2 KB)  TX bytes:131224 (131.2 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:bd:b9:7e:76:27  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1ebd:b9ff:fe7e:7627/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:14294 (14.2 KB)

martin@martin-F5RL:~$ 


```

And the iwconfig gives:

```
martin@martin-F5RL:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"mossdale"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 06:4A:14:DF:FC:07   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```

lsmod gives:

```

martin@martin-F5RL:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12663  1 
xt_state               12514  1 
ipt_REJECT             12512  2 
xt_tcpudp              12531  4 
iptable_filter         12706  1 
nf_nat_h323            12749  0 
nf_conntrack_h323      52412  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13553  1 nf_nat_pptp
nf_conntrack_proto_gre    13395  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16921  0 
nf_conntrack_sip       24749  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12595  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
iptable_nat            13016  1 
nf_nat                 24959  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  4 iptable_nat,nf_nat
nf_conntrack           73847  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21974  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
joydev                 17393  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174055  1 
arc4                   12473  2 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
parport_pc             32114  0 
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
rt2800usb              22300  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48858  3 rt2800usb,rt2800lib,rt2x00usb
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              436455  3 rt2800lib,rt2x00usb,rt2x00lib
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178679  2 rt2x00lib,mac80211
snd                    62064  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                72846  0 
serio_raw              13027  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  0 
radeon                733693  3 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
asus_laptop            23693  0 
sparse_keymap          13658  1 asus_laptop
input_polldev          13648  1 asus_laptop
mac_hid                13077  0 
shpchp                 32325  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_atiixp            12999  0 
atl2                   28040  0 
usb_storage            39646  0 
martin@martin-F5RL:~$ 



```

```
martin@martin-F5RL:~$ sudo lshw -C network
[sudo] password for martin: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:fa9f0000-fa9fffff
  *-network
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:3f:49:3a
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 firmware=L2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:feac0000-feafffff memory:feaa0000-feabffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 1c:bd:b9:7e:76:27
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-23-generic-pae firmware=0.29 ip=10.42.0.1 link=yes multicast=yes wireless=IEEE 802.11bgn
martin@martin-F5RL:~$ 


```

```
martin@martin-F5RL:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 06:4A:14:DF:FC:07
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"mossdale"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 3110092ms ago
                    IE: Unknown: 00086D6F737364616C65
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD070050F202000100
          Cell 02 - Address: A0:21:B7:57:4A:31
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"tonybryan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005e7fb85f185
                    Extra: Last beacon: 12280ms ago
                    IE: Unknown: 0009746F6E79627279616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180206F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000

eth0      Interface doesn't support scanning.

martin@martin-F5RL:~$ 


```

Typing iwlist scan with wlan0 responded with "Unknown command 'wlan0' (check iwlist --help)

As I mentioned the version I'm running is:

```

martin@martin-F5RL:~$lsb_release -d 
Ubuntu 12.04 LTS

```

The kernel is:

```

martin@martin-F5RL:~$uname -mr
3.2.0-23-generic-pae i686

```
 
Restarting the network responded with:

```

martin@martin-F5RL:~$ sudo /etc/init.d/networking restart

* Restart is deprecated because it may not enable again some interfaces 

* Reconfiguring network interfaces ...
[OK]

```
I hope some of this output helps find a solution, thanks.

Martin

---

### Post by parcdulas on 2012-11-30
My ISP (virginmedia) upped my speed from 10Mb to 20Mb and sent a new wireless hub (No charge!) As soon as the new hub/modem was installed and working on my desktop (ethernet cable connection) I tried the loptop on wireless and it worked straight away so it seems it was a problem with the wireless hub I was using (LinkSys)

---

