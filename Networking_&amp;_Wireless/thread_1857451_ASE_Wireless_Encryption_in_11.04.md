---
title: "ASE Wireless Encryption in 11.04"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by Pete.uk352 on 2011-10-10
[SIZE=3][FONT=Arial]Hi all, [/FONT][/SIZE]
[SIZE=3][FONT=Arial]After a bit of help, I am attempting to connect to my university wireless. I have a wired connection at home and that works fine. The university asks for WPA2-Enterprise with AES security. I believe I have the relevant CA certificate but I am unsure how to configure for AES Encryption.[/FONT][/SIZE]
[SIZE=3][FONT=Arial]My system:[/FONT][/SIZE]
[SIZE=3][FONT=Arial]HP – G61 Notebook[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Intel Pentium D 64bit[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Natty 11.04 64bit[/FONT][/SIZE]
[SIZE=3][FONT=Arial]Lshw –C[/FONT][/SIZE]
```
 *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:5d:a7:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d3500000-d350ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:f8:55:f9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff

```
 
[SIZE=3][FONT=Arial]lsmod [/FONT][/SIZE]
```
Module                  Size  Used by
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  560 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  1 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
joydev                 17606  0 
snd_hda_intel          33176  4 
arc4                   12529  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 118238  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ipt_REJECT             12576  1 
ipt_LOG                17016  6 
mac80211              294370  1 ath9k
xt_multiport           12597  2 
snd                    67382  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           13851  1 ath9k
xt_limit               12711  8 
xt_tcpudp              12603  22 
xt_state               12578  5 
ipt_addrtype           12599  4 
ip6table_filter        12815  1 
psmouse                73535  0 
ip6_tables             27845  1 ip6table_filter
ath9k_hw              323077  2 ath9k,ath9k_common
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12649  0 
nf_nat                 25736  2 nf_nat_irc,nf_nat_ftp
serio_raw              13166  0 
nf_conntrack_ipv4      19640  7 nf_nat
ath                    23773  2 ath9k,ath9k_hw
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
uvcvideo               72195  0 
nf_conntrack_ftp       13359  1 nf_nat_ftp
videodev               82052  1 uvcvideo
nf_conntrack           81956  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
v4l2_compat_ioctl32    17078  1 videodev
iptable_filter         12810  1 
cfg80211              178528  3 ath9k,mac80211,ath
ip_tables              27456  1 iptable_filter
x_tables               29581  11 ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6table_filter,ip6_tables,iptable_filter,ip_tables
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
i915                  515121  3 
drm_kms_helper         42136  1 i915
ahci                   25951  3 
drm                   227534  4 i915,drm_kms_helper
r8169                  48022  0 
libahci                26642  1 ahci
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
```
 
[SIZE=3][FONT=Arial]lspci [/FONT][/SIZE]
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```
 
[SIZE=3][FONT=Arial]Any Help will be appreciated, thanks People.:)[/FONT][/SIZE]

---

### Post by Pete.uk352 on 2011-10-13
[FONT=Arial]Done some more reading around and found that AES is part of the WPA2 standard. I have also found the relevant certificate (just in case it helps somebody they are at /ect/ssl/certs). Sadly I still cannot connect to my uni network, any one had similar problems doing this??   :confused:[/FONT]

---

### Post by Pete.uk352 on 2011-10-13
Sorted. Please find attached screen shot of my wireless settings. Hope this helps somebody.  ;)

---

