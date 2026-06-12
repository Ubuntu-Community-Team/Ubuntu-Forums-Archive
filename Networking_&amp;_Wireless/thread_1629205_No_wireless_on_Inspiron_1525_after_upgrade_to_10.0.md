---
title: "No wireless on Inspiron 1525 after upgrade to 10.04 Lucid"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by Kernelingus on 2010-11-23
I have one of those Dell Inspiron 1525s from a couple years ago that shipped with Hardy.  Its OEM adaptor is the Intel iwl3945, which worked fine until I upgraded to 8.04.  At that point NetworkManager stopped recognizing the adaptor, but I could still manage it manually or with Wifi-Radar.

Now that I'm up to 10.04, Wifi-Radar no longer works at all and the NetworkManager problem persists.  I have one of those little USB wifi sticks with the RealTek chipset, and the system picks that one up just fine.  So what's up with the iwl3945?

$lspci

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

$lsmod

> Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_idt      51914  1 
snd_hda_codec_intelhdmi    11622  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
mmc_block               8258  2 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                68727  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               105922  1 iwl3945
i915                  282354  3 
sbp2                   19448  0 
usbhid                 36110  0 
drm_kms_helper         29297  1 i915
mac80211              204922  2 iwl3945,iwlcore
hid                    67032  1 usbhid
ricoh_mmc               2923  0 
sdhci_pci               5470  0 
dell_wmi                1793  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  3 iwl3945,iwlcore,sdhci
snd                    54148  17 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
cfg80211              126485  3 iwl3945,iwlcore,mac80211
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24177  2 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  2 sbp2,ohci1394
sky2                   40775  0 
ahci                   32008  2 
luke@dell-desktop:~$ lsmod
Module                  Size  Used by
usb_storage            39425  1 
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8901  2 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_idt      51914  1 
snd_hda_codec_intelhdmi    11622  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
mmc_block               8258  2 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                68727  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               105922  1 iwl3945
i915                  282354  3 
sbp2                   19448  0 
usbhid                 36110  0 
drm_kms_helper         29297  1 i915
mac80211              204922  2 iwl3945,iwlcore
hid                    67032  1 usbhid
ricoh_mmc               2923  0 
sdhci_pci               5470  0 
dell_wmi                1793  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  3 iwl3945,iwlcore,sdhci
snd                    54148  17 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
cfg80211              126485  3 iwl3945,iwlcore,mac80211
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24177  2 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  2 sbp2,ohci1394
sky2                   40775  0 
ahci                   32008  2 

What am I missing here?

---

### Post by lukeiamyourfather on 2010-11-23
Have you been upgrading from version to version or doing a clean install? I'd try a live disc to see if it works there. Also check the hardware drivers in case that one has a proprietary driver. What do you get when you run this?

```
lshw -C network
```

---

### Post by Kernelingus on 2010-11-23
Been upgrading version to version.  First encountered NetworkManager issue on a live CD however, IIRC.

Here's what I get with lshw -C network

>  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e7:a6:62
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:c0:67:75
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:fe7ff000-fe7fffff

Intel says something about how "iwlwifi" drivers, which are now part of the kernel, are supposed to work for this adaptor.  I don't know what the deal is with iwl3945.  I tried blacklisting it to see if the system would detect the device and load a more appropriat driver, but that didn't work.

Dunno where to go from here.

---

### Post by Kernelingus on 2010-11-23
By default, /etc/NetworkManager/nm-system-settings.conf has the following:

> [ifupdown]
managed=false

Changing this to "true" and restarting did the trick.  :D

---

