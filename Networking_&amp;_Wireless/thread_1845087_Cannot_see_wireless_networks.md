---
title: "Cannot see wireless networks"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by Awes0meSauce on 2011-09-16
Hello everyone, I just installed Ubuntu 11.04 on my old Dell Inspiron 1501 laptop and everything works great except for my wireless. When I installed, I was hard wired so I could install the 200 something updates! So this morning I went to setup my wireless but the thing is my laptop does not detect any wireless networks at all. I only have an edit connections options. Now I have not tried manually typing in the SSID and selecting the security, in past installs I was able to just choose a wireless network, type in the password, and I was on my merry way. Here is some info on my wireless:

```
lspci -nn

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
**05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)**
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
``````
lsmod

Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
radeon                982152  3 
snd_seq_midi_event     14899  1 snd_seq_midi
**b44                    36000  0 (I believe this is the one you are looking for)**
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
dell_laptop            13827  0 
ssb                    51945  1 b44
ttm                    76664  1 radeon
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14438  1 dell_laptop
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42136  1 radeon
**wl                   2568244  0 (****and this one?)**
drm                   227534  5 radeon,ttm,drm_kms_helper
edac_core              53845  0 
i2c_algo_bit           13400  1 radeon
psmouse                73535  0 
shpchp                 37297  0 
soundcore              12680  1 snd
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14991  1 wl
k8temp                 13016  0 
sp5100_tco             13744  0 
edac_mce_amd           23464  0 
i2c_piix4              13303  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  5 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
pata_atiixp            13165  0 
libahci                26642  1 ahci

```I hope you have  all the info that you need, if not please tell me. Any help would be much appreciated, thanks for your time.

---

### Post by wildmanne39 on 2011-09-16
Hi, open synaptic and type in bcm or broadcom and remove every thing with a green square by it. There should only be between 2 and 4 packages there that have a green square by it if there is more post a screenshot of it and do not remove any of them.

Then restart your computer.

Now run this command please:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
disconnect your wired connection and restart your computer and it should be working if not post back.
Thank you

---

### Post by Awes0meSauce on 2011-09-16
> **wildmanne39 said:**
> Hi, open synaptic and type in bcm or broadcom and remove every thing with a green square by it. There should only be between 2 and 4 packages there that have a green square by it if there is more post a screenshot of it and do not remove any of them.

Then restart your computer.

Now run this command please:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```disconnect your wired connection and restart your computer and it should be working if not post back.
Thank you
Thank you so much! :D It worked like a charm after a reboot. In fact, I'm posting this via wireless. I attached a picture in case anyone is having a similar problem. Just remove the package my cursor is on, run the command and your good to go. Again, thank you.

[http://tiny.cc/d5u0y](http://tiny.cc/d5u0y)

---

### Post by wildmanne39 on 2011-10-02
Hi, your welcome! I am glad it worked.

---

