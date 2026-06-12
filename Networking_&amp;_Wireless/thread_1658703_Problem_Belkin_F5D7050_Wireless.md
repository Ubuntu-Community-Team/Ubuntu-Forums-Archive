---
title: "Problem Belkin F5D7050 Wireless"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by RaZYeLLe on 2011-01-03
Hello Guys,

i am complitly new in Ubuntu and the world of Linux in general, so i said to my self its better late then never, i installed the last one 10.10. but i am having trouble with my wifi usb adapter (Belkin**F5D7050 v 1000**), the same adapter works perfect under XP in the same PC.
when i go to NM i dont see it in the list of network cards "i see just my two other normal network cards + loopback" and i have permanent small "x"  on the icon of NM up in the task bar, even if check or uncheck "Enable Networking", it alwayes show a info bubble "you are now offline", here is the result of all the command line that can help getting better view on my problem, i am available for all your questions and thank you guys in advance. 

 						julija@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

julija@ubuntu:~$ lsusb
Bus 005 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 050d:7050 Belkin Components F5D7050 Wireless G Adapter v1000/v2000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

julija@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 11)
0b:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

julija@ubuntu:~$ sudo lshw -C network
[sudo] password for julija: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 11
       serial: 00:30:05:95:cd:f5
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:0b:05.0
       logical name: eth0
       version: 10
       serial: 00:11:6b:95:62:42
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:5000(size=256) memory:f0200000-f02000ff memory:20e00000-20e1ffff

julija@ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8                1069  0 
isofs                  30022  0 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
binfmt_misc             6599  1 
p54usb                 11206  0 
p54common              25426  1 p54usb
rt73usb                22442  0 
crc_itu_t               1383  1 rt73usb
rt2500usb              18049  0 
rt2x00usb               9779  2 rt73usb,rt2500usb
rt2x00lib              27275  3 rt73usb,rt2500usb,rt2x00usb
led_class               2633  2 p54common,rt2x00lib
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
mac80211              231541  4 p54usb,p54common,rt2x00usb,rt2x00lib
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
cfg80211              144470  3 p54common,rt2x00lib,mac80211
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
i915                  290938  3 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm_kms_helper         30200  1 i915
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 i915,drm_kms_helper
ppdev                   5556  0 
parport_pc             26058  1 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26360  2 i915
lp                      7342  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
soundcore                880  1 snd
output                  1883  1 video
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
agpgart                32011  2 drm,intel_agp
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40172  1 
8139too                19581  0 
floppy                 54311  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp
tg3                   123310  0 

julija@ubuntu:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      no wireless extensions.

julija@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:6b:95:62:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x5000 
eth1      Link encap:Ethernet  HWaddr 00:30:05:95:cd:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66232 (66.2 KB)  TX bytes:66232 (66.2 KB)

julija@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      Interface doesn't support scanning.

julija@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

julija@ubuntu:~$ nm-tool
NetworkManager Tool
State: disconnected
- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:30:05:95:CD:F5
  Capabilities:
    Carrier Detect:  yes
  Wired Properties
    Carrier:         off

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:11:6B:95:62:42
  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s
  Wired Properties
    Carrier:         off

julija@ubuntu:~$ uname -r -m
2.6.35-22-generic i686

---

### Post by PatchesTheCaveman on 2011-01-03
Hi RaZYeLLe.  Happy New Year!

There are updated drivers for your wireless USB dongle that might help.  Plug into a wired Ethernet Internet connection and run this command to install them:
```
sudo apt-get install linux-backports-modules-wireless-`lsb_release -cs`-generic
```

Please note that the ` character used above is an accent grave/backtick, not an apostrophe/single quote.  It can be found to the left of 1 and below Escape on most US keyboards.

---

### Post by ryanryanryan on 2012-01-28
I'm am new to Ubuntu, and i have a similar issue...

Running 10.10. Same wireless router.

Pardon my ignorance, do i need to install the software that came with my wireless router? Or, do I just need to execute the above command in the terminal?

Thanks!

Ryan.

---

### Post by calande on 2012-02-25
Hello, I'm using Oneiric and its default driver for my Belkin F5D7050. The wifi icon does show up, connects to my wifi network, but right away disappears with no connectivity. Maybe I need a different driver?

---

### Post by praseodym on 2012-02-25
Hi,

@RaZYeLLe: Blacklist the following driver:

```
echo "blacklist rt2500usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv rt2500usb rt73usb
sudo modprobe -v rt73usb
```
and replug the stick.

To the others, please show

```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by calande on 2012-02-25
Thank you. There you go:
```
$ lsusb
Bus 001 Device 040: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]
```
```
$ lsmod
Module                  Size  Used by
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20092  1 rt73usb
rt2x00lib              48146  2 rt73usb,rt2x00usb
mac80211              393421  2 rt2x00usb,rt2x00lib
cfg80211              172427  2 rt2x00lib,mac80211
nfs                   297836  1 
lockd                  78804  1 nfs
fscache                50674  1 nfs
auth_rpcgss            39545  1 nfs
nfs_acl                12771  1 nfs
sunrpc                205320  17 nfs,lockd,auth_rpcgss,nfs_acl
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52412  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13553  1 nf_nat_pptp
nf_conntrack_proto_gre    13395  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16921  0 
nf_conntrack_sip       24749  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12595  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
iptable_nat            13016  0 
nf_nat                 24958  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
nf_conntrack           70103  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21975  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
arc4                   12473  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
zl10353                13540  1 
cx88_dvb               33317  0 
cx88_vp3054_i2c        12840  1 cx88_dvb
videobuf_dvb           13867  1 cx88_dvb
dvb_core               94826  2 cx88_dvb,videobuf_dvb
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_via82xx            24720  2 
gameport               15060  1 snd_via82xx
snd_via82xx_modem      18377  0 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
snd_mpu401_uart        13865  1 snd_via82xx
ac97_bus               12642  1 snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_mpu401_uart,snd_seq_midi
nvidia               7098131  34 
snd_seq_midi_event     14475  1 snd_seq_midi
cx88_alsa              18089  0 
tuner_xc2028           26635  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
snd_pcm                80435  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,cx88_alsa
tuner                  26836  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
cx8802                 18608  1 cx88_dvb
cx8800                 33328  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
snd                    55902  14 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,cx88_alsa,snd_seq,snd_pcm,snd_seq_device,snd_timer
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
psmouse                73673  0 
k8temp                 12905  0 
ir_nec_decoder         12490  0 
cx88xx                 78930  4 cx88_dvb,cx88_alsa,cx8802,cx8800
snd_page_alloc         14115  3 snd_via82xx,snd_via82xx_modem,snd_pcm
serio_raw              12990  0 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  2 cx88_vp3054_i2c,cx88xx
tveeprom               17009  1 cx88xx
i2c_viapro             12969  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videobuf_dma_sg        18786  5 cx88_dvb,cx88_alsa,cx8802,cx8800,cx88xx
soundcore              12600  1 snd
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_core          25409  5 videobuf_dvb,cx8802,cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  4 cx88_alsa,cx8802,cx8800,cx88xx
shpchp                 32356  0 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_cherry             12547  0 
usbhid                 41905  0 
hid                    77367  2 hid_cherry,usbhid
sata_via               13534  0 
pata_via               13398  0 
skge                   44767  0 
sata_promise           18006  3 
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
charles@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 047d:1002 Kensington Expert Mouse Pro
Bus 003 Device 003: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard
Bus 001 Device 040: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]
charles@ubuntu:~$ lsmod
Module                  Size  Used by
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20092  1 rt73usb
rt2x00lib              48146  2 rt73usb,rt2x00usb
mac80211              393421  2 rt2x00usb,rt2x00lib
cfg80211              172427  2 rt2x00lib,mac80211
nfs                   297836  1 
lockd                  78804  1 nfs
fscache                50674  1 nfs
auth_rpcgss            39545  1 nfs
nfs_acl                12771  1 nfs
sunrpc                205320  17 nfs,lockd,auth_rpcgss,nfs_acl
ipt_MASQUERADE         12663  1 
xt_state               12514  1 
ipt_REJECT             12512  2 
xt_tcpudp              12531  4 
iptable_filter         12706  1 
nf_nat_h323            12749  0 
nf_conntrack_h323      52412  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13553  1 nf_nat_pptp
nf_conntrack_proto_gre    13395  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16921  0 
nf_conntrack_sip       24749  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12595  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
iptable_nat            13016  1 
nf_nat                 24958  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  4 iptable_nat,nf_nat
nf_conntrack           70103  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21975  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
arc4                   12473  2 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
zl10353                13540  1 
cx88_dvb               33317  0 
cx88_vp3054_i2c        12840  1 cx88_dvb
videobuf_dvb           13867  1 cx88_dvb
dvb_core               94826  2 cx88_dvb,videobuf_dvb
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_via82xx            24720  2 
gameport               15060  1 snd_via82xx
snd_via82xx_modem      18377  0 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
snd_mpu401_uart        13865  1 snd_via82xx
ac97_bus               12642  1 snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_mpu401_uart,snd_seq_midi
nvidia               7098131  34 
snd_seq_midi_event     14475  1 snd_seq_midi
cx88_alsa              18089  0 
tuner_xc2028           26635  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
snd_pcm                80435  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,cx88_alsa
tuner                  26836  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
cx8802                 18608  1 cx88_dvb
cx8800                 33328  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
snd                    55902  14 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,cx88_alsa,snd_seq,snd_pcm,snd_seq_device,snd_timer
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
psmouse                73673  0 
k8temp                 12905  0 
ir_nec_decoder         12490  0 
cx88xx                 78930  4 cx88_dvb,cx88_alsa,cx8802,cx8800
snd_page_alloc         14115  3 snd_via82xx,snd_via82xx_modem,snd_pcm
serio_raw              12990  0 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  2 cx88_vp3054_i2c,cx88xx
tveeprom               17009  1 cx88xx
i2c_viapro             12969  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videobuf_dma_sg        18786  5 cx88_dvb,cx88_alsa,cx8802,cx8800,cx88xx
soundcore              12600  1 snd
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_core          25409  5 videobuf_dvb,cx8802,cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  4 cx88_alsa,cx8802,cx8800,cx88xx
shpchp                 32356  0 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_cherry             12547  0 
usbhid                 41905  0 
hid                    77367  2 hid_cherry,usbhid
sata_via               13534  0 
pata_via               13398  0 
skge                   44767  0 
sata_promise           18006  3 
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash

```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
$ rfkill list
```

;)

---

### Post by praseodym on 2012-02-25
Remove the IP tables (firewall). Normally you dont need it:

```
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by calande on 2012-02-25
Thanks. I applied it, rebooted, but now the dongle keeps trying to connect :(

---

### Post by praseodym on 2012-02-25
Did you set up an "Ad-Hoc"-network? Remove your current wireless profile and set up a new one in "Infrastructure" mode. Dont forget the encryption.

---

### Post by calande on 2012-02-25
Thanks. Yes, I have an infrastructure type of connection. I unplugged and plugged the dongle back, it worked for 20-30 sec, I was able to access the Internet (4 bars), then it fell. I tried to reconnect it and it tried 2-3 times, then it didn't even try to reconnect. When I use the Windows partition, this dongle works flawlessly with full throughput. Any idea?

---

### Post by praseodym on 2012-02-25
Strange. Please again:

```
cat /etc/udev/rules.d/70-persistent-net.rules
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

---

### Post by calande on 2012-02-25
Thanks. While I was running the commands, the dongle was trying to connect. Here's the output:

```
$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x11ab:0x4320 (skge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:d4:78:a3:e0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x050d:0x705a (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:17:3f:ad:79:6a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"



$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#NetworkManager#iface eth0 inet dhcp
# This is an autoconfigured IPv6 interface
#NetworkManager#iface eth0 inet6 auto



$ cat /etc/resolv.conf
# Generated by NetworkManager




$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
```

---

### Post by praseodym on 2012-02-25
Go to the NM-applet->wireless->Edit->IPv4-settings and change to "Automatic DHCP (addresses only)" and add the nameservers of your provider or the google public nameservers 8.8.8.8 and 8.8.4.4 there. Router firmware is up-to-date? MAC-addressfilter in the router is off?

---

### Post by calande on 2012-02-25
I checked what you mentioned and changed the DNS to use Google's. My dongle tries to connect, is connected for a second or more, then says it's disconnected and retries to connect. At some point it disappears from the Network applet. I have to physically remove the dongle, wait a minute and plug it back in. Thanks.

---

### Post by praseodym on 2012-02-26
Did you uninstall the FW?

> sudo apt-get remove --purge ufw gufw
Remove the iptables again

---

### Post by calande on 2012-02-26
OK, now, after removing iptables again, running the above command and rebooting, my dongle doesn't even show up in the Network applet. If I remove it and plug it back in after a minute, it shows up, gets connected and after a second it says it's disconnected...

---

### Post by praseodym on 2012-02-26
Why is the line

> auto eth0

in your "interfaces"? Cable connection is always preferred. Remove this line and reboot

---

### Post by calande on 2012-02-26
Thanks. OK, done but same problem. I think we'll forget it. Next week, I'm going to search for a different NIC. Thanks again ;)

---

### Post by praseodym on 2012-02-26
Try a driver update:

```
sudo apt-get install linux-headers-$(uname -r) build-essential linux-backports-modules-cw-3.1-oneiric-generic
```

---

### Post by calande on 2012-02-26
Thanks. Same problem...

---

