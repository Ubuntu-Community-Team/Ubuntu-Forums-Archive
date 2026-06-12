---
title: "Karmic wired connection..again!!"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Neo~ on 2010-02-21
okay i thinks it's time to ask for some help

i spent 2 days after installing Ubuntu 9.10 reading dozens of threads and articles trying to make my wired connection works (right now i'm using windows to post this)

i read that it might be dhcp bug thing so i downloaded and installed dhcpcd.deb package and ran
```
sudo dhcpcd eth0
```and it already got my an IP but still no connection
i tried to edit the dhclient.conf but still nothing

finally i deleted the Auto eth0 and re-create another one and it WORKS perfectly!!

then after few updates it asked me to reboot after logging in again the connection was disconnected again!! and i'm unable to restore connection since then

tried to delete and re-create new eth0 but still no connection:(
when i ran
 ```
sudo dhcpcd eth0
``` the output was

> noha@bogy:~$ sudo dhcpcd eth0
[sudo] password for noha: 
err, eth0: timed out
warn, eth0: using IPV4LL address 169.254.231.219
noha@bogy:~$ dhcpcd.sh: interface eth0 has been configured with new IP=169.254.231.219I would appreciate any help

---

### Post by northd_tech on 2010-02-21
Can you post the results of the following commands when you run them in a terminal?

```
lspci

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig

sudo iwlist scan

nm-tool
```

---

### Post by Neo~ on 2010-02-22
Thank you Northd_tech
i just logged in into Ubuntu to try the commands you posted once i'm in my eth0 connection just worked!!
I'm posting this from Ubuntu now
any way the out put to these commands is
> noha@bogy:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)

> noha@bogy:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_timer              22276  2 snd_pcm,snd_seq
x_tables               16544  1 ip_tables
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                56500  0 
ppdev                   6688  0 
serio_raw               5280  0 
parport_pc             31940  1 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
e100                   32420  0 
mii                     5212  1 e100
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

> noha@bogy:~$ uname -a
Linux bogy 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

> noha@bogy:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801EB/ER (ICH5/ICH5R) integrated LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:1a:4d:6c:d2:5e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.10 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:f8000000-f8000fff ioport:a000(size=64)

> noha@bogy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:6c:d2:5e  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe6c:d25e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4753579 (4.7 MB)  TX bytes:596436 (596.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
> 
noha@bogy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

> noha@bogy:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

> noha@bogy:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:1A:4D:6C:D2:5E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

What's that supposed to mean?
Now I'll try to restart or log off and log in again to see if it's still working

---

### Post by Neo~ on 2010-02-22
This became really annoying
each time i configure my wired connection and able to connect (I tried so many things,actually i don't know which of them make it works!!) then i restart or log off and log in again it disconnect!!

when i type this

```
sudo dhcpcd eth0
```the outcome is

> noha@bogy:~$ sudo dhcpcd eth0
[sudo] 
password for noha: 

err, eth0: timed out
warn, eth0: using IPV4LL address 169.254.231.219

noha@bogy:~$ dhcpcd.sh: interface eth0 has been configured with new IP=169.254.231.219


any ideas please??

---

### Post by Neo~ on 2010-02-25
It's me again
still having the same problem:confused:

I decided to give Wicd a try but still unable to connect(posting from windows now)
when i try to connect it tells me can't get ip

when i ran

```
sudo dhcpcd eth0
```

it tells me dhcpcd is already running

any clue please?
I don't want to give up trying but this bug is really frustrating:(

---

### Post by cap10Ibraim on 2010-02-25
I have a wired connection too (it works fine) here how it looks 

[IMG]http://lh6.ggpht.com/_tcUf5ZJRmuc/S4YgvkkxmOI/AAAAAAAAAHo/77ACG1J0Qok/s512/Screenshot-1.png[/IMG]

[IMG]http://lh5.ggpht.com/_tcUf5ZJRmuc/S4Ygvi30EFI/AAAAAAAAAHs/tyJb3fe-vck/s512/Screenshot-2.png[/IMG]

[IMG]http://lh4.ggpht.com/_tcUf5ZJRmuc/S4Ygv5iy5qI/AAAAAAAAAHw/yuk1O3xjfJs/s512/Screenshot-3.png[/IMG]

[IMG]http://lh5.ggpht.com/_tcUf5ZJRmuc/S4YgwA2i-EI/AAAAAAAAAH0/hmesGjkUnJw/s512/Screenshot-4.png[/IMG]

---

### Post by brunoscunha on 2010-02-25
I have the same issue. Prior to the NM update (yesterday) the wired connection was working perfectly.
My wired setup is the same as shown above, and still it does not connect. It just stays there trying to connect

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
```

lsmod
```
root@bruno-laptop:/home/bruno# lsmod
Module                  Size  Used by
pppoe                  11076  0 
pppox                   3016  1 pppoe
tun                    13788  0 
ppp_deflate             4732  0 
zlib_deflate           20088  1 ppp_deflate
bsd_comp                5436  0 
ppp_async               8860  1 
crc_ccitt               1852  1 ppp_async
isofs                  31620  0 
pata_pcmcia            11228  1 
snd_hda_codec_analog    61724  1 
pcmcia                 36808  1 pata_pcmcia
snd_hda_intel          25696  2 
snd_hda_codec          84384  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec
arc4                    1660  2 
ecb                     2524  2 
snd_pcm_oss            37312  0 
snd_mixer_oss          16220  1 snd_pcm_oss
snd_pcm                76416  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
iptable_filter          3100  0 
snd_seq_oss            29280  0 
snd_seq_midi            6624  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_rawmidi            22336  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                51088  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
b43                   122200  0 
mac80211              181140  1 b43
joydev                 10240  0 
option                 25184  1 
ppdev                   6688  0 
usbserial              36264  4 option
btusb                  11856  0 
snd_timer              21540  2 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             31940  1 
psmouse                56500  0 
serio_raw               5280  0 
cfg80211               93052  2 b43,mac80211
yenta_socket           24296  4 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_infineon            8200  0 
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
tpm                    15680  1 tpm_infineon
tpm_bios                6268  1 tpm
ricoh_mmc               3676  0 
hp_accel               11228  0 
lis3lv02d               7452  1 hp_accel
input_polldev           3716  1 lis3lv02d
led_class               4096  3 b43,sdhci,hp_accel
snd                    61188  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9060  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
ssb                    35524  1 b43
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
e1000e                122188  0 
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
```

uname -a

```
Linux bruno-laptop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux

```

sudo lshw -C network

```
root@bruno-laptop:/home/bruno# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1b:38:c1:8a:74
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.3-0 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:e4600000-e461ffff memory:e4620000-e4620fff ioport:4020(size=32)
  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:e4000000-e4003fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:a3:a1:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:c1:8a:74  
          inet6 addr: fe80::21b:38ff:fec1:8a74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1556192 (1.5 MB)  TX bytes:45511 (45.5 KB)
          Memory:e4600000-e4620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9191 (9.1 KB)  TX bytes:9191 (9.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:77.54.55.67  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1326133 (1.3 MB)  TX bytes:210338 (210.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:a3:a1:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1a:73:a3:a1:0d  
          inet addr:169.254.6.175  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-A3-A1-0D-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B
```

iwconfig

```
eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.
```

sudo iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:F0:FE:57:F8
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Butterfly"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c0e4222d03
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0009427574746572666C79
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D00050000000F000000000000000000000000000000
                    IE: Unknown: 2D1A4C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160D00010000000F000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 02 - Address: 00:05:CA:65:3C:C8
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ZON-3CC0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000729ece5842
                    Extra: Last beacon: 980ms ago
                    IE: Unknown: 00085A4F4E2D33434330
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1603000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000013127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3403000000000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B286010005CA653CC81021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 03 - Address: 00:1E:E5:8C:91:C4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"asterix"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004716698e177
                    Extra: Last beacon: 872ms ago
                    IE: Unknown: 000761737465726978
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 05040001000C
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 00:05:CA:65:3C:C9
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000729ecf6c7f
                    Extra: Last beacon: 908ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1603000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000013127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3403000000000000000000000000000000000000000000
          Cell 05 - Address: 00:13:F7:76:59:2E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Usa a tua palha&#65533;o"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b59996181
                    Extra: Last beacon: 776ms ago
                    IE: Unknown: 00115573612061207475612070616C6861E76F
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F03010000000013F776592E0213F776592E64002C010808
          Cell 06 - Address: 00:22:B0:78:26:C4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"DLink-7826C4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000eb3bf9a60
                    Extra: Last beacon: 760ms ago
                    IE: Unknown: 000C444C696E6B2D373832364334
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD870050F204104A000110103B0001031047001071AC0CB326BA51D7E74E0022B07826C4104400010110210006442D4C696E6B1023000D4456412D4733313730692F50541024000D4456412D4733313730692F50541042000830303030303030301054000800060050F20400011011000D4456412D4733313730692F505410080002008E1041000100
          Cell 07 - Address: 00:24:8C:55:0F:A4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"ZON-C3C2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004610f8d8388
                    Extra: Last beacon: 268ms ago
                    IE: Unknown: 00085A4F4E2D43334332
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 00:05:CA:66:15:08
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"ZON-1500"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011a98f8813c
                    Extra: Last beacon: 1028ms ago
                    IE: Unknown: 00085A4F4E2D31353030
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B286010005CA661508103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0103
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1602000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020015127A
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 09 - Address: 00:05:CA:66:15:09
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011a98f88c5e
                    Extra: Last beacon: 1028ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0103
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1602000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020015127A
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 10 - Address: 00:24:17:6E:AF:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"ThomsonAC76D4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001549d7c4007
                    Extra: Last beacon: 688ms ago
                    IE: Unknown: 000D54686F6D736F6E414337364434
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD810050F204104A0001101044000102103B00010310470010BF5B05922124556492AB004C98BEB6601021000754484F4D534F4E1023000A54686F6D736F6E2054471024000337383410420009303932324E543745411054000800060050F20400011011000D54686F6D736F6E20544737383410080002008410570001001041000100
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 11 - Address: 00:18:39:8E:0F:E8
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"La de casa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d0d647d80
                    Extra: Last beacon: 628ms ago
                    IE: Unknown: 000A4C612064652063617361
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3408000001000000000000000000000000000000000000
          Cell 12 - Address: 00:05:CA:71:1A:C8
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ZON-1AC0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f39828162
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 00085A4F4E2D31414330
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B286010005CA711AC8103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160D000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000013127A
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340D000000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 13 - Address: 00:05:CA:71:1A:C9
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f3983a8ba
                    Extra: Last beacon: 276ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160D000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000013127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340D000000000000000000000000000000000000000000

ppp0      Interface doesn't support scanning
```


nm-tool

```
root@bruno-laptop:/home/bruno# nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             disconnected
  Default:           no
  HW Address:        00:1B:38:C1:8A:74

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:1A:73:A3:A1:0D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    zon-casa:        Infra, 00:1F:C6:F4:06:89, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA
    k:               Infra, 00:1E:52:78:BB:0A, Freq 2462 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    ZON-E232:        Infra, 00:24:8C:B2:4D:2B, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP
    ZON-5620:        Infra, 00:05:CA:73:56:28, Freq 2467 MHz, Rate 48 Mb/s, Strength 48 WEP
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:73:56:29, Freq 2467 MHz, Rate 54 Mb/s, Strength 45
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:71:1A:C9, Freq 2472 MHz, Rate 54 Mb/s, Strength 24
    ZON-1AC0:        Infra, 00:05:CA:71:1A:C8, Freq 2472 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:66:15:09, Freq 2417 MHz, Rate 54 Mb/s, Strength 48
    ZON-1500:        Infra, 00:05:CA:66:15:08, Freq 2417 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2
    ZON-C3C2:        Infra, 00:24:8C:55:0F:A4, Freq 2462 MHz, Rate 54 Mb/s, Strength 58 WEP
    Usa a tua palha&#65533;o: Infra, 00:13:F7:76:59:2E, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    La de casa:      Infra, 00:18:39:8E:0F:E8, Freq 2447 MHz, Rate 54 Mb/s, Strength 58 WEP
    asterix:         Infra, 00:1E:E5:8C:91:C4, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WEP
    DLink-7826C4:    Infra, 00:22:B0:78:26:C4, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    Butterfly:       Infra, 00:1C:F0:FE:57:F8, Freq 2472 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:72:49:D9, Freq 2472 MHz, Rate 54 Mb/s, Strength 42
    ZON-49D0:        Infra, 00:05:CA:72:49:D8, Freq 2472 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:65:3C:C9, Freq 2422 MHz, Rate 54 Mb/s, Strength 52
    ThomsonAC76D4:   Infra, 00:24:17:6E:AF:4C, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA
    ZON-3CC0:        Infra, 00:05:CA:65:3C:C8, Freq 2422 MHz, Rate 54 Mb/s, Strength 58 WPA WPA2


- Device: ttyUSB0  [Vodafone Default] ------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         77.54.55.67
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64

    DNS:             4.2.2.1
    DNS:             4.2.2.2
```

Some help would be greatly appreciated

---

### Post by idlehands on 2010-02-25
Same here. rebooted today, after updates ostensibly, and tada no wired network , no wireless. everything just spins. Thought my cable was wonky again. 

I can manually set an ip, and get to my internal network, but my routing skills are weak so that's about as far as i got.. 

what gives?

---

### Post by brunoscunha on 2010-02-25
> **idlehands said:**
> Same here. rebooted today, after updates ostensibly, and tada no wired network , no wireless. everything just spins. Thought my cable was wonky again. 

I can manually set an ip, and get to my internal network, but my routing skills are weak so that's about as far as i got.. 

what gives?

I don't even think I have wireless, I have to test that at home. I just want to connect to my work network

---

### Post by Neo~ on 2010-02-25
Thanks for sharing guys, glad to know that I'm not the only person in the planet having this issue
I read in couple of threads that it's a dhclient bug in Ubuntu karmic but I'm not familiar with these technical issues. I'm just a medical student

cap10Ibraim
yes my wired configuration looked like yours when using Network manager (now I'm using wicd),one time it worked just fine and the other time it didn't work at all!!
each time i restart or log in Ubuntu I pray to be lucky enough and get connected:(

the real problem is, I don't know what's the problem is !!
totally clueless :confused:

---

### Post by Neo~ on 2010-02-27
Hi again,
i just tried to use static ip and open dsn options in wicd and it just work
i think i'll mark this thread as solved after all !!

---

### Post by redlightbreaks on 2010-03-03
Hi, I'm having a very similar problem, except I have never gotten wired or wireless internet to work on 9.10... could you explain a little more about what you mean by -->

"finally i deleted the Auto eth0 and re-create another one and it WORKS perfectly!!"

How do you delete the Auto eth0? and how do you re-create another? Are you just doing this in network manager?

Any advice from anyone would be extremely helpful, currently don't have any way of getting files from the linux box so typing out page after page of ifconfig output is tough at the moment.

Thanks!

---

