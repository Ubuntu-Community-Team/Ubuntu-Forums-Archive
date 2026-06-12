---
title: "sharing a wireless connection with an adjacent machine"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by 036f7e7a49e280a1 on 2011-09-01
Hello,

I have a Linux box and a windows box. The Linux box has wireless internet access (thanks to ndlswrapper:)) but I'd rather not have to buy a separate wireless card for the windows box beside it.

Is there a way to connect the windows box through Ethernet cable to  the Linux box so that it can share the wireless connection? I know you can do something similar for direct file transfers ...

---

### Post by spiky001 on 2011-09-01
If you open network manager then go to edit connections select wired connection edit, Then ipv4 tab and set 
Methord to shared connection. Tick connect automatic and availble to all users

---

### Post by 036f7e7a49e280a1 on 2011-09-01
thank you,

I tried setting eth0 to be shared but that didn't work.
after a little thinking I tried setting the wireless connection to "shared" and that worked.:)

So I guess you have to "share" your internet connection, in this case wireless, with other machines.

edit: how do you set a thread as "resolved" ?

edit2: spiky001 was right, I should have set the wired connection as shared.

---

### Post by spiky001 on 2011-09-01
Thread tools

---

### Post by northd_tech on 2011-09-01
Here is the documentation for Internet Connection Sharing:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

On the **ndiswrapper** thing- it might be possible to get native Linux support for your wireless hardware.  Could you post the output from these terminal commands:

```
sudo lshw- C network
lspci -vvnn | egrep 'net|ireless|etwork'
ifconfig
iwconfig
lsmod
```

---

### Post by 036f7e7a49e280a1 on 2011-09-01
Thanks for the documentation

here's the output for those commands

I'm assuming you meant "sudo lshw -C network" 

```
  *-network:0
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth1
       version: 08
       serial: 00:d0:b7:be:59:48
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:17 memory:febff000-febfffff ioport:ec00(size=64) memory:fea00000-feafffff memory:fe900000-fe9fffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth0
       version: 10
       serial: 00:1c:25:5e:93:33
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.42.43.1 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1GB/s
       resources: irq:22 ioport:e800(size=256) memory:febfec00-febfecff memory:febc0000-febdffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 14:d6:4d:39:44:63
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192su driverversion=1.55+D-Link Corporation,08/05/20 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11g
```

lspci -vvnn | egrep 'net|ireless|etwork'

```
04:01.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 08)
04:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
```

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1c:25:5e:93:33  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe5e:9333/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:839810 (839.8 KB)  TX bytes:8569190 (8.5 MB)
          Interrupt:22 Base address:0xc00 

eth1      Link encap:Ethernet  HWaddr 00:d0:b7:be:59:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:220888 (220.8 KB)  TX bytes:220888 (220.8 KB)

wlan0     Link encap:Ethernet  HWaddr 14:d6:4d:39:44:63  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::16d6:4dff:fe39:4463/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39867961 (39.8 MB)  TX bytes:6098977 (6.0 MB)
```

iwconfig

```
wlan0     IEEE 802.11g  ESSID:"MuadDib"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 68:7F:74:91:0A:2A   
          Bit Rate=21.5 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod

```
Module                  Size  Used by
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          1369  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46894  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4428  1 nf_nat_pptp
nf_conntrack_proto_gre     3957  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             3543  1 
nf_nat                 15560  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10346  4 iptable_nat,nf_nat
nf_conntrack           60975  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9899  2 iptable_filter,iptable_nat
x_tables               14175  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
serpent                17517  2 
twofish                 5419  2 
twofish_common         12799  1 twofish
aes_i586                7268  2 
aes_generic            26863  1 aes_i586
xts                     2031  3 
gf128mul                8015  1 xts
dm_crypt               11331  3 
ndiswrapper           184677  0 
isofs                  29250  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  72 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
nvidia               9961216  38 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
agpgart                31724  2 nvidia,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
e100                   28211  0 
r8169                  34140  0 
mii                     4381  2 e100,r8169
pata_jmicron            1843  0 
```

---

