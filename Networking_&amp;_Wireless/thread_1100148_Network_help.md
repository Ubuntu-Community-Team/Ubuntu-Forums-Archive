---
title: "Network help"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by MaynardHSH on 2009-03-18
First of im gonna say that i've been using ubuntu hardy for about 4 months or so, and so far i really didnt have any problems with ny network, usually network manager used to work fine till a week ago, i've been trying some of the things that i found here on ubuntuforums but none of them helped me, or maybe im not really used to work with codes and whatnot, so bottom line is that i have no internet :P, hope anyone can help me to work this out cuze i really dont want to reformat my pc and i dont think that helps a lot since the thing is to work around the problem and not to ignore it i know what to do if this ever happens again, anyways here are some of the things that i think are useful in order to know the problem.

```
~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```
```
~$ lsmod
Module                  Size  Used by
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ipv6                  267908  12 
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
af_packet              23812  6 
snd_via82xx            31128  2 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  4 
via_ircc               27796  0 
snd_cmipci             39296  3 
snd_ac97_codec        102180  1 snd_via82xx
snd_pcsp               13600  1 
irda                  203068  1 via_ircc
gameport               16008  2 snd_via82xx,snd_cmipci
ac97_bus                3200  1 snd_ac97_codec
crc_ccitt               3072  1 irda
i2c_viapro              9876  0 
snd_pcm_oss            51232  0 
snd_mixer_oss          18432  1 snd_pcm_oss
snd_pcm                86660  5 snd_via82xx,snd_cmipci,snd_ac97_codec,snd_pcsp,snd_pcm_oss
snd_page_alloc         12168  2 snd_via82xx,snd_pcm
snd_opl3_lib           13952  1 snd_cmipci
snd_hwdep              10884  1 snd_opl3_lib
snd_mpu401_uart         9984  2 snd_via82xx,snd_cmipci
snd_seq_dummy           4996  0 
snd_seq_oss            35968  0 
i2c_core               24832  1 i2c_viapro
snd_seq_midi           10784  0 
snd_rawmidi            27168  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                58320  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  9232  0 
snd_timer              25988  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    64708  30 snd_via82xx,snd_cmipci,snd_ac97_codec,snd_pcsp,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
via_agp                11136  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  1 via_agp
soundcore               8800  1 snd
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
pata_via               13316  2 
floppy                 59588  0 
pata_acpi               8320  0 
via_rhine              26632  0 
mii                     6400  1 via_rhine
libata                159600  3 ata_generic,pata_via,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```
tried to reset my eth0 iface with
```
$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 6501
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0a:e6:cd:ae:44
Sending on   LPF/eth0/00:0a:e6:cd:ae:44
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67

```
```
$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0a:e6:cd:ae:44
Sending on   LPF/eth0/00:0a:e6:cd:ae:44
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

also tried 
```
$ sudo dmesg | grep eth0
[   27.848179] eth0: VIA Rhine II at 0xdffffe00, 00:0a:e6:cd:ae:44, IRQ 11.
[   27.848893] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[   39.601395] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   57.129305] eth0: no IPv6 routers present
[  288.426491] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x4 length 0 status 00000600!
[  288.426500] eth0: Oversized Ethernet frame df9fe040 vs df9fe040.
[  288.426504] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x5 length 0 status 00000600!
[  288.426507] eth0: Oversized Ethernet frame df9fe050 vs df9fe050.
[  294.021082] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  304.262135] eth0: no IPv6 routers present
[  372.822410] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  383.382656] eth0: no IPv6 routers present
[  425.190668] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  435.864791] eth0: no IPv6 routers present
[  536.464241] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  546.463413] eth0: no IPv6 routers present
[  646.419889] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  656.726602] eth0: no IPv6 routers present
[  919.680839] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  930.286180] eth0: no IPv6 routers present
[ 1005.031088] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1015.624053] eth0: no IPv6 routers present
[ 1191.890937] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x1 length 0 status 00000600!
[ 1191.890947] eth0: Oversized Ethernet frame ded0b010 vs ded0b010.

```

also 
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:cd:ae:44  
          inet6 addr: fe80::20a:e6ff:fecd:ae44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:2324
          TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:900 (900.0 B)  TX bytes:68280 (66.6 KB)
          Interrupt:11 Base address:0xae00 

eth0:avahi Link encap:Ethernet  HWaddr 00:0a:e6:cd:ae:44  
          inet addr:169.254.8.74  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xae00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140139 (136.8 KB)  TX bytes:140139 (136.8 KB)

```

dhclient

```
$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0a:e6:cd:ae:44
Sending on   LPF/eth0/00:0a:e6:cd:ae:44
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

also i think if this one helps but i do noticed something strange today when i tried all of the above

```
$ sudo dmesg | grep eth0
[   40.965759] eth0: VIA Rhine II at 0xdffffe00, 00:0a:e6:cd:ae:44, IRQ 11.
[   40.966473] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[   52.902983] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   70.107189] eth0: no IPv6 routers present
[ 1780.147165] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1790.724933] eth0: no IPv6 routers present
[ 2167.056279] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2178.025749] eth0: no IPv6 routers present
[ 2412.265550] eth0: link down
[ 2444.636749] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2470.099187] eth0: link down
[ 2472.482510] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2583.386012] eth0: link down
[ 2615.757217] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2635.668331] eth0: link down
[ 2982.013177] eth0: link down
[ 2982.013600] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

dunno if this helps but still im posting it 

Network Settings-Host

127.0.0.1 localhost
127.0.1.1 badass.motherfucka
::1       ip6-localhost  ip6-loopback
fe00::0   ip6-localnet
ff00::0   ip6-mcastprefix
ff02::1   ip6-allnodes
ff02::2   ip6-allrouters
ff02::3   ip6-allhosts

....i think thats all, or at least all i can think of, so i hope anyone can help i do can connect through usb since my modem its eth/usb compatible but i want to learn more cuze i really like ubuntu :)

thx in advance.


Edit: ok nvm i cant connect through usb either for some reason :/...soooo help anyone?

---

