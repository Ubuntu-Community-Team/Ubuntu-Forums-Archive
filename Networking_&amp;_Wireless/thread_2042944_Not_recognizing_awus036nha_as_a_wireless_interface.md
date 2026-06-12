---
title: "Not recognizing awus036nha as a wireless interface"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by paperweight1 on 2012-08-15
I just got an alfa awus036nha, which has an atheros ar9271 chipset and  it doesn't seem to be working.  I think the driver I want is ath9k_htc  and I'm almost certain that that installed correctly.  The firmware  seems to be there as well.  The device shows up fine under lsusb, but  the interface doesn't show up with iwconfig/ifconfig.  Can anyone point  out something stupid that I'm doing please?

I accidentally posted this already in General Help.  I didn't know how to move it, so I just reposted here.

---

### Post by praseodym on 2012-08-15
Which system do you use? Please show:

```
uname -a
lsusb
lsmod
dmesg | grep 9170
```

---

### Post by paperweight1 on 2012-08-15
```
adam@adam-HP-Pavilion-dv6-Notebook-PC:~$ uname -a
Linux adam-HP-Pavilion-dv6-Notebook-PC 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
adam@adam-HP-Pavilion-dv6-Notebook-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 064e:e258 Suyin Corp. 
Bus 003 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
adam@adam-HP-Pavilion-dv6-Notebook-PC:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
nf_conntrack_irc       13383  0 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
bnep                   18281  2 
vboxdrv               287130  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
ip6t_LOG               16974  3 
xt_hl                  12521  6 
ip6t_rt                12558  3 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
nf_conntrack_ipv6      13906  9 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  8 
xt_limit               12711  12 
xt_tcpudp              12603  16 
xt_addrtype            12713  0 
binfmt_misc            17540  1 
xt_state               12578  15 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
arc4                   12529  2 
nf_conntrack_ftp       13452  1 nf_nat_ftp
iptable_nat            13229  0 
nf_nat                 25891  3 ipt_MASQUERADE,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iwlwifi               332525  0 
nf_conntrack           81926  11 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
mac80211              506816  1 iwlwifi
radeon                804372  0 
i915                  472941  3 
ttm                    76949  1 radeon
drm_kms_helper         46978  2 radeon,i915
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
rts_pstor             445196  0 
cfg80211              205544  2 iwlwifi,mac80211
x_tables               29846  17 ipt_MASQUERADE,xt_DSCP,ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_nat,iptable_mangle,iptable_filter,ip_tables
wmi                    19256  1 hp_wmi
hp_accel               25976  0 
drm                   242038  6 radeon,i915,ttm,drm_kms_helper
i2c_algo_bit           13423  2 radeon,i915
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87692  0 
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lis3lv02d              19876  1 hp_accel
serio_raw              13211  0 
mac_hid                13253  0 
input_polldev          13896  1 lis3lv02d
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
adam@adam-HP-Pavilion-dv6-Notebook-PC:~$ dmesg | grep 9170
adam@adam-HP-Pavilion-dv6-Notebook-PC:~$ 

```

---

