---
title: "WiFi not found Dell Inspiron Ubuntu 10.04"
date: 2012-07-25
forum: Networking &amp; Wireless
---

### Post by Redeen on 2012-07-25
WiFi was working well, but at some point, perhaps after an update, it stopped. First I could only connect at home, now it fails to display available wifi sources at all.  

I am running Ubuntu 10.04 LTS Lucid on a Dell Inspiron 1420. I have skipped upgrades because I installed Ubuntu Studio over plain vanilla Ubuntu, and what with the custom kernel of the Studio distro, didn't want to rock the boat. 

Listing my hardware shows both Broadcom Netlink BCM5906M nad Intel Pro/Wireless 3945ABG[Golan].  

I have tried a lot of different suggestions on the forum, to no avail, and at this point, probably need to untangle bad fixes.  I will make a separate post on attempts to do a clean install of the latest Ubuntu Studio, but to summarize - could not do it from DVD or stick.  Was hoping an upgrade might solve this WiFi issue or at least give me a fresh chance to reconfigure. 


DIAGNOSTICS

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)


rfkill list all 
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxdrv               122371  0 
snd_hda_codec_idt      52074  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_usb_audio          75765  0 
joydev                  8740  0 
snd_usb_lib            15801  1 snd_usb_audio
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_idt,snd_hda_intel
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_pcm                70694  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_hwdep               5412  2 snd_usb_audio,snd_hda_codec
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                68727  0 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
i915                  290740  2 
iwlcore               106149  1 iwl3945
dell_laptop             6888  0 
sdhci_pci               5470  0 
drm_kms_helper         29329  1 i915
snd                    54244  18 snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              205434  2 iwl3945,iwlcore
dcdbas                  5422  1 dell_laptop
psmouse                63677  0 
serio_raw               3978  0 
drm                   163779  3 i915,drm_kms_helper
intel_agp              24375  2 i915
sdhci                  15494  1 sdhci_pci
led_class               2864  3 iwl3945,iwlcore,sdhci
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
cfg80211              126528  3 iwl3945,iwlcore,mac80211
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
ohci1394               26950  0 
hid                    67288  1 usbhid
ieee1394               81181  1 ohci1394
ahci                   32680  3 
tg3                   109324  0 

Sorry my first post is so long!  I am Okay with simply doing a clean install to Ubuntu Studio 12.04 if that turns out to be simplest and I can get past the problem booting from thumb drive (cannot write a DVD). LMK if more info is needed, and thank you in advance.

---

### Post by Redeen on 2012-07-26
It looks like the upgrade will fix the problem and is overdue.

---

