---
title: "Gateway ML6732 Sound problems"
date: 2008-08-31
forum: Multimedia Software
---

### Post by drozel on 2008-08-31
I have spent the last week going through the forums and the Comprehensive Sound Problem Solutions Guide, but have not found a solution.

About eight days ago, my sound stopped working. It had worked fine for at least three months before that. I went through the Guide and got to the "aplay" and "lspci" parts and found no sound cards even though my sound card is integrated into the laptop. There is no option in BIOS to disable or enable it.

My laptop is an out-of-the-box Gateway ML6732. I will provide any information that is needed.

---

### Post by minky311 on 2008-08-31
What happens when you type the following two things into terminal
```
cat /proc/asound/cards
```
And
```
cat /proc/asound/modules
```

---

### Post by drozel on 2008-08-31
```
root@michael-laptop:~# cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
root@michael-laptop:~# cat /proc/asound/modules
cat: /proc/asound/modules: No such file or directory
root@michael-laptop:~# 

```

---

### Post by minky311 on 2008-08-31
Could you reboot your computer and press F2 repeatedly to get into the bios and tell me what it says for your onboard sound.
Also what does it output in terminal when you type in asoundconf list

---

### Post by drozel on 2008-08-31
I couldn't see anything that said anything about sound in BIOS.


Here is "asoundconf list"
```
root@michael-laptop:~# asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

root@michael-laptop:~# 

```

---

### Post by minky311 on 2008-08-31
When you go to system->preferences->sound under playback is alsa listed as an option?

---

### Post by drozel on 2008-08-31
Yes, ALSA is listed

---

### Post by drozel on 2008-09-02
*bump*

---

### Post by minky311 on 2008-09-02
Could you post the output of
```
lspci -v
```
and of 
```
lsmod | grep snd
```

---

### Post by drozel on 2008-09-02
```
root@michael-laptop:~# lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, fast devsel, latency 0
	Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at f0704800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: 00000000f0800000-00000000f08fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0368
	Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0300000-f03fffff
	Prefetchable memory behind bridge: 00000000f0900000-00000000f09fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0368
	Capabilities: [a0] Power Management version 2

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Gateway 2000 Unknown device 0368
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f0704c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
	Capabilities: [50] Subsystem: Gateway 2000 Unknown device 0368

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f0704000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: medium devsel, IRQ 10
	Memory at c2100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, fast devsel, latency 0, IRQ 220
	I/O ports at 4000 [size=256]
	Memory at f0400000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] Express Endpoint IRQ 0
	Capabilities: [84] Vendor Specific Information

```

and

```
root@michael-laptop:~# lsmod | grep snd
root@michael-laptop:~# 

```

Respectively

---

### Post by minky311 on 2008-09-02
Go into the terminal and type the following
```
sudo modprobe snd-hda-intel
```
If everything goes as planned when you type in
```
cat /proc/asound/modules

```
It should show up.

---

### Post by drozel on 2008-09-03
Thank you very much. I had to install the kernal sound modules found here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). THen I did as you said, and it works to some extend. No YouTube sound or Totem sound, but other sounds work. I'll be back if I can't get the others to work, but I feel I can get it. Thank you eternally.

---

