---
title: "Atheros AR5001X  disabled in 10.10"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by kcbiker on 2011-08-10
My old Winbook laptop had good wifi connection under Ubuntu 9.10 but shows 'disabled' under Ubuntu 10.04 and 10.10.  At least under 10.10 it came up with working video (had to mess with GRUB on 10.04 before video would work).  I have an onboard wi-fi card that has never worked well with any Linux as far as I know but the Atheros PCMCIA card worked solid under Karmic (9.10).  Here is some diag. info.  

sudo lshw -c network

  *-network:0 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:7b:9e:c2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:e0001000-e0001fff
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 8b
       serial: 00:40:d0:64:0c:72
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.147 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:c000(size=256) memory:e0000800-e00008ff
  *-network DISABLED
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:11:6b:61:f3:c8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-30-generic firmware=N/A latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:5 memory:e4000000-e400ffff

lspci

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:02.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
01:04.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b
01:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lsmod

Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
arc4                    1165  2 
ath5k                 130083  0 
mac80211              231927  1 ath5k
ath                     8153  1 ath5k
led_class               2633  1 ath5k
snd_intel8x0           25664  2 
snd_ac97_codec         99227  1 snd_intel8x0
i915                  295819  3 
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
joydev                  8767  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30136  1 i915
pcmcia                 35973  0 
snd_seq_midi_event      6047  1 snd_seq_midi
ipw2200               136715  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
libipw                 39808  1 ipw2200
drm                   168092  2 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144822  5 ath5k,mac80211,ath,ipw2200,libipw
yenta_socket           21518  0 
intel_agp              26566  2 i915
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    49102  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
lib80211                5058  2 ipw2200,libipw
i2c_algo_bit            5168  1 i915
shpchp                 29886  0 
serio_raw               4022  0 
soundcore                880  1 snd
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
firewire_ohci          21234  0 
via_rhine              19038  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 via_rhine

iwconfig

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:40:d0:64:0c:72  
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe64:c72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4575709 (4.5 MB)  TX bytes:726519 (726.5 KB)
          Interrupt:11 Base address:0x8800 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:7b:9e:c2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xe000 Memory:e0001000-e0001fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:6b:61:f3:c8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Hope someone can help on this.

Thanks

---

### Post by chili555 on 2011-08-10
> 0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]
1: phy1: Wireless LAN
Soft blocked: no
Hard blocked: no
Often, the hardware switch blocks all wireless, not just the on-board. If you move the switch to activate wireless and unload the ipw2200 module, does the Atheros work?```
sudo rmmod -f ipw2200
```My Intel 2200 worked great except it didn't do WPA. If you want to stop it, I'd suggest you blacklist the driver module instead of using the switch.

---

### Post by kcbiker on 2011-08-10
Chilli555 is the MAN!    I did the sudo rmod -f ipw2200 and the little green light came on for the first time since I moved off version 9.10.  Thanks so much.  Will I need to run this at each power up or will it stay in place?

:D

---

### Post by chili555 on 2011-08-10
It will stay in place after you do:```
sudo su
echo "blacklist ipw2200" >> /etc/modprobe.d/blacklist.conf
exit
```Would you please use thread tools at the top and Mark Solved?

---

### Post by kcbiker on 2011-08-10
Fantastic!   Wi-Fi came up alive after the restart.  Great job Chili555.  THANKS  :D

---

