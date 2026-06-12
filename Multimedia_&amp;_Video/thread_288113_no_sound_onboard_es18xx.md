---
title: "no sound onboard es18xx"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by mardybear on 2006-10-29
Greetings...

I'm new to linux and recently installed Ubuntu on an old system with onboard sound. It's a P2 400 Mhz dual boot system. Win98 installs and uses the sound chip with no problem. I've tried several ubuntu and alsa help pages but still can't get my sound to work. Hopefully i haven't messed up the system too much already...

I've pasted the output of modinfo for my es18xx sound chip below. Is this what i would enter next or are the parameters different: $ sudo modprobe snd_es18xx isapnp=0 port=0x220 mpu_port=0x330 dma1=1 dma2=5 irq=5 fm_port=0x388  ???

Any assistance would be appreciated. I've pasted stuff below. Let me know if you need any more info and what to try next. At one point i was able to get the sound chip device recognized, but it still didn't work. I've read that the es18xx chip is a problem with linux....but it's probably just me! Thanks for your help.

Marty


aplay --list-devices
aplay: device_list:221: no soundcards found...


$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at 44000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-400fffff
        Prefetchable memory behind bridge: 41000000-41ffffff

0000:00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 05)
        Subsystem: Compaq Computer Corporation NC3121 Fast Ethernet NIC (WOL)
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at 40200000 (32-bit, prefetchable) [size=4K]
        I/O ports at 2000 [size=32]
        Memory at 40100000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at 20000000 [disabled] [size=1M]
        Capabilities: <available only to root>

0000:00:0e.0 Network controller: 3Com Corporation 3CRWE777 PCI(PLX) Wireless Adaptor [Airconnect] (rev 02)
        Subsystem: 3Com Corporation 3CRWE777 PCI(PLX) Wireless Adaptor [Airconnect]
        Flags: medium devsel, IRQ 11
        I/O ports at 2080 [size=128]
        Memory at 42000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 2400 [size=64]

0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 2040 [size=16]

0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 2020 [size=32]

0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Rage Pro Turbo AGP 2X
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11
        Memory at 41000000 (32-bit, prefetchable) [size=16M]
        I/O ports at 1000 [size=256]
        Memory at 40000000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 40020000 [disabled] [size=128K]
        Capabilities: <available only to root>


modinfo soundcore
filename:       /lib/modules/2.6.15-27-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92


modinfo es18xx
modinfo: could not find module es18xx
grumpy@grumpy-desktop:~$ modinfo soundcore
filename:       /lib/modules/2.6.15-27-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92
grumpy@grumpy-desktop:~$ modinfo snd-es18xx
filename:       /lib/modules/2.6.15-27-386/updates/alsa/isa/snd-es18xx.ko
author:         Christian Fischbach <fishbach@pool.informatik.rwth-aachen.de>, Abramo Bagnara <abramo@alsa-project.org>
description:    ESS ES18xx AudioDrive
license:        GPL
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:        snd-pcm,snd,snd,snd-opl3-lib,snd-mpu401-uart
alias:          pnp:cESS1868dESS1868dESS0000*
alias:          pnp:cESS1868dESS8601dESS8600*
alias:          pnp:cESS1868dESS8611dESS8610*
alias:          pnp:cESS0003dESS1869dESS0006*
alias:          pnp:cESS1869dESS1869dESS0006*
alias:          pnp:cESS1878dESS1878dESS0004*
alias:          pnp:cESS1879dESS1879dESS0009*
srcversion:     1A2A6AF73D4242CEFFD289F
parm:           dma2:DMA 2 # for ES18xx driver. (array of int)
parm:           dma1:DMA 1 # for ES18xx driver. (array of int)
parm:           irq:IRQ # for ES18xx driver. (array of int)
parm:           fm_port:FM port # for ES18xx driver. (array of long)
parm:           mpu_port:MPU-401 port # for ES18xx driver. (array of long)
parm:           port:Port # for ES18xx driver. (array of long)
parm:           isapnp:PnP detection for specified soundcard. (array of bool)
parm:           enable:Enable ES18xx soundcard. (array of bool)
parm:           id:ID string for ES18xx soundcard. (array of charp)
parm:           index:Index value for ES18xx soundcard. (array of int)

---

### Post by mardybear on 2006-10-31
Nevermind....was able to fix it myself with the help of the forum posts...especially this one if someone's having similar problems:

[http://ubuntuforums.org/showthread.php?t=148077&highlight=es1869+no+sound](http://ubuntuforums.org/showthread.php?t=148077&highlight=es1869+no+sound)

Also had some learning to do, regarding editing files, checking the bios hardware parameters, etc.

Gold star for me   :KS 

Marty

---

