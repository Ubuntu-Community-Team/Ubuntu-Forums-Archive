---
title: "*sigh* Sound is fubar"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by Albi on 2007-03-28
I'll keep this short.
I dual boot windows, I installed a program to mount my linux partition, Windows doesnt shut down properly, I press power button, boot into ubuntu, says drive wasn't unmounted cleanly, starts fscking it, fsck dies with exit status 1, no more sound.

I tried pretty much everything I could find on this forum, and everything SHOULD work, but it doesn't, amarok/totem/xmms just "pretend" to play the song, but no sound comes out and running them in terminal spews no error message.  Speakers are fine, I tested them with the LiveCD.

Anyways, here are the outputs of some commands

```
lbi@albi-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```

albi@albi-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Int
erface (rev 02)
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02
) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc900000-fc9fffff
        Prefetchable memory behind bridge: b7f00000-f7efffff

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Cont
roller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at ef00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Cont
roller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at ef20 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Cont
roller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at ef40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Cont
roller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at ef80 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Con
troller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 193
        Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [No
rmal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fca00000-feafffff
        Prefetchable memory behind bridge: 50000000-500fffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bri
dge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller
 (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at fc00 [size=16]
        Memory at 50100000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 
02)
        Subsystem: ASUSTeK Computer Inc. P4P800 Mainboard
        Flags: medium devsel, IRQ 10
        I/O ports at 0400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) 
AC'97 Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. P4P800 Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at e800 [size=256]
        I/O ports at ee80 [size=64]
        Memory at febff800 (32-bit, non-prefetchable) [size=512]
        Memory at febff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600] 
(prog-if 00 [VGA])
        Subsystem: C.P. Technology Co. Ltd Unknown device 2070
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 177
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at c000 [size=256]
        Memory at fc9f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fc9c0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Second
ary)
        Subsystem: C.P. Technology Co. Ltd Unknown device 2071
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fc9e0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethe
rnet Controller (rev 13)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Contr
oller (Asus)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at feafc000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at d800 [size=256]
        Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio
 Decoder (rev 05)
        Flags: bus master, medium devsel, latency 64, IRQ 209
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
```


Also did the following:
*Reinstalled alsa using the instructions from this thread:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)
I only installed the intel8x0 module

Also pasted this command:
```
sudo modprobe snd-intel8x0
```
but when i do this right after
```
albi@albi-desktop:~$ modinfo snd-intel_8x0
modinfo: could not find module snd-intel_8x0
```

Strange

I also did this, which may have messed it up even more:
```
albi@albi-desktop:~$ sudo asoundconf set-default-card ICH5
```


Alsamixer has everything on as well, shouldn't leave that out.

So is there anything short of a reinstall that can save me?

---

### Post by Albi on 2007-03-28
Kern.log has this output:
```
Mar 25 12:51:33 localhost kernel: [17179574.372000] ICH5: IDE controller at PCI slot 0000:00:1f.1
Mar 25 12:51:33 localhost kernel: [17179574.372000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Mar 25 12:51:33 localhost kernel: [17179574.372000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
Mar 25 12:51:33 localhost kernel: [17179574.372000] ICH5: chipset revision 2
Mar 25 12:51:33 localhost kernel: [17179574.372000] ICH5: not 100%% native mode: will probe irqs later
Mar 25 12:51:33 localhost kernel: [17179574.372000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
```

Edit: Should probably have edited that in...
Edit2: It showed this even before the error

---

### Post by briguy on 2007-04-03
Try modinfo snd-intel8x0

---

