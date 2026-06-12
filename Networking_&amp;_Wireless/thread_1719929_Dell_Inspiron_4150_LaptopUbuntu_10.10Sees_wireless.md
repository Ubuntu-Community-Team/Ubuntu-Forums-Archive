---
title: "Dell Inspiron 4150 Laptop/Ubuntu 10.10/Sees wireless router, will not connect"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by Untuned on 2011-04-02
I have Ubuntu 10.10 installed on two other laptops, and the wireless access works without a hitch.  I am not able to get it to work for this computer.  It sees my router, but will not connect.  Here is some information: 

result of lspci:


00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
02:03.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)

Result of ifconfig:

eth2      Link encap:Ethernet  HWaddr 00:08:74:4c:5c:35  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe4c:5c35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4682569 (4.6 MB)  TX bytes:382322 (382.3 KB)
          Interrupt:11 Base address:0x2c00 

eth3      Link encap:Ethernet  HWaddr 00:02:2d:7f:92:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


Result of iwconfig:

lo        no wireless extensions.

eth2      no wireless extensions.

eth3      IEEE 802.11b  ESSID:"Tuned"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Result of lsmod:


Module                  Size  Used by
radeon                828445  1 
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
drm                   168092  3 radeon,ttm,drm_kms_helper
i2c_algo_bit            5168  1 radeon
michael_mic             1744  4 
orinoco_cs              5050  1 
orinoco                64558  1 orinoco_cs
cfg80211              144470  1 orinoco
binfmt_misc             6599  1 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
joydev                  8767  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 35973  1 orinoco_cs
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              26694  1 
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
snd                    49038  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi_aio            1733  0 
dcdbas                  5402  0 
pcmcia_core            14657  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
psmouse                59033  0 
soundcore                880  1 snd
shpchp                 29886  0 
ppdev                   5556  0 
agpgart                32011  3 ttm,drm,intel_agp
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
video                  18712  0 
parport_pc             26058  1 
output                  1883  1 video
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
3c59x                  32011  0 
floppy                 54311  0 
mii                     4425  1 3c59x

Result of sudo lshw -C network:

 *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 78
       serial: 00:08:74:4c:5c:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.104 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth3
       serial: 00:02:2d:7f:92:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.35-24-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b



I know this is a lot of info, but I don't even recognize what the wireless card is, or I would have shortened my thread.  Thank you.

---

### Post by gordintoronto on 2011-04-02
How do you know it sees your router?  Your wireless card did not appear under lspci. Is it a USB unit? (use lsusb) Or try lspcmcia

If the wireless adapter sees your router, then the hardware is fully supported. It's just a matter of getting the encryption type and password correct.

---

### Post by Untuned on 2011-04-02
The computer sees the router, but when I click to connect to it, nothing happens, and it says "Wireless network disconnected".  I do not know what wireless adapter it uses, but it is not usb.  When I typed lspcmcia, the result is:


Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:01.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:01.1)
Socket 2 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:03.0)
Socket 2 Device 0:	[orinoco_cs]		(bus ID: 2.0)


It is not a question of password because I disabled the encryption on the router just to simplify things.

---

### Post by gordintoronto on 2011-04-03
You should have a network manager icon on the top panel, near the right. You can right-click it and select "edit connections." Select the Wireless tab, then Add, and type in the SSID, which should be all lower-case. If you have no encryption, you should be able to "OK" out of there.

---

