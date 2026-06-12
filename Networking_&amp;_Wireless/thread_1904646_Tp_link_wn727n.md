---
title: "Tp link wn727n"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by Laufer on 2012-01-05
Hi i have the same model of adaptor and i dont now or cand connect it to my wireless network
```
laufer@ubuntu:~$ sudo su
[sudo] password for laufer: 
root@ubuntu:/home/laufer# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux ubuntu 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
root@ubuntu:/home/laufer# lspci -nnk | grep -iA2 net
01:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
root@ubuntu:/home/laufer# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntu:/home/laufer# lsusb
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 055f:021f Mustek Systems, Inc. SNAPSCAN e22
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 148f:5370 Ralink Technology, Corp. 
Bus 001 Device 006: ID 09da:9090 A4 Tech Co., Ltd 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ubuntu:/home/laufer# lsusb
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 055f:021f Mustek Systems, Inc. SNAPSCAN e22
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 09da:9090 A4 Tech Co., Ltd 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ubuntu:/home/laufer# rfkill list all
root@ubuntu:/home/laufer# lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_intel8x0           25652  2 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_ac97_codec        100646  1 snd_intel8x0
softcursor              1189  1 bitblit
ac97_bus                1002  1 snd_ac97_codec
vga16fb                11385  0 
snd_pcm_oss            35308  0 
vgastate                8961  1 vga16fb
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               467048  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    50103  1 nouveau
drm_kms_helper         29329  1 nouveau
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162377  4 nouveau,ttm,drm_kms_helper
soundcore               6620  1 snd
gspca_zc3xx            45189  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
gspca_main             21199  1 gspca_zc3xx
i2c_algo_bit            5028  1 nouveau
joydev                  8740  0 
shpchp                 28835  0 
nvidia_agp              4483  1 
i2c_nforce2             5199  0 
videodev               34361  1 gspca_main
ppdev                   5259  0 
usbhid                 36110  0 
agpgart                31724  3 ttm,drm,nvidia_agp
v4l1_compat            13251  1 videodev
lp                      7028  0 
parport_pc             25962  1 
parport                32635  3 ppdev,lp,parport_pc
hid                    67288  1 usbhid
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
pata_amd                8766  1 
floppy                 53016  0 
root@ubuntu:/home/laufer#
```

---

### Post by coffeecat on 2012-01-05
@Laufer, I've moved your post into its own thread and changed the title since you are using Ubuntu, not Backtrack. Please start your own threads if you need help rather than posting in others'. I've also added code tags to make your terminal output readable.

---

