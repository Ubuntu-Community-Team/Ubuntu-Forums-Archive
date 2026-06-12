---
title: "wireless help on wubi ubuntu 11.10"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by Moose187 on 2012-04-23
ok, my desktop and laptop are both having problems connecting to wireless, my desktop's ethernet port is broken so i have a dlink wireless usb reciever model DWA-130 and it doesnt even register that it exists. now my laptop i can do terminal on that version for some weird reason and i dont remember the specifics but it says i have a valid card but no matter what i do it says wireless is disabled. is there any advice or guide that may help my predicament?:confused:

thanks in advance if i dont reply, kinda hard to when both pc's are down internet wise. :lolflag:

---

### Post by wildmanne39 on 2012-04-23
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Moose187 on 2012-04-23
hey thanks man, ill try that out when i get home and see if i can get it working. and how do i get terminal to come up on my desktop? it doesnt have the option or icon anywhere.

---

### Post by wildmanne39 on 2012-04-23
Hi, those command will give us the information needed to help you and you can open the terminal with ctrl+alt+t.
Thanks

---

### Post by Moose187 on 2012-04-23
> **wildmanne39 said:**
> Hi, those command will give us the information needed to help you and you can open the terminal with ctrl+alt+t.
Thanks

i have just one question, do i do each line seperate or just when i am prompted with the ability to enter the command line?
 
and sorry for replying with questions, im new to a linux based anything, but so far you guys are being more helpful then microsoft when i tried to ask how to fix my win7 when it runs like its overclocked (always running 100%cpu and keeps overheating) thats why i installed ubuntu with windows so i can see if its my comp or something with windows... plus i like ubuntu.

---

### Post by wildmanne39 on 2012-04-23
Hi, one line at a time.
Thanks

---

### Post by Moose187 on 2012-04-23
ok so i tried this one first(cat /etc/lsb-release; uname -a) and this is what i got;

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

the second one(lspci -nnk) got me this;00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: i915
	Kernel modules: intelfb, i915
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel modules: i2c-i801
01:04.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20]
	Subsystem: Conexant Systems, Inc. Soft Data Fax Modem with SmartCP [14f1:200c]
01:05.0 Multimedia audio controller [0401]: Creative Labs [SB Live! Value] EMU10k1X [1102:0006]
	Subsystem: Creative Labs Device [1102:1003]
	Kernel driver in use: EMU10K1X
	Kernel modules: snd-emu10k1x
01:05.1 Input device controller [0980]: Creative Labs [SB Live! Value] Input device controller [1102:7004]
	Subsystem: Creative Labs Device [1102:1003]
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:2a59]
	Kernel driver in use: r8169
	Kernel modules: r8169

next one (lsusb) got this;Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 003: ID 07d1:3a08 D-Link System predator Bootloader Download

the next one(iwconfig) was this:
lo        no wireless extensions.

eth0      no wireless extensions.

and the next one after that was rfkill list all which did nothing

the last one was lsmod: which i got this:
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40253  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_emu10k1x           24294  2 
snd_ac97_codec        134826  1 snd_emu10k1x
snd_pcm                96755  2 snd_emu10k1x,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_emu10k1x,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  11 snd_emu10k1x,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
i915                  566711  3 
psmouse                73882  0 
soundcore              12680  1 snd
emu10k1_gp             12650  0 
serio_raw              13166  0 
ac97_bus               12730  1 snd_ac97_codec
gameport               19693  2 emu10k1_gp
snd_page_alloc         18529  2 snd_emu10k1x,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 

btw i have no clue what any of this means really lol but am willing to learn. and thanks for helping a noob like me

---

### Post by wildmanne39 on 2012-04-24
Hi, it looks like you need ndiswrapper with a windows driver, do you have the disc that came with the wireless adapter?

Here is a link to help.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Thanks

---

### Post by Moose187 on 2012-04-24
i actually do but it wont do anything by itself, ive tried to run it but nothing and i can open it though and there is a folder called drivers in there, right now im at work though so it may not be til tomorrow until i can post the contents of the folder, but if you know a way to fix it ill try asap!

and thanks again for your help

---

### Post by wildmanne39 on 2012-04-24
Hi, you need to read the link I gave you it tells you how to use the drivers from the disc or you can download them.

If you need help let us know where you have a problem at and we will help you.

I have not use ndiwrapper in many years so I am a little rusty but I am going to install it just for the practice.
Thanks

---

