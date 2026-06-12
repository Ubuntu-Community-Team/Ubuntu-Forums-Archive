---
title: "No AV/C Complian cam connected or not switched on?"
date: 2011-07-07
forum: Multimedia Software
---

### Post by rechlac on 2011-07-07
Greeting all, I been facing this problem for some days now.  I have installed ubuntu 10.4 and now 9.1 with same result.  After I manage to get the priv for /dev/dv1394, I got this error from Kino (1.3.3).  Camcorder is Panasonic GS-NV27, using 4pin firewire for connection.  Suggestion are welcome.

```

No AV/C compliant cam connected or not switch on?
 in console with dvgrab;
Error: no camera exists

```lspci
```

 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)
04:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```lsmod
```

Module                  Size  Used by
firewire_ohci          22976  0 
firewire_core          47296  1 firewire_ohci
crc_itu_t               1852  1 firewire_core
raw1394                25308  0 
ieee1394               86596  1 raw1394
binfmt_misc             8356  1 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
ppdev                   6688  0 
snd_hda_codec_conexant    20060  1 
snd_hda_codec_nvhdmi     4828  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_conexant,snd_hda_codec_nvhdmi,snd_hda_intel
snd_usb_audio          84224  2 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
lp                      8964  0 
arc4                    1660  2 
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            16284  1 snd_usb_audio
parport                35340  2 ppdev,lp
snd_hwdep               7200  2 snd_hda_codec,snd_usb_audio
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
ecb                     2524  2 
snd_seq_midi            6432  0 
iwlagn                109052  0 
snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
sdhci_pci               7100  0 
iwlcore               112508  1 iwlagn
sdhci                  17472  1 sdhci_pci
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                56180  0 
joydev                 10272  0 
serio_raw               5280  0 
led_class               4096  2 iwlcore,sdhci
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
snd                    59204  21 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              11692  1 iptable_filter
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
soundcore               7264  1 snd
mac80211              181236  2 iwlagn,iwlcore
x_tables               16544  1 ip_tables
cfg80211               93052  3 iwlagn,iwlcore,mac80211
usbhid                 38208  0 
video                  19380  0 
output                  2780  1 video
tg3                   109600  0 
intel_agp              27484  0 
agpgart                34988  1 intel_agp

```dmesg|grep fire
```

[    1.711697] firewire_ohci 0000:08:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.780042] firewire_ohci: Added fw-ohci device 0000:08:06.0, OHCI version 1.10
[    2.280107] firewire_core: created device fw0: GUID 00023f87c9402a1b, S400
[  672.340342] firewire_ohci 0000:08:06.0: PCI INT A disabled
[  672.340350] firewire_ohci: Removed fw-ohci device.
[  688.906286] firewire_ohci 0000:08:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  688.976072] firewire_ohci: Added fw-ohci device 0000:08:06.0, OHCI version 1.10
[  688.976104] firewire_ohci: IRQ 00030010 selfID AR_req busReset
[  688.976131] firewire_ohci: IRQ 00020000 busReset
[  688.976138] firewire_ohci: 1 selfIDs, generation 1, local node ID ffc0
[  688.976147] firewire_ohci: selfID 0: 807f8842, phy 0 [-..] S400 gc=63 +0W Lci
[  688.976169] firewire_ohci: AR evt_bus_reset, generation 1
[  689.476457] firewire_core: created device fw0: GUID 00023f87c9402a1b, S400
[  752.994017] firewire_ohci: IRQ 00200000 cycle64Seconds
[  817.027542] firewire_ohci: IRQ 00200000 cycle64Seconds
[  881.060894] firewire_ohci: IRQ 00200000 cycle64Seconds
[  945.062751] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1009.064221] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1073.065815] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1137.067450] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1201.068884] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1265.070357] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1329.072053] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1393.073420] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1457.074996] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1521.076533] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1585.078202] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1649.079549] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1713.081206] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1777.082832] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1841.084376] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1905.085740] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 1969.087303] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2033.089004] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2097.090416] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2161.091980] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2225.093458] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2289.095044] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2353.096543] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2417.098128] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2481.099630] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2545.101161] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2609.102878] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2673.104260] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2737.105779] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2801.107341] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2865.108914] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2929.110561] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 2993.111979] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 3057.113633] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 3121.115173] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 3185.116593] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 3249.118080] firewire_ohci: IRQ 00200000 cycle64Seconds
[ 3313.119612] firewire_ohci: IRQ 00200000 cycle64Seconds

```ACTION taken
```

Add my user to VIDEO, DISK.
sudo ln /dev/fw0 /dev/raw1394
recomment blacklist-firewire.conf, initramfs, reboot and still nothing.

```

---

### Post by no2498 on 2011-07-07
see if this program finds the cam xawtv
it installs a cam grabber

---

### Post by rechlac on 2011-07-07
Well, Kino / dvgrab didn't detect a camera at all.  So far I google I didn't see any reference for xawtv with firewire.

update
```

tried install kdenlive also can't detect camera.

```
anybody could help out?  Thank!
No body have any idea?

---

