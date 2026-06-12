---
title: "Cisco aironet 350/Ubuntu 9.10/hp pavilion ze1250"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by YeeP on 2009-11-21
I have run all commands requested in this thread:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

My wireless card does not seem to be seeing anything as far as wireless networks. Furthermore I dont think that Ubuntu even sees it. Here are all of the results from the other thread.

```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)

 lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

 lspci -nn | grep 'Bireless Brand' (no response)

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:0b:5a:68  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe0b:5a68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26978 errors:2 dropped:0 overruns:2 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58441012 (58.4 MB)  TX bytes:2506615 (2.5 MB)
          Interrupt:11 Base address:0xe000 

eth2      Link encap:Ethernet  HWaddr 00:0f:f8:4e:61:63  
          inet6 addr: fe80::20f:f8ff:fe4e:6163/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:202 (202.0 B)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-F8-4E-61-63-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:202 (202.0 B)
          Interrupt:3 Base address:0x100 


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-115 dBm  Noise level=0 dBm
          Rx invalid nwid:4  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-115 dBm  Noise level=0 dBm
          Rx invalid nwid:4  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0


iwconfig wifi0
wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-115 dBm  Noise level=0 dBm
          Rx invalid nwid:4  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0


 lsmod
Module                  Size  Used by
isofs                  31620  0 
udf                    80900  1 
crc_itu_t               1852  1 udf
savage                 30620  2 
drm                   159584  3 savage
binfmt_misc             8356  1 
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
airo_cs                 4252  1 
airo                   72924  1 airo_cs
snd_via82xx            23576  2 
gameport               11368  1 snd_via82xx
snd_mpu401_uart         6940  1 snd_via82xx
snd_seq_dummy           2656  0 
snd_via82xx_modem      11204  5 
snd_ac97_codec        101216  2 snd_via82xx,snd_via82xx_modem
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
pcmcia                 36808  1 airo_cs
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  6 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
snd_seq_oss            28576  0 
ip_tables              11692  1 iptable_filter
sbp2                   22888  0 
snd_seq_midi            6432  0 
yenta_socket           24200  3 
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
joydev                 10272  0 
x_tables               16544  1 ip_tables
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
via_ircc               24016  0 
rsrc_nonstatic         11644  1 yenta_socket
lp                      8964  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vt8231                 14952  0 
snd_timer              22276  2 snd_pcm,snd_seq
irda                  189564  1 via_ircc
ppdev                   6688  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 32272  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_viapro              7312  0 
psmouse                56180  0 
snd                    59204  24 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             31940  1 
crc_ccitt               1852  1 irda
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_via82xx,snd_via82xx_modem,snd_pcm
parport                35340  3 lp,ppdev,parport_pc
serio_raw               5280  0 
via_rhine              22212  0 
mii                     5212  1 via_rhine
video                  19380  0 
output                  2780  1 video
ohci1394               29900  0 
ieee1394               86596  2 sbp2,ohci1394
via_agp                 7932  1 
agpgart                34988  2 drm,via_agp


lsmod | grep "wlan_module_name" (no reponse)

dmesg
airo(eth2): cmd:103 status:7f03 rsp0:0 rsp1:ff10 rsp2:c0f0  (a bunch of these)

sudo lshw -C network
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 51
       serial: 00:c0:9f:0b:5a:68
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.2 latency=16 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:e800(size=256) memory:f0000000-f00000ff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth2
       serial: 00:0f:f8:4e:61:63
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      No scan results

wifi0     No scan results




lsb_release -d
Description:	Ubuntu 9.10

 uname -mr
2.6.31-14-generic i686

udo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                              Ignoring unknown interface eth0=eth0.



```

Any help would be much appreciated.

Thank you,
Ryan

---

### Post by YeeP on 2009-11-23
BTT, if anyone can help I would really appreciate it. I am lost at this point and tired of using my wife's laptop with winblows. :mad:

---

