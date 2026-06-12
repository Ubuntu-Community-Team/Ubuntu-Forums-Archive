---
title: "Realtek wireless in 12.04 will randomly stop working, must restart computer"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by rainwalker on 2013-02-09
The networking applet will still show me as connected (until I disconnect), but nothing loads in a browser nor responds to ping. If I try to disconnect/reconnect, all I get is an endless spinning activity circle. Turning wireless off and back on does not fix the issue. 

I haven't had any luck pinpointing the cause. It has happened with my personal wireless network as well as at my university. I can't tell if it happens after a certain amount of time. The only "solution" I've found is to restart my computer.

I have very little networking knowledge, so I'm not sure how to go about debugging things. Any suggestions?

lspci -nn:
```
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
```

lsmod | sort:
```
arc4                   12529  2 
binfmt_misc            17540  1 
bluetooth             180153  10 rfcomm,bnep
bnep                   18281  2 
cfg80211              205774  2 rtlwifi,mac80211
edac_core              53746  0 
edac_mce_amd           23709  0 
fglrx                3264017  55 
hid                    99636  2 hid_logitech_dj,usbhid
hid_logitech_dj        18730  0 
i2c_piix4              13301  0 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
ip6t_LOG               16974  4 
ip6t_rt                12558  3 
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
ipt_LOG                12919  5 
ipt_REJECT             12576  1 
joydev                 17693  0 
k10temp                13166  0 
lp                     17799  0 
mac80211              506862  2 rtl8192se,rtlwifi
mac_hid                13253  0 
Module                  Size  Used by
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_conntrack_ipv6      13906  7 
nf_conntrack_netbios_ns    12665  0 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_defrag_ipv6         13412  1 nf_conntrack_ipv6
nf_nat                 25891  1 nf_nat_ftp
nf_nat_ftp             12704  0 
nvram                  14413  1 thinkpad_acpi
parport                46562  3 parport_pc,ppdev,lp
parport_pc             32866  0 
pci_stub               12622  1 
ppdev                  17113  0 
psmouse                97485  0 
r8169                  62154  0 
rfcomm                 47604  0 
rtl8192se              99989  0 
rtlwifi               111245  1 rtl8192se
serio_raw              13211  0 
shpchp                 37277  0 
snd                    79041  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33773  4 
snd_hwdep              17764  1 snd_hda_codec
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_timer              29990  2 snd_pcm,snd_seq
soundcore              15091  1 snd
sp5100_tco             13791  0 
thinkpad_acpi          81819  0 
uas                    18180  0 
ums_realtek            18248  0 
usbhid                 47238  1 hid_logitech_dj
usb_storage            49198  1 ums_realtek
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxpci                23237  0 
vesafb                 13844  1 
video                  19596  0 
wmi                    19256  0 
x_tables               29891  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
xt_addrtype            12713  4 
xt_hl                  12521  6 
xt_limit               12711  12 
xt_state               12578  14 
xt_tcpudp              12603  18
```

sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:af:4a:77
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:c000(size=256) memory:d0204000-d0204fff memory:d0200000-d0203fff memory:d0220000-d023ffff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 10
       serial: 88:9f:fa:fa:a5:9c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.2.0-37-generic firmware=N/A ip=192.168.1.126 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:d000(size=256) memory:d0500000-d0503fff
```

---

### Post by assiotis on 2013-03-22
I have the exact same problem, not sure what to do, didn't use to happen with oneiric. I tried different networks, different routers on the same network

[INDENT][FONT=fixedsys]03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 35)[/FONT][/INDENT]

---

