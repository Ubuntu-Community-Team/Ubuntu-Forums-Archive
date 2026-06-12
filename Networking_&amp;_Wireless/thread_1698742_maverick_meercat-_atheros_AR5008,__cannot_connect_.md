---
title: "maverick meercat- atheros AR5008,  cannot connect wireless"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by fewjr on 2011-03-02
Hello All,
     I'm sorry for asking for help on this so quickly, but I never got wifi working on Ibex and could never figure it out. I haven't used Ubuntu in a while. I have to put this computer downstairs and it needs wifi for down there for my daughter. I am connected via eth0 right now, upstairs. I just nuked Ibex and legacy Grub and installed Meercat. I am duel booting with WinXP, but want my daughter wants to learn Linux. She is very interested. I am able to see my network, but cannot authenticate with my WEP key. Any help you folks could lend would be greatly appreciated.
             
     Here is some info:
lsb_release -d
Description:	Ubuntu 10.10


uname -mr
2.6.35-27-generic-pae i686



The wireless card I'm using is a Dlink DWA-556 Atheros AR5008



francis@goblin-lanbox:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2)
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:5b:98:d4  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe5b:98d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12061683 (12.0 MB)  TX bytes:992123 (992.1 KB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:5a:bf:0a:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:5b:98:d4  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe5b:98d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12061683 (12.0 MB)  TX bytes:992123 (992.1 KB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:5a:bf:0a:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

francis@goblin-lanbox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"tubescreamer"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


 lsmod
Module                  Size  Used by
aes_i586                7280  230 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
dm_crypt               11385  0 
snd_hda_codec_nvhdmi    13615  1 
snd_hda_codec_realtek   218492  1 
nvidia               9331115  38 
snd_hda_intel          22299  2 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
ir_lirc_codec           3092  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
lirc_dev                9393  1 ir_lirc_codec
ir_sony_decoder         1889  0 
ir_jvc_decoder          1950  0 
ir_rc6_decoder          2334  0 
arc4                    1165  2 
ir_rc5_decoder          1950  0 
ir_nec_decoder          2014  0 
tuner                  20578  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cx8800                 27450  0 
ath9k                  89204  0 
cx88xx                 74544  1 cx8800
ath9k_common            5982  1 ath9k
ath9k_hw              292329  2 ath9k,ath9k_common
i2c_algo_bit            5168  1 cx88xx
ir_common               5167  1 cx88xx
ir_core                14654  8 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx,ir_common
ath                     8153  2 ath9k,ath9k_hw
tveeprom               11178  1 cx88xx
v4l2_common            17329  3 tuner,cx8800,cx88xx
videodev               43098  4 tuner,cx8800,cx88xx,v4l2_common
mac80211              231959  2 ath9k,ath9k_common
v4l1_compat            13359  1 videodev
btcx_risc               3700  2 cx8800,cx88xx
videobuf_dma_sg         9870  2 cx8800,cx88xx
agpgart                32075  1 nvidia
soundcore                880  1 snd
videobuf_core          16907  3 cx8800,cx88xx,videobuf_dma_sg
cfg80211              144694  4 ath9k,ath9k_common,ath,mac80211
i2c_nforce2             5275  0 
shpchp                 29982  0 
lp                      7342  0 
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
led_class               2633  1 ath9k
k8temp                  3228  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
usb_storage            40236  0 
video                  18712  0 
ahci                   19198  2 
output                  1883  1 video
forcedeth              49753  0 
libahci                21792  1 ahci
pata_amd                8746  0 


sudo lshw -C network
[sudo] password for francis: 
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:d0:5b:98:d4
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.106 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1GB/s
       resources: irq:42 memory:fd107000-fd107fff ioport:dc00(size=8) memory:fd108000-fd1080ff memory:fd109000-fd10900f
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:5a:bf:0a:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-27-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fd000000-fd00ffff


 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results



Thank you in advance
fewjr

---

### Post by fewjr on 2011-03-04
Just like to mention I am doing alot of reading, but with work and kids sports I've not figured this out yet. I believe that I have to go with Madwifi drivers, but I think the driver that is installed is already Madwifi. I am confused if I need ath9k or athpci. Please help.

fewjr

---

### Post by fewjr on 2011-03-04
Problem solved. Was set to open instead of shared network. A lot of copy/paste for nothing....except I had time to settle down and think.

fewjr

---

