---
title: "Can't connect to access point after setting up..."
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by rainbowagent7 on 2010-01-03
Hi I'm a newborn to Linux/Ubuntu, but am loving it so far. I have a firm grasp of the basics, and follow instructions very well, however, this is my first time setting up a wireless access point (on any OS), so please bear with me for my incompetence on the subject.

Here's my problem: I have a Sonicwall SOHO TZW that I am trying to set up as a wireless access point. I changed my computers IP address to match the subnet of the Sonicwall and was able to log into the interface to setup. Everything went fine, I setup the Sonicwall with PPPoE (which is what my ISP uses), and enabled the DHCP server. I exited setup, reset my IP for DHCP, and tried to access the net through The sonicwall with my wireless PCI card (also set to DHCP), with no luck. 

After many hours of checking and re-checking settings, I finally reset my IP to be able to access the Sonicwall interface, which told me "you have not specified a DNS server address", which I thought was done through DHCP:confused:. I'm confused, any help would be greatly appreciated as I'm sure It's probably related to my TCP/IP settings somehow???

## you guys/gals are awesome, I've seen a lot of great help here, thanks in advance!

```
 $ lspci
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
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
``````

$ iwconfig
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


``````

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:95:b0:a9:bf  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd400 

eth1      Link encap:Ethernet  HWaddr 00:0c:41:e9:7f:d0  
          inet addr:192.168.1.46  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fee9:7fd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1097 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:902557 (902.5 KB)  TX bytes:184096 (184.0 KB)
          Interrupt:12 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10115 (10.1 KB)  TX bytes:10115 (10.1 KB)

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

``````

lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
rt2500pci              15356  0 
rt2x00pci               7900  1 rt2500pci
rt2x00lib              29756  2 rt2500pci,rt2x00pci
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
mac80211              181076  2 rt2x00pci,rt2x00lib
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ns558                   5404  0 
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
ppdev                   6688  0 
cfg80211               93052  2 rt2x00lib,mac80211
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          6920  6 snd_seq_dummy,snd_opl3_lib,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usblp                  12636  0 
eeprom_93cx6            1916  1 rt2500pci
gameport               11368  2 ns558
parport_pc             31940  1 
shpchp                 32272  0 
i2c_sis630              6024  0 
i2c_sis96x              3904  0 
snd                    59204  21 snd_intel8x0,snd_ac97_codec,snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_intel8x0,snd_wss_lib,snd_pcm
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
tulip                  48320  0 
sis900                 19932  0 
mii                     5212  1 sis900
sis_agp                 6972  1 
agpgart                34988  1 sis_agp
floppy                 54916  0 
usbhid                 38208  0 



```## here are some command line tidbits I thought anyone helping me could use, if you need anything else ## just say the word, also sorry if I didn't wrap the text right, I'm as new to posting on forums as I am to ## installing an access point!

---

