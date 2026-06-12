---
title: "no soundcard detected under dapper with acer aspire 5601AWLMi laptop"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by nikolausi on 2006-08-18
Hi,

installed dapper darke on my notebook and after little work everythings works fine except for the sound.

I followed the hints in thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

The soundcard is not detected.
> nikolaus@nikolaus-laptop:~$ aplay -l
aplay: device_list:221: no soundcards found...


Then i listed all pci devices (see below)
Is *0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)* actually my soundcard?
How do I get the driver? Is this problem likely to be resolved with future Ubuntu updates (The notebook is a quite new model)
thanks in advance, n.

> nikolaus@nikolaus-laptop:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c8100000-c81fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d7f00000
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: 52000000-520fffff
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <available only to root>

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <available only to root>

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 66
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1840 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 66
        Memory at c8004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=56
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: c8300000-c83fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000051f00000
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1880 [size=16]

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7149 (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at c8120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)        Subsystem: Intel Corporation: Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at 52000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at 3000 [size=256]
        Memory at c8300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 168, IRQ 201
        Memory at c8301000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 54000000-55fff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 57, IRQ 10
        Memory at c8302000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:0a:09.3 0805: Texas Instruments: Unknown device 803c (prog-if 01)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0094
        Flags: bus master, medium devsel, latency 57, IRQ 201
        Memory at c8300400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>


---

### Post by snofix on 2006-08-22
There is a known sound-problem with acer notebooks, but usually the sound card should be detected - the problem is just that there is no sound when trying to play a file.
The problem seems to be solved allready, have a close look at this thread:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2104)

But back to your problem:
Did you allready check if the sound-modules are loaded?
try "lsmod" and see if there any modules loaded starting with snd.
If not try to execute "modprobe snd-hda-intel"

Or you can try to reconfigure your soundcard using the "alsaconf" command.

---

### Post by quail-linux on 2006-08-31
Hi,
I have the same laptop and i found this page very helpful to getting my sound running [http://ubuntuforums.org/showthread.php?t=202555&page=5](http://ubuntuforums.org/showthread.php?t=202555&page=5)

---

