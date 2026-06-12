---
title: "Dlink DWL-650+ Airplus causes freeze"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by drew212 on 2009-07-29
It shows on ubuntu wiki that the Dlink DWL-650+ should be supported, but everytime i plug the card in it causes ubuntu to freeze. Here is the pastebin for the kernel from card insertion to ubuntu restart: [http://paste.ubuntu.com/235360/](http://paste.ubuntu.com/235360/)

---

### Post by karabelf on 2009-08-09
I am also experiencing the exact same problem.  So if anyone has a solution to this conflict it would be greatly appreciated.

I am only new to Ubuntu and Linux in general so if there is anything required to help solve this problem.  Please let me know including beginners instructions on how to do this.

---

### Post by crep4ever on 2009-08-10
Same here. DWL-G650 D-Link AirPlus Wifi card (pcmcia) on an Acer Laptop (Aspire 1622LM). The freeze happens most of the time just before the connection is established (after a few seconds of the "connecting.." phase).

I am experiencing this problem since the release of jaunty (fresh install).

$cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

$lsusbBus 

001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)
02:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:04.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


$sudo lshw -C network

  *-network               
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:16
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:56:d1:1b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:13:46:97:ff:c8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.192 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 02:87:f1:d3:0d:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


$lsmod

Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
sbp2                   30476  0 
lp                     17156  0 
arc4                    9856  2 
joydev                 18368  0 
ecb                    10752  2 
ath5k                 107520  0 
mac80211              217592  1 ath5k
cfg80211               38288  2 ath5k,mac80211
pcmcia                 44748  0 
snd_atiixp_modem       20360  0 
snd_atiixp             24204  4 
snd_ac97_codec        112292  2 snd_atiixp_modem,snd_atiixp
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  2 snd_pcm_oss
snd_pcm                83076  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
soundcore              15200  2 snd
video                  25360  0 
yenta_socket           32396  3 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
ppdev                  15620  0 
led_class              12036  1 ath5k
serio_raw              13444  0 
snd_page_alloc         16904  3 snd_atiixp_modem,snd_atiixp,snd_pcm
output                 11008  1 video
shpchp                 40212  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
irda                  197308  0 
i2c_piix4              18448  0 
ati_agp                14988  1 
agpgart                42696  2 drm,ati_agp
crc_ccitt              10112  1 irda
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

$iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Livebox-F0F0"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:16:CE:55:9D:68   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=62/100  Signal level:-51 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

$ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:56:d1:1b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:16 Adresse de base:0xa000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1486 erreurs:0 :0 overruns:0 frame:0
          TX packets:1486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:74380 (74.3 KB) Octets transmis:74380 (74.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:46:97:ff:c8  
          inet adr:192.168.1.192  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::213:46ff:fe97:ffc8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:16638 erreurs:0 :0 overruns:0 frame:0
          TX packets:14724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:17594141 (17.5 MB) Octets transmis:2504072 (2.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-46-97-FF-C8-66-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)


$nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:0A:E4:56:D1:1B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto Livebox-F0F0] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k_pci
  State:             connected
  Default:           yes
  HW Address:        00:13:46:97:FF:C8

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Livebox-F0F0:   Infra, 00:16:CE:55:9D:68, Freq 2442 MHz, Rate 54 Mb/s, Strength 65 WEP
    default:         Infra, 00:17:9A:44:CE:8F, Freq 2437 MHz, Rate 54 Mb/s, Strength 79

  IPv4 Settings:
    Address:         192.168.1.192
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


$uname -r -m 

2.6.28-14-generic i686

---

### Post by crep4ever on 2009-10-19
up. Is there anything I could do ?

---

### Post by claypole on 2009-12-13
Anyone manage to fix this? Would love to get this card working.

---

### Post by teklife on 2012-04-24
having the same problem. i don't know what airplus is, but i managed to get the card sorta working after installing drivers with ndiswrapper. 

the wireless networks now show up, and am able to connect, then the computer freezes shortly thereafter. when i remove the card, the computer instantly un-freezes. any advice?

---

### Post by lisati on 2012-04-24
Thread closed.

@teklife: a lot can change in three years. Please start a new thread, and, if necessary, refer back to this one.

---

