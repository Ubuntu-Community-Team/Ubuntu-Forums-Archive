---
title: "HP Tower w AMD 64-bit CPU, Ubuntu9.04, Netgear Wireless PCI Card"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by fremeup on 2009-07-22
HP tower(vertical desktop) with Wireless PCI card from Netgear, running Ubuntu 9.04.  Unable to connect as simply(or at all in this case, thus the problem) to wireless network as I have done with other Ubuntu LiveCD's on another computer(laptop, though).
Side note:  I get a prompt to press, I think, shift + F10 to configure a Realtek something.  More on that later, but it comes up with or without my having physically installed the wireless card.
Interestingly enough, I don't believe I see Netgear anywhere here
type what is past ($ )the dollar sign and space are not typed


ubuntu@ubuntu:~$ lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:08.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem


ubuntu@ubuntu:~$ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 13ba:0017  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




<<Here I suspect a problem(below)

ubuntu@ubuntu:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



ubuntu@ubuntu:~$ lsmod

Module                  Size  Used by
binfmt_misc            18572  1 
ppdev                  16904  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
radeon                357792  2 
drm                   123232  3 radeon
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
snd_atiixp             27796  3 
snd_ac97_codec        133848  1 snd_atiixp
ac97_bus               10368  1 snd_ac97_codec
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                64028  0 
shpchp                 44572  0 
serio_raw              14468  0 
pcspkr                 11136  0 
k8temp                 13440  0 
i2c_piix4              20112  0 
snd                    78792  16 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_atiixp,snd_pcm
squashfs               48656  1 
aufs                  193384  1 
exportfs               13440  1 aufs
isofs                  43688  1 
nls_iso8859_1          13440  0 
nls_cp437              15104  1 
vfat                   21120  0 
fat                    65592  1 vfat
hid_dell               10752  0 
usbhid                 47040  1 hid_dell
usb_storage            94912  0 
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
8139too                36608  0 
8139cp                 31488  0 
mii                    14464  2 8139too,8139cp
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

---

### Post by fremeup on 2009-07-22
I looked on the PCI Card and read the following:
"Wireless PCI Adapter WG311v3
Rev. A1
MAC(the MAC address here)
S/N(the social security )then  MADE IN CHINA.

By the by, I don't know which data it is "safe" to post...(here or from terminal replies...)

---

