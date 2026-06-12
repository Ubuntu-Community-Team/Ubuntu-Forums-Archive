---
title: "wireless too slow"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by Mr.Pytagoras on 2012-06-07
Hi 

I have an Atheros wifi card. If I connect to anything with wifi I can not get higher speed then 1.2MB/s, I tried many hotspots (WPA, WEP, no-encryption) and created an adhoc  network and tried the speed between two computers but still 1.2MB is the higher limit. 

Here are some information about the wireless:
```
jkalmar@supercomp:~$ lspci | grep -i wireless
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
``````
jkalmar@supercomp:~$ lspci -vv -s 03:00.0
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e034
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at b0600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k
```

and lsmod
```
jkalmar@supercomp:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
ipt_MASQUERADE         12759  0 
xt_state               12578  0 
ipt_REJECT             12576  0 
xt_tcpudp              12603  0 
iptable_filter         12810  0 
nf_nat_h323            17002  0 
nf_conntrack_h323      62913  1 nf_nat_h323
nf_nat_pptp            12629  0 
nf_conntrack_pptp      13830  1 nf_nat_pptp
nf_conntrack_proto_gre    13656  1 nf_conntrack_pptp
nf_nat_proto_gre       12767  1 nf_nat_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      12953  1 nf_nat_tftp
nf_nat_sip             17086  0 
nf_conntrack_sip       29730  1 nf_nat_sip
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12704  0 
nf_conntrack_ftp       13452  1 nf_nat_ftp
iptable_nat            13229  0 
nf_nat                 25891  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           81926  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
snd_hrtimer            12744  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  2 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17693  0 
arc4                   12529  2 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd                    78855  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k                 132390  0 
i915                  468651  3 
psmouse                87603  0 
serio_raw              13211  0 
mac80211              506816  1 ath9k
mei                    41616  0 
drm_kms_helper         46978  1 i915
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
drm                   242038  4 i915,drm_kms_helper
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
i2c_algo_bit           13423  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
video                  19596  1 i915
wmi                    19256  1 acer_wmi
mac_hid                13253  0 
coretemp               13525  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
mmc_block              27300  2 
usbhid                 47199  0 
hid                    99559  1 usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
tg3                   152032  0
```

```
jkalmar@supercomp:~$ lsmod | grep ath
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
```


I have already google this, and found a solution but it didn't work for me.
[This]("http://ubuntuforums.org/showthread.php?t=1746326") and [this]("http://ubuntuforums.org/showthread.php?t=1877120") didn't help.

Any idea how to speed it up?

---

