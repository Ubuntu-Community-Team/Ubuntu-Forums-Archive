---
title: "ubuntu 10.04 wireless problems"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by keefy777 on 2010-12-04
Hi all
I cannot get wireless working at all on my laptop
i have 
acer extensa 5235 running 10.04 i never had problems till i had to try using a windows server then all hell broke loose
Under network connections my network shows up but it cannot connect

under iwconfig i get
lo  no wireless extensions
etho no wireless extensions
wlano  IEEE 802.11bgn  ESSID:off/any
Mode: managed Acess Point: Not associated Tx:Power=20dbm
Retry long limit:7  RTS thr:off  Fragment thr:off
Powermanagement : on

your help would be greatly appreciated as i will never go back to windows so its either fix it or go caveman with no internet at all
Ps if there are anyother codes that you want please ask as im sure the one i just posted is useless

---

### Post by MooPi on 2010-12-04
Can you give us the results of 
```
lspci
```
```
lsmod
```

---

### Post by keefy777 on 2010-12-22
keith@keith:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)

---

### Post by keefy777 on 2010-12-22
keith@keith:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_conexant    22641  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
i915                  286079  3 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 306138  0 
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              205402  1 ath9k
ath                     7611  1 ath9k
drm_kms_helper         29297  1 i915
acer_wmi               13861  0 
intel_agp              24119  2 i915
psmouse                63245  0 
serio_raw               3978  0 
atl1c                  28083  0 
cfg80211              126496  3 ath9k,mac80211,ath
led_class               2864  2 ath9k,acer_wmi
drm                   162409  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
lp                      7060  0 
parport                32635  2 ppdev,lp
ahci                   32200  4 
keith@keith:~$ 

I hope this helps its driving me mad

---

### Post by grahammechanical on 2010-12-22
Did you connect to the Windows server by setting up a new wireless connection and thus preserving the settings for the original wireless connection? In other words, are the connection settings the correct ones for the router/modem you want to connect to?

regards.

---

### Post by keefy777 on 2010-12-22
No i was in canada and had a complete mare lost all my internet connections so i have nothing bar the etho connection which i can connect with

---

### Post by keefy777 on 2010-12-22
Sod it im going for 10.10 lets hope that sorts it

---

### Post by grahammechanical on 2010-12-22
Your comment made me smile. You sound English. Not cockney are you?

A fresh install will allow the OS to detect all the hardware and connections. It is a brutal way of doing things. Sometimes it has to be done. Although I think we should sort things out with out needing to do that.

Regards.

---

### Post by keefy777 on 2010-12-22
Well did an upgrade to 10.10 and would you believe it totally ****** .
Wont load at all bloody knightmare i think i am gonna stick to letter writing and pidgeons caveman stylie

---

### Post by keefy777 on 2011-01-02
Bump 
Please anybody help

---

