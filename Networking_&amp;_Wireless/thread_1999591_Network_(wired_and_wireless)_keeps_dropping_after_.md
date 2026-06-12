---
title: "Network (wired and wireless) keeps dropping after upgrade to 12.04"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by farrukh_najmi on 2012-06-08
I have upgraded to 12.04 on two laptops and one desktop all with different network cards. On the laptops I had problems with wifi connections kee getting dropped (wired worked). On the desktop I see the wired connection keeps getting dropped. It seems like many posts exist regarding such issues in 12.04 but nothing that has helped me fix the problem. Can someone plese tell me if there is a solution. I have reverted the laptops to 11.10 so I have some reliable systems :-(. However on the desktop I would like to fix this problem seen in 12.04.

Here is a similar question posted with no answer (sorry I found it after posting mine):

[http://askubuntu.com/questions/126227/12-04-wired-network-doesnt-work-rtl8111-8168b](http://askubuntu.com/questions/126227/12-04-wired-network-doesnt-work-rtl8111-8168b)

Here is info on my networking hardware on the wired desktop:

> 
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:f0100000-f01fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 5c:ac:4c:b0:11:62
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.0.0-20-generic firmware=N/A ip=10.0.0.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f0100000-f010ffff

        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:f0500000-f08fffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: 60:eb:69:2b:12:19
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0010000-f001ffff


---

### Post by farrukh_najmi on 2012-06-08
The following link finally fixed the problem for me:

[http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)

---

### Post by farrukh_najmi on 2012-06-21
I spoke too soon. I am still having the network drop issue on both wired and wireless 
networks. I would really appreciate if someone can help me get this fixed. Thanks.

---

### Post by wildmanne39 on 2012-06-21
Hi, let's see if we can fix the wireless issue, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by farrukh_najmi on 2012-06-22
Hi wildmanne39, Since I posted I returned the wireless adapter I had borrowed. So now I just have a wired network. I found that reinstalling the network drivers again seemed to make the network adapter claimed and working (of and on). It seems to stop working after some unknown event. Also it may be intermittently dropping and restarting. The problem seems to be something about the RTL8111/8168B PCI Express Gigabit Ethernet controller, according to what I have read. Any idea what to try next? Thanks very much.


Here is the output you requested:

```

cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux wellfleet1 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8168

ifconfig
eth4      Link encap:Ethernet  HWaddr 00:24:1d:76:88:94  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe76:8894/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35498963 (35.4 MB)  TX bytes:2491505 (2.4 MB)
          Interrupt:43 Base address:0x4000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:466810 (466.8 KB)  TX bytes:466810 (466.8 KB)

rfkill list all
(returns no output)

lsmod
Module                  Size  Used by
vboxnetadp             13382  0
vboxnetflt             28302  0
vboxdrv               268179  2 vboxnetadp,vboxnetflt
bnep                   18139  2
rfcomm                 46621  0
bluetooth             185573  10 bnep,rfcomm
parport_pc             32866  0
ppdev                  17113  0
binfmt_misc            17540  1
dm_crypt               23125  0
xt_hl                  12521  6
ip6t_rt                12558  3
nf_conntrack_ipv6      13906  6
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1
ipt_LOG                12919  4
xt_limit               12711  6
xt_tcpudp              12603  22
xt_addrtype            12713  4
xt_state               12578  13
nvidia              12319264  44
ip6table_filter        12815  1
ip6_tables             27864  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1
tuner_simple           18551  1
ip_tables              27473  1 iptable_filter
tuner_types            24318  1 tuner_simple
tda9887                14154  1
x_tables               29846  12 xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
tda8290                22616  0
snd_hda_codec_realtek   223867  1
tuner                  27428  2
msp3400                36458  1
snd_hda_intel          33773  3
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
saa7127                18234  1
saa7115                23031  1
snd_usb_audio         122982  2
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_hwdep              13668  2 snd_hda_codec,snd_usb_audio
snd_seq_midi           13324  0
ivtv                  160120  0
cx2341x                28331  1 ivtv
i2c_algo_bit           13423  1 ivtv
v4l2_common            16454  6 tuner,msp3400,saa7127,saa7115,ivtv,cx2341x
snd_pcm                97188  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
videodev               98259  7 tuner,msp3400,saa7127,saa7115,ivtv,cx2341x,v4l2_common
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
edac_core              53746  0
serio_raw              13211  0
sp5100_tco             13791  0
v4l2_compat_ioctl32    17128  1 videodev
joydev                 17693  0
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
k10temp                13166  0
snd                    78855  21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_mce_amd           23709  0
tveeprom               21249  1 ivtv
i2c_piix4              13301  0
hid_logitech_dj        18593  0
wmi                    19256  0
mac_hid                13253  0
firewire_sbp2          22941  0
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
ses                    17417  0
enclosure              15269  1 ses
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
uas                    18180  0
usb_storage            49198  1
firewire_ohci          41000  0
firewire_core          63558  2 firewire_sbp2,firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13204  0
r8168                 244911  0
pata_jmicron           12747  0



```

> **wildmanne39 said:**
> Hi, let's see if we can fix the wireless issue, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by wildmanne39 on 2012-06-22
Hi, if you compiled a new driver or reinstalled the driver then I do not know how to help with your wired issue, as I mentioned when I answered your post it was to help with wireless because I have been working with wireless issues and I know very little about wired issues.

---

### Post by gordintoronto on 2012-06-22
Where did you get a "wellfleet1" kernel?

---

