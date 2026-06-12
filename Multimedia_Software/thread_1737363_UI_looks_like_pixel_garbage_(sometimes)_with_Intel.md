---
title: "UI looks like pixel garbage (sometimes) with Intel GMA i965"
date: 2011-04-23
forum: Multimedia Software
---

### Post by lazlo on 2011-04-23
Hi *,

I have a [Lenovo Thinkpad X201 Tablet]("http://www.thinkwiki.org/wiki/Category:X201_Tablet") with a Intel HD Graphics adapter running **Ubuntu 10.10** (maverick) for **x86_64**.

Recently I have expirenced problems related to drawing the gnome/gtk UI widgets on the screen. It's a bit hard to describe, it shows *pixel garbage* where icons in the UI should/have been. Checkout my **screen shot** to get a idea. The first effects of the problem can be seen when the system has booted and displays the GDM login window.
What makes puzzles me a bit is the fact that the problem show more often when I run on batteries / without power supply attached.

Worse: the problem is not always visible( like 1 of 5 times i boot the system)

(Obviously) I'm running Xorg/Gnome/Metacity/GTK as most Ubuntu users do.

Please let me know what other kind of information might be helpful.

Here the output of "lspci":

```
lazlo@siru:~$ lspci -vvv -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 215a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 45
	Region 0: Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 1800 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
```

Versions of Xorg and Intel drivers:
```
lazlo@siru:~$ dpkg-query -W xorg xserver-xorg-video-intel
xorg	1:7.5+6ubuntu3
xserver-xorg-video-intel	2:2.12.0-1ubuntu5.2
```

I already check the Xorg.log and could verify Xorg is using the "intel" driver module.. but no more than that.

Thanks in advance!

Lazlo

---

### Post by lazlo on 2011-05-30
Small update: Problem only comes up when running on batteries. Problem is gone when laptop lid is closed / system goes into suspend and resumes. After this procedure the graphical output is okay again.

Also added a new screenshot that shows the problem.

---

