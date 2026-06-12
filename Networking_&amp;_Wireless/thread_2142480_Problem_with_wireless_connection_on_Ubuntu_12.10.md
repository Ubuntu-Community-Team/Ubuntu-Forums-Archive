---
title: "Problem with wireless connection on Ubuntu 12.10"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by yuvalf11 on 2013-05-05
Hey guys,

I'm pretty new in ubuntu. I have ubuntu 12.10 on my hp Pavilion g series, and I just installed some updates and now I can't connect to a wireless network. When i ran the system testing it's comment was:
> 
Error: root: Could not find def gateway info in /proc
Error: root: could not find default gateway by running route


when I wrote in the terminal lspci -nn | grep 0280, it returned:
> 
01:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]

Help will be great, thanks!

---

### Post by Hadaka on 2013-05-05
Hi, please post the output of..
```
lsmod
rfkill list all
```
thanks.

---

### Post by yuvalf11 on 2013-05-05
The output:
> 
Module                  Size  Used by
ipt_MASQUERADE         12664  1 
xt_state               12515  1 
ipt_REJECT             12486  2 
xt_tcpudp              12532  4 
iptable_filter         12707  1 
nf_nat_h323            12810  0 
nf_conntrack_h323      51811  1 nf_nat_h323
nf_nat_pptp            12537  0 
nf_conntrack_pptp      13554  1 nf_nat_pptp
nf_conntrack_proto_gre    13581  1 nf_conntrack_pptp
nf_nat_proto_gre       12672  1 nf_nat_pptp
nf_nat_tftp            12421  0 
nf_conntrack_tftp      12818  1 nf_nat_tftp
nf_nat_sip             16946  0 
nf_conntrack_sip       24511  1 nf_nat_sip
nf_nat_irc             12543  0 
nf_conntrack_irc       13113  1 nf_nat_irc
nf_nat_ftp             12549  0 
nf_conntrack_ftp       13107  1 nf_nat_ftp
iptable_nat            12978  1 
nf_nat                 20317  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      14081  4 iptable_nat,nf_nat
nf_conntrack           66308  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12650  1 nf_conntrack_ipv4
ip_tables              17792  2 iptable_filter,iptable_nat
x_tables               21936  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_idt      59762  1 
joydev                 17162  0 
coretemp               13169  0 
rfcomm                 37277  0 
kvm                   357807  0 
bnep                   17708  2 
parport_pc             31969  0 
bluetooth             183270  10 rfcomm,bnep
ppdev                  12818  0 
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
binfmt_misc            17261  1 
microcode              18210  0 
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
psmouse                84878  0 
snd_hda_intel          32516  3 
serio_raw              13032  0 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
rtsx_pci_ms            12876  0 
memstick               15843  1 rtsx_pci_ms
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
wmi                    18591  1 hp_wmi
arc4                   12474  2 
rt2800pci              18153  0 
rt2800lib              57182  1 rt2800pci
crc_ccitt              12628  1 rt2800lib
rt2x00pci              14152  1 rt2800pci
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              48602  3 rt2800pci,rt2800lib,rt2x00pci
mac_hid                13038  0 
i915                  457241  3 
drm_kms_helper         47304  1 i915
lpc_ich                16926  0 
mac80211              461261  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              175574  2 rt2x00lib,mac80211
eeprom_93cx6           13169  1 rt2800pci
mei                    35797  0 
snd                    62146  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   238811  4 i915,drm_kms_helper
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13198  1 i915
video                  18895  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17239  0 
ahci                   25497  2 
r8169                  55977  0 
libahci                25938  1 ahci
rtsx_pci               32060  2 rtsx_pci_ms,rtsx_pci_sdmmc
yuval@Bens-Ubuntu:~$ rfkill
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1ubuntu3 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm





Thanks!

---

### Post by yuvalf11 on 2013-05-05
```

Module                  Size  Used by
ipt_MASQUERADE         12664  1 
xt_state               12515  1 
ipt_REJECT             12486  2 
xt_tcpudp              12532  4 
iptable_filter         12707  1 
nf_nat_h323            12810  0 
nf_conntrack_h323      51811  1 nf_nat_h323
nf_nat_pptp            12537  0 
nf_conntrack_pptp      13554  1 nf_nat_pptp
nf_conntrack_proto_gre    13581  1 nf_conntrack_pptp
nf_nat_proto_gre       12672  1 nf_nat_pptp
nf_nat_tftp            12421  0 
nf_conntrack_tftp      12818  1 nf_nat_tftp
nf_nat_sip             16946  0 
nf_conntrack_sip       24511  1 nf_nat_sip
nf_nat_irc             12543  0 
nf_conntrack_irc       13113  1 nf_nat_irc
nf_nat_ftp             12549  0 
nf_conntrack_ftp       13107  1 nf_nat_ftp
iptable_nat            12978  1 
nf_nat                 20317  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      14081  4 iptable_nat,nf_nat
nf_conntrack           66308  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12650  1 nf_conntrack_ipv4
ip_tables              17792  2 iptable_filter,iptable_nat
x_tables               21936  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_idt      59762  1 
joydev                 17162  0 
coretemp               13169  0 
rfcomm                 37277  0 
kvm                   357807  0 
bnep                   17708  2 
parport_pc             31969  0 
bluetooth             183270  10 rfcomm,bnep
ppdev                  12818  0 
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
binfmt_misc            17261  1 
microcode              18210  0 
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
psmouse                84878  0 
snd_hda_intel          32516  3 
serio_raw              13032  0 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
rtsx_pci_ms            12876  0 
memstick               15843  1 rtsx_pci_ms
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
wmi                    18591  1 hp_wmi
arc4                   12474  2 
rt2800pci              18153  0 
rt2800lib              57182  1 rt2800pci
crc_ccitt              12628  1 rt2800lib
rt2x00pci              14152  1 rt2800pci
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              48602  3 rt2800pci,rt2800lib,rt2x00pci
mac_hid                13038  0 
i915                  457241  3 
drm_kms_helper         47304  1 i915
lpc_ich                16926  0 
mac80211              461261  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              175574  2 rt2x00lib,mac80211
eeprom_93cx6           13169  1 rt2800pci
mei                    35797  0 
snd                    62146  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   238811  4 i915,drm_kms_helper
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13198  1 i915
video                  18895  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17239  0 
ahci                   25497  2 
r8169                  55977  0 
libahci                25938  1 ahci
rtsx_pci               32060  2 rtsx_pci_ms,rtsx_pci_sdmmc
yuval@Bens-Ubuntu:~$ rfkill
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1ubuntu3 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm



```

---

### Post by Hadaka on 2013-05-05
Hi,looks like you have alot of goodies in there.
let's try to reset your wireless driver and also
remove the windows mgmt thing.
please do..
```

sudo rmmod -f hp-wmi
sudo modprobe -rfv rt2800pci
modprobe rt2800pci
 
```
does that help?

---

### Post by yuvalf11 on 2013-05-05
No, I still have the same problem. when I tried to log into my wireless network, a message pops:
> 
Connection activation failed
(32) Connection could not be found.


---

### Post by Hadaka on 2013-05-05
Hi, my knowledge of iptables,conntrack is very limited
so I am not sure where to look on your network for a
problem.Perhaps someone with more experience in this
area will chime in. sorry i was not able to help you.

---

### Post by yuvalf11 on 2013-05-05
I don't know how but now it's working.
Thank you very much!

---

### Post by alien_sporez on 2013-06-09
Sadly, I'm having the exact same problem. The only difference is, I can connect wirelessly to my office WiFi, but not to my home WiFi.

Output from **rfkill list all** and **lsmod**

```
david@Aspire:~$ rfkill list all0: phy0: Wireless LAN
            Softblocked: no
            Hardblocked: no
1: brcmwl-0: Wireless LAN
            Softblocked: no
            Hardblocked: no
2: acer-wireless: Wireless LAN
            Softblocked: no
            Hardblocked: no
david@Aspire:~$ lsmod
Module                 Size  Used by
michael_mic           12540  0
arc4                  12543  0
pci_stub              12550  1
vboxpci               22896  0
vboxnetadp            25636  0
vboxnetflt             27261 0
vboxdrv              285137  3vboxnetadp,vboxnetflt,vboxpci
dm_crypt              22321  1
joydev                17097  0
acer_wmi              27592  0
sparse_keymap         13658  1 acer_wmi
parport_pc            27504  0
ppdev                 12817  0
kvm_amd               50336  0
uvcvideo              71279  0
kvm                  376505  1 kvm_amd
videobuf2_vmalloc     12920  1 uvcvideo
videobuf2_memops      13042  1 videobuf2_vmalloc
videobuf2_core        39161  1 uvcvideo
rfcomm                37420  0
bnep                  17669  2
bluetooth            202069  10 bnep,rfcomm
videodev              95806  2 uvcvideo,videobuf2_core
lib80211_crypt_tkip   17160  0
microcode             18286  0
snd_hda_codec_conexant   52256  1
snd_seq_midi          13132  0
snd_seq_midi_event    14475  1 snd_seq_midi
wl                  2902185  0
binfmt_misc           17260  1
snd_hda_codec_hdmi    36185  1
lib80211              14040  2 wl,lib80211_crypt_tkip
k10temp               12958  0
psmouse               81038  0
snd_hda_intel         38307  5
snd_rawmidi           25114  1 snd_seq_midi
serio_raw             13031  0
cfg80211             436177  1 wl
snd_hda_codec        117580  3snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep             13272  1 snd_hda_codec
snd_seq               51280  2snd_seq_midi_event,snd_seq_midi
snd_pcm               80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
sp5100_tco            13447  0
i2c_piix4             13066  0
snd_seq_device        14137  3snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc        14230  2 snd_pcm,snd_hda_intel
snd_timer             24411  2 snd_pcm,snd_seq
snd                   56485  20snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore             12600  1 snd
mac_hid               13037  0
lp                     13299  0
parport               40753  3 lp,ppdev,parport_pc
radeon               870822  3
i2c_algo_bit          13197  1 radeon
ttm                   71289  1 radeon
drm_kms_helper        47545  1 radeon
drm                  228750  5ttm,drm_kms_helper,radeon
wmi                   18590  1 acer_wmi
atl1c                 36175  0
video                 18894  1 acer_wmi
ahci                  25507  2
libahci               26108  1 ahci
```

Any help would be greatly appreciated. I'm also a bit of a noob.

---

