---
title: "Need help getting madwifi drivers working"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by RyanPriceDotCa on 2009-05-21
Hello, I am running Ubuntu 9.04 and am having trouble getting madwifi installed.  I was able to get the latest version checked out using svn and used the make / make install commands which were also successful as far as I could tell (no printed errors).

I am now trying to use the madwifi drivers and don't seem to be able to get my laptop to use them.  Below is the result of my lshw -C network command.  It still shows my wireless card using ath_pci as the driver instead of madwifi.

Any ideas?

```

ryan@RyansAmazingLaptopOfAwesome:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:66:46:5e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.191 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:9e:2d:df:4c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:7a:b8:4f:c0:e8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by t0mppa on 2009-05-21
ath_pci is a driver from Madwifi (a group making these drivers, not the name of a single driver) and the only one of them that needs to be compiled from source. So, what exactly is wrong?

---

### Post by RyanPriceDotCa on 2009-05-21
Well I'm not sure what's wrong then.  I have run the hardware drivers and it shows "Alternate Atheros madwifi driver" as enabled.

However, when clicking on my network manager I am not able to connect to any wireless networks - it doesn't even show a list of available networks... the wireless networks option is just greyed out.

I'm at a loss for where to go from here.

---

### Post by t0mppa on 2009-05-21
Ok then, post result of 'lsmod', 'iwconfig', 'ifconfig' & 'dmesg | grep ath' to see if there's something else wrong.

---

### Post by RyanPriceDotCa on 2009-05-21
lsmod:
```
ryan@RyansAmazingLaptopOfAwesome:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxnetflt             91016  0 
vboxdrv               117544  1 vboxnetflt
input_polldev          11912  0 
joydev                 18368  0 
sbp2                   30476  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
wlan_scan_sta          21248  1 
snd_seq_midi           14336  0 
ath_rate_sample        20608  1 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
pcmcia                 44748  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  25360  0 
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
ath_pci               208568  0 
pcspkr                 10496  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                61972  0 
intel_agp              34108  1 
agpgart                42696  2 intel_agp
serio_raw              13316  0 
fujitsu_laptop         20104  0 
output                 11008  1 video
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
wlan                  234480  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               371488  3 ath_rate_sample,ath_pci
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

iwconfig:
```
ryan@RyansAmazingLaptopOfAwesome:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

ifconfig:
```
ryan@RyansAmazingLaptopOfAwesome:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1b:9e:2d:df:4c  
          inet6 addr: fe80::21b:9eff:fe2d:df4c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:17:42:66:46:5e  
          inet addr:192.168.0.191  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:42ff:fe66:465e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19368057 (19.3 MB)  TX bytes:8096021 (8.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:680 (680.0 B)  TX bytes:680 (680.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-9E-2D-DF-4C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:31134 (31.1 KB)
          Interrupt:18 
```

and the last one:
```
ryan@RyansAmazingLaptopOfAwesome:~$ dmesg | grep ath
[    3.200442] device-mapper: multipath: version 1.0.5 loaded
[    3.200445] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.771648] ath_pci 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.771663] ath_pci 0000:05:00.0: setting latency timer to 64
[   13.332359] MadWifi: ath_attach: Switching rfkill capability off.
[   13.374627] ath_pci: wifi0: Atheros 5424/2424: mem=0x8c100000, irq=18
[  322.872744] ath0: no IPv6 routers present

```

Thanks in advance.

---

### Post by Bucky Ball on 2009-05-21
Atheros chipset on wireless card. Should be supported already. System->Admininstration->Hardware Drivers. What have you got in there?

First port of call if you have not yet been online with your fresh install: Plug in a hardwire ethernet cable (if possible) and get your updates. Follow your nose, give it some time and this will (should) detect card and load the appropriate Atheros drivers for you 'automagically'.

Go to System->Admininstration->Synaptic Package Manager and do a search for:

ubuntu-restricted-modules

...and

ubuntu-restricted-extras

Make sure they are installed.

---

### Post by RyanPriceDotCa on 2009-05-21
@Bucky Ball: I did have wireless working with a different driver, but I am wanting to get madwifi working anyway.  Right now I am connected through a ethernet trying to get it to work.  Thanks for the suggestion though.

---

### Post by Bucky Ball on 2009-05-21
Have you got those things installed?

ubuntu-restricted-modules

...and

ubuntu-restricted-extras

---

### Post by RyanPriceDotCa on 2009-05-21
Yes I do have those packages installed

---

### Post by t0mppa on 2009-05-22
Can't see any problems there. Try 'iwlist scan' then and see if it can find any networks. If that works as well, try to connect manually, maybe network manager is just playing tricks.

---

