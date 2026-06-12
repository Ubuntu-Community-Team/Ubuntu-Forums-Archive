---
title: "Choppy sounds"
date: 2008-12-28
forum: Multimedia Software
---

### Post by RandumKiwi on 2008-12-28
I'm having major issues with my sounds being really choppy/slow whenever it plays. I've looked everywhere for a solution, but I can't find anything. I've even tried following this thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) ...but no solution.

Any help would be much appreciated, thanks

I'm running a Toshiba satellite M50  

Here's the specs:

```
randum@Gremlin:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff00
	Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ATI Technologies Inc Device 5a31
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: 66MHz, medium devsel
	I/O ports at 8400 [size=16]
	Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8410 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=04, subordinate=08, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: c0200000-c02fffff
	Prefetchable memory behind bridge: 50000000-53ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at c0003400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ATI IXP AC97 controller
	Kernel modules: snd-atiixp

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at c0003800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ATI IXP MC97 controller
	Kernel modules: snd-atiixp-modem

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 17
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: fglrx_pci
	Kernel modules: radeonfb, fglrx

04:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: Askey Computer Corp. Device 7094
	Flags: bus master, medium devsel, latency 168, IRQ 21
	Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci

04:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at c0211000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 0000a400-0000a4ff
	I/O window 1: 0000a800-0000a8ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

04:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at a000 [size=256]
	Memory at c0210000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too
```

```
randum@Gremlin:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
randum@Gremlin:~$ speaker-test 

speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 30.100764
 0 - Front Left
Time per period = 30.056097
 0 - Front Left
```

---

### Post by RandumKiwi on 2008-12-28
*bump*

---

### Post by mlegge on 2008-12-28
Double bump:)

I too have a Toshiba Satellite Pro M50, and have exactly the same problem.

---

### Post by RandumKiwi on 2008-12-29
Updating alsa to the latest version didn't help...

[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

---

### Post by RandumKiwi on 2008-12-29
Note: In an effort to figure out what's wrong, I've even resorted to wiping my pc, and reinstalling ubuntu, but the issue still exists.


EDIT: Nevermind, since I've completely wiped my computer, I thought I'll just use big brother debian instead, now I'm having no problems after setting up pulse. None at all :)

---

### Post by tiffmc on 2009-02-10
I'm having the exact same problem. It is driving me insane. I have no idea how to fix it :(

---

### Post by gcranston on 2009-03-15
I had similar choppy audio.  I think it _may_ be fixed now by bumping up the priority of the pulseaudio process, and killing mprime (background process using spare cpu cycles   [www.mersenne.org](www.mersenne.org)).

I will be trying these independently to see what happens, but at least I"m not tearing my hair out every time (I Can't Get No) Satisfaction skips on me...

---

### Post by markbuntu on 2009-03-16
Check that your users and root are members of the following groups which you can check in System/Administration/Users and Groups.
pulse
pulse-rt
pulse-access
This should fix the priority problem but if it does not you can also uncomment these lines in /etc/pulse/daemon.conf
```

; high-priority = yes
; nice-level = -11

```
You can also edit these lines in the file /etc/pulse/daemon.conf to look like this
```

default-fragments = 5
default-fragment-size =25

```

You can play around with these numbers to find the best ones for your machine.

Don't forget to logout/login for the group settings to take effect. You can stop and restart pulse from a terminal 
```

killall pulseaudio

pulseaudio -D

```

If you are still having problems you can run pulseaudio in verbose mode from a terminal and look at the messages
```

killall pulseaudio

pulseaudio -vvv

```

---

### Post by zorkerz on 2009-05-19
Hey their my friends has a toshiba satellite M50 -mx2. Even short sounds are choppy and play for a very very long time. Ive done tried the htings discussed on this thread without any luck. I have also attached the output of pulseaudio in verbose mode. Here I think are the relevant lines.

> E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.sounds works find on this computer in XP. Anyone have any ideas what may be going on?

---

