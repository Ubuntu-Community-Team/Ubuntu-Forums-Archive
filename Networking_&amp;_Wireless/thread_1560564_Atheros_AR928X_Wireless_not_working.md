---
title: "Atheros AR928X Wireless not working"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by Legend28469 on 2010-08-25
I know there have been a few posts about this, but this one is brand new.

I purchased a new MSI Wind U123 which came preloaded with Windows 7 Starter.

I tried getting drivers for it... but.. none of that seemed to work, anyways I checked in device manager and it gave an error 10

I preceded to installing Ubuntu Network Remix (9.10) wifi wasn't working and then i upgraded to 10.04

It isn't working at all I've tried madwifi (for those going to say to do so) and everything... so i feel hopeless...

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

I dont see the relevancy but heres lsusb
```
Bus 005 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 5986:0203 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:24:21:67:a6:13  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe67:a613/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57799930 (57.7 MB)  TX bytes:2379187 (2.3 MB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3104 (3.1 KB)  TX bytes:3104 (3.1 KB)

```

iwconfig (please notice there are no wlan0 (for some reason)
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

lsmod

```
Module                  Size  Used by
ath_pci               193325  0 
wlan                  223148  1 ath_pci
ath_hal               398604  1 ath_pci
rfcomm                 33421  4 
binfmt_misc             6587  1 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
ppdev                   5259  0 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_realtek   203310  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               56990  0 
ath9k                 306010  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
btusb                  10925  2 
mac80211              205146  1 ath9k
i915                  285076  5 
ath                     7611  1 ath9k
videodev               34361  1 uvcvideo
psmouse                63245  0 
drm_kms_helper         29297  1 i915
cfg80211              126517  3 ath9k,mac80211,ath
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24119  2 i915
serio_raw               3978  0 
drm                   162409  6 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
led_class               2864  1 ath9k
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  0 
r8169                  34076  0 
mii                     4381  1 r8169

```

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

Currently on Ubuntu Network Edition 10.04.1

Its as if it knows my wireless card is there, but is unable to use it. I've tried getting the original drivers from Atheros for Windows 7, didn' work.. and yes I've turned on the wifi using FN + F11 a few times.. i've even tried the windows update drivers... and in ubuntu i've tried madwifi... nothing seems to work...

---

### Post by Legend28469 on 2010-08-25
bump.

---

### Post by Legend28469 on 2010-08-25
Bump =c

---

### Post by Hobgoblin on 2010-08-25
Are you saying the wifi didn't work in Windows when you purchased the (new) system?

Perhaps it is faulty?

---

