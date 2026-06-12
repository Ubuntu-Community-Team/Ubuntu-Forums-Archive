---
title: "Major sound issues, possibly self-inflicted"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by Yoshiman007 on 2007-09-30
I have been using Ubuntu for about half a year now, and have had many a sound/video problem in the past. However, most were fixable through some simple menu or option changing. But now, through a cruel twist of fate (probably WINE), I have f****d up my sound, and i apologize, but there is no better fitted word for what has happened...My current working theory is that the sound was turned down at some point in WINE, but i didn't realize that until today. In the two weeks that I have been trying to fix the problem, i have tried to reinstall/rebuild/recompile/reconfigure anything having to do with my sound. And now I have reached this point where I am out of options, hence the posting. I am not clear on what i should be posting for your analysis, but aplay -l and lspci -v would be a good start.

I'm running a IBM Thinkpad T43 with on board Sound(looks like ICH6 to me, but that's really up to you), Ubuntu Fiesty, and i use Compiz-fusion and Wine if that helps....

aplay -l gives:
```
jgrover@jgrover-laptop:~$ aplay -l
aplay: device_list:222: no soundcards found...

```
lspci -v gives(not gonna bold anything, i'm not positive if the sound is listed or not...might be Multimedia audio controller):
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: IBM Unknown device 0575
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 0582
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at 90080000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at b0000000 (32-bit, prefetchable) [size=256M]
        Memory at 90000000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: IBM Unknown device 0582
        Flags: fast devsel
        Memory at 30000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: 90100000-901fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 90200000-902fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000c00fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0565
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0565
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0565
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 0565
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: IBM Unknown device 0566
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at 90040000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=07, sec-latency=64
        I/O behind bridge: 00004000-00007fff
        Memory behind bridge: 90300000-9fffffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
        Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: IBM Unknown device 0567
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at 90040800 (32-bit, non-prefetchable) [size=512]
        Memory at 90040400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: IBM Unknown device 0576
        Flags: medium devsel, IRQ 19
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: IBM Unknown device 0568
        Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: IBM Unknown device 056a
        Flags: bus master, 66MHz, medium devsel, latency 0
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: IBM Unknown device 056b
        Flags: medium devsel, IRQ 11
        I/O ports at 18a0 [size=32]

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
        Subsystem: IBM Unknown device 0577
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at 90100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

04:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: IBM ThinkPad R40e (2684-HVG) Cardbus Controller
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at 90300000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=04, secondary=05, subordinate=06, sec-latency=176
        Memory window 0: c8000000-cbfff000 (prefetchable)
        Memory window 1: 94000000-97fff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

04:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 1010
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at 90301000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

```

let's throw in the asoundconf -list:
```
jgrover@jgrover-laptop:~$ asoundconf -list
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card CARD
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio

```

Well, i've been stumped for a week or so on this, followed many a guide (including the "Comprehensive"-ish one). So in my act of desperation, i come here...anything will be greeted with great appreciation, and any instructions/information getting will be followed as quickly as i can manage. Specific instructions would be extra appreciated, I've only gotten used to the terminal in the past three months.

---

### Post by Yoshiman007 on 2007-10-01
I hate to bump...but does anyone have anything on these sound issues? Seems like many people have the same problems, but with no fix...Anyone? Anything?

---

