---
title: "RLT8185L detected as Bluetooth maybe?"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by NEO Dan on 2011-11-05
So I am attempting to get a friend running 11.10 on a Gateway MT3705. AFIK Bluetooth is not an option on this model.

Unfortunately I am a total NOOB when it comes to most things nix based, but I think the wireless pci card may be picked up as a bluetooth:
```
pita@POS1000:~$ sudo lspci -nn 
[sudo] password for pita: 
00:00.0 Host bridge [0600]: ATI Technologies Inc Device [1002:5a31] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
pita@POS1000:~$ lsmod
Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  10 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
iptable_nat            13016  0 
nf_nat                 24958  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           70103  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
joydev                 17393  0 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                925020  3 
psmouse                73673  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
ttm                    65224  1 radeon
video                  18908  0 
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
i2c_piix4              13093  0 
ati_agp                13242  0 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
pata_atiixp            12967  2 
sky2                   49317  0 
pita@POS1000:~$
```Everything else seems to work OTB. I can't find any wireless options, and I've tried switching the unit on and off with the function keys. It was on when I did the clean install. 

Any help would be most appreciated.

Thanks!

Regards,
Dan

---

