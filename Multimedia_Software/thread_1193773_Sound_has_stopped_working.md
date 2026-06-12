---
title: "Sound has stopped working"
date: 2009-06-21
forum: Multimedia Software
---

### Post by Jordanwb on 2009-06-21
I'm trying to watch a video on youtube (if flash'll stop crashing Firefox) and I'm not getting any sound. I play an mp3 through vlc and nothing. I have the sound turned up to max. I go to volume control and I don't have any of the alsa related devices, just pulse-audio. It was working fine last night.

Lsmod:

> jordanwb@jordanwb-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  0 
nls_cp437              13696  0 
vfat                   18816  0 
fat                    58272  1 vfat
usb_storage            82880  0 
binfmt_misc            16776  1 
ppdev                  15620  0 
radeon                342816  2 
drm                    96296  3 radeon
vboxnetflt             92200  0 
vboxdrv               121384  1 vboxnetflt
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               63240  0 
psmouse                61972  0 
ieee80211_crypt_tkip    16896  0 
led_class              12036  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
ati_agp                14988  0 
shpchp                 40212  0 
serio_raw              13316  0 
wl                   1489748  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
i2c_piix4              18448  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
agpgart                42696  2 drm,ati_agp
k8temp                 12416  0 
video                  25360  0 
output                 11008  1 video
cbc                    11648  1 
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
sha256_generic         20352  0 
dm_crypt               20996  1 
aes_i586               15744  1 
aes_generic            35880  1 aes_i586

lspci:

> jordanwb@jordanwb-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

I did update some of the software last night. One/Some of them was Alsa related. How can I find out what was updated? Perhaps a downgrade'll fix it.

[Edit]

I don't know what happened. I rebooted and sound is working again. :confused:

---

