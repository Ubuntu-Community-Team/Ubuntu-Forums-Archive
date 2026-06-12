---
title: "Wifi lost ubuntu 10.04 / broadcom 4818"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by spamix on 2011-02-11
hi,

I'lve lost my wifi after an update 8.04 to 10.04. Before this update, wifi was perfectly working. I'm behind a router ( Freebox ) , wifi is working on my other XP PC in // . 
I tried to change static/dchp, WEP, WAP, but i still don't have wifi with ubuntu10.04. XP still working fine in any case.
I spent almost 1 week trying to load differents drivers and config but the without succes. I've never been able to load the STA driver. Now, i try to remove the ssb module assuming it may be the cause. but it re appear after each reboot.
  
here is my config.

> [INDENT]uname -a
Linux  pc-moi_linux 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC  2011 i686 GNU/Linux
[/INDENT]lshw -C network 

> [INDENT]  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:dc:13:75
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=8139too  driverversion=0.9.28 duplex=full ip=192.168.0.46 latency=64 link=yes  maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:5000(size=256) memory:c8209400-c82094ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:c8206000-c8207fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:14:a5:19:36:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
[/INDENT][INDENT] 
lsmod 


> 
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
joydev                  8740  0 
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
pcmcia                 30784  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                676897  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   163524  0 
ttm                    49943  1 radeon
mac80211              205402  1 b43
drm_kms_helper         29329  1 radeon
snd                     54180  15  snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  1 
tifm_7xx1               3690  0 
rsrc_nonstatic         10015  1 yenta_socket
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
sbp2                   19448  0 
video                  17375  0 
output                  1871  1 video
intel_agp              24375  0 
tifm_core               6045  1 tifm_7xx1
cfg80211              126528  2 b43,mac80211
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               2864  2 b43,sdhci
drm                   162409  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
agpgart                31724  3 ttm,intel_agp,drm
lp                      7028  0 
parport                32635  2 ppdev,lp
8139too                18545  0 
usbhid                 36110  0 
hid                    67064  1 usbhid
ohci1394               26950  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
ssb                    38934  1 b43                                 <======= here
ieee1394               81181  2 sbp2,ohci1394

/etc/network/interfaces 

> 
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 198.162.1.1
netmask 255.255.255.0
 
 auto eth1
iface eth1 inet dhcp                   ( static or dynamic gives same result )
# iface wlan0 inet dhcp
# address 192.168.0.10
# netmask 255.255.255.0
# network 192.168.0.0
# broadcast 192.168.0.255
gateway 192.168.0.254
# wireless-essid 00:24:D4:AE:16:0E
wireless-essid freebox_sgplnx
wireless-key ABCDEF0123
# key ABCDEF01234
# wireless-rate 24M 
# mtu 1400
#wireless-rate 54M
iwxonfig 

> 
eth1      IEEE 802.11bg  ESSID:"freebox_sgplnx"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

ifconfig
 
> 
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:dc:13:75  
       inet adr:192.168.0.46  Bcast:192.168.0.255  Masque:255.255.255.0
                 adr inet6: 2a01:e35:8a64:f2a0:2c0:9fff:fedc:1375/64 Scope:Global
                 adr inet6: fe80::2c0:9fff:fedc:1375/64 Scope:Lien
                 UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
                 Packets reçus:4975 erreurs:0 :0 overruns:0 frame:0
                 TX packets:4849 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 lg file transmission:1000 
                 Octets reçus:2938391 (2.9 MB) Octets transmis:657669 (657.6 KB)
                 Interruption:20 Adresse de base:0x5000 

eth1      Link encap:Ethernet  HWaddr 00:14:a5:19:36:91  
                 UP BROADCAST MULTICAST  MTU:1500  Metric:1
                 Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
                 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 lg file transmission:1000 
       Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

eth1:avahi Link encap:Ethernet  HWaddr 00:14:a5:19:36:91  
                 inet adr:169.254.5.87  Bcast:169.254.255.255  Masque:255.255.0.0
                 UP BROADCAST MULTICAST  MTU:1500  Metric:1
       lo        Link encap:Boucle locale  
          
inet adr:127.0.0.1  Masque:255.0.0.0 
       adr inet6: ::1/128 Scope:Hôte
                 UP LOOPBACK RUNNING  MTU:16436  Metric:1
                 Packets reçus:22 erreurs:0 :0 overruns:0 frame:0
                TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 lg file transmission:0 
                Octets reçus:1476 (1.4 KB) Octets transmis:1476 (1.4 KB)

[/INDENT]I'm using wicd. here is his log file /var/log/wicd:[INDENT]> 
.../...
2011/02/11 09:06:55 :: iwconfig eth1
2011/02/11 09:06:55 :: attempting to set hostname with dhclient
2011/02/11 09:06:55 :: using dhcpcd or another supported client may work better
2011/02/11 09:06:55 :: /sbin/dhclient -r eth1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Listening on LPF/eth1/00:14:a5:19:36:91
Sending on   LPF/eth1/00:14:a5:19:36:91
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.254 port 67
send_packet: Network is unreachable                          [COLOR=Red]<***** ??????[/COLOR]
send_packet: please consult README file regarding broadcast address.
2011/02/11 09:06:55 :: ifconfig eth1 0.0.0.0 
2011/02/11 09:06:55 :: /sbin/ip route flush dev eth1
2011/02/11 09:06:55 :: ifconfig eth1 down
2011/02/11 09:06:56 :: ifconfig eth1 up
2011/02/11 09:06:56 :: wpa_cli -i eth1 terminate
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory                     [COLOR=Red]<*********** ??????[/COLOR]
2011/02/11 09:06:56 :: attempting to set hostname with dhclient
2011/02/11 09:06:56 :: using dhcpcd or another supported client may work better
2011/02/11 09:06:56 :: /sbin/dhclient -r eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
..../....  an so on

I've removed all b43 drivers, blacklisted ssb in /etc/modeprobe.d/blacklist.conf

```

.../...
blacklist amd76x_edac
blacklist b43
blacklist ssb

```I made 

```

rmmod b43 to be sure
rmmod ssb
depmod

```but after each reboot, ssb is back again, with used set to 0.

Except hanging me, i don't know what to do. I'd like to remove this bloody ssb. Do you think it's the cause of my problem ?  any clue ?


thanks, regards.
[/INDENT]

---

