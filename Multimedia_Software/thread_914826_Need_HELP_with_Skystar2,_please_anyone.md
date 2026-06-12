---
title: "Need HELP with Skystar2, please anyone?"
date: 2008-09-09
forum: Multimedia Software
---

### Post by lukin on 2008-09-09
Hi there!
i love your efforts you`re providing for the community, so i thought i could use a little help myself, well i have DVB-S cars SKYSTAR2 rev 2.6 D
so i hoping that you guys help me out here
how do i get my ubuntu system to recognize my Skystar2?
how do i install it, do i need any drivers for that?
what app do i need to use to watch satellite channel? before i made the move from Vista, i was between DVBviewer and Skyview, so is there any good or powerful app out there for ubuntu to use with my Skystar2?

and by the way the sudo lspci command returns something like the following

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 662 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA (rev 01)
00:0a.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

and i`m on ubuntu Hardy Heron 8.04 LTS fully updated and running fast thank GOD for this little wonder!! i love it.

so any help would be so much appreciated
love you guys

---

### Post by xc3RnbFO8P on 2008-09-09
> how do i get my ubuntu system to recognize my Skystar2?
how do i install it, do i need any drivers for that?
It might work out of the box. 
> is there any good or powerful app out there for ubuntu to use with my Skystar2?
Try Kaffeine its in Add/Remove (all available application).
If it doesnt work show the output of **lspci -vn**

---

### Post by lukin on 2008-09-10
thanks for getting back to me but after downloading all the packages that come with Kaffeine and installed it, i get nothing, are there any steps further required prior to using the app, i certainly don`t know my way around this, i need help so please!

and the output of the command lspci -vn gives out something like the following
00:00.0 0600: 1039:0662 (rev 01)
	Flags: bus master, medium devsel, latency 64
	Memory at c0000000 (32-bit, non-prefetchable) [size=512M]

00:01.0 0604: 1039:0004 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fc000000-febfffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000bfffffff
	Capabilities: <access denied>

00:02.0 0601: 1039:0964 (rev 36)
	Flags: bus master, medium devsel, latency 0

00:02.5 0101: 1039:5513 (rev 01) (prog-if 80 [Master])
	Subsystem: 1019:1631
	Flags: bus master, medium devsel, latency 128
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at fff0 [size=16]
	Capabilities: <access denied>

00:02.7 0401: 1039:7012 (rev a0)
	Subsystem: 1019:1b13
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at dc00 [size=256]
	I/O ports at d800 [size=128]
	Capabilities: <access denied>

00:03.0 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
	Subsystem: 1019:1631
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]

00:03.1 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
	Subsystem: 1019:1631
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fbffe000 (32-bit, non-prefetchable) [size=4K]

00:03.2 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
	Subsystem: 1019:1631
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fbffd000 (32-bit, non-prefetchable) [size=4K]

00:03.3 0c03: 1039:7002 (prog-if 20 [EHCI])
	Subsystem: 1019:1631
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at fbffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.0 0200: 1039:0900 (rev 90)
	Subsystem: 1019:1631
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at d400 [size=256]
	Memory at fbffb000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: <access denied>

00:05.0 0101: 1039:0181 (rev 01) (prog-if 85 [Master SecO PriO])
	Subsystem: 1019:1631
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at d000 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at c800 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c000 [size=16]
	I/O ports at bc00 [size=128]
	Capabilities: <access denied>

00:0a.0 0280: 13d0:2103 (rev 02)
	Subsystem: 13d0:2103
	Flags: bus master, slow devsel, latency 64, IRQ 22
	Memory at fbfe0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at b800 [size=32]

01:00.0 0300: 10de:0393 (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at a0000000 (64-bit, prefetchable) [size=512M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at febe0000 [disabled] [size=128K]
	Capabilities: <access denied>

---

### Post by xc3RnbFO8P on 2008-09-11
This is your tuner:
> 00:0a.0 0280: 13d0:2103 (rev 02)
Subsystem: 13d0:2103
Flags: bus master, slow devsel, latency 64, IRQ 22
Memory at fbfe0000 (32-bit, non-prefetchable) [size=64K]
I/O ports at b800 [size=32]
Information from linuxtv [TechniSat SkyStar 2 TV PCI / Sky2PC PCI]("http://www.linuxtv.org/wiki/index.php/TechniSat_SkyStar_2_TV_PCI_/_Sky2PC_PCI")

Acording to this site:
[http://wiki.ubuntuusers.de/B2C2]("http://wiki.ubuntuusers.de/B2C2")
Try this first:
> Sudo modprobe stv0299
and try Kaffeine.
If it dont work:
> sudo gedit /etc/modules
add these 2 lines:
> Budget
stv0299
Save and restart the computer and try Kaffeine.
Sill dont work.
Open gedit again and copy/paste this:
> #!/bin/bash
#/etc/init.d/dvb
rm -rf /dev/ost
rm -rf /dev/dvb
#for major and minor devicenumber see here
#vi /usr/src/linux/Documentation/devices.txt
cd /dev
mkdir dvb
chmod 755 /dev/dvb
cd dvb
mkdir adapter0
cd adapter0
mknod -m 0660 frontend0 c 212 3
mknod -m 0660 demux0 c 212 4
mknod -m 0660 dvr0 c 212 5
mknod -m 0660 ca0 c 212 6
chown root.video /dev/dvb/adapter0/*''
chmod 744 /etc/init.d/dvb

save it as /etc/init.d/**dvb**
Restart the computer and:
> sudo update-rc.d dvb defaults

Try kaffeine again.

---

### Post by ragip on 2008-09-12
what is the result?
i wonder because i want to get rid of windows on my other computer which has a dvb card :)

---

### Post by lukin on 2008-09-13
well i tried eveything as stated above but unfortunately down the drain, what the hell!
i just don`t get it, why does it have to be so ******* hard to configure a friggin` little device on a system i totally adore.
too bad didn`t work out, sorry for all you guys checking the thread in hopes of a better workaround to this ****!
but i still gotta say that it doesn`t hurt to mention that when i issued the first command "Sudo modprobe stv0299"
it returned a no-way "bash: Sudo: command not found"
so if you guys can decipher anything, please!
willing to try anything here so keep`em coming 
hear from ya soon!
love y`all!

---

### Post by ragip on 2008-09-15
after a quick research i ve found, my tv card, Avermedia dvb-s pro is not supported (yet)
it is sad :(

---

### Post by Blonddeeni on 2008-11-18
Errrr, Lukin.
I'm not sure if this'll help, but did you use a capital "S" for your sudo command? It's meant to be a lowercase "s", but not sure if your post is a capital because of the way we type in a post, or if that was the actual command you used. 
Uppercase / lowercase = command not found. Been there, done (keep doing) that. :)
Sorry but no help on the skystar card. I have one and it works sweet, but then I'm using Mythbuntu. 
Cheers.
Blonddeeni.

---

