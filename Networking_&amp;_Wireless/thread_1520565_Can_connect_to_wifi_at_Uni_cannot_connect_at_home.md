---
title: "Can connect to wifi at Uni cannot connect at home"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by nimonika on 2010-06-29
So I had to reinstall Lucid. Before the reinstall wifi worked smoothly at home and Uni. After the reinstall, Wifi works at Uni, but strangely does not work at home. It connects to the network - well atleast it shows me that it is connected, but there is no data transmission. Please can some advise on how to troubleshoot this.

Thanks

---

### Post by nimonika on 2010-06-29
Please find attached output of certain commands

monika@monika-laptop:~$ lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:0d:cd:3b  
          inet6 addr: fe80::21f:16ff:fe0d:cd3b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:139105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:191566690 (191.5 MB)  TX bytes:8128299 (8.1 MB)
          Memory:f2700000-f2720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:324455 (324.4 KB)  TX bytes:324455 (324.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:ef:a4:fe  
          inet6 addr: fe80::216:eaff:feef:a4fe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10505 (10.5 KB)

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


monika@monika-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

lsmod
Module                  Size  Used by
ipt_MASQUERADE          1407  0 
xt_state                1098  0 
ipt_REJECT              1928  0 
xt_tcpudp               2011  0 
iptable_filter          2271  0 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             4414  0 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  3 iptable_nat,nf_nat
nf_conntrack           61583  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
binfmt_misc             6587  1 
softcursor              1189  1 bitblit
snd_hda_codec_conexant    22641  1 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
rfcomm                 33421  4 
ppdev                   5259  0 
sco                     7885  2 
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
bridge                 45582  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
stp                     1655  1 bridge
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
i915                  285076  3 
zaurus                  2404  0 
drm_kms_helper         29297  1 i915
bnep                    9436  2 
iwlagn                105694  0 
snd_seq_dummy           1338  0 
l2cap                  30624  16 rfcomm,bnep
cdc_ether               3541  1 zaurus
thinkpad_acpi          68083  0 
snd_seq_oss            26726  0 
tpm_tis                 7390  0 
drm                   162377  4 i915,drm_kms_helper
intel_agp              24119  2 i915
iwlcore               105922  1 iwlagn
i2c_algo_bit            5028  1 i915
uvcvideo               56990  0 
tpm                    13484  1 tpm_tis
psmouse                63245  0 
snd_seq_midi            4557  0 
usbnet                 14943  2 zaurus,cdc_ether
video                  17375  1 i915
videodev               34361  1 uvcvideo
led_class               2864  2 thinkpad_acpi,iwlcore
cdc_wdm                 8218  0 
cdc_acm                13538  0 
mii                     4381  1 usbnet
tpm_bios                5266  1 tpm
btusb                  10925  2 
agpgart                31724  2 drm,intel_agp
v4l1_compat            13251  2 uvcvideo,videodev
snd_rawmidi            19056  1 snd_seq_midi
usbhid                 36110  0 
lp                      7028  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nvram                   6171  1 thinkpad_acpi
serio_raw               3978  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
output                  1871  1 video
hid                    67032  1 usbhid
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205146  2 iwlagn,iwlcore
snd                    54148  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,thinkpad_acpi,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              126517  3 iwlagn,iwlcore,mac80211
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
ahci                   32168  2 
e1000e                119824  0 


 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:0d:cd:3b
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f2700000-f271ffff memory:f2925000-f2925fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:ef:a4:fe
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f2500000-f2501fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=no multicas

********part of dmesg **********

[ 4694.988113] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 4724.884053] wlan0: Trigger new scan to find an IBSS to join
[ 4791.416932] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4791.416941] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 9166.664239] e1000e: eth0 NIC Link is Down
[ 9279.920909] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 9279.920918] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 9508.716208] e1000e: eth0 NIC Link is Down
[ 9729.329398] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 9729.329407] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 9822.232242] e1000e: eth0 NIC Link is Down
[10202.201764] wlan0: Trigger new scan to find an IBSS to join
[10206.000132] wlan0: Trigger new scan to find an IBSS to join
[10210.000036] wlan0: Trigger new scan to find an IBSS to join
[10210.000599] wlan0: Creating new IBSS network, BSSID f6:7c:a7:c0:91:68
[10240.000103] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)

---

### Post by nimonika on 2010-06-29
output of ip link

ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 100
    link/ether 00:1f:16:0d:cd:3b brd ff:ff:ff:ff:ff:ff
3: usb0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 02:80:37:ec:02:00 brd ff:ff:ff:ff:ff:ff
4: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 00:16:ea:ef:a4:fe brd ff:ff:ff:ff:ff:ff
5: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether 9e:9f:61:03:8a:51 brd ff:ff:ff:ff:ff:ff

---

