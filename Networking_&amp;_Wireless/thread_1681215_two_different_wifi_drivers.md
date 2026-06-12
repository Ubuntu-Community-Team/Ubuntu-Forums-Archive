---
title: "two different wifi drivers?"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by u-noob-tu on 2011-02-03
when i go into additional drivers, only two drivers pop up, both for my wireless card. however, i can only use the first one because if i try to use them both it breaks my wifi, forcing me to reinstall the first driver. ordinarily, this wouldnt bother me because it works with just one, but i realized the other day that the reason it takes forever to do anything internet related is because im getting pathetic transfer speeds. the highest i can remember is only 800 kb/s. ive tried standing right next to the router and it makes no difference. i know its my drivers fault because i get the same speeds at two different home wifi networks (both houses roughly the same size). my ipod gets a better connection. the driver im using is a broadcom b43 proprietary driver. the one that breaks the working driver is a broadcom STA proprietary driver. i havent bothered to try the second without the first because i just didnt think about it, but i think i will soon and see if it makes any difference. does anyone have an idea as to why my driver sucks? im tired of waiting 20 minutes to watch a 3 minute youtube video.

---

### Post by u-noob-tu on 2011-02-04
Gentle *BUMP*

---

### Post by TBABill on 2011-02-04
Yes, you CANNOT use both. They conflict. And if you have installed both then  you may have a bit of a mess in /etc/modules and /etc/modprobe.d/blacklist.conf. Fixable, but will have to be step by step.

First, need to know which wireless device you have. Some need the b43, others the STA. Please just run these in a terminal and post the outputs ```
lspci
``` and ```
lsmod
``` and then paste the contents of the file /etc/modprobe.d/blacklist.conf

---

### Post by u-noob-tu on 2011-02-04
okay heres the output of lspci:```
 ryan@ryan-Studio-1737:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
ryan@ryan-Studio-1737:~$ 
```

and heres lsmod:```
 ryan@ryan-Studio-1737:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54919  1 
joydev                  8767  0 
snd_hda_intel          22203  4 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
i915                  295243  3 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
arc4                    1165  2 
drm                   168092  3 i915,drm_kms_helper
dell_wmi_aio            1733  0 
snd_timer              19067  2 snd_pcm,snd_seq
b43                   168681  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              231959  1 b43
uvcvideo               55847  0 
snd                    49038  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                2852  0 
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
cfg80211              144694  2 b43,mac80211
mtd                    18877  2 sm_common,nand
psmouse                59033  0 
intel_agp              26566  2 i915
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
sdhci_pci               6339  0 
usbhid                 36882  0 
hid                    67742  1 usbhid
firewire_ohci          21234  0 
sdhci                  15890  1 sdhci_pci
ahci                   19198  2 
led_class               2633  2 b43,sdhci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
tg3                   123310  0 
ssb                    39320  1 b43
libahci                21728  1 ahci
ryan@ryan-Studio-1737:~$ 
```

and heres blacklist.conf:```
 # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

not sure what any of this means.

---

### Post by TBABill on 2011-02-04
In lsmod you see b43 and ssb listed. Those need to be blacklisted, meaning the system will ignore them. So to do this just ```
sudo gedit /etc/modprobe.d/blacklist.conf
``` and add these 2 lines to the end of the file ```
blacklist b43
blacklist ssb
``` You also must place the character # in front of where it says "blacklist bcm43xx", which will REMOVE the blacklist effect without removing the text (in case it needs to be restored later). The # statements are ignored.

Then ```
sudo apt-get update
``` then ```
sudo apt-get install --reinstall bcmwl-kernel-source
```

Once that is done, open modules file and verify "wl" is listed without quotes. The wl is the actual driver (named the STA driver) so it must be listed in /etc/modules to be activated upon boot. TO verify, just ```
sudo gedit /etc/modules
``` and ONLY if it is not listed, add only the letters wl as a last line of the file. IMPORTANT: make sure you REMOVE the b43 and ssb lines from /etc/modules OR you can just precede them with # to ignore them. If wl is already there, just get rid of b43 and ssb or # them, then restart and see if it works.

---

