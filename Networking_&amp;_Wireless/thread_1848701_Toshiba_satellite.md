---
title: "Toshiba satellite"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by ManAbradesStars on 2011-09-23
Hello,

I have a toshiba satellite l645, or more accuratly my roommate does, and I just installed Ubuntu on it, and its not detecting any wireless networks. To be fair, my internet kinda of sucks, but when I boot in windows I can access the network fine, so I figured I'd check if there was some issue with the wireless card being used properly by Ubuntu. I am still pretty new to linux, and all that I do know I learned working on web servers, and this installation is my frist adventure into linux personal computing. I know enough shell commands to have run some things that I think may be useful to anyone who wants to help me, so here is the out put of a couple commands I ran:

[SIZE=3]**Output of lsmod**[/SIZE]:

```

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_seq_dummy           1338  0 
softcursor              1189  1 bitblit
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
i915                  288611  3 
snd                    54244  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29329  1 i915
soundcore               6620  1 snd
drm                   162377  4 i915,drm_kms_helper
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
psmouse                63677  0 
video                  17375  1 i915
uvcvideo               57374  0 
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
serio_raw               3978  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39841  0 
ahci                   32360  3 

```[SIZE=3]**output of lspci -knn**[/SIZE] :

```

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
    Kernel modules: i2c-i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

```when I review the output of those commands, I gleam a vague sense of what I am looking at, but not enough to take any real steps, so any advice you guys would have for moving forward is greatly appreciated, including commands to run, files to check, and so forth if any one would like more information.

Thanks!

---

### Post by garvinrick4 on 2011-09-23
"07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
Subsystem: Realtek Semiconductor Co., Ltd. Device 8181

#Open a terminal and copy and paste these commands one at a time.

 ```
sudo add-apt-repository ppa:lexical/hwe-wireless
``` 
 ```
sudo apt-get update
``` 
 ```
sudo apt-get install rtl8192ce-dkms
``` 
 ```
sudo reboot
```
Take out your wired cable and wireless should be working.

---

### Post by ManAbradesStars on 2011-09-29
Hey, Thanks for the reply, windows 7 wrote over the grub files, and so after dealing with that, and working all week, I was just now able to get back to this. I never even tried it with an Ethernet cable, it looks like the Ethernet card is not working either. I nosed around a bit on the ubuntu documentation to work on this, and decided to run pppoeconf as the root user, and it said:
>  sorry, no working Ethernet card could be found. If you have a Ethernet card that was not autodetected, you may want to try running modconf

And so I did, and it says not found. 

What do?

---

