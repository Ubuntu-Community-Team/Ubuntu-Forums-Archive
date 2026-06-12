---
title: "Wireless broken with last updated"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by Lucio1972 on 2012-04-06
I follow this  [thread]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")
but my Wireless is now broken ....



```

cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux COMPUTER_1 2.6.35-32-generic #67-Ubuntu SMP Mon Mar 5 19:35:26 UTC 2012 i686 GNU/Linux

lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7309]
    Kernel driver in use: forcedeth
--
01:09.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
    Subsystem: Netgear WG311v3 802.11g Wireless PCI Adapter [1385:6b00]

lsusb
Bus 002 Device 002: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 001 Device 002: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


rfkill list all

<nothing>


lsmod
Module                  Size  Used by
ufs                    73069  0 
qnx4                    6877  0 
hfsplus                71344  0 
hfs                    41410  0 
minix                  25303  0 
ntfs                   95030  0 
msdos                   6436  0 
jfs                   171034  0 
xfs                   693543  0 
exportfs                3449  1 xfs
reiserfs              225974  0 
ndiswrapper           184207  0 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  2 msdos,vfat
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218460  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
nvidia               7088432  34 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49102  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
psmouse                59027  0 
serio_raw               4022  0 
i2c_nforce2             5179  0 
agpgart                32011  1 nvidia
k8temp                  3228  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67934  1 usbhid
btrfs                 489690  0 
zlib_deflate           19266  1 btrfs
usb_storage            40492  1 
floppy                 54311  0 
sata_nv                19420  0 
pata_amd                8746  2 
crc32c                  2531  1 
forcedeth              49433  0 
libcrc32c                887  1 btrfs



```Help me please ... !!!!! thx

---

