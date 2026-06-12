---
title: "No sound HDA ati alc883"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by talvik on 2007-01-01
Sorry for posting another sound card problem.

I have a ACER Aspire 3660 with hda ati sb alc883 (I think) runnin Kubuntu 6.10. I have followed many instrunctions from posts at this forum and from AlSA's site.

I compiled and installed Alsa-driver lib util both version 1.0.14rc1 and 1.0.13. I tried something I downloaded from realtek(which is basically an automated compilation from alsa files). And I tried ATIIXP FAQ from alsa's site. Everything goes fine until i try to play something.
I didnt forget to unmute in alsamixer. And alsaconf detects this: hda-intel ATI Technologies Inc Unknown device 437b (rev 01)  

Here is some of the stuff you usualy ask:
```
aplay -l:
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lspci -v:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0101
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 217
        Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 217
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: ATI Technologies Inc IXP SB400 USB2 Host Controller
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 217
        Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Acer Incorporated [ALI] Unknown device 0101
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at d0007000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 82 [Master PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 0101
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 209
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: ATI Technologies Inc Unknown device 437b
        Flags: bus master, slow devsel, latency 64, IRQ 209
        Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Acer Incorporated [ALI] Unknown device 0101
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=09, subordinate=0c, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0300000-d03fffff
        Prefetchable memory behind bridge: 20000000-21ffffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0101
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Acer Incorporated [ALI] Unknown device 0101
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at d0200000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Capabilities: <access denied>

09:01.0 CardBus bridge: Texas Instruments Unknown device 8039
        Subsystem: Acer Incorporated [ALI] Unknown device 0101
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at d0310000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=09, secondary=0a, subordinate=0b, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

09:01.2 Mass storage controller: Texas Instruments Unknown device 803b
        Subsystem: Acer Incorporated [ALI] Unknown device 0101
        Flags: bus master, medium devsel, latency 64, IRQ 185
        Memory at d0311000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

09:01.3 Class 0805: Texas Instruments Unknown device 803c (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0101
        Flags: bus master, medium devsel, latency 64, IRQ 185
        Memory at d0312000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0418
        Flags: bus master, medium devsel, latency 168, IRQ 225
        Memory at d0300000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

```
/etc/modules:
 /etc/modules: kernel modules to load at boot time.
lp
snd-atiixp-modem

```


Sorry for the stupid post but I can't go on much longer without amarok.](*,) 
And HAPPY NEW YEAR FOR U ALL

---

### Post by crazy22 on 2007-01-03
Hi!
I had the same problem.....

1.  to  **/etc/modprobe.d/snd-hda-intel.modprobe** I added
options snd-hda-intel model=3stack-6ch

2.  to **/etc/modprobe.d/alsa-base**  I added
options snd-hda-intel model=3stack-6ch 

3.  to **/etc/modules** I added
options snd-hda-intel model=3stack-6ch

Reboot and open alsamixer.
Change <channel> to 6ch.
You have to UNMUTE <PCM>, <SURROUND>, <CENTER>, <LFE>.
Now plug your headphones in to the MIC jack or in Line-in jack and there should be SOUND coming out.

At least I got it working like this.
Hope it helps you too. :D 
Only problem is the Line-out and the laptop speakers won't work. :-k 

Regards,
crazy22

---

### Post by talvik on 2007-01-03
That was some strange solution. But it worked!!!
But I'll keep looking to get it right. I don't need speakers but I want t use the mic in.

Thank You
AmaroK rocks, but I just wished it wouldn't take so long to get some sound

---

### Post by jamaisvu on 2007-08-04
[FONT=Franklin Gothic Medium]Guess what -- I've got this problem too. Just with a twist:[/FONT]

> **crazy22 said:**
> 1.  to  **/etc/modprobe.d/snd-hda-intel.modprobe** I added
options snd-hda-intel model=3stack-6ch

[FONT=Franklin Gothic Medium]This file does not exist.

Anyone know what I've not done?
[/FONT]

---

### Post by jamaisvu on 2007-08-04
Don't worry. I've managed to solve it myself. In case anyone's interested, this is how it worked:

1) downloaded realtek-linux-audiopack-4.06a.tar.bz2 (from some German site or other) (to find it, do K, Run Command, [FONT=Courier New]gg:realtek-linux-audiopack-4.06a.tar.bz2[/FONT])
2) used Ark to extract all the files to a directory
3) opened a Konsole window and cd'ed to that directory
4) [FONT=Courier New]sudo passwd root[/FONT]
5) entered my password three times
6) [FONT=Courier New]su[/FONT]
7) entered my (sorry, root's) password again
8) [FONT=Courier New]./install[/FONT]
9) went and made some coffee
10) drank coffee
11) install finally finished
12) rebooted
13) made another coffee
14) logged in
15) woohoo, it's the KDE welcome sound!

Oh yes, and the sound was coming over this Acer's built-in speakers!

---

### Post by crazy22 on 2007-10-23
There is NO sound problem with 7.10.
Also updating the alsa drivers to version 1.0.14 solves the problems.


Regards,
crazy22

---

### Post by Donny K. on 2007-11-18
If some of you still have problems with your HDA cards you might check this thread: [http://ubuntuforums.org/showthread.php?p=3796486#post3796486](http://ubuntuforums.org/showthread.php?p=3796486#post3796486)

---

