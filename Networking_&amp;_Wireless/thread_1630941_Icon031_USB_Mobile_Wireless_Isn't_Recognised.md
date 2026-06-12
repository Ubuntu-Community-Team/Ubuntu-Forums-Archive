---
title: "Icon031 USB Mobile Wireless Isn't Recognised"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by demonboy on 2010-11-25
Hi,

Here in India I've been given a USB dongle for my Airtel SIM that isn't recognised by Ubuntu. 

The dongle is an Icon031 EDGE, model: GI0031, serial number begins ME.

usb-devices shows that the driver appears to be installed:

> 
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0af0 ProdID=c031 Rev=01.00
S:  Manufacturer=Option Wireless Technology
S:  Product=Globetrotter HSxPA Modem
S:  SerialNumber=serial_number
C:  #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso

lspci (the following terminal grabs were taken whilst my other dongle, a Huawei, was connected)
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
lsusb
> 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 014: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 004: ID 0ac8:c326 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfig
> 
eth0      Link encap:Ethernet  HWaddr 00:13:77:d3:c6:ba  
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
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11692 (11.6 KB)  TX bytes:11692 (11.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:110.225.101.86  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1710323 (1.7 MB)  TX bytes:325564 (325.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:c9:e4:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig
```


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

ppp0      no wireless extensions.



```lsmod
```

Module                  Size  Used by
hso                    30724  0 
ppp_deflate             3726  0 
zlib_deflate           19266  1 ppp_deflate
bsd_comp                4791  0 
ppp_async               6778  1 
crc_ccitt               1351  1 ppp_async
option                 13133  2 
usb_wwan                9953  1 option
usbserial              33100  7 option,usb_wwan
usb_storage            40172  0 
hidp                   11664  0 
rfcomm                 33811  8 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  17 hidp,rfcomm,bnep
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
ipt_REJECT              2004  1 
xt_comment               732  2 
nfsd                  241120  11 
ipt_LOG                 4490  5 
xt_multiport            1577  2 
lockd                  65605  1 nfsd
xt_limit                1394  7 
nfs_acl                 2257  1 nfsd
xt_tcpudp               1927  13 
auth_rpcgss            34001  1 nfsd
ipt_addrtype            1611  4 
sunrpc                193114  12 nfsd,lockd,nfs_acl,auth_rpcgss
xt_state                1014  7 
exportfs                3449  1 nfsd
parport_pc             26058  0 
ppdev                   5556  0 
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
snd_hda_codec_realtek   217971  1 
arc4                    1165  2 
nf_nat_ftp              1398  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
snd_hda_intel          22107  1 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
snd_seq_midi            4588  0 
joydev                  8735  0 
i915                  292683  4 
snd_rawmidi            17783  1 snd_seq_midi
nf_conntrack_ftp        5361  1 nf_nat_ftp
ath5k                 130083  0 
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1302  1 
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30168  1 i915
mac80211              231541  1 ath5k
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ip_tables              10460  1 iptable_filter
snd_timer              19067  2 snd_pcm,snd_seq
x_tables               15921  12 ipt_REJECT,xt_comment,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
ath                     8153  1 ath5k
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  5 i915,drm_kms_helper
usbhid                 36882  0 
uvcvideo               55847  0 
btusb                  10969  2 
snd                    49006  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              144470  3 ath5k,mac80211,ath
soundcore                880  1 snd
hid                    67742  2 hidp,usbhid
intel_agp              26424  2 i915
bluetooth              50500  10 hidp,rfcomm,sco,bnep,l2cap,btusb
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
videodev               43098  1 uvcvideo
psmouse                59033  0 
v4l1_compat            13359  2 uvcvideo,videodev
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
serio_raw               4022  0 
output                  1883  1 video
lp                      7342  0 
led_class               2633  1 ath5k
agpgart                32011  2 drm,intel_agp
parport                31492  3 parport_pc,ppdev,lp
sky2                   45127  0 


```Any clues?

---

### Post by alexfish on 2010-11-26
Hi

have you looked here

[http://www.pharscape.org/](http://www.pharscape.org/)

the site is dedicate to option devices RE hso, they also have a forum


alexfish

---

### Post by demonboy on 2010-11-26
Hi alex. I tried to join their forum but there was a problem with registering. I wasn't sure how active the site was so i'll try again on your recommendation.

---

### Post by alexfish on 2010-11-26
Hi 
maybe send a pm

[Pharscape]("http://ubuntuforums.org/member.php?u=716902")

---

### Post by demonboy on 2010-11-28
I wasn't aware he was a member, so thanks for that.

---

### Post by alexfish on 2010-11-29
You have Two Threads , same device

Stay on your thread here at "Absolute Beginners Talk"

[http://ubuntuforums.org/showthread.php?p=10179082#post10179082](http://ubuntuforums.org/showthread.php?p=10179082#post10179082)

alexfish

---

