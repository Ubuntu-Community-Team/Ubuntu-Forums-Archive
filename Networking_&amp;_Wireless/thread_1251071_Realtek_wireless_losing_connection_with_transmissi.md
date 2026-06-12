---
title: "Realtek wireless losing connection with transmission"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by fidelandche on 2009-08-27
Hi,

  I have the following laptop; Gateway ML6226B.

  From the first code;

 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

  From the second code;

Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

 From the third code;
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:c6:19:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15936 (15.9 KB)  TX bytes:15936 (15.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:e0:94:ca  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fee0:94ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12025 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8253342 (8.2 MB)  TX bytes:1293684 (1.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-E0-94-CA-34-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

IEEE 802.11bg  ESSID:"BTHomeHub2-KM3N"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:4E:9E:F5:19   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=16/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

From the fourth code;

         Module                  Size  Used by
xt_limit               10116  8 
xt_tcpudp              11008  7 
ipt_LOG                13700  8 
ipt_MASQUERADE         10752  0 
xt_DSCP                11264  0 
ipt_REJECT             11136  1 
nf_conntrack_irc       13220  0 
nf_conntrack_ftp       15652  0 
xt_state               10112  6 
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
joydev                 18496  0 
snd_hda_intel         434100  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  4 snd_hda_intel,snd_pcm_oss
iptable_nat            13700  0 
nf_nat                 25876  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21388  9 iptable_nat,nf_nat
snd_seq_dummy          10756  0 
nf_conntrack           72008  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_seq_oss            37760  0 
rtl8187                53376  0 
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
iptable_mangle         10880  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
iptable_filter         10752  1 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
mac80211              217592  1 rtl8187
x_tables               23044  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
eeprom_93cx6           10240  1 rtl8187
pcmcia                 44748  0 
snd                    62756  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1              13824  0 
psmouse                61972  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
video                  25360  0 
intel_agp              34108  1 
tifm_core              15900  1 tifm_7xx1
soundcore              15200  1 snd
serio_raw              13444  0 
pcspkr                 10496  0 
cfg80211               38288  2 rtl8187,mac80211
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
agpgart                42696  3 drm,intel_agp
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

From code six,

[FONT=monospace] *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c6:19:25
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:e0:94:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.64 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 22:82:6f:26:84:a5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

From code seven;

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:4E:9E:F5:19
                    ESSID:"BTHomeHub2-KM3N"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=14/100  Signal level:65/65  
                    Encryption key:on
                    IE: Unknown: 000F4254486F6D65487562322D4B4D334E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000025c7a1864e
                    Extra: Last beacon: 84ms ago

pan0      Interface doesn't support scanning.

 From code eight;

    Ubuntu 9.04
From code nine;

2.6.28-15-generic i686

From code ten;

 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface wlan0=wlan0.

   The problems I have are the following, I can connect wirelessly without any problems but the signal strength is very** poor**, out of the four bars which show the signal strength, **I only get one!!** But on my partners and son's laptops all running 9.04 they get full signal strength. My other son runs a mac book,he gets full signal strength as well. When I was running Vista I had no problems with this.

   Also when I use transmission and I am browsing the Internet at the same time, I will lose connection, so I have to restart my laptop to regain my connection!! So I can only have Transmission running or FF running at a time but not both together.

[U][COLOR=Red][B]I have now found a solution to my problem, I found another post on this forum talking about the same Realtek Driver as me, followed the instructions to install a package and now I have full signal strength
[/B][/COLOR][/U] 
[/FONT]

---

