---
title: "pppconfig does not detect modem w/hardware controller"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by StuartZ on 2009-11-17
I have an actiontec electronics device 0480 which lists on lspci but does not get detected by pppconfig nor gnome-ppp.  As far as I can tell this modem has an onboard controller.  I'm too new and stumped.   karmic32 9.10

---

### Post by StuartZ on 2009-11-18
This modem is supposed to work with serial_devices module.  How do I activate it or get it working?

---

### Post by StuartZ on 2009-11-19
Why does it say <access denied> after capabilities?

lspci -vv output:

00:03.0 Communication controller: Agere Systems Venus Modem (V90, 56KFlex)
	Subsystem: Actiontec Electronics Inc Device 0480
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (63000ns min, 3500ns max)
	Interrupt: pin A routed to IRQ 3
	Region 0: Memory at 44000000 (32-bit, non-prefetchable) [size=256]
	Region 1: I/O ports at 1c00 [size=256]
	Region 2: I/O ports at 2000 [size=256]
	Region 3: I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: serial

---

### Post by StuartZ on 2009-11-21
OK, so I figured out I need to use sudo lspci -vv for access..  It istalking to it and serial driver is running, but pppconfig and gnome ppp can not auto detect it.  Help!

---

### Post by hoss2001 on 2009-12-17
I had this all typed and the message board refused to send. Hope I get in everything I had the first time. First you need to run wvdialconf to find out which port your modem is on. It'll look something like ttyS0, ttyS1, ttyS2 etc. wvdialconf should also return and init string. you'll need both the init string and port number for pppconfig. Check the site [www.modemhelp.net](www.modemhelp.net) to find their recommend init string. I found their's a lot closer to one from windoze query. Also they have a page that tells about basic AT commands. Now when you get to the autodetect part of pppconfig, you should have the option for manual setup. On the port number page, you'll change to the port returned by wvdialconf. After you've finished manual setup, from the main page, open advanced options. The init string will show ATZ with the recommendation to leave it as is. I know from experience that ATZ turns off every US Robotics modem I've tried. You can try it, but my advice is to get as close as possible to factory recommended string. It''ll start like AT&F ...or something similar.
If wvdialconf doesn't return a port number your modem may not be full hardware, and you'll need a driver.
Hope this helps, but you may need more info. I'm still a linux newbie myself.

---

