---
title: "no wireless after upgrade"
date: 2012-06-30
forum: Networking &amp; Wireless
---

### Post by raymondvillain on 2012-06-30
Running 11.10 (64 bit) on an HP dv6308nr notebook computer (AMD chips, nvidia graphics).  Tried to use 12.04 but had to go back to 11.10.

This machine is dual boot, Windows Vista and Ubuntu.

Booting to Windows my wireless works well.

Booting to Ubuntu I have no wireless at all.  The little orange light on the front of the machine used to change to blue, indicating wireless was active.  It does that now for Windows, but when I boot to Ubuntu it stays orange, indicating no wireless capability.  Network over plug in cable works fine.

Before I tried upgrading to 12.04 wireless worked perfectly in Ubuntu.

Why is ubuntu now disabling wireless, apparently at the hardware level?

Is there a way to fix this?

---

### Post by wildmanne39 on 2012-07-01
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by raymondvillain on 2012-07-01
```
daddy@VULCAN:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux VULCAN 3.0.0-22-generic #36-Ubuntu SMP Tue Jun 12 17:37:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
```
daddy@VULCAN:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
	Kernel modules: wl, ssb

```
```
daddy@VULCAN:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

```
```
daddy@VULCAN:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
```
daddy@VULCAN:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
```
daddy@VULCAN:~$ lsmod
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166150  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13844  1 
binfmt_misc            17540  1 
snd_hda_codec_conexant    62190  1 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33390  2 
snd_hda_codec         104968  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
nvidia               8107305  37 
joydev                 17693  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
r852                   18277  0 
serio_raw              13166  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
r592                   18144  0 
nand_ids               12723  1 nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
snd                    68266  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53746  0 
nand_ecc               13230  1 nand
k8temp                 13057  0 
memstick               16569  1 r592
edac_mce_amd           23709  0 
mtd                    33181  2 sm_common,nand
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wl                   2568210  0 
nv_tco                 13687  0 
i2c_nforce2            13058  0 
lib80211               14991  1 wl
wmi                    19256  1 hp_wmi
video                  19597  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
forcedeth              67563  0 
pata_amd               14121  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sata_nv                32305  3 

```

Thanks for checking on this, hope my replies help identify the problem.

---

### Post by wildmanne39 on 2012-07-01
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Reboot
Thanks

---

### Post by raymondvillain on 2012-07-01
It works!

Many thanks for your help, wildmanne39!  I am so relieved.

The last set of instructions, when executed, gave a response to the effect that broadcom-sta-common and broadcom-sta-source were never installed and it did remove bcmwl-kernel-source.

Thanks so much!  I'll mark this solved.

---

### Post by wildmanne39 on 2012-07-01
Hi, your welcome!
Enjoy

---

