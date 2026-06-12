---
title: "Ubuntu Hardy w/ Linksys WMP110 -- Can't connect to network"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by mfive on 2009-02-08
Ok, so I'm a ubuntu newbie, and I'm using gnome as well.

I've searched and searched and tried several different methods, including using madwifi, wicd (with WEXT drivers turned on), and of course, ndiswrapper.

I STILL cannot get this card to work.
I'm currently using Wicd, and I can SEE other networks. If I click "Connect" to a specific network, it will say that it connects and "assigns" me an IP, but I can never get internet from it. Nor can I log into my router.

I'm all about getting a different wifi card, provided it has some sort of "extended range" feature, as I'm stretching it distance wise already. (This card is reporting my router is 35% signal). Distance is not the connecting factor, as I have 2 computers in the same room on XP connected just fine.

The machine is home built using an ASRock motherboard.

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:F0:43:3D   
          Bit Rate=36 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
lsmod
Module                  Size  Used by
ndiswrapper           192664  0 
rfcomm                 41744  2 
l2cap                  25600  13 rfcomm
bluetooth              60900  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6404  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
battery                14212  0 
ip6table_filter         3584  1 
iptable_raw             3328  0 
xt_comment              2688  0 
xt_policy               4736  0 
ipt_ULOG               10116  0 
ipt_TTL                 3200  0 
ipt_ttl                 2816  0 
ipt_TOS                 3200  0 
ipt_tos                 2560  0 
ipt_SAME                3200  0 
ipt_REJECT              5632  4 
ipt_REDIRECT            2944  0 
ipt_recent             10264  0 
ipt_owner               2944  0 
ipt_NETMAP              2944  0 
ipt_MASQUERADE          4608  0 
ipt_LOG                 7296  11 
ipt_iprange             2688  0 
ipt_ECN                 3840  0 
ipt_ecn                 3200  0 
ipt_CLUSTERIP           9604  0 
ipt_ah                  2816  0 
ipt_addrtype            2816  0 
nf_nat_tftp             2816  0 
nf_nat_snmp_basic      11140  0 
nf_nat_sip              5760  0 
nf_nat_pptp             4608  0 
nf_nat_proto_gre        3716  1 nf_nat_pptp
nf_nat_irc              3712  0 
nf_nat_h323             8576  0 
nf_nat_ftp              4352  0 
nf_nat_amanda           3328  0 
ts_kmp                  3072  5 
nf_conntrack_amanda     5888  1 nf_nat_amanda
nf_conntrack_tftp       6036  1 nf_nat_tftp
nf_conntrack_sip       10132  1 nf_nat_sip
nf_conntrack_proto_sctp     9864  0 
nf_conntrack_pptp       8064  1 nf_nat_pptp
nf_conntrack_proto_gre     7040  1 nf_conntrack_pptp
nf_conntrack_netlink    28800  0 
nf_conntrack_netbios_ns     3840  0 
nf_conntrack_irc        7576  1 nf_nat_irc
nf_conntrack_h323      51164  1 nf_nat_h323
ipv6                  272932  22 nf_conntrack_h323
nf_conntrack_ftp       10144  1 nf_nat_ftp
xt_tcpmss               3200  0 
xt_pkttype              2816  4 
xt_physdev              3600  0 
xt_NFQUEUE              2816  0 
xt_NFLOG                2944  0 
xt_multiport            4224  4 
xt_MARK                 3200  0 
xt_mark                 2816  0 
xt_mac                  2816  0 
xt_limit                3584  0 
xt_length               2816  0 
xt_helper               3584  0 
xt_hashlimit           11276  0 
ip6_tables             15844  2 ip6table_filter,xt_hashlimit
xt_dccp                 4356  0 
xt_conntrack            3712  0 
xt_CONNMARK             4224  0 
xt_connmark             3200  0 
xt_CLASSIFY             2688  0 
xt_tcpudp               4096  20 
xt_state                3328  12 
iptable_nat             8324  0 
nf_nat                 20268  14 ipt_SAME,ipt_REDIRECT,ipt_NETMAP,ipt_MASQUERADE,nf_nat_tftp,nf_nat_sip,nf_nat_pptp,nf_nat_proto_gre,nf_nat_irc,nf_nat_h323,nf_nat_ftp,nf_nat_amanda,nf_conntrack_netlink,iptable_nat
nf_conntrack_ipv4      19080  14 iptable_nat
nf_conntrack           66752  29 ipt_MASQUERADE,ipt_CLUSTERIP,nf_nat_tftp,nf_nat_snmp_basic,nf_nat_sip,nf_nat_pptp,nf_nat_irc,nf_nat_h323,nf_nat_ftp,nf_nat_amanda,nf_conntrack_amanda,nf_conntrack_tftp,nf_conntrack_sip,nf_conntrack_proto_sctp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_conntrack_netlink,nf_conntrack_netbios_ns,nf_conntrack_irc,nf_conntrack_h323,nf_conntrack_ftp,xt_helper,xt_conntrack,xt_CONNMARK,xt_connmark,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  1 
nfnetlink               5784  1 nf_conntrack_netlink
iptable_filter          3840  1 
ip_tables              14820  4 iptable_raw,iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  44 xt_comment,xt_policy,ipt_ULOG,ipt_TTL,ipt_ttl,ipt_TOS,ipt_tos,ipt_SAME,ipt_REJECT,ipt_REDIRECT,ipt_recent,ipt_owner,ipt_NETMAP,ipt_MASQUERADE,ipt_LOG,ipt_iprange,ipt_ECN,ipt_ecn,ipt_CLUSTERIP,ipt_ah,ipt_addrtype,xt_tcpmss,xt_pkttype,xt_physdev,xt_NFQUEUE,xt_NFLOG,xt_multiport,xt_MARK,xt_mark,xt_mac,xt_limit,xt_length,xt_helper,xt_hashlimit,ip6_tables,xt_dccp,xt_conntrack,xt_CONNMARK,xt_connmark,xt_CLASSIFY,xt_tcpudp,xt_state,iptable_nat,ip_tables
ac                      6916  0 
af_packet              23684  2 
lp                     12324  0 
loop                   19076  0 
snd_intel8x0           35356  2 
snd_ac97_codec        100772  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_es1938             23844  3 
snd_seq_dummy           4868  0 
gameport               16008  2 snd_es1938
snd_pcm_oss            42016  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                78596  4 snd_intel8x0,snd_ac97_codec,snd_es1938,snd_pcm_oss
snd_opl3_lib           12928  1 snd_es1938
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_es1938
snd_seq_oss            35456  0 
snd_seq_midi            9248  0 
snd_rawmidi            25632  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_seq_dummy,snd_opl3_lib,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56868  25 snd_intel8x0,snd_ac97_codec,snd_es1938,snd_seq_dummy,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
evdev                  12928  3 
intel_agp              25620  1 
button                  9232  0 
soundcore               8800  1 snd
parport_pc             36644  1 
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
agpgart                34760  1 intel_agp
parport                37704  3 ppdev,lp,parport_pc
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
ext3                  136584  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36496  0 
sr_mod                 17828  0 
cdrom                  37280  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
usbhid                 32384  0 
hid                    38784  1 usbhid
ata_piix               19588  2 
8139cp                 25088  0 
pata_acpi               8320  0 
libata                159600  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151180  4 sg,sr_mod,sd_mod,libata
floppy                 59332  0 
8139too                27776  0 
mii                     6400  2 8139cp,8139too
ehci_hcd               38412  0 
uhci_hcd               27152  0 
usbcore               146284  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36616  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

Any help would be appreciated, even if it is to steer me into buying a different range booster network adapter that will work. 

Thanks a million!

---

### Post by mfive on 2009-02-10
Anybody? Anybody at alll???

---

### Post by mfive on 2009-02-11
Ok, Update!!!

I just upgraded to Ubuntu 8.10. I can see all wireless routers. I can even connect to them and Ubuntu tells me it has connected. I can see that it is getting an IP address, but if I try to ping my router I get nothing.

Also, I'm not getting any internet at all in Firefox.

---

### Post by superprash2003 on 2009-02-11
post output of **ifconfig** from the terminal.. also post output of **iwconfig**

---

