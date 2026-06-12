---
title: "I need help setting up my wireless access point !!!"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by rainbowagent7 on 2010-01-13
Thanx in advance to anyone who helps me. I'm a new convert to Ubuntu, and I can say I'll probably be a lifer !!! anyways, my fiance @ I will be in school soon and desperately need wireless. She is 8 months pregnant and ready to pop! I want to get things set up to make it as easy as possible for her.
   With that said I'll make this short & sweet: I have a Sonicwall access point, which I am able to set up through the interface, but after that I am unable to achieve a connection through my wireless card. I have a good understanding of everything involved, but really have no hands on experience when it comes to networking. I can give some info that might help, and if you need more just specify what:


```

lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV15BR [GeForce2 Ultra, Bladerunner] (rev a4)



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:95:b0:a9:bf  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd400 

eth1      Link encap:Ethernet  HWaddr 00:0c:41:e9:7f:d0  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fee9:7fd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11040233 (11.0 MB)  TX bytes:1844704 (1.8 MB)
          Interrupt:11 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:f3:dc:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-66-F3-DC-AE-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




lsmod
Module                  Size  Used by
nls_utf8                1568  1 
udf                    80900  1 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
ipt_REJECT              2812  1 
ipt_LOG                 5344  1 
xt_limit                2176  2 
xt_tcpudp               2780  7 
xt_state                1820  6 
ipt_addrtype            2204  4 
ip6table_filter         3164  1 
ip6_tables             13004  1 ip6table_filter
nf_nat_irc              2012  0 
nf_conntrack_irc        4992  1 nf_nat_irc
nf_nat_ftp              2652  0 
nf_nat                 17808  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      13352  8 nf_nat
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
nf_conntrack_ftp        6880  1 nf_nat_ftp
nf_conntrack           67608  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
arc4                    1660  2 
iptable_filter          3100  1 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
ip_tables              11692  1 iptable_filter
x_tables               16544  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
ppdev                   6688  0 
ns558                   5404  0 
rt2500pci              15356  0 
rt2x00pci               7900  1 rt2500pci
rt2x00lib              29756  2 rt2500pci,rt2x00pci
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00pci,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
eeprom_93cx6            1916  1 rt2500pci
snd_wavefront          37332  0 
snd_cs4236             29620  0 
snd_wss_lib            26012  2 snd_wavefront,snd_cs4236
snd_opl3_lib           10396  2 snd_wavefront,snd_cs4236
snd_hwdep               7200  2 snd_wavefront,snd_opl3_lib
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_intel8x0,snd_ac97_codec,snd_cs4236,snd_wss_lib,snd_pcm_oss
snd_mpu401              7016  0 
snd_mpu401_uart         6940  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_page_alloc          9156  3 snd_intel8x0,snd_wss_lib,snd_pcm
snd_seq_dummy           2656  0 
i2c_sis96x              3904  0 
i2c_sis630              6024  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  21 snd_intel8x0,snd_ac97_codec,snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
gameport               11368  2 ns558
shpchp                 32272  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
tulip                  48320  0 
sis900                 19932  0 
mii                     5212  1 sis900
floppy                 54916  0 
sis_agp                 6972  1 
agpgart                34988  1 sis_agp
usbhid                 38208  0 

```


   Also, I should have mentioned that @ the interface for the Sonicwall it said that "no DNS server had been specified", but I set it up for DHCP, and I thought my ISP is using PPPoE (which I also thought used DHCP). I'm confused, but like I said, I'm a new convert to Ubuntu, and a noob to networking alltogether, so please bear with me.

---

### Post by shredder12 on 2010-01-13
Well, it seems that you are able to identify the wireless network and since you haven't got any IP address for wlan0 you are unable to connect.

So, are you able to see the network and what error do you get when you try to connect?

---

