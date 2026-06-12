---
title: "Alsamixer Doesn't Work, And Neither Does My Sound"
date: 2008-09-02
forum: Multimedia Software
---

### Post by Kgamer on 2008-09-02
Hey, I'm quite new to Linux, and for the past year of usng Kubuntu 7.10 and 8.04, no one has been able to get my sound working.

First of all, my sound isn't working, Im Running a Ei Systems 485 With Kubuntu 8.04, and Windows XP Dual-Boot. My soundcard is an on-board Realtek AC'97, and It doesn't seem to be working. I followed [this guide](http://ubuntuforums.org/showthread.php?t=205449) to install the Driver, but it doesn't seem to have worked, and i'll post my results:

Step 1: ```
aplay -l
```
Result: ```
aplay: device_list:205: no soundcards found...
```

Step 2: ```
lspci -v
```
Result:  (I Bold Italic and Underlined My sound card)```
Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
        Memory at <ignored> (64-bit, non-prefetchable)
        Capabilities: <access denied>

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Memory at 40000000 (32-bit, prefetchable) [size=64M]
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <access denied>

00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fdffe000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 44000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at fa00 [size=8]
        I/O ports at f900 [size=4]
        I/O ports at f800 [size=8]
        I/O ports at f700 [size=4]
        I/O ports at f600 [size=16]
        Memory at fdffd000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 44080000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fdffc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fdffb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fdffa000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: 66MHz, medium devsel
        I/O ports at 0500 [size=16]
        Memory at fdff9000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f400 [size=16]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: fdc00000-fdcfffff

[b][i][u]00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
        Subsystem: Foxconn International, Inc. Realtek ALC 653
        Flags: 66MHz, slow devsel, IRQ 20
        Memory at fdff8000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>[/b][/i][/u]

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200] (prog-if 00 [VGA controller])
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 20
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at ee00 [size=256]
        Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fde00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Foxconn International, Inc. Unknown device 0c81
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at de00 [size=256]
        Memory at fddff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```

Step 3: My soundcard Driver is listed [HERE](http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI)

Step 4: ```
sudo modprobe snd-(+Tab)
```
Result: ```
Display all 159 possibilities? (y or n)
snd-ac97-codec      snd-es1938          snd-pcm-oss
snd-ad1816a         snd-es1968          snd-pcsp
snd-ad1848          snd-es968           snd-pcxhr
snd-ad1848-lib      snd-fm801           snd-pdaudiocf
snd-ad1889          snd-gina20          snd-pdplus
snd-adlib           snd-gina24          snd-portman2x4
snd-ak4114          snd-gusclassic      snd-pt2258
snd-ak4117          snd-gusextreme      snd-rawmidi
snd-ak4531-codec    snd-gus-lib         snd-riptide
snd-ak4xxx-adda     snd-gusmax          snd-rme32
snd-ali5451         snd-hda-intel       snd-rme96
snd-aloop           snd-hdsp            snd-rme9652
snd-als100          snd-hdspm           snd-rtctimer
snd-als300          snd-hifier          snd-sb16
snd-als4000         snd-hwdep           snd-sb16-csp
snd-asihpi          snd-i2c             snd-sb16-dsp
***_snd-atiixp**_*          snd-ice1712         snd-sb8
snd-atiixp-modem    snd-ice1724         snd-sb8-dsp
snd-au8810          snd-ice17xx-ak4xxx  snd-sbawe
snd-au8820          snd-indigo          snd-sb-common
snd-au8830          snd-indigodj        snd-sc6000
snd-azt2320         snd-indigoio        snd-seq
snd-azt3328         snd-intel8x0        snd-seq-device
snd-bt87x           snd-intel8x0m       snd-seq-dummy
```

Step 5: ```
sudo modprobe snd-atiixp
```
Result: ```
liam@ubuntu:~$   
```



Also, my Alsamixer doesn't work;

When I try to run it from the Konsole, all i get is: 
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```
I've tried uninstalling and re-installing it, but to no avail. Can anyone help? It would be GREATLY appreciated....

Kgamer.

---

### Post by prshah on 2008-09-02
> **Kgamer said:**
>  for the past year of usng Kubuntu 7.10 and 8.04,
my sound isn't working,  My soundcard is an on-board Realtek AC'97,

Step 1: Is sound enabled in your BIOS? Easy check: does sound work in Windows? Difficult way: Check BIOS.

---

### Post by Kgamer on 2008-09-02
yep it works in windows, no problem.

---

### Post by prshah on 2008-09-02
> **Kgamer said:**
> yep it works in windows, no problem.

Can you post the output of ```
lsmod | grep -i soundcore
modinfo soundcore
```

---

### Post by Kgamer on 2009-01-18
Hey, sorry about not replying. Yeah, this is my output:

```
liam@Kubuntu-PC:~$ lsmod | grep -i soundcore
soundcore              15328  0
liam@Kubuntu-PC:~$ modinfo soundcore
filename:       /lib/modules/2.6.27-9-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586
liam@Kubuntu-PC:~$

```

---

### Post by markbuntu on 2009-01-18
There are some options for the AC'97 and you may need to add one to the /etc/modprobe.d/alsa-base to get that to work. The most common is

options snd_atiixp model=quirk

There is more on that in this file which you will find on your machine

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

---

### Post by Kgamer on 2009-01-19
Great, I'll give it go, and see what happens

---

