---
title: "Problem with HWNUm-300"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by daniel91090 on 2010-07-20
Hello, I'm French and I have a problem with my wireless card (HWNUm-300). I get the driver here: [http://drivers.softpedia.com/progDownload/Realtek-RTL8192SU-RTL8188SU-RTL8191SU-RTL8192GU-Wireless-802-11b-gn-USB-2-0-Network-Adapter-Driver- 108450618-Download-85695.html]("http://drivers.softpedia.com/progDownload/Realtek-RTL8192SU-RTL8188SU-RTL8191SU-RTL8192GU-Wireless-802-11b-gn-USB-2-0-Network-Adapter-Driver- 108450618-Download-85695.html")

I installed with ndisgtk. He said the driver is installed and the hardware is present. But I can not capture any wifi network. If someone an idea?? I would send her a box of wine.;) Thank you.

Daniel


> daniel@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

daniel@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:071f Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 06f8:e031 Guillemot Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

daniel@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Cypress [Radeon HD 5800 Series]
01:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)


daniel@ubuntu:~$ lspci -nn | grep -i net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)


daniel@ubuntu:~$ sudo lshw -C network
[sudo] password for daniel: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: e0:cb:4e:b7:25:49
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:c800(size=256) memory:fafff000-faffffff(prefetchable) memory:faff8000-faffbfff(prefetchable) memory:fbdf0000-fbdfffff(prefetchable)

daniel@ubuntu:~$ lsmod
Module                  Size  Used by
arc4                    1473  0 
rt73usb                24256  0 
crc_itu_t               1715  1 rt73usb
rt2x00usb              11260  1 rt73usb
rt2x00lib              32133  2 rt73usb,rt2x00usb
led_class               3764  1 rt2x00lib
mac80211              238448  2 rt2x00usb,rt2x00lib
cfg80211              148546  2 rt2x00lib,mac80211
ndiswrapper           244768  0 
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
usb_storage            49833  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_via      33207  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2151  4 
xt_state                1490  7 
snd_hda_intel          25677  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
ip6table_filter         2887  1 
snd_pcm_oss            41394  0 
ip6_tables             19618  1 ip6table_filter
snd_mixer_oss          16299  1 snd_pcm_oss
nf_nat_irc              1577  0 
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
nf_conntrack_irc        4429  1 nf_nat_irc
snd_seq_dummy           1782  0 
nf_nat_ftp              2513  0 
snd_seq_oss            31219  0 
nf_nat                 19501  2 nf_nat_irc,nf_nat_ftp
snd_seq_midi            5829  0 
nf_conntrack_ipv4      12980  9 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack           73966  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2791  1 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              18390  1 iptable_filter
x_tables               22461  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
snd                    71106  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_atk0110           10033  0 
i2c_piix4               9639  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
psmouse                64576  0 
softcursor              1565  1 bitblit
serio_raw               4918  0 
joydev                 11072  0 
edac_core              45423  0 
soundcore               8052  1 snd
edac_mce_amd            9278  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
fglrx                2353422  35 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41084  0 
hid                    83440  1 usbhid
pata_marvell            3225  0 
r8169                  39650  0 
mii                     5237  1 r8169
pata_atiixp             4209  0 
ohci1394               30260  0 
ahci                   37838  1 
ieee1394               94771  1 ohci1394

daniel@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

daniel@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:b7:25:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:29 Adresse de base:0x6000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:18 erreurs:0 :0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:1060 (1.0 KB) Octets transmis:1060 (1.0 KB)

daniel@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

daniel@ubuntu:~$ uname -r -m 
2.6.32-23-generic x86_64

daniel@ubuntu:~$ cat  /etc/network/interfaces
auto lo
iface lo inet loopback

daniel@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E0:CB:4E:B7:25:49

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


---

### Post by fixeon on 2010-10-30
Salut :) did you try installing the linux driver for RTL8192SU?
you'll find it here:
[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

