---
title: "Ubuntu 12.04 wireless not working on my Acer Aspire 7000"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by millner on 2012-06-26
[/CODE]windows@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu quantal (development branch)"
Linux ubuntu 3.5.0-1-generic #1-Ubuntu SMP Tue Jun 19 14:24:43 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
windows@ubuntu:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Acer Incorporated [ALI] Device [1025:0112]
	Kernel driver in use: forcedeth
--
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
	Kernel modules: wl, ssb
windows@ubuntu:~$ lsusb
Bus 001 Device 003: ID 0951:1643 Kingston Technology DataTraveler G3 4GB
Bus 001 Device 002: ID 5986:0100 Acer, Inc Orbicam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
windows@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

windows@ubuntu:~$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
windows@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17461  1 
fat                    61282  1 vfat
usb_storage            48838  1 
uas                    17890  0 
bnep                   18140  2 
rfcomm                 46619  0 
parport_pc             32688  0 
bluetooth             208922  8 bnep,rfcomm
ppdev                  17073  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
snd_hda_codec_realtek    73449  1 
joydev                 17457  0 
acer_wmi               32244  0 
sparse_keymap          13890  1 acer_wmi
snd_hda_intel          33491  3 
snd_hda_codec         133856  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
nouveau               895650  3 
snd_seq_midi           13324  0 
ttm                    83595  1 nouveau
wl                   2573568  0 
drm_kms_helper         46784  1 nouveau
drm                   275484  5 nouveau,ttm,drm_kms_helper
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
pcmcia                 48964  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13413  1 nouveau
tifm_7xx1              13042  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
snd                    78734  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                86228  0 
serio_raw              13215  0 
yenta_socket           31817  0 
pcmcia_rsrc            18288  1 yenta_socket
videobuf2_memops       13368  1 videobuf2_vmalloc
tifm_core              15690  1 tifm_7xx1
edac_core              52451  0 
soundcore              15047  1 snd
nv_tco                 13564  0 
edac_mce_amd           23303  0 
mxm_wmi                12979  1 nouveau
k8temp                 12978  0 
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i2c_nforce2            13013  0 
video                  19335  2 acer_wmi,nouveau
wmi                    19070  3 acer_wmi,nouveau,mxm_wmi
lib80211               14381  1 wl
mac_hid                13205  0 
pata_amd               14118  0 
sata_nv                31830  1 
forcedeth              67156  0 
[/CODE]

---

### Post by nothingspecial on 2012-06-26
Please don't create duplicate threads.

Thanks.

---

