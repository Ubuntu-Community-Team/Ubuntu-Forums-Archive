---
title: "Can't get wireless to work"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by zlyoga on 2010-06-21
So I I have an asus ee pc 1005peb
Initially I installed ubuntu netbook edition on it and wireless worked fine out of the box

But I had to do a full disk encryption for work and ende3d up reinstalling the os with the desktop version rather than netbook, because it was easier to go about full disk encryption this way.

I'm using version 10.04

But now I can not get wireless to work.
What might be different between the two versions to cause this problem?

I can detect networks using wifi-radar, but once I hit connect I get stuck at "Aquiring IP Address (DHCP)" forever

---

### Post by zlyoga on 2010-07-03
Any insight anyone?

---

### Post by roosh on 2010-07-03
I've been hearing there are problems with Lucid's wireless. Could you please run these commands in a terminal and post their outputs:
```
lsusb
``` ```
lspci
``` ```
lsmod
```

---

### Post by zlyoga on 2010-07-04
> **roosh said:**
> I've been hearing there are problems with Lucid's wireless. Could you please run these commands in a terminal and post their outputs:
```
lsusb
``` ```
lspci
``` ```
lsmod
```

```

lee@cutenetbook:~$ lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 003: ID 13d3:5111 IMC Networks 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lee@cutenetbook:~$ lspci

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)

01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

lee@cutenetbook:~$ lsmod

Module                  Size  Used by

nls_iso8859_1           3249  0 

nls_cp437               4919  0 

vfat                    8901  0 

fat                    47767  1 vfat

binfmt_misc             6587  1 

ppdev                   5259  0 

snd_hda_codec_realtek   203168  1 

snd_hda_intel          21877  2 

snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel

snd_hwdep               5412  1 snd_hda_codec

snd_pcm_oss            35308  0 

snd_mixer_oss          13746  1 snd_pcm_oss

arc4                    1153  2 

snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss

joydev                  8708  0 

snd_seq_dummy           1338  0 

snd_seq_oss            26726  0 

ath9k                 306010  0 

snd_seq_midi            4557  0 

mac80211              204922  1 ath9k

snd_rawmidi            19056  1 snd_seq_midi

snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi

ath                     7611  1 ath9k

snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

uvcvideo               56990  0 

snd_timer              19098  2 snd_pcm,snd_seq

videodev               34361  1 uvcvideo

psmouse                63245  0 

v4l1_compat            13251  2 uvcvideo,videodev

snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

lp                      7028  0 

cfg80211              126485  3 ath9k,mac80211,ath

atl1c                  28083  0 

serio_raw               3978  0 

led_class               2864  1 ath9k

snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore               6620  1 snd

snd_page_alloc          7076  2 snd_hda_intel,snd_pcm

parport                32635  2 ppdev,lp

sha256_generic         11191  2 

aes_i586                7268  2 

aes_generic            26863  1 aes_i586

dm_crypt               11331  1 

fbcon                  35102  72 

tileblit                2031  1 fbcon

font                    7557  1 fbcon

bitblit                 4707  1 fbcon

softcursor              1189  1 bitblit

vga16fb                11385  0 

vgastate                8961  1 vga16fb

i915                  282354  4 

drm_kms_helper         29297  1 i915

drm                   162471  5 i915,drm_kms_helper

i2c_algo_bit            5028  1 i915

intel_agp              24177  2 i915

ahci                   32008  2 

usb_storage            39425  0 

agpgart                31724  2 drm,intel_agp

video                  17375  1 i915

output                  1871  1 video

lee@cutenetbook:~$ 





```

---

### Post by camorri on 2010-07-05
I have the same wireless card, and it works once I configured it for my router. 

```
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

It used the ath9k driver. Please run the command 'lsmod | grep ath9k' and post the results. I would expect to see several lines of output. If not, the driver is not loaded. 

If it is loaded, you may need to configure the hardware through Network Manager.

---

### Post by zlyoga on 2010-07-10
I need to use it for wireless at work where there are many different routers I might use depending on where in the building I am.

---

### Post by camorri on 2010-07-12
Please run the command > command 'lsmod | grep ath9k' no quotes,  and post the results. That driver should work. Beyond that, you will need a little configuration for the different access points you may need to connect to. You can enter the config through Network Manager.

---

