---
title: "Is my graphics card working?"
date: 2009-10-10
forum: Multimedia Software
---

### Post by jcao219 on 2009-10-10
I am on a Asus 1000HE netbook.
I am dualbooting Windows XP and Ubuntu Netbook Remix.

I can only run it on minimal graphics setting.
On normal, the task bar disappears and the display is messed up.

On windows, I can play some 3d games reasonably well.

My graphics card is a Mobile Intel 945GM express chipset.

---

### Post by damis648 on 2009-10-10
If it works on windows, it should be fine. What setting is the 'normal' setting you set it to?

---

### Post by UpsideDownFace on 2009-10-10
Open a terminal - ( Applications>:Accessories>:Terminal )
Then type "sudo lspci" (without the quotes)
This will give about 10 lines which will include something like "Display" or "VGA"
Then type "sudo lspci -v" and scroll up to the bit you just identified

I did 
 "sudo lspci > lspci.txt
and then
"sudo lspci -v >> lspci.txt"
 and used the text editor to pick out just these bits :-


00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)


00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
	Subsystem: IBM ThinkPad R50e
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Capabilities: [d0] Power Management version 1

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: IBM ThinkPad R50e
	Flags: bus master, fast devsel, latency 0
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at d0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 1

So you can see the display on my laptop is working

---

### Post by jcao219 on 2009-10-10
> **UpsideDownFace said:**
> Open a terminal - ( Applications>:Accessories>:Terminal )
Then type "sudo lspci" (without the quotes)
This will give about 10 lines which will include something like "Display" or "VGA"
Then type "sudo lspci -v" and scroll up to the bit you just identified

I did 
 "sudo lspci > lspci.txt
and then
"sudo lspci -v >> lspci.txt"
 and used the text editor to pick out just these bits :-


00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)


00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
	Subsystem: IBM ThinkPad R50e
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Capabilities: [d0] Power Management version 1

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: IBM ThinkPad R50e
	Flags: bus master, fast devsel, latency 0
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at d0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 1

So you can see the display on my laptop is working

I think my graphics card is working, but I can't understand why Normal visual effects setting doesn't work.

@damis: The setting is when I go to Preferences -> Appearance -> Visual Effects.
I can run minimum, but not normal.  When I set it to normal, it goes "Searching for available drivers..." and then the taskbar disappears.  Everything is mixed up.

---

