---
title: "New member to the &quot;no headphone sound&quot; club. Help?"
date: 2009-03-14
forum: Multimedia Software
---

### Post by magnoliasouth on 2009-03-14
I have searched high and low, but I'm sorry. I just cannot follow a lot of what is being explained here.

First off I read, and attempted to follow, the **[Comprehensive Sound Problems Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")**. The immediate problem there is that the post does not appear to have been updated and isn't current.  For example, the link they provide in #3 is broken and I couldn't find what he described at the main site. Personally, it probably shouldn't remain a sticky if it's out of date, or it could be updated again (with dates included?). In any case, my point is that it didn't help. Sorry for the ramble there.

I've read a number of other posts with similar problems of my own. None of their fixes appear to help me, or if they do, I cannot find them.

So the problem is that when I plug in the headphones, the sound output continues through my speakers AND there is no sound in the headphones at all.

In the Alsa Mixer, the Headphone Jack Sense **[COLOR="Blue"]is checked[/COLOR]**.

I've see a lot of posts on finding out what sound card and whatever else there is, so I'll post it here in case anyone needs to know.

I'm running Hardy Heron, if it matters. The code is below of steps 1 & 2 in the Comprehensive post. So.... Can anyone help me?

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
	Flags: bus master, fast devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA controller])
	Subsystem: IBM NetVista A30p
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 88000000 (32-bit, prefetchable) [size=128M]
	Memory at 80000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM NetVista A30p
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM NetVista A30p
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM NetVista A30p
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: IBM NetVista A30p
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at c0080000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c0100000-c01fffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: IBM NetVista A30p
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1860 [size=16]
	Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: IBM NetVista A30p
	Flags: medium devsel, IRQ 9
	I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: IBM NetVista A30p
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at c0080c00 (32-bit, non-prefetchable) [size=512]
	Memory at c0080800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
	Subsystem: IBM NetVista A30p
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at c0100000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2000 [size=64]
	Capabilities: <access denied>
```

---

### Post by markbuntu on 2009-03-14
There is comprehensive troubleshooting help here. The soluton to your problem is very hardware specific (ie depends on make and model of your machine). Look in the drivers HDA section. If you are lucky there is a fix for your specific machine.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by magnoliasouth on 2009-03-15
Yikes. Do you mean the drivers HDA section in the link you provided? Perhaps HDA sound chips?

If so, I don't see mine listed, or at least I don't think I do. Judging from what I see in my stuff above, I believe mine to be a ICH4? 

I really do not understand what I'm supposed to be looking for. :(

---

### Post by markbuntu on 2009-03-15
OOOPs, yours is a AC'97. Look at the bottom of the **drivers** section. there is a note about the AC'97 and its driver

---

### Post by magnoliasouth on 2009-03-15
First off, WOW! =D> to you. I didn't realize that you were the one who wrote that until just now. Thank you so very much for trying to help this illiterate user. :oops:

Let's see, should I post remaining questions here? Or id it preferred that I post them over there? 

For now, am I then supposed to open this file
/[COLOR="Blue"]user[/COLOR]/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz
and use the HDA sound chip tweaks? Or skip opening the file? 

If so, is that blue part the home folder or my name? 

I really do apologize and am grateful for your patience. I am a previous Windows user and while I could do minor tweaks and fixes, that would be all I could do. Reading something like all of that is particularly overwhelming and I'm very sorry for my super newb status.

**[COLOR="Green"]ETA: Oops. I just now noticed that both suggest the same file, so I'm guessing my answer is yes. Sorry about that. I suppose any file manager will open a .gz file? Well I have to run some errands, but will try it this evening. Thanks again![/COLOR]**

---

