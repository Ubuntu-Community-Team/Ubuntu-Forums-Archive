---
title: "Dell insprion 1525 wireless not working"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by radicaledward on 2011-10-07
hey, I'm new to linux, I'm trying to get my wireless working with a DELL inspiron 1525, downloaded the most recent ubuntu last night, downloaded the broadcom STA driver and it says that it's loaded and working...
tried wicd, to config and it failed
heres

lspci:
code:```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
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
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


```


lsmod
code:
```


Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_codec_hdmi     27535  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
i915                  451033  3 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
joydev                 17322  0 
wl                   2642531  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
dell_laptop            13515  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14054  1 dell_laptop
snd                    55295  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   17878  0 
psmouse                73312  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
uvcvideo               66851  0 
soundcore              12600  1 snd
drm_kms_helper         40745  1 i915
videodev               75143  1 uvcvideo
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
drm                   184164  4 i915,drm_kms_helper
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
mtd                    26720  2 sm_common,nand
i2c_algo_bit           13184  1 i915
lib80211               14570  1 wl
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
libahci                25548  1 ahci
sky2                   49172  0 
theo@theocrastus:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_codec_hdmi     27535  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
i915                  451033  3 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
joydev                 17322  0 
wl                   2642531  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
dell_laptop            13515  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14054  1 dell_laptop
snd                    55295  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   17878  0 
psmouse                73312  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
uvcvideo               66851  0 
soundcore              12600  1 snd
drm_kms_helper         40745  1 i915
videodev               75143  1 uvcvideo
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
drm                   184164  4 i915,drm_kms_helper
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
mtd                    26720  2 sm_common,nand
i2c_algo_bit           13184  1 i915
lib80211               14570  1 wl
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
libahci                25548  1 ahci
sky2                   49172  0 


```

hope this helps!

---

### Post by westie457 on 2011-10-07
Hi assuming you are using Natty you have the wrong drivers installed. 
Open Software Centre Click the Settings.... button (bottom left) in Ubuntu Software tab check the top 4 boxes and close the window.

Open Synaptic Package Manager if you have it installed -if not then install it.

In the quick search box type in bcm you should have something that looks like this picture. Mark the firmware -b43-installer and b43-fwcutter to install and mark the STA driver for complete removal. Click apply, When this has finished unplug the cable and reboot. Log in to your wireless.

---

### Post by radicaledward on 2011-10-07
that worked perfectly, thanks a bunch, I guess sometimes all of the general instructions are just wrong...

---

### Post by nariknahom on 2011-10-14
> **westie457 said:**
> Hi assuming you are using Natty you have the wrong drivers installed. 
Open Software Centre Click the Settings.... button (bottom left) in Ubuntu Software tab check the top 4 boxes and close the window.

Open Synaptic Package Manager if you have it installed -if not then install it.

In the quick search box type in bcm you should have something that looks like this picture. Mark the firmware -b43-installer and b43-fwcutter to install and mark the STA driver for complete removal. Click apply, When this has finished unplug the cable and reboot. Log in to your wireless.

This worked perfectly .
(Dell Inspiron 1525 with bcm4311)

---

