---
title: "acer aspire 5100 internet woes...."
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by jon31592 on 2009-12-05
ok guys, obviously im new here, and to ubuntu and linux in general. im a previous windows user (acer aspire 1500) and needed something diffrent and ubuntu 9.10 was free and looked simple and intresting and all and so i made the switch. but when i did the first thing i tryed to do was get online, this was easyer said than done. all the talk of madwifi and build essental and ndiswrapper and ndisgtk confused me to no end. im all for learning stuff about ubuntu (on my computer, im on my bros now and he dont like it) so i think i should be good after i get the internet working. can you guys please help me out?

---

### Post by uncaspi on 2009-12-05
Do you see the network icon right to the top in panel?
Troubleshooting:
Open a terminal window. Application>Accessories>terminal
sudo lshw , to see if you have the wireless card or wired card present on the bus.
sudo /sbin/ifconfig   to look at the interfaces and see if they got an ip address.
if not type sudo dhclient eth0   if you want card 0 to connect.
Se if the card now got an ip address sudo /sbin/ifconfig
Try to reach the outside world if you are connected by typing ping google.com
If not try to ping your router i.e ping 192.168.0.1 or ping 192.168.1.1
If not type netstat -r to se if you got the right gateway to the router
i.e.  Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

which shows my default route to the router via card eth0
If you not have the default route you must add it if you have the router address by sudo /sbin/route add default gw 192.168.1.1 eth0   in my case.
So we got to take it from there

---

### Post by drpjkurian on 2009-12-06
> **jon31592 said:**
> ok guys, obviously im new here, and to ubuntu and linux in general. im a previous windows user (acer aspire 1500) and needed something diffrent and ubuntu 9.10 was free and looked simple and intresting and all and so i made the switch. but when i did the first thing i tryed to do was get online, this was easyer said than done. all the talk of madwifi and build essental and ndiswrapper and ndisgtk confused me to no end. im all for learning stuff about ubuntu (on my computer, im on my bros now and he dont like it) so i think i should be good after i get the internet working. can you guys please help me out?

Hi Jon
Welcome to Ubuntu forums
Please give a try to my thread if your wireless card is Atheros.
The URl is [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

All the best
Dr kurian

---

### Post by jon31592 on 2009-12-06
yeah i see the icon, but im not connected
when i started i did 
sudo dhclient wlan0 
instead of eth0, but i did do etho after i realized the mistake. 
idk if that made a diff or not
i got all the way to the pings before i was havin some troubble
 
when i ping [www.google.com]("http://www.google.com") i get
ping: unknown host [www.google.com]("http://www.google.com")
 
and when i ping the router i get 
connect: Network is unreachable
 
and then when  type netstat -r i get
destination gateway genmask flags mss window irtt iface
link-local    *        255.255.0.0  u      0      0        0  wlan0
link-local    *        255.255.0.0  u      0      0        0  eth0
 
knowing me i prolly did something wrong...

---

### Post by carcar1 on 2009-12-06
My acer aspire 5100 works perfectly????  ITs right next to me minus that wubi dies down when new kernel comes along.

---

### Post by uncaspi on 2009-12-06
You must add default route to your router as I mentioned above in my first reply.

---

### Post by jon31592 on 2009-12-06
ok  so i went back and typed in 
sudo /sbin/route gw 192.168.0.1 wlan0
and i get somethin like this
 
usage: route [-nNvee] [-FC] [<AF>]          list kernal routing tables
          route [-v] [-FC] {add|del|flush} ...  modify routing table for AF
 
          route {-h|--help} [<AF>]                detailed usage syntax for specified AF
          route {-v|--version}                       desplay version/author and exit
 
           -v,  --verbose                be verbose
           -n,  --numeric                dont resolve names
           -e,  --extend                  display other/more information
           -f,  --fib                         display Forwarding Information Base (default)
           -c,  --cache                    display routing cache instead of FIB
 
  <AF>=Use '-A <af>' or '--<af>'; default: inet
  List of possible address families (which support routing):
     inet (DARPA Internet) inet6 (IPv6) ax25 (AMPR AX.25)
     netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP)
     x25 (CCITT X.25)
 
 
 
and if i 
sudo /sbin/route add default gw 192.168.0.1 wlan0
i get 
SIOCADDRT: no such process
 
and if i 
sudo /sbin/route add default gw 192.168.0.1wlan0
i get
192.168.0.1wlan0: unknown host
 
 
 
idk maby i just dont get it. i prolly doing it all wrong.

---

### Post by northd_tech on 2009-12-06
Hi Jon.

Can you post the results here when you run these commands in a terminal window?

```
sudo lshw -C network

lspci

lsusb

ifconfig

iwconfig

lsmod

netstat -v
```

That should tell us a bit about the hardware and your modules.

---

### Post by jon31592 on 2009-12-06
I type 
sudo lshw -C network
I get

*-network:0 
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
bus info: pci@0000:06:01.0
logical name: eth0
version: 10
serial: 00:1e:ec:56:f6:dc
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
resources: irq:21 ioport:a000(size=256) memory:b0210000-b02100ff
*-network:1
description: Wireless interface
product: AR2413 802.11bg NIC
vendor: Atheros Communications Inc.
physical id: 2
bus info: pci@0000:06:02.0
logical name: wmaster0
version: 01
serial: 00:19:7d:1d:e3:ac
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
resources: irq:22 memory:b0200000-b020ffff
@
I type 
lspci
I get
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
I type 
lsusb
I get 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
@
I type 
ifconfig
I get
eth0 Link encap:Ethernet HWaddr 00:1e:ec:56:f6:dc 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 Base address:0xa000 
@
@
eth0:avahi Link encap:Ethernet HWaddr 00:1e:ec:56:f6:dc 
inet addr:169.254.12.29 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:21 Base address:0xa000 
@
@
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
@
@
wlan0 Link encap:Ethernet HWaddr 00:19:7d:1d:e3:ac 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
@
@
wmaster0 Link encap:UNSPEC HWaddr 00-19-7D-1D-E3-AC-00-00-00-00-00-00-00-00-00-00 
UP RUNNING MTU:0 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
@
@
I type
iwconfig
I get 
lo no wireless extensions.
@
@
eth0 no wireless extensions.
@
@
wmaster0 no wireless extensions.
@
@
wlan0 IEEE 802.11bg ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
@
@
I type 
lsmod
I get 
Module Size Used by
nls_iso8859_1 3740 0 
nls_cp437 5372 0 
vfat 10716 0 
fat 51452 1 vfat
binfmt_misc 8356 1 
ppdev 6688 0 
iptable_filter 3100 0 
pcmcia 36808 0 
snd_hda_codec_realtek 203328 1 
ip_tables 11692 1 iptable_filter
x_tables 16544 1 ip_tables
snd_hda_intel 26920 2 
sdhci_pci 7100 0 
yenta_socket 24200 1 
snd_hda_codec 75708 2 snd_hda_codec_realtek,snd_hda_intel
arc4 1660 2 
sdhci 17472 1 sdhci_pci
rsrc_nonstatic 11644 1 yenta_socket
snd_hwdep 7200 1 snd_hda_codec
acer_wmi 15936 0 
pcmcia_core 35792 3 pcmcia,yenta_socket,rsrc_nonstatic
ecb 2524 2 
snd_pcm_oss 37920 0 
snd_mixer_oss 16028 1 snd_pcm_oss
snd_pcm 75296 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
lp 8964 0 
parport 35340 2 ppdev,lp
i2c_piix4 9932 0 
ath5k 124260 0 
mac80211 181236 1 ath5k
ath 8060 1 ath5k
snd_seq_dummy 2656 0 
joydev 10272 0 
snd_seq_oss 28576 0 
snd_seq_midi 6432 0 
shpchp 32272 0 
snd_rawmidi 22208 1 snd_seq_midi
snd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midi
snd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 22276 2 snd_pcm,snd_seq
snd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 59204 16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp 4188 0 
led_class 4096 3 sdhci,acer_wmi,ath5k
cfg80211 93052 3 ath5k,mac80211,ath
soundcore 7264 1 snd
snd_page_alloc 9156 2 snd_hda_intel,snd_pcm
psmouse 56180 0 
serio_raw 5280 0 
usb_storage 52544 0 
8139too 22620 0 
8139cp 19260 0 
mii 5212 2 8139too,8139cp
radeon 636000 2 
ttm 36212 1 radeon
drm 159584 4 radeon,ttm
i2c_algo_bit 5760 1 radeon
video 19380 0 
output 2780 1 video
ati_agp 6760 0 
agpgart 34988 3 ttm,drm,ati_agp
@
I type
netstat -v
I get
the whole thing wont show but theres a bunch of stuff about unix, streams and connected.... at the bottom there is 
netstat: no support for `AF IPX' on this system.
netstat: no support for `AF AX25' on this system.
netstat: no support for `AF X25' on this system.
netstat: no support for `AF NETROM' on this system.
@
@
@
hope all this helps, and no I diddent type all this..... open office and usb works great!

---

### Post by northd_tech on 2009-12-07
> **jon31592 said:**
> 
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

That first one is your cable network adapter (Realtek 8139), and shows up as "eth0" when you ran ifconfig and iwconfig.  Have you tried hooking up a cable and connecting that way?  Usually it will automatically work on "eth0" when you hook up the cable or reboot ubuntu.

Your wireless driver looks to be an Atheros AR2413 and shows up as "wlan0" in iwconfig.

It looks like the modules are loaded, but I haven't worked with those 2 specifically under Linux before.  You might have a module conflict or configuration problem.  I've been talking to someone else having problems with an ubuntu that also shows that same "wmaster0" interface.  I'm suspicious of that one because I've not seen that before today, and "eth0" looks a lot more "normal" to me.

How about posting what you get from "less /etc/modules" "less /etc/modules.d" and "uname -a" terminal commands also.

If you search this forum for Atheros AR2413, you will probably find some helpful threads about your wireless adapter- I remember seeing some of those here.

---

### Post by jon31592 on 2009-12-07
no, i havent tryed that. if i can find my cable i will try for sure tho.  
this is wat i get.
 
less /etc/modules
 
# /etc/modules: kernal modules to load at boot time.
#
# this file contains the names of kernal modules that should be loaded
# at boot time, one per line. lines beginning with "#" are ignored.
 
lp
/etc/modules (end)
 
 
 
less /etc/modules.d
 
/etc/modules.d: no  such file or directory
 
 
 
uname -a
 
Linux jonathan-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2
009 i686 GNU/LINUX
 
 
 
and i havent done a serch yet but i will look into it

---

### Post by jon31592 on 2009-12-07
yeah works but i dont quite like it being tethered. but hey, at least my bro can have his comp back... yay!

---

